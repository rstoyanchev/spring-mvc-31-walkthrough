!SLIDE subsection
# Java web config

!SLIDE incremental bullets
# DispatcherServlet
# Config

!SLIDE

## Defaults listed in
## `DispatcherServlet.properties`

!SLIDE smaller

## DispatcherServlet.properties

    @@@ 

    org.springframework.web.servlet.HandlerMapping=\
         ...BeanNameUrlHandlerMapping,\
         ...DefaultAnnotationHandlerMapping
    
    org.springframework.web.servlet.HandlerAdapter=
         ...HttpRequestHandlerAdapter,\
         ...SimpleControllerHandlerAdapter,\
         ...AnnotationMethodHandlerAdapter
    
    org.springframework.web.servlet.ViewResolver=\
         ...InternalResourceViewResolver
    
    org.springframework.web.servlet.HandlerExceptionResolver=\
         ...AnnotationMethodHandlerExceptionResolver,\
	     ...ResponseStatusExceptionResolver,\
	     ...DefaultHandlerExceptionResolver
    
    ...

!SLIDE bullets incremental
## Defaults turned off (by type)
## as you add to your config

* `HandlerMapping`
* `HandlerAdapter`
* `ViewResolver`
* ...

!SLIDE bullets incremental
## Intended to be

* Flexible
* Transparent
* Agnostic (fit diverse needs)

!SLIDE incremental bullets
# MVC XML Namespace
### (Spring 3.0)

!SLIDE bullets incremental
# Higher-level config

* Compact
* Expressive
* No Spring MVC beans to see

!SLIDE
# It's also...

!SLIDE
# more opinionated

!SLIDE bullets incremental
# Intended to be

* A common starting point
* Low barrier of entry
* Convenient

!SLIDE
# What about transparency?

!SLIDE
# Flexibility?

!SLIDE incremental bullets
# MVC Java Config
### (New in Spring 3.1)

!SLIDE
## Similar to the MVC namespace
## but in Java

!SLIDE bullets incremental
# Transparent & Flexible

* Easy to see the underlying beans
* and customize them

!SLIDE small
# A common starting point
### (comparable to `<mvc:annotation:driven/>`)

	@@@ java

        @EnableWebMvc
        @Configuration
        public class WebConfig {




        }

!SLIDE smaller
# Customizations

	@@@ java

    @EnableWebMvc
    @Configuration
    public class WebConfig {













    }

!SLIDE smaller
# Customizations

	@@@ java

    @EnableWebMvc
    @Configuration
    public class WebConfig implements WebMvcConfigurer {













    }

!SLIDE smaller
# Customizations

	@@@ java

    @EnableWebMvc
    @Configuration
    public class WebConfig extends WebMvcConfigurerAdapter {













    }

!SLIDE smaller
# Customizations

	@@@ java

    @EnableWebMvc
    @Configuration
    public class WebConfig extends WebMvcConfigurerAdapter {

      @Override
      protected void addFormatters(FormatterRegistry reg) {
        // ...
      }








    }

!SLIDE smaller
# Customizations

	@@@ java

    @EnableWebMvc
    @Configuration
    public class WebConfig extends WebMvcConfigurerAdapter {

      @Override
      protected void addFormatters(FormatterRegistry reg) {
        // ...
      }

      @Override
      public void addInterceptors(InterceptorRegistry reg){
        // like <mvc:interceptors>
      }



    }

!SLIDE smaller
# Customizations

	@@@ java

    @EnableWebMvc
    @Configuration
    public class WebConfig extends WebMvcConfigurerAdapter {

      @Override
      protected void addFormatters(FormatterRegistry reg) {
        // ...
      }

      @Override
      public void addInterceptors(InterceptorRegistry reg){
        // like <mvc:interceptors>
      }

      // ... see all options in WebMvcConfigurer

    }

!SLIDE
## So far no Spring MVC beans in sight
### (Configuration is imported rather than extended)

!SLIDE bullets incremental
# Shift into low gear

* Remove `@EnableWebMvc` annotation
* Change base class to `WebMvcConfigurationSupport`
* You're now extending the actual configuration
* May override base class `@Bean` methods

!SLIDE
# Replacing `web.xml`
# with Java
### (Servlet 3.0)

!SLIDE 
## Create an implementation of `WebApplicationInitializer`

!SLIDE smaller

    @@@ java

    public class MyWebAppInitializer
           implements WebApplicationInitializer {

      @Override
      public void onStartup(ServletContext container) {

        AnnotationConfigWebApplicationContext cxt =
          new AnnotationConfigWebApplicationContext();
        cxt.register(MyWebConfig.class);

        ServletRegistration.Dynamic disp = 
          container.addServlet("d", new DispatcherServlet(cxt));

        disp.setLoadOnStartup(1);
        disp.addMapping("/");
      }

    }



