# Using The Events Calendar tribe_context()

## What is Tribe__Context? 
`Tribe__Context` is a class built into The Events Calendar code as a way to fetch values from various sources in a flexible and ordered manner, kind of like a table of contents and a way to bring some order to the chaos of a WordPress site. This provides a dynamic and versatile way to read values from different contexts and sources in the WordPress ecosystem.

### Locations
The `Tribe__Context` class maintains a list of registered context locations, each associated with a specific data field or functionality. All of these locations can be read (return the data associated with them) and some of the location can be written (change the data associated with them)

Baseline TEC & ET Locations:
- `post_id`: Retrieves the ID of the current post (if available).
- `permalink_structure`: Retrieves the permalink structure option from the WordPress settings.
- `plain_permalink`: Checks if the permalink structure is empty to determine if it's a plain permalink.
- `posts_per_page`: Reads and writes the number of posts per page (pagination) from and to various sources.
- `is_main_query`: Determines if the current query is the main query on the page.
- `paged`: Reads and writes the current page number for paginated queries from and to various sources.
- `page`: Reads and writes the current page number from and to various sources.
- `name`: Reads and writes the name/post_name of the current post from and to various sources.
- `post_type`: Determines the current post type by analyzing the request URL.
- `single`: Checks if the current query is for a single post.
- `taxonomy`: Reads and writes the current taxonomy from and to various sources.
- `post_tag`: Reads and writes the current post tag (or tag taxonomy) from and to various sources.
- `bulk_edit`: Reads if the current request is for a bulk edit action.
- `inline_save`: Checks if the current request is for an inline post save action.
- `event_display`
- `view`
- `view_data`
- `event_date`
- `event_sequence`
- `ical`
- `start_date`
- `end_date`
- `featured`
- `tribe_events_cat`
- `remove_date_filters`
- `event_display_mode`
- `tribe_event_display`
- `keyword`
- `events_per_page`
- `month_posts_per_page`
- `now`
- `start_of_week`
- `tec_post_type`
- `event_post_type`
- `venue_post_type`
- `organizer_post_type`
- `event_category`
- `view_url`
- `view_prev_url`
- `view_request`
- `earliest_event_date`
- `shortcode`

ECP Locations:
- `hide_subsequent_recurrences`: Controls the visibility of subsequent recurrences in the context.
- `geoloc_search`: Manages the geolocation search in the context.
- `geoloc_lat`: Reads and writes the latitude for geolocation in the context.
- `geoloc_lng`: Reads and writes the longitude for geolocation in the context.
- `event_manager`: Determines if the current context is related to the event manager.

- `event_manager`
- `related_series`
- `tec_organizer_category`
- `tec_venue_category`
