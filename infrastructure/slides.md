!SLIDE subsection
# @MVC support classes

!SLIDE
# Old 
## `DefaultAnnotationHandlerMapping`, `AnnotationMethodHandlerAdapter`, `AnnotationMethodExceptionResolver`
<br>
# New
## `RequestMappingHandlerMapping`, `RequestMappingHandlerAdapter`, `ExceptionHandlerExceptionResolver`

!SLIDE incremental bullets
# New classes named after...

* __`{@RequestMapping}`__`HandlerMapping`
* __`{@RequestMapping}`__`HandlerAdapter`
* __`{@ExceptionHandler}`__`ExceptionResolver`

!SLIDE bullets incremental
# Why does it matter?

* Better internal design
* More flexible
* Customizable @MVC
* Help address many JIRA issues

!SLIDE bullets incremental
# What you should know

* Existing classes continue to exist
* However no new features
* Verify what you have in use

!SLIDE 
## To upgrade simply replace occurrences of
## the old classes with the new ones in your config

!SLIDE bullets incremental
# Or if using..

* `<mvc:annotation-driven />`
* `@EnableWebMvc`
* No action required

!SLIDE bullets incremental
# After the upgrade

* Things should work the same
* Some request mapping scenarios<br> no longer supported
* Review 3.1.1 docs for important notes
* `@RequestMapping` javadoc also updated

!SLIDE
## More on this subject
<br>
## Thursday 4pm<br>
<br>
## <a href="http://devnexus.com/s/presentations#id-1321">"An In-depth Look At Spring MVC 3.1"</a>





