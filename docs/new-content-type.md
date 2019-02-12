
Add New Content-Type to AddEvent
========================================================================================================================

1. Add content-type to Musora files
    1. */config/**add-event.php*** → "eligible-types"
    1. */config/**add-event.php*** → "nice-names"
    1. */config/**railcontent.php*** → "types-for-calendars" array
    1. */musora/app/Services/**UrlHelperService**.php* (You'll have to figure out exactly where to put it in here)
    1. if brand is Drumeo, also add to Drumeo's UrlHelperService. Commit changes.
1. Commit and deploy changes to Musora
1. ssh into Musora (production) container\* and run the following artisan commands:
    1. `php artisan CreateAllCelendarsForBrand`        
    1. `php artisan getCalendarIdsProduction` (note that a `getCalendarIdsSandbox` command is available)
        1. Copy the output of this command
1. Paste the above copied output into the relevant application's "*config/**add-event.php***" config file.
    * Protip: output is formatted to allow simple replacement of entire array, no need to hunt down and place just the one new item).
1. Commit and deploy changes to the relevant 
application
1. Does the content for the new type already exist in the CMS?
    * If **NO**, (the content does *not* yet exist) your work here is done—as the content is created it will be synchronized with AddEvent.
    * If **YES**, (the content *does* already exist), then the content was *not* syncronized with AddEvent as it was created, and therefore you must now run a command to update AddEvent's record. 
        1. ssh into Musora (production) container\*
        2. run the artisan command `AddEventCommand`
        3. 
        * you will need to run the "*sync brand*" function of Musora's `AddEventCommand` artisan command.
        * either run this command on production (ssh into production node using railenvironment's `kx` shortcut)

\* to ssh into a production container, from railenvironment_manager container, run the "*kubectlset*" command (Protip: use the alias `kset`), selecting the appropriate options when prompted. Then run the "*kubectlExec*" command (Protip: use the alias `kx`).
