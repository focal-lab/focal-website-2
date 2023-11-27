---
# Leave the homepage title empty to use the site title
title:
date: 2022-10-24
type: landing

sections:
  - block: markdown
    design:
      background:
        image:
          filename: chips1.JPG
          filters:
            brightness: 0.8
          parallax: false
          position: center
          size: cover
        text_color_light: true
      spacing:
        padding: ["80px", "0", "100px", "0"]
    content:
      title: 
      text: |
        <div class="container">
          <div class="row justify-content-center">
            <div class="col-xl-10">

        # **<p>Forest Change Analysis Lab</p>**
        <p>Disturbance ecology &nbsp; | &nbsp; Forest management &nbsp; | &nbsp; Data science</p>


          </div>
        </div>
  - block: markdown
    id:
    design:
      spacing:
        padding: ["25px", "0", "10px", "0"]
    content:
      title: 
      text: |
        <div class="container">
          <div class="row justify-content-center align-items-center">
            <div class="col-lg-6 py-2">

        The Forest Change Analysis Lab (FOCAL) at the [University of California, Davis](http://www.ucdavis.edu) works at the intersection of disturbance ecology and data science. We collect and analyze data to inform forest management in an era of climate change, drought, and large high-severity wildfires. We rely as much on large geospatial datasets as on field-based measurements of forests. We work closely with forest managers in an effort to address pressing forest management needs.

          </div>

          <div class="col-sm-auto align-items-center align-content-center py-2">

        {{< figure src="flagged-seedlings-square.jpg" class="round" >}}

          </div>
        </div>

  - block: markdown
    id: research-header
    content:
      title:
      subtitle:
      text: |
        # <div style="text-align: center">**Current Research**</div>
    design:
      columns: '1'
      background:
        image:
          filename: amriv.JPG
          filters:
            brightness: 0.7
          parallax: true
          position: center
          size: cover
        text_color_light: true
  
  - block: portfolio
    id: projects
    content:
      title:
      subtitle:
      text: 
      filters:
        # Folders to display content from
        folders:
          - current-research
        # Only show content with these tags
        tags: []
        # Exclude content with these tags
        exclude_tags: []
        # Which Hugo page kinds to show (https://gohugo.io/templates/section-templates/#page-kinds)
        kinds:
          - page
      # Field to sort by, such as Date or Title
      sort_by: 'Date'
      sort_ascending: false
      # Default portfolio filter button
      # 0 corresponds to the first button below and so on
      # For example, 0 will default to showing all content as the first button below shows content with *any* tag
      default_button_index: 0
      # Filter button toolbar (optional).
      # Add or remove as many buttons as you like.
      # To show all content, set `tag` to "*".
      # To filter by a specific tag, set `tag` to an existing tag name.
      # To remove the button toolbar, delete the entire `buttons` block.
      # buttons:
      #   - name: All
      #     tag: '*'
      #   - name: Deep Learning
      #     tag: Deep Learning
      #   - name: Other
      #     tag: Demo
    design:
      # See Page Builder docs for all section customization options.
      # Choose how many columns the section has. Valid values: '1' or '2'.
      columns: '1'
      # Choose a listing view
      view: masonry
      # For Showcase view, flip alternate rows?
      flip_alt_rows: false
      spacing:
        padding: ["60px", "0", "60px", "0"]
  - block: contact
    id: contact
    content:
      title: Contact
      subtitle: ''
      text: ''
      # Contact details - edit or remove options as needed
      email: djyoung@ucdavis.edu
      # phone: 888 888 88 88
      # appointment_url: 'https://calendly.com'
      address:
        street: Derek Young, Department of Plant Sciences, University of California Davis
        city: Davis
        region: CA
        postcode: '95616'
        country: United States
        country_code: US
      directions: Plant and Environmental Sciences Building
      # office_hours:
      #   - 'Monday 10:00 to 13:00'
      #   - 'Wednesday 09:00 to 10:00'
      contact_links:
        - icon: users
          icon_pack: fas
          name: Lab member contact info
          link: '/people/'
      # Automatically link email and phone or display them just as text?
      autolink: true
      # Choose an email form provider (netlify/formspree)
      # form:
      #   provider: netlify
      #   formspree:
      #     # If using Formspree, enter your Formspree form ID
      #     id: ''
      #   netlify:
      #     # Enable CAPTCHA challenge to reduce spam?
      #     captcha: false
      # # Coordinates to display a map - set your map provider in `params.yaml`
      # coordinates:
      #   latitude: '37.4275'
      #   longitude: '-122.1697'
    design:
      # Choose how many columns the section has. Valid values: '1' or '2'.
      columns: '1'
---