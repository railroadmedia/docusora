<!-- new-content-type-backend-instructions -->

Add New Content Type
========================================================================================================================

Add New Content-Type And Create AddEvent Calendar
------------------------------------------------------------------------------------------------------------------------

### Step 1: Add New Content Type

Are you adding a new show, or a semester-pack?


#### if Show

1. add content slug to these **Musora** files:
    1. in */config/add-event.php*, add to `'eligible-types'`
    1. in */config/add-event.php*, add to `'nice-names'` (and "nice name" too obviously)
    1. in */config/railcontent.php* add to `'types-for-calendars'`
1. Commit and deploy changes to Musora
    

#### if Semester Pack

##### Add to application

1. in the application's *config/railcontent.php*, Add parent-slug to `semester-packs-for-calendars`
1. Commit and deploy *the application*

If no AddEvent Calendar required, this is all that's needed—you don't need to add anything to Musora's config.


##### Add to CMS

1. add slug of the parent content to brand-appropriate "*semester-packs-for-calendars*"
1. create item in brand-appropriate "*semester-pack-schedule-labels*"
    * key is parent's slug
    * value will have dashes replaced by spaces and will be ALL CAPS.    
1. Commit and deploy changes to Musora


### Step 2: Create and Sync AddEvent Calendar

(ssh into production Musora container. See section below for details)

Does the content exist in the CMS?

* If **yes** run `$ php artisan AddEvent {application}`, select `syncForBrand`.
* If **no** run `$ php artisan AddEvent {application}`, select `CreateAllCalendarsForBrand`.

If content does *not* yet exist in the CMS, once the calendar is created—using the steps above—it will automatically be sync'd.


### Step 3: Set Calendar-Id In Application

(ssh into production Musora container. See section below for details)
    
1. run `$ php artisan AddEvent {application}`, select `getCalendarIdsProduction` option
1. copy output
1. Paste array into relevant application's "*config/**add-event.php***" file.
1. Commit and deploy changes to ***the relevant application***


2 - How To SSH Into Production Musora Container
----------------------------------------------------------------------

To ssh into a production container: 

1. from railenvironment_manager container, run the "*kubectlset*" command (`$ r kubectlset`)\*
    * Protip: use the alias "kset" (`$ kset`)
1. select the appropriate options when prompted.
1. sun the "*kubectlExec*" command (`$ r kubectlExec`)\**.
    * Protip: use the alias "kx" (`$ kx`)
