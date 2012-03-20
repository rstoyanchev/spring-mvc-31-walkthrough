
!SLIDE subsection
# URI Variables In More Places

!SLIDE small
# URI variables in data binding

    @@@ java
    
    // GET /manu/chao

	@RequestMapping(value="/{firstName}/{lastName}")
	public String search(@ModelAttribute Person person,
                         BindingResult result) {

        // "manu".equals(person.getFirstName())
        // "chao".equals(person.getLastName())

	}

!SLIDE incremental bullets small
# `@PathVariable` values available
# in the model for rendering

    @@@java


    @RequestMapping("/apps/edit/{slug}")
    public String editForm(@PathVariable String slug){

        // ...

    }

!SLIDE small transition=fade
# `@PathVariable` values available
# in the model for rendering

    @@@java


    @RequestMapping("/apps/edit/{slug}")
    public String editForm(@PathVariable String slug){

        // No need to add "slug" to the model

    }

!SLIDE small bullets incremental
# `@PathVariable` values

* Values merged into the model prior to rendering
* Except for "automated" content generation <br> like JSON & XML

!SLIDE small
# URI variables in redirect strings

    @@@java

    @RequestMapping(value="/{year}/{month}/{slug}",
                    method=RequestMethod.POST)
    public String createRoom() {




        return "redirect:/{year}/{month}/{slug}";
    }

!SLIDE small
# URI variables in redirect strings

    @@@java

    @RequestMapping(value="/{year}/{month}/{slug}",
                    method=RequestMethod.POST)
    public String createRoom() {

        // No need to add "year", "month", "slug"


        return "redirect:/{year}/{month}/{slug}";
    }

!SLIDE small
# URI variables in redirect strings

    @@@java

    @RequestMapping(value="/{year}/{month}/{slug}",
                    method=RequestMethod.POST)
    public String createRoom() {

        // No need to add "year", "month", "slug"
        // to the the model explicitly

        return "redirect:/{year}/{month}/{slug}";
    }

!SLIDE
## `@ModelAttribute` ..
## instantiated from a URI variable

!SLIDE incremental bullets small
# Pre-requisites
## (`@ModelAttribute` from a URI variable)

* Model attribute name matches URI variable name
* A `Converter<String, ?>` is available
* The converter can load object from database

!SLIDE smaller
# Example

    @@@ java

    @RequestMapping(value="/{account}", method = PUT)
    public String update(@ModelAttribute Account account) {

		// ...



    }

!SLIDE smaller
# Example

    @@@ java

    @RequestMapping(value="/{account}", method = PUT)
    public String update(@ModelAttribute Account account) {

        // Model attribute name matches URI variable name
        
        

    }


!SLIDE smaller
# Example

    @@@ java

    @RequestMapping(value="/{account}", method = PUT)
    public String update(@ModelAttribute Account account) {

        // Model attribute name matches URI variable name

        // Converter<String, Account> is registered

    }



