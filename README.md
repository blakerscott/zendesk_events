# Zendesk Events Module

### A custom Drupal module that interacts with the Zendesk REST API.  This module analyzes all new tickets created in a target  Zendesk instance, and adds custom tags and/or internal comments to each ticket.  The algorithm determines which tag to add, and which tickets to add an internal comment to, based on whether or not the ticket's Org has a current event in the *High Traffic Event* Google Calendar.  That information is provided via the [Calendar Events Module](https://github.com/blakerscott/calendar_events).
