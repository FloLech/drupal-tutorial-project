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

## Theming
* Located in web/themes
* Create Sub / Child theme baes on Parent (override components)
* In case of Bootsrtap:
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
Configuration --> Search pages --> Regenerate Index
Module: Search API