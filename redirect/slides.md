
!SLIDE subsection
# Redirect & Flash Attributes

!SLIDE
# `RedirectAttributes`

!SLIDE
## A new controller method argument

!SLIDE smaller
# Example

    @@@ java

        @RequestMapping(method=POST)
        public String save(Entity entity, Errors errors,
                           RedirectAttributes redirectAttrs){

            // ...

            return "redirect:/someUrl";
        }

!SLIDE bullets incremental
# The two main cases

* Redirect URL query parameters
* Flash attributes

!SLIDE smaller
# Redirect URL query params

    @@@ java

        @RequestMapping(method=POST)
        public String save(Entity entity, Errors errors,
                           RedirectAttributes redirectAttrs){

            // ...

            redirectAttrs.addAttribute("id", entity.getId);
            redirectAttrs.addAttribute("date", new Date());

            return "redirect:/someUrl";
        }

!SLIDE bullets
# Redirects to

* `/someUrl?id=123&date=03/21/2012`

### _(note the DataBinder-formatted date value)_

!SLIDE
## What if you wanted keep the URL free of
## some parames that "pollute" the URL?

!SLIDE
## Or had a complex object you wanted to store
## temporarily until after the redirect?

!SLIDE bullets incremental
# Flash attributes

* A way to pass attributes across a redirect
* Without involving the URL

!SLIDE smaller
# Before the redirect

    @@@ java

      @RequestMapping(method=POST)
      public String save(Entity entity, Errors errors,
                         RedirectAttributes redirectAttrs){

        // ...

        redirectAttrs.addFlashAttribute("message", "Yay!");

        return "redirect:/someUrl";
      }

!SLIDE bullets incremental
# After the redirect

* Nothing special to do
* Flash attributes should be in the model
* But won't survive another refresh
* "Consumed" immediately

!SLIDE bullets incremental
# Flash storage

* `SessionFlashMapManager` used by default
* Cookie-based implementation
* Planned <a href="https://jira.springsource.org/browse/SPR-8997">SPR-8997</a>





