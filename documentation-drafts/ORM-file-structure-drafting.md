# ORM File Structure Drafting

## Based on Google Maps API documentation:

- APIs (they have this organized in a chart with specifics under each API)
  - Events
  - Series
  - Organizers
  - Venues
  - Tickets
  - Attendees
- Get started
  - Getting started guide
  - Create your first event
  - Search for events 

## Current Structure:
- ORM - Fetching Posts
  - Create args
    - Event specific args
    - Event creation use cases 
    - Event creation examples
  - ORM Basics
  - Query Args
    - Basic Query
    - Query Events 

## Proposed New Structure:
- ORM - Overview
  - Create
    - Events
      - Event specific args
      - Arg examples
      - Use cases
    - Venues
    - ...etc
  - Find
    - Events
    - Venues
    - ...etc
  - Delete
    - Events
    - Venues
    - ...etc
  - Update
    - Events
    - Venues
    - ...etc

## Examples:
- [ ] 'author'
- [ ] 'date'
- [ ] 'date_utc'
- [X] 'description'
- [ ] 'excerpt'
- [X] 'slug'
- [ ] 'status'
- [X] 'title'
- [X] 'timezone'
- [ ] 'all_day'
- [X] 'start_date'
- [X] 'end_date'
- [ ] 'image' (G said to skip for now)
- [X] 'cost'
- [X] 'currency_symbol'
- [X] 'currency_position'
- 
- [ ] 'url'
- 
- [X] 'venue'
- [X] 'show_map'
- [X] 'hide_from_upcoming'
- 
- [X] 'hide_from_listings'
- [X] 'sticky'
- [X] 'featured'
- 
- [X] 'categories'
- [X] 'tags'
- 

- [ ] 'organizer'
- [X] 'duration'
- 
- [X] 'recurrence'
- [ ] 'series'





