!SLIDE section

# The many hells of Computer Science

<!-- you can explain that -->

!SLIDE quote

# There are only two hard things in Computer Science: cache invalidation and naming things.
## Phil Karlton

!SLIDE

# Easy cache invalidation

## LRU Caches + Auto expiring keys

!SLIDE code

      @@@ ruby

      class User
        def cache_key
          "user#" + id + "#" +
            updated_at.to_millis
        end
      end


      cache user.cache_key do
        ...
      end


!SLIDE

# Easy naming

## There is no easy naming. Sorry folks!

!SLIDE

# Maybe there are more hard things

<!-- Mother of GOD -->

!SLIDE

# Encoding hell

## Use UTF-8. Use iconv wisely

!SLIDE image

![Encoding](encoding.png)

!SLIDE

# Timezones, i18n, l11n, Accessibility hell

## Always use UTC :D
## Treat i18n, l11n and accesibility as first class citizens


!SLIDE

# Deployment and environments hell

## Define enviroments from square one
## Automatize deployment as much as you can

!SLIDE image

< despliegue con mina gif animado :D >

!SLIDE

# Documentation/Code sync hell

## Self explanatory code
## Document APIs
## Document wisely
## Treat documentation as part of the code


!SLIDE code smaller

    @@@ java

    /**
     * Returns the user names in alphabetical order
     * @returns the names
     */
    public String[] orderedNames() {
      return sortAlphabetically(this.getNames());
    }

    /*
     * Sort with quicksort algorithm
     */
    private String[] sortAlphabetically(String[] words) {
      // lines of elegant yet uninteligible code ;)
    }



!SLIDE

# Multithreading hell

## Use multi process
## Avoid too much low level

!SLIDE bullets

# Inter Process Communication

* Unix Sockets
* Queues
* Shared memory

!SLIDE

# Or use a library! Or switch to erlang :P


!SLIDE

# Fragmentation hell

## Do your HTML5/CSS3/JS homework
## SOLID also applies (SMACSS, etc)
## Know how to tame browsers
## Know how to tame mobile

!SLIDE 

# MVC Inception

## Inside an webapp MVC there is another MVC

!SLIDE image

< mierda de un proeycto en Chrome >

!SLIDE image

< mierda proyecto en IE >

!SLIDE image

< mierda en emulador de iphone >


!SLIDE section

# The "six" commandments
## Parting note


!SLIDE
# SOLID (SRP in particular)

## SOLID &#x2192; Simple &#x2192; Easy to change &#x2192; Happiness

!SLIDE
# YAGNI 

## YAGNI &#x2192; Simple &#x2192; Easy to change &#x2192; Happiness

!SLIDE

# TESTs, TESTs, TESTs

## Test &#x2192; YAGNI + SOLID &#x2192; Simple &#x2192; Easy to change &#x2192; Happiness

!SLIDE

# Refactor, Refactor, Refactor

## Refactor code and tests
## Refactoring &#x2192; Better code & tests &#x2192; ... &#x2192; Happiness


!SLIDE

# DRY more than your code

## Automatize, share, extract

!SLIDE

# The most important commandment

## Do what feels right!

<!-- EJemplo de Twitter y ; -->
