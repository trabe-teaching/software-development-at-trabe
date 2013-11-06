!SLIDE section

# The many hells of Computer Science

<!-- you can explain that -->

!SLIDE quote

# There are only two hard things in Computer Science: cache invalidation and naming things.
## Phil Karlton

!SLIDE

# Easy cache invalidation

## LRU Caches + Auto expiring keys

!SLIDE code small

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

!SLIDE image

![Yao Ming](yao.png)

!SLIDE

# Maybe there are more hard things

!SLIDE image

![Mother of God](mother_of_god.png)

!SLIDE

# Encoding hell

## Use UTF-8. Use iconv wisely

!SLIDE image

![Encoding](encoding.png)

!SLIDE

# Timezones, i18n, l11n, Accessibility hell

## Always use UTC __:D__
## Treat i18n, l11n and accesibility as first class citizens

<!-- Ejemplo del correo de los cojones de los SAI -->
<!-- Ejemplo de timestamps, UTC, queries datetime vs time  -->

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

# Or use a library!
# Or switch to erlang :P


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


!SLIDE bullets title-first chain-bullets
# SOLID (SRP in particular)

* &#x2193;
* Simple
* &#x2193;
* Easy to change
* &#x2193;
* Happiness __\\(^o^)/__

!SLIDE bullets title-first chain-bullets
# YAGNI

* &#x2193;
* Simple
* &#x2193;
* Easy to change
* &#x2193;
* Happiness __\\(^o^)/__

!SLIDE bullets title-first chain-bullets

# TESTs, TESTs, TESTs

* &#x2193;
* YAGNI + SOLID
* &#x2193;
* Simple
* &#x2193;
* Easy to change
* &#x2193;
* Happiness __\\(^o^)/__

!SLIDE bullets title-first chain-bullets

# Refactor, Refactor, Refactor
##(code and tests)

* &#x2193;
* Better code & tests
* &#x2193;
* ... 
* &#x2193;
* Happiness __\\(^o^)/__

!SLIDE

# DRY more than your code

## Automatize, share, extract

!SLIDE

# The most important commandment

## Do what feels right!

<!-- EJemplo de Twitter y ; -->
