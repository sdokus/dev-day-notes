# Seat Layout and Reservation - Exploratory QA 

## Phase 1 - Set up Sandbox
1. Create a new InstaWP sandbox.
2. Download the following plugins from `#tec-bot-sandbox` using the command `bot package feat/slr-support for [plugin]`: TEC, ECP, ET, and ETP
    - I am getting an error for ETP license not being valid but Leah says that is expected and okay. 
3. Download the [slr-test.zip](https://github.com/the-events-calendar/event-tickets-seating-service/blob/routes-local-development/dev/plugins/slr-test.zip) file. 
4. Upload and activate each of these plugins to the sandbox.
5. Using the Slack bot run `bot deploy seating routes-local-development to staging`
6. Head over to the `Tickets > __TEST__ Setup` section and set the “Service Backend URL” and “Service Frontend URL” to Staging. 
7. Set up Tickets Commerce with Stripe.

(Found the formal instructions for testing [here](https://docs.google.com/document/d/1DiWKWqeE-4ca0rrpW26qzoktB62UkRUZqihTUhV75Z4/edit?usp=sharing))

(Also able to just use this link to auto-create sandbox: https://app.instawp.io/launch?t=slr-testing-site&d=v2)

(Also found this [Alpha Version Demo](https://drive.google.com/file/d/13tQe_l7Ua_NkFFkzjPXcszzHg4gkEYQY/view?t=2) which was helpful for orienting to what is expected or not)

## Phase 2 - Explore SLR 
- :white_check_mark: Submit a couple of events through CE: 1 with tickets and 1 without tickets
- :white_check_mark: Add new seating map and seat layout
- :white_check_mark: Add event with block editor and seat layout tickets
- :white_check_mark: Simulate checking out seats as an admin 
  - :beetle: Potential issue where admin email overrides purchaser email on success screen - this exists in non-SLR zips too (pre-existing)
- :white_check_mark: Simulate checking out seats in incognito window
- :x: Add event with seat layout tickets with classic editor (not available bc of Classic Editor)
- :x: Submit CE event with seat layout ticket (not available bc of Classic Editor)
- :x: Add Series Pass with seat layout tickets (not available bc of Classic Editor)
- :beetle: Duplicate an event with existing seat layout ticket
  - Seat layout tickets duplicated - one with original event's capacity and one with "fresh" capacities
  - On save, seat layout tickets converted to "regular" tickets and capacity changed to 0 available on backend, shows as "unlimited" on frontend
  - Already reported in spreadsheet
- :white_check_mark: Activating WooCommerce and then resubmitting an event with tickets
  - Having both TC and WC activated defaults to TC being the ticket handler with CE submitted tickets with no option to switch this while submitting a ticket. 
- On CE event:
  - :white_check_mark: Manually add attendee 
  - :white_check_mark: Move attendee to ticket on same event
  - :x: Attempting to access "Seats" tab on CE event with tickets - shows "Something went wrong with the Seat Layout tool. Try again or go to our knowledge base for troubleshooting help."
  - 
- Deleting Attendees
- Moving Attendees' seats
- 