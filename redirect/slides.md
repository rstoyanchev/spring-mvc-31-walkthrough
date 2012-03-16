
!SLIDE subsection
# Redirect & Flash Attributes

!SLIDE
# `RedirectAttributes`

!SLIDE
## A new controller method argument

!SLIDE smaller
# E.g.

    @@@ java

        @RequestMapping(method=POST)
        public String save(Entity entity, Errors errors,
                           RedirectAttributes redirectAttrs){

            // ...

            return "redirect:/someUrl";
        }

!SLIDE bullets incremental
# Two cases for using it

* Append params to redirect URL
* Add flash attributes

!SLIDE smaller
# E.g.

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
### _(note formatted date)_

* `/someUrl?id=123&date=03/21/2012`

!SLIDE
## What if you wanted to avoid
## "polluting" the URL?

!SLIDE
## Or had a complex object you'd
## rather not pass as an id?

!SLIDE bullets incremental
# Flash attributes

* Pass attributes across a redirect
* Not involving the URL
* Access them after the redirect

!SLIDE smaller
# E.g.

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
* Flash attributes are in the model
* But won't survive a refresh(!)

!SLIDE bullets incremental
# About flash storage

* `FlashMapManager` abstraction
* HTTP Session implementation
* Cookie-based planned
* See <a href="https://jira.springsource.org/browse/SPR-8997">SPR-8997</a>





