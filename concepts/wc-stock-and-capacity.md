# WooCommerce Stock and Capacity

## 1. Stock Management

### 1.1 Ticket Stock Reduction

- When an Attendee is Registered: 
  - The stock for a ticket is reduced when an attendee is registered for an event. 
  - The stock reduction logic is handled in the `attendee_decreases_inventory` method. 
    - Order Status Check: 
      - The method checks the order status. 
      - If the order is canceled or refunded and has been restocked, the inventory is not decreased. Otherwise, the inventory is decreased. 
    - Order Meta Check: 
      - For refunded orders, inventory is only decreased if the order was not marked as restocked. 
- Handling Refunds: 
  - If an order is refunded and not restocked, the stock is adjusted accordingly. The `handle_restock_action_for_refunded_order` method handles restocking of tickets when an order is refunded and ensures stock levels are updated.

### 1.2 Restocking Inventory

- Restock Action: The `add_restock_action_for_refunded_order` method adds a restock action for refunded orders, allowing admins to manually restock tickets if needed.
- Restock Processing: The `handle_restock_action_for_refunded_order` method processes the restocking by increasing stock levels and updating the order notes.

## 2. Capacity Management

### 2.1 Event Capacity

- Capacity Check: 
  - ET+ handles capacity management by monitoring the number of tickets sold and comparing it with the event’s capacity. 
  - If an event’s capacity is reached, further ticket sales are restricted.

### 2.2 Capacity Updates

- Dynamic Updates: 
  - Capacity adjustments are handled dynamically as tickets are sold or refunded. 
  - Capacity checks ensure that the event does not exceed its maximum capacity.

## 3. Attendee Management

### 3.1 Tracking Attendees

- Attendee Data: The plugin tracks attendees via methods such as `get_attendees_by_id`, which retrieves attendees associated with a specific order.
- Displaying Attendees: The `include_your_tickets` method includes a template for displaying attendees on the checkout page, showing relevant attendee information.

### 3.2 Updating Attendees

- Order Notes: The `update_order_note_for_deleted_attendee` method adds notes to WooCommerce orders when attendees are deleted, providing a record of such actions.

### 3.3 Handling Attendee Emails

- Resending Emails: The `allow_resending_email` method determines if resending an email to an attendee is permitted, considering the order status and any applied filters.

## 4. Order and Ticket Post Types

### 4.1 Post Types Management

- Order Post Types: The `get_active_order_post_type_name` method retrieves the post type name for orders, accommodating different WooCommerce order storage methods (e.g., HPOS).
- Cache Invalidation: The `filter_cache_listener_save_post_types` method ensures that changes to ticket, attendee, and order post types trigger cache invalidation to keep data consistent.
