---
title: Change the Spring Boot startup banner
parent: Spring CookBooks
grand_parent: Spring Framework
nav_order: 1
---

# Change the Spring Boot startup banner
*Source: https://www.theserverside.com/blog/Coffee-Talk-Java-News-Stories-and-Opinions/spring-boot-banner-change-hide-customize-ascii-art-example-remove*
## How do you turn off the Spring Boot banner?
The first line of defense against Spring Boot’s banner? Simply turning it off.

```console
spring.main.show-banner=false
```
This turns the banner off completely, so you won’t see it anymore. However, turning the Spring Boot banner off entirely can feel like a drastic measure.

My preference? Simply customize it.

You can replace the default Spring banner by adding a file named banner.txt in the resources folder of your application.


## How do you customize the Spring Boot banner?
You can add any text you want to the banner.txt file. My suggestion? Add data that will help with the troubleshooting effort, including:

The active version of the Spring Boot framework in use
The currently active Spring profile
The currently configured logging levels
The name of the Spring Boot application
Custom Spring Boot banner example
Here’s a simple, sample Spring Boot banner that provides basic, but important, configuration information when your application starts up:

### Custom Spring Boot banner example
Here’s a simple, sample Spring Boot banner that provides basic, but important, configuration information when your application starts up:

```console
${application.title} ${application.version}
${spring.application.name} is starting
The currently active profile is: ${spring.profiles.active}
The web application is running on port: ${server.port}
Powered by Spring Boot Version ${spring-boot.version}
```
### Custom ASCII banner art
Oh, and if you do pine for the ASCII art the standard banner provides, you can always create your own.

There’s actually a custom Spring Boot banner generator available at datenkollektiv.de, which generated the ASCII art below for me:
<pre>
  _____ _        ___                      ___ _    _     
 |_   _| |_  ___/ __| ___ _ ___ _____ _ _/ __(_)__| |___ 
   | | | ' \/ -_)__ \/ -_) '_\ V / -_) '_\__ \ / _` / -_)
   |_| |_||_\___|___/\___|_|  \_/\___|_| |___/_\__,_\___|
                                                         
${application.title} ${application.version}
Powered by Spring Boot ${spring-boot.version}
</pre>
If you want to customize your development environment and give it some ASCII flair, it’s definitely a link worth checking out.