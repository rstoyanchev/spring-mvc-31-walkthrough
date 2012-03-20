!SLIDE subsection
# Content Negotiation 

!SLIDE
## In 3.0 content negotiation was based on
## `@RequestMapping(headers="..")`

!SLIDE incremental bullets smaller
# Producing content

    @@@ java

    @RequestMapping(header="Accept=application/json")
    @ResponseBody
    public Entity getEntity() {

    }

!SLIDE incremental bullets smaller
# Consuming content

    @@@ java

    @RequestMapping(header="Content-Type=application/json")
    @ResponseBody
    public String save(@RequestBody Entity entity) {

    }

!SLIDE
## However, header matching is not expressive
## enough for content negotiation

!SLIDE bullets incremental small
# Clients may request more general content types

* For example `"Accept=*/*"` or `"Accept=text/*"`
* Not an exact match
* But semantically it does

!SLIDE bullets incremental small
# Requested content may not be producible

* A simple match or no match = 404 `NOT_FOUND`
* It should be 406 `NOT_ACCEPTABLE` 
* or 415 `UNSUPPORTED_MEDIA_TYPE` 

!SLIDE bullets incremental small
# More than just mapping

* What content will actually be produced?
* Previously depended on .. 
* the order of `HttpMessageConvertet` registrations
* Less control
* Harder to reason about

!SLIDE incremental bullets small
# `@RequestMapping` <br> `consumes/produces`
### (new in Spring 3.1)

* Use instead of `headers=".."`
* `"Content-Type"` and `"Accept"` headers

!SLIDE incremental bullets small
# Producing content

    @@@ java

    @RequestMapping(header="Accept=application/json")
    @ResponseBody
    public Entity getEntity() {

    }

!SLIDE incremental bullets small transition=fade
# Producing content

    @@@ java

    @RequestMapping(produces="application/json")
    @ResponseBody
    public Entity getEntity() {

    }

!SLIDE incremental bullets small
# Consuming content

    @@@ java

    @RequestMapping(header="Content-Type=application/json")
    @ResponseBody
    public String save(@RequestBody Entity entity) {

    }

!SLIDE incremental bullets small transition=fade
# Consuming content

    @@@ java

    @RequestMapping(consumes="application/json")
    @ResponseBody
    public String save(@RequestBody Entity entity) {

    }

!SLIDE
## What happens to existing `headers=".."`?

!SLIDE
## `"Accept"` and `"Content-Type"`
## automatically converted to `consumes/produces`

!SLIDE bullets incremental small
# `produces=".."` condition

* Overall much more reliable!
* Guarantees actual content type written out
* Or returns appropriate HTTP status




