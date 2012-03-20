
!SLIDE subsection
# Partial validation

!SLIDE smaller
# Partial validation

    @@@ java

    @RequestMapping(method = RequestMethod.PUT)
    public String update(
        @Valid(group=MyGroup.class) Account account) {

		// ...

	}
	
!SLIDE subsection
# `UriComponents`

!SLIDE small
# Build URI

    @@@ java
    
	    UriComponents uriComp = 
	        UriComponentsBuilder.fromPath("/foo")
	            .queryParam("bar").build();
	
	
	
	    uriComp.toUri();
    
!SLIDE small
# Build URI template and expand

    @@@ java
    
	    UriComponents uriComp = 
	        UriComponentsBuilder.fromPath("/{foo}")
	            .queryParam("bar").build();

		uriComp = uriComp.expand("fooValue");
	
	    uriComp.toUri();

!SLIDE small
# Build URI template, expand & encode

    @@@ java
    
	    UriComponents uriComp = 
	        UriComponentsBuilder.fromPath("/{foo}")
	            .queryParam("bar").build();

		uriComp = uriComp.expand("fooValue").encode();
	
	    uriComp.toUri();

!SLIDE smaller
# Create `"Location"` header

    @@@ java

	@RequestMapping(method = RequestMethod.POST)
	public ResponseEntity createCustomer(UriComponentsBuilder b) {

		// Builder contains path relative to current URL...

	    UriComponents uriComponents = 
	        b.path("/customers/{id}").buildAndExpand(id);
	
		HttpHeaders headers = new HttpHeaders();
		headers.setLocation(uriComponents.toUriString()));
		return new ResponseEntity(headers, HttpStatus.CREATED);
	}


    