!SLIDE subsection
# New @MVC support classes

!SLIDE bullets incremental
# We are talking about

* `DefaultAnnotationHandlerMapping`
* `AnnotationMethodHandlerAdapter`
* `AnnotationMethodHandlerExceptionResolver`

!SLIDE bullets incremental
# Being replaced with

* `RequestMappingHandlerMapping`
* `RequestMappingHandlerAdapter`
* `ExceptionHandlerExceptionResolver`

!SLIDE incremental bullets
# Named after...

* __`{@RequestMapping}`__`HandlerMapping`
* __`{@RequestMapping}`__`HandlerAdapter`
* __`{@ExceptionHandler}`__`ExceptionResolver`

!SLIDE bullets incremental
# Why does it matter?

* (besides better internal design)
* More customizable(!)
* Address many JIRA issues
* More things possible

!SLIDE bullets incremental
# What you should know

* Existing classes continue to exist
* However no new features
* Verify what you have in use

!SLIDE bullets incremental
# To upgrade

* Search old classes in your config
* Replace with the new ones

!SLIDE bullets incremental
## Or if using `<mvc:annotation-driven />` or `@EnableWebMvc`

* No action required

!SLIDE bullets incremental
# After the upgrade

* Things should work the same
* Minor behavior changes
* Review 3.1.1 docs for important notes
* `@RequestMapping` javadoc also updated






