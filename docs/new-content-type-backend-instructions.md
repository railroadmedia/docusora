<!-- new-content-type-backend-instructions -->

New Content Type Backend Instructions
=========================================================================

Jonathan, March 2019

1 - Add New Content-Type And Create AddEvent Calendar
--------------------------------------------------------------------------- 

### 1.1 - Add to Musora Config

1. Are you adding a new show, or a semester-pack?
    1. if show or other non-semester-pack content, add content type to these **Musora** files:
        1. /config/add-event.php
            1. "eligible-types"
            1. "nice-names"
        1. /config/railcontent.php
            1. "types-for-calendars"
    1. if semester-pack:
        1. create item in brand-appropriate "*semester-packs-for-calendars*"
            * just the slug of the parent content (the content with the type "semester-pack", parent to the "semester-pack-lessons"). Array is indexed - no key necessary.
        1. create item in brand-appropriate "*semester-pack-schedule-labels*"
            * make the key is the parent's slug
            * make the value a string that will be have the dashes replaced by spaces and will be shown in all-caps.    
1. Commit and deploy changes to Musora


### 1.2 - SSH into production Musora

1. ssh into Musora (production) container\* and run the following options of the "AddEventCommand" (`$ php artisan AddEvent {application}`)
    1. "*CreateAllCalendarsForBrand*"        
    1. "*getCalendarIdsProduction*" (note that a "*getCalendarIdsSandbox*" command is available)
        1. Copy the resultant array
1. Paste the above copied values into the array of the relevant application's "*config/**add-event.php***" config file.
    * Protip: output is formatted to allow simple replacement of entire array—no need to hunt down and place just the one new item.
1. Commit and deploy changes to the relevant application

\* to ssh into a production container, from railenvironment_manager container, run the "*kubectlset*" command (`$ r kubectlset`) (Protip: use the alias "kset" (`$ kset`)), selecting the appropriate options when prompted. Then run the "*kubectlExec*" command (`$ r kubectlExec`) (Protip: use the alias "kx" (`$ kx`)).


### 1.3 - Adding to CMS

Does the content for the new type already exist in the CMS?
* If **NO**, (the content does *not* yet exist) your work here is done—as the content is created it will be synchronized with AddEvent.
* If **YES**, (the content *does* already exist), then the content was *not* syncronized with AddEvent as it was created, and therefore you must now run a command to update AddEvent's record. 
	1. ssh into Musora (production) container\*
	2. run the artisan command "AddEventCommand" (`$ php artisan AddEvent {application}`)
	3. run the "*syncForBrand*" option


2 - New Semester-Pack NOT Requiring AddEvent Calendar
------------------------------------------------------------------------

1. Add parent-slug to brand-appropriate "*semester-packs-for-calendars*"
    * just the slug of the parent content (the content with the type "semester-pack", parent to the "semester-pack-lessons"). Array is indexed - no key necessary.
    * When adding a new semester-pack that does *not* require an AddEvent Calendar, it is only necessary to add this to the application's config. You don't need to add it to Musora's config. 
1. Commit and deploy the application
