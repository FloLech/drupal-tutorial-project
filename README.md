# Drupal Tutorial Project
Project Used To Learn Drupal by the course:
https://www.youtube.com/watch?v=j7nWAKX_o5w

## Tutorial Notes
Tutorial Stopped at: 13:00

## Start the Project
* make sure docker is up
* run 'ddev start' in 'drupal' directory

## Login
* User: master
* PW: Hallo123456!

## phpMyAdmin
http://127.0.0.1:8036

## Drupal Error Handling
* In case Drupal does not Respond clean all tables starting with `cache_` via phpMyAdmin
* in web/sites/default/settings.php add `$config['system.logging']['error_level'] = 'verbose';`

## Used Modules
* Display Suite
    * https://www.drupal.org/project/ds
    * composer require drupal/ds
    * Activate under "Extend", Display Suite and Display Suite Extras
    
* Bootstrap Theme (3)
    * https://www.drupal.org/project/bootstrap
    * composer require drupal/bootstrap
    * Activate in Appearance
    
* Bootstrap Layouts
    * https://www.drupal.org/project/bootstrap_layouts
    * composer require drupal/bootstrap_layouts
    * Enable in Extend Section

* Search API
    * https://www.drupal.org/project/search_api
    * composer require drupal/search_api
    * Enable in Extend Section --> Search API, Database Search Defaults and Database Search

* Facets
    * https://www.drupal.org/project/facets
    * composer require drupal/facets
    * Enable in Extend --> Facets

* Entity Embed
    * https://www.drupal.org/project/entity_embed
    * composer require drupal/entity_embed
    * Enable in Extend --> Entity Embed
    
* Chaos Tool Suite (ctools)
    * https://www.drupal.org/project/ctools
    * composer require drupal/ctools
    * Enable in Extend --> Chaos Tools
    
* Entity Browser
    * https://www.drupal.org/project/entity_browser
    * composer require drupal/entity_browser
    * Enable in Extend --> Entity Browser, Entity Browser IEF
    
* Inline Entity Form
    * https://www.drupal.org/project/inline_entity_form
    * composer require drupal/inline_entity_form

* Video Embed Field (might be used for not Vimeo and Youtube Videos)
    * https://www.drupal.org/project/video_embed_field
    * composer require drupal/video_embed_field
    
* Override Node options
    * https://www.drupal.org/project/override_node_options
    * composer require drupal/override_node_options
    * Enable in Extend --> Override Node Options
    
    

## Theming
* Located in web/themes
* Create Sub / Child theme based on Parent (override components)
* In case of Bootstrap:
    * find starterkit direcotry
    * copy to `themes/custom/desired_themename/`
    * Replace THEMENAME with desired_themename
    * Change THEMENAME.starterkit.yml to desired_themename.info.yml
    * First install and activate Bootstrap, than install and active child theme
* Define regions in desired_themename.info.yml file

## Blocks
* Blocks are to be found under Structure --> Blocks
* Use blocks region demonstration to view Arrangement of Blocks (On top of blocks Page)
* Themes implement regions
* Blocks Fill Regions

## Regions
* Create a new region by
    * Defining region in `desired_themename.info.yml` under regions (key : label)
    * Adding to template:
        * Copy template from parent template (page.html.twig)
        * Edit Template in child directory:
            * Add Blocks using TWIG in template file {{ page.REGION_NAME }}

## Menus
* To be managed through Structure --> Menus

## Views
* To be found under Structure --> Views
* Views can be seen as a query builder
* SQL Queries cna be displayed by Views --> Settings --> "Show SQL query"
    * Shows SQL Query in Structure --> Views --> Item, in the Preview section 
* When adding views Pages, Blocks and Menu Entries can be generated
* Displays (e.g. Blocks) can be added in the Display Section
* Displayed Content (Fields) can be changed by each single display
* Menu Items can als be created in this view (Page Settings)

### Parameters for Views
* Can be sent via Path
* Edit Path in Views Page
* Use %NAME to get parameter from URL (e.g. %user)
* Add contextual filters in Views Edit Screen
    * Example Authored By
* Validation criteria might be used in conjunction
    
## Drush

### Clear Cache
* run `ddev exec drush cr`

## Search
* Configuration --> Search pages --> Regenerate Index
* Module: Search API

### Search API
* Configuration --> Search API
* Edit Default Index to contain Entities
* Under "Edit" define content Types to be indexed
* Under "Fields" define what fields are to be indexed
    * e.g. add Body
* Reindex after Changes to Indexes (Under View --> "Index now")

### Displaying Search Results
* Create a View
* Content --> Index that has been defined in the Search API
* Sort Criteria --> Add Relevancy (DESC)
* No Results behaviour --> Text Area or similar

### Facets
* Go to Configuration --> Facets
* Add facet
* Select Field Source and Field
* Add block to block layout --> on corresponding page

## Media Handling
* Create Media Upload Button
    * Configuration --> Text Editor Embed Buttons
    * Add Button
    * Embed Type = Entity, Entity Type = Media
    
* Add button to Editor
    * Configuration --> Text Formats and Editors
    * Configure desired editor
    * Add Button (Media Library) to Button Group
    * Activate Display embedded entities
    * Disable restirct images
    * For Embeded Videos: Select "Full Content"

## Media Browser
* Configuration --> Entity Browser
    * Add new Entity Browser
    * Display plugins = iFrame
    * Auto Open entity Browser = true

* Create View to display Media
    * Select Media to be displayed
    * Add field: Entity Browser bulk select
    
* Add Media Browser To Embed Button
    * Set Media Library as Entity Browser
    
* Add "Add Image" to Media Browser
    * Configuration --> Entity Browser
    * Edit desired browser
    * Widget Settings --> Add Widget Settings
    * Add widget Plugin --> "Entity Form"
    * Configure Upload Form (Type = Media, Bundle = Image)

* Adjust Upload Form
    * Structure --> Display Modes --> Form Modes
    * Add From Mode --> Media
    * Name e.g. "Library"
    * In Structure --> Media --> Image, select Display Form Layouts from Dropdown
    * Custom Display Settings --> activate "Library"
    * New Tab appears --> "Library"
    * Adjust form in this tab
    * In Configuration --> Entity Browser --> Set Form Mode in Widget to "Library"
    
    
## User Roles and Permissions
* People --> Roles --> Add Role
* Dropdown --> Edit Permissions
    * Set permissions as desired
    * Tip: use multiple browser to validate settings
* Use Override Node Options to set granular capabilities