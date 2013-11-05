!SLIDE cover

# Software Development at Trabe

!SLIDE image

![Who we are](who_we_are.png)

!SLIDE image

![Trabe](trabe.png)

<!--
  a qué nos dedicamos, qué hacemos para quién, tecnologías, etc
-->

!SLIDE image

![Men at work](men_at_work.png)

!SLIDE

# Shiny happy opinionated people

!SLIDE bullets toc bullets-first

# Contents

* Ideas, Methodology & Tools
* Real life examples
* The many hells of Computer Science
* The ten commandments

!SLIDE section

# Ideas

!SLIDE quote

# A good design is easy to change, rather than easy to configure
## someone, somewhere

!SLIDE

# There is no silver bullet

## Every architecture/design solution has pros & cons

!SLIDE

# Architecture & technology should fit the problem

!SLIDE

# Simple is better

!SLIDE bullets columns

# Simple solutions are easier to:

* design
* code
* mantain
* evolve
* document
* grasp

!SLIDE

## Architecture: the UNIX way

# Orchestrate simple components, each doing one thing, <br/>and doing it well

!SLIDE

# Design: SOLID rock

## KISS & DRY driven

!SLIDE

# S for SRP
## Single Responsability Principle

!SLIDE

# SOLID leads to Design Patterns
## (Designs patterns are SOLID)

!SLIDE image

![Be OO, my friend](be_oo_my_friend.png)

!SLIDE bullets bullets-first

# Other useful buzzwords

* YAGNI
* CoC


!SLIDE code smallest

    @@@ xml
    <action path="/admin/ShowConfiguration"
      type="controller.admin.ShowConfigurationAction"
      scope="request">
      <forward name="success" 
               path=".admin.ShowConfiguration"/>
    </action>

!SLIDE image

![Y U NO admin.ShowConfiguration](yu_no_admin_showconfiguration.png)
