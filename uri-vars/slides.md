
!SLIDE subsection
# URI Variables In More Places

!SLIDE small
# URI variables &
# data binding

    @@@ java

	@RequestMapping(value="/{firstName}/{lastName}")
	public String search(Person person,
                         BindingResult result) {

        // person.getFirstName() is populated
        // person.getLastName()  is populated

        if (result.hasErrors()) {
            return "search";
        }

        // ...

	}

!SLIDE incremental bullets small
# `@PathVariable` values
# in views

    @@@java


    @RequestMapping("/apps/edit/{slug}")
    public String editForm(@PathVariable String slug){



    }

!SLIDE small transition=fade
# `@PathVariable` values
# in views

    @@@java


    @RequestMapping("/apps/edit/{slug}")
    public String editForm(@PathVariable String slug){

        // No need to add "slug" to the model

    }

!SLIDE small bullets incremental
# `@PathVariable` values

* Merged in the model prior to rendering
* Except for "automated" view types
* E.g, JSON, XML

!SLIDE small
# URI Variables in `"redirect:"`

    @@@java

    @RequestMapping(
        value="/{year}/{month}/{slug}/rooms",
        method=RequestMethod.POST)

    public String createRoom() {







        return "redirect:/{year}/{month}/{slug}";
    }

!SLIDE small
# URI Variables in `"redirect:"`

    @@@java

    @RequestMapping(
        value="/{year}/{month}/{slug}/rooms",
        method=RequestMethod.POST)

    public String createRoom() {


        // No need to add "year", "month", "slug"




        return "redirect:/{year}/{month}/{slug}";
    }

!SLIDE small
# URI Variables in `"redirect:"`

    @@@java

    @RequestMapping(
        value="/{year}/{month}/{slug}/rooms",
        method=RequestMethod.POST)

    public String createRoom() {


        // No need to add "year", "month", "slug"

        // Expanded from model attributes


        return "redirect:/{year}/{month}/{slug}";
    }

!SLIDE
# `@ModelAttribute`
# Instantiated from
# URI Variable

!SLIDE

    @@@ java


    @RequestMapping(
            value="/{account}", 
            method = RequestMethod.PUT)

    public String update(Account account) {




    }

!SLIDE transition=fade

    @@@ java


    @RequestMapping(
            value="/{account}", 
            method = RequestMethod.PUT)

    public String update(Account account) {

        // Account retrieved from database
        // via Converter<String, Account>

    }


!SLIDE incremental bullets small
# `@ModelAttribute` from
# URI Variable
## _(Conditions)_

* Model attribute must match URI variable or request param name
* A `Converter<String, Account>` must be registered


