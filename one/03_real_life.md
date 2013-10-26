!SLIDE

# FEDERICO

<!--
UDC-Federico
Ejemplo de arquitectura para integrar múltiples aplicaciones
Problema: Identidad unica, compartir información entre sistemas (1 diagrama)
Solución ideal:
Federacion de autenticacion
Bus + Adaptadores + Pull+Push + Operaciones WS
Webs diferentes tecnologías consumen WS
Solución de compromiso
Sólo Pull, Tareas periódicas
Arquitectura del core: BD + LDAP + Adaptadores + Traductores +  Bus + Publicar ops core como WS
Adaptadores: BD, LDAP, WS, Comandos SSH, etc.
Herramientas de despliegue espefícas: Rake
-->

<!-- arquitectura -->

<!-- del diseño inicial a la cruda realidad -->

!SLIDE

## Problem

# Signup/signin on multiple services
# Consolidate personal info

!SLIDE

## Solution

# Orchestrate services through a Service Bus
# Single sign on

<!-- garabato de arquitectura de Federico: ideal vs real -->

!SLIDE bullets

# Technology

* Java stack
* Ruby for automation

!SLIDE

# NeoSAI

!SLIDE

## Context

# Laboratory Management System

!SLIDE

## Problem

# Different kinds of UIs

!SLIDE bullets

# Solution

* Basic CRUD: forms & listings
* Advanced CRUD: JS components + AJAX
* Complex tasks: Single-page app + REST

!SLIDE

## Problem

# Integrate new & legacy app

!SLIDE bullets

# Solution

* Shared DB
* REST APIs (JSON preferred)
* SSO
* UI integration via IFrame + HTML5 PubSub

<!-- diagrama -->

!SLIDE

## Problem

# Integrate "nonintegrable" third party software

!SLIDE bullets

# Solution

* Ad hoc REST API

<!-- diagrama -->

!SLIDE

## Problem

# Mail log: different sources

!SLIDE bullets

# Solution

* Wrapper + REST API

<!-- diagrama -->

!SLIDE

## Problem

# Complex permission checks

!SLIDE bullets

# Solution

* Policy objects

<!-- ejemplo de permiso loco -->

!SLIDE

## Problem

# Run the same business logic from different places

!SLIDE bullets

# Solution

* Context objects
* Runnable from controllers, console, APIs, cron jobs

!SLIDE

## Problem

# Run business logic as different users, even as no user

!SLIDE bullets

# Solution

* Context objects
* Runnable as user
* NullUser (NullObject pattern)

<script>
User = function(name) {
  this.name = name;
}

greet = function(user) {
  alert('Hi ' + user.name + '!');
}
</script>

!SLIDE execute

    @@@ coffeescript
    class User
      constructor : (name) ->
        this.name = name

    greet = (user) ->
      alert "Hi #{user.name}!"

    john = new User('John')

    greet john

!SLIDE execute

    @@@ coffeescript
    class Stranger extends User
      constructor : ->
        this.name = 'stranger'

    stranger = new Stranger

    greet stranger

!SLIDE

## Problem

# Limit data access based on user roles

!SLIDE bullets

# Solution

* Inject user with model access methods
* Model access implementation based on role

<!-- Best with diagram -->


!SLIDE
# AQUI LO DEL DCI!!!

Llegamos a la arquitectura a través de mirar el DCI
explicar el DCI con ejemplo de transferencia entre cuentas (con diag)

* No lo usamos tal cual por limitaciones tecnológicas.

!SLIDE
## Problem
# Present same model object in different ways on different views

!SLIDE bullets
# Solution

* Decorator pattern
* Decorate associations too
* One or multiple decorators
* Variant: presenter pattern

<!--
Buscador: externo -> Indexador
Tareas en segundo plano
-->
