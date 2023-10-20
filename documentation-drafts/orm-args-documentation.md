# The Events Calendar ORM - Creating an Event

## Description
This document provides a list of acceptable arguments and their descriptions for creating an event using the Events Calendar ORM.

## Arguments

### Post Fields

#### 'author'
- Type: Integer
- Description: The event author ID
- Example: 'author' => 1

#### 'date'
- Type: String
- Description: The event publication date. If in the future the status will automatically be 'Scheduled' 
- Format: 'YYYY-MM-DD HH:MM:SS'
- Example: 'date' => '2023-05-19 17:00:00'

#### 'date_utc'
- Type: String
- Description: The event publication date (UTC time zone).
- Format: 'UTC±X'
- Example: 'date_utc' => 'UTC-5'

#### 'description'
- Type: String
- Description: The event description. 
- Example: 'description' => 'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.'

#### 'excerpt'
- Type: String
- Description: The event excerpt.
- Example: 'excerpt' => 'Lorem ipsum dolor sit amet.'

#### 'slug'
- Type: String
- Description: The event slug.
- Example: 'slug' => 'my-event-slug',

### 'status'
- Type: String
- Description: The event post status. 
- Options: 'publish', 'draft', or 'pending'
- Example: 'status' => 'publish

#### 'title'
- Type: String
- *Required*
- Description: The title of the event.
- Example: 'title' => 'My Event'

### Event Meta Fields

#### 'timezone'
- Type: String (**** Included in test as required, but in REST endpoints required is false? )
- Description: The timezone location where the event will take place. 
- Format: 'Country/City'
- Example: 'timezone' => 'America/New_York'

#### 'all_day'
- Type: Boolean
- Description: Whether the event lasts the whole day or not 
- True Examples: 'Yes', 1, true
- False Examples: 'No', 0, false, null
- Example: 'all_day' => 1

#### 'start_date'
- Type: DateTime
- *Required*
- Description: The start date and time of the event.
- Format: 'YYYY-MM-DD HH:MM:SS'
- Example: 'start_date' => '2023-05-20 14:30:00'

#### 'end_date'
- Type: DateTime
- *Required*
- Description: The end date and time of the event.
- Format: 'YYYY-MM-DD HH:MM:SS'
- Example: 'end_date' => '2023-05-20 17:00:00'

#### 'image'
- Type: String
- Description: The event featured image ID or URL
- Example: 'image' => 'http://example.com/vacation.jpg'

#### 'cost'
- Type: String (**** Is it a string though? Worked as an integer)
- Description: The event cost. Should be a numeric value. 0 = free. Only used if no ticketing plugin is active.
- Example: 'cost' => 28.50

#### 'website'
- Type: String
- Description: The event website URL. (*** in other examples this was 'url' but in the API it's 'website')
- Example: 'website' => 'http://example.com'

### Event Presentation Data

#### 'show_map'
- Type: Boolean
- Description: Whether the event should show a map or not.
- True Examples: 'Yes', 1, true
- False Examples: 'No', 0, false, null
- Example: 'show_map' => 'No'

#### 'show_map_link'
- Type: Boolean
- Description: Whether the event should show a map link or not.
- True Examples: 'Yes', 1, true
- False Examples: 'No', 0, false, null
- Example: 'show_map_link' => true

#### 'hide_from_listings'
- Type: Boolean (***** also works as 'hide_from_upcoming'? Or is that different?)
- Description: Whether events should be hidden in the calendar view or not.
- True Examples: 'Yes', 1, true
- False Examples: 'No', 0, false, null
- Example: 'hide_from_listings' => null

#### 'sticky'
- Type: Boolean 
- Description: Whether the event should be sticky in the calendar view or not.
- True Examples: 'Yes', 1, true
- False Examples: 'No', 0, false, null
- Example: 'sticky' => 1

#### 'featured'
- Type: Boolean 
- Description: Whether the event should be featured on the site or not.
- True Examples: 'Yes', 1, true
- False Examples: 'No', 0, false, null
- Example: 'featured' => false

### Taxonomies

#### 'categories'
- Type: Array [Integer]
- Description: The event category ID or name. (*** Is there a different meta for singular 'category'? In the API endpoint it's plural, but in other places it's singular (same for tags vs tag) )
- Example: 'categories' => [ 1 , 9 ]

#### 'tags'
- Type: Array [Integer]
- Description: The event tag ID or name.
- Example: 'tags' => [ 4 , 6 , 12 ]

### Linked Posts

#### 'venue'
- Type: Array [Integer]
- Description: The event venue ID or data. (**** For 'or data' is that to create a new venue from the ORM? Should an example be included?)
- Example: 'venue' => [ 2 ]

#### 'organizer'
- Type: Array [Integer]
- Description: The event organizer ID or data. 
- Example: 'organizer' => [ 1 , 24 ]

### Not Included in REST Endpoints, but found elsewhere

#### 'duration'
- Type: Integer
- Description: Duration of event specified in minutes.
- Example: 'duration' => 300 

#### 'recurrence'
- Type: String
- Description: Recurrence rule if the event repeats. 
- Format: iCalendar RRULE format. Compatibility with the iCalendar standard is one of the new features of the CT1 implementation and it can be used to replace the verbose recurrence format used in the _EventRecurrence post meta, if preferred
- Example: 'recurrence' => 'RRULE:FREQ=DAILY;COUNT=10’

#### 'series'
- Type: Integer
- Description: The Series ID.
- Example: 'series' => 3

#### 'currency_symbol'
- Type: String
- Description: The currency symbol for the cost of the event. 
- Example: 'currency_symbol' => '$'

#### 'currency_position'
- Type: String
- Description: Where the currency symbol is in relation to the cost. 
- Example: 'currency_position' => 'postfix' 


## Usage Example

```php
$args  = [
    'title'                     => 'A test event',
    'start_date'                => '2023-01-01 09:00:00',
    'end_date'                  => '2023-01-01 11:00:00',
    'all_day'                   => 0,
    'timezone'                  => 'Europe/Paris',
    'status'                    => 'publish',   
    'organizer'                 => [ $organizer_1, $organizer_2 ],
    'category'                  => $cat,
    'tag'                       => $tag,
    'show_map'                  => 1,
    'show_map_link'             => false,
    'cost'                      => 23.89,
    'currency_symbol'           => '$',
    'currency_position'         => 'postfix',
    'url'                       => 'http://the-event.com'
    'hide_from_upcoming'        => 1
    'sticky'                    => 1,
    'featured'                  => 1,
];

$event = tribe_events()->set_args( $args )->create();
