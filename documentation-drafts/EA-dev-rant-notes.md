# Dev Rant: Event Aggregator w/ Luca

## Notes
- Client = website running Events Calendar 
- "Under the hood" Google Calendar, iCalendar, and .ics are all the same, just different names 
- Any request (other than .csv file) to a URL (for example) is firing a request to the EA server to import _something_
- Server goes to URL and if it can access the API, downloads the file, makes the file uniform (translates) and then sends back to the client website
- At time of preview, all the data has been received from the requested source, it just needs to be imported into the client website
- If there are a lot of events, it needs to repeat this process through multiple requests
- Failures can happen at either step (requesting the data or importing the data)
  - EA requests data from source (i.e. Google Calendar) repeatedly, the source can deny this request or could have some failure that happens somewhere between getting the request and sending the data
- There is a check of a hash for an expected value to make sure the data received is valid
- Three servers "talking" to each other:
  - [client website] <---> [EA server] <---> [source website]
- 25 events are processed at a time, with a 30 second time limit
- Background operation (not foreground), which means during peak hours if the servers are too busy the imports can fail
- Transients are pieces of information stored in the options table that took a long time to retrieve 
  - Time that the info is stored is set by developers 
  - Other plugins can also delete all transients 
- Cron = scheduled tasks to "try" but can only happen when website is visited? 
  - "real" crons do not depend on users to hit website in order to run 
- Reasons queue gets stuck:
  - Disruption at the options table level 
  - Customer tries deleting things in the database 
- Queue has a self-cleaning process every 15 minutes (check happens on a cron, which only happens when someone uses the website)
- 2 queue processing systems in EA:
  - Asynchronous (same system as WooCommerce) ((more solid))
  - Cron-based (older version)
- Google/Eventbrite/Meta doesn't make this process easy by always sending all events, not just updated ones as a way of intentionally slowing down imports as a way to try to keep people using their service
  - Websites have to expose their user information in these APIs, but they don't want to 
  - Websites also put limits on how many API requests you can do per day
- Duplicates are created because logic airs on the conservative side to make sure that events are not deleted unintentionally (i.e. if the source has very similar events but the id is different, the logic says to keep both as an intentional way of avoiding deleting events that shouldn't be deleted)
- API needs to be publically accessible in order to work since EA server needs to be anonymous 
  - otherwise tokens would be needed and customers using EA would need to be taken to the source site in order to get permission
- Is there any limit to how many events can be imported using EA in one import? No, but it will take more time the more events you try to import
- If there is a failed import, that is communicated back to the EA server so that import does not count towards the import limit
- Distributed Denial of Service Attack 
- RB = recurring backend engine (AKA the custom tables)