!SLIDE section

# Real life examples

!SLIDE

# FEDERICO

<!--
Ejemplo de arquitectura para integrar múltiples aplicaciones
-->

!SLIDE problem

# Problem

## Signup/signin on multiple services
## Consolidate personal info

!SLIDE solution

# Solution

## Orchestrate services through a Service Bus
## Single Sign On

!SLIDE image
< arquitectura ideal >

<!--
Solución ideal:
Federacion de autenticacion
Bus + Adaptadores + Pull+Push + Operaciones WS
Webs diferentes tecnologías consumen WS
-->

!SLIDE image

< arquitectura chapuxera xD >
<!--
Solución de compromiso
Sólo Pull, Tareas periódicas
Adaptadores: BD, LDAP, WS, Comandos SSH, etc.
-->

!SLIDE bullets

# Technology

* Java stack
* Ruby for automation

<!--
Herramientas de build y despliegue específicas: Rake
-->

!SLIDE

# NeoSAI

!SLIDE problem

# Context

## Laboratory Management System

!SLIDE image

< arquitectura de NeoSAI new >


!SLIDE problem

# Problem

## Different kinds of UIs

!SLIDE solution bullets

# Solution

* Basic CRUD: forms & listings
* Advanced CRUD: JS components + AJAX
* Complex tasks: Single-page app + REST


!SLIDE problem

# Problem

## Integrate new & legacy app


!SLIDE solution bullets

# Solution

* Shared DB
* REST APIs (JSON preferred)
* SSO
* UI integration via IFrame + HTML5 PubSub

!SLIDE image

< diagrama arq neosai, a nivel apps y frames >

!SLIDE problem

# Problem

## Integrate "nonintegrable" third party software

!SLIDE solution

# Solution

## Ad hoc REST API

!SLIDE image

< diag testo WAMP mierda ad hoc cona >

!SLIDE problem

# Problem

## Mail log: different sources

!SLIDE solution

# Solution

## Wrapper + REST API

< diagrama >
<!--
  ventaja, no tenemos que tocar las aplicaciones, SRP
  desventaja, rendimiento
-->

!SLIDE problem

# Problem

## Complex permission checks

!SLIDE solution

# Solution

## Policy objects

!SLIDE

# Can change a report if I am the author or its author is one of my subordinates and the report has not been signed

!SLIDE code

    @@@ ruby

    class ReportsController
      def edit
        report = Report.find(params[:id])
        can_edit = ReportEditorPolicy.
          new(current_user, report).comply?
        ...

!SLIDE code

    @@@ ruby
    class ReportEditorPolicy < Policy
      def initialize(user, report)
        ...
      end

      def comply?
        (owner_of_report? or
        subordinate_report?) and
        unsigned_report?
      end

      ...


!SLIDE problem

# Problem

## Run the same business logic from different places

!SLIDE solution

# Solution

## Context objects
## Runnable from controllers, console, APIs, cron jobs

!SLIDE code

    @@@ ruby
    class CreateUserContext
      def initialize(user_params, notifier)
        ...
      end

      def run
        user = User.new(user_params)
        if user.save
          notifier.send(:new_user, user)
        end
      end
    end




!SLIDE problem

# Problem

## Run business logic as different users, even as no user

!SLIDE solution bullets

# Solution

* Context objects
* Runnable as user
* NullUser (NullObject pattern)

!SLIDE bullets

# NullObject pattern

* Remove branching logic
* Avoid null errors
* Improves testability

<!-- No ramas -> menos tests -> SRP -->


!SLIDE code

    @@@ coffeescript
    class User
      constructor : (name) ->
        this.name = name

    greet = (user) ->
      if user
        alert "Hi #{user.name}!"
      else
        alert "Hi stranger!"

!SLIDE code

    @@@ coffeescript
    john = new User('John')
    keith = null

    greet john    # Hi John!
    greet keith   # Hi stranger!

!SLIDE code

    @@@ coffeescript
    class Stranger extends User
      constructor : ->
        this.name = 'stranger'

    greet = (user) ->
      alert "Hi #{user.name}!"

    greet john    # Hi John!
    greet keith   # Hi stranger!

!SLIDE problem

# Problem

## Limit data access based on user roles

!SLIDE solution bullets

# Solution

* Inject user with model access methods
* Model access implementation based on role
* Similar to State pattern (sort of)

!SLIDE image

< Diagrama de inyeccción en base al rol. Chain of resposibility >


!SLIDE
# DCI

## Data, Context, Interaction

<!--
Llegamos a la arquitectura a través de mirar el DCI
explicar el DCI con ejemplo de transferencia entre cuentas (con diag)
No lo usamos tal cual por limitaciones tecnológicas.
-->

!SLIDE code

    @@@ ruby
    class BankAccount
      attr_accessor :balance
    end

    module TransferSource
      def withdraw(amount)
        self.balance -= amount
      end
    end

    module TransferTarget
      def deposit(amount)
        self.balance += amount
      end
    end

!SLIDE code

    @@@ ruby
    class TransferContext
      def initialize(source, target, amount)
        ...
      end

      def run
        source.extends(TransferSource)
        target.extends(TransferTarget)

        source.withdraw(amount)
        target.deposit(amount)
      end
    end

!SLIDE bullets

# DCI

* SRP
* Reusability
* Testability
* Best with dynamic langs
* Beware of implementation quirks


!SLIDE problem
# Problem
## Present same model object in different ways on different views

!SLIDE solution bullets
# Solution

* Decorator pattern
* Decorate associations too
* One or multiple decorators
* Variant: presenter pattern

!SLIDE code

    @@@ ruby
    class User
      def initialize(name, email)
        ...
      end
    end

    class UserDecorator
      def initialize(user)
        ...
      end

      def name
        user.name
      end

      def email
        user.name + "<" + user.email + ">"
      end
    end

!SLIDE code

    @@@ ruby
    user = User.new('john', 'john@gmail.com')
    decorated_user = UserDecorator.new(user)
    mail = new Mail()

    mail.send to: decorated_user.email

!SLIDE problem

# Problem
## Global search

!SLIDE solution

# Solution
## External Indexer (REST API)

!SLIDE image

< diagrama app lucene api rest >


!SLIDE problem

# Problem
## Long running contexts

!SLIDE solution

# Solution
## Execute contexts in background
## Jobs queues
## Jobs executor

!SLIDE image

< diagrama de colas más mierda >
