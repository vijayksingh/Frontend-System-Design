# Frontend-System-Design
A collection of notes and examples related to Frontend system design. 

I am going to follow RADIO Framework to solve System Design Questions. 
A quick summary : 
> Start by understanding the Requirements, defining the high level Architecture and the Data Model. Then define the Interfaces between the components in the product and talk about any Optimizations or dive deep into specific areas which require special attention

### What is RADIO about?
- Requirements Exploration: Understand the problem thoroughly and determine the scope by asking a number of clarifying questions.  
- Architecture/High-level Design: Identify the key components of the product and how they are related to each other.  
- Data Model: Describe the various data entities, the fields they contain and which component(s) they belong to.  
- Interface Definition (API): Define the interface (API) between components in the product, functionality of each API, their parameters and responses.  
**Optimizations and Deep Dive**: Discuss about possible optimization opportunities and specific areas of interest when building the product.  

## Examples and Questions related to System Design. 

### System Design (Google Calender)
To create a Google Calendar application, the following requirements and frontend component design would be necessary:

- Requirement: The calendar application should allow users to create, edit, and delete calendar events.
  - Frontend component design: The calendar application would include a "Create Event" form that allows users to input the details of a new event, such as the title, location, start and end time, and any other relevant information. The form would also include buttons for saving and canceling the event. The application would also include an "Edit Event" form that allows users to modify the details of an existing event, as well as a delete button for removing the event from the calendar.
  - API Design
    - POST: The calendar application would include a `POST /events` endpoint that allows clients to create a new event by sending a request with the event details as the request body. The endpoint would return the newly created event object as the response
    - PUT: The application would also include a `PUT /events/{id}` endpoint that allows clients to update an existing event by sending a request with the updated event details as the request body. The endpoint would return the updated event object as the response
    - DELETE: Finally, the application would include a `DELETE /events/{id}` endpoint that allows clients to delete an event by sending a request with the event ID as the URL parameter. The endpoint would return a success or error response to indicate whether the event was successfully deleted

- Requirement: The calendar application should allow users to view and navigate their calendar events by day, week, or month.
  - Frontend component design: The calendar application would include a main calendar view that displays the events for the selected time period (day, week, or month) in a grid format. The calendar view would include controls for switching between the different time periods and for moving forward or backward in time. The application would also include a "Day" view that shows all events for a specific day in a list format, as well as a "Week" view that shows all events for a week in a grid format.
  - API Design: 
    - GET: The calendar application would include a `GET /events` endpoint that allows clients to retrieve a list of events for a specific time period. The endpoint would accept query parameters for specifying the start and end date of the time period, as well as pagination parameters for controlling the number of events returned. The endpoint would return an array of event objects that fall within the specified time period

- Requirement: The calendar application should allow users to invite other users to their calendar events.
  - Frontend component design: The calendar application would include an "Invite" button on the "Create Event" and "Edit Event" forms that allows users to select other users from their contacts list and invite them to the event. The application would also include a notification system that alerts users when they have been invited to an event, and allows them to accept or decline the invitation.
  - API design:
    - POST: The calendar application would include a `POST /events/{id}/invitations` endpoint that allows clients to invite other users to an event by sending a request with the user IDs as the request body. The endpoint would


- Requirement: The calendar application should allow users to set reminders for their calendar events.
  - Frontend component design: The calendar application would include a "Reminders" section on the "Create Event" and "Edit Event" forms that allows users to set one or more reminders for an event. The reminders could be set to trigger at a specific time before the event, or on a recurring basis. The application would also include a notification system that sends reminders to the user when they are due.
  - API Design: 
    - POST: /events/{id}/reminders: This endpoint would allow clients to create a new reminder for a specific event by sending a request with the reminder details as the request body. The request body could include fields for the reminder type (e.g. time-based or recurring), the trigger time or frequency, and any other relevant data. The endpoint would return the newly created reminder object as the response
    - GET /events/{id}/reminders: This endpoint would allow clients to retrieve a list of reminders for a specific event. The endpoint would accept query parameters for filtering the reminders (e.g. by type or trigger time), as well as pagination parameters for controlling the number of reminders returned. The endpoint would return an array of reminder objects for the specified event.
    - PUT /events/{id}/reminders/{reminder_id}: This endpoint would allow clients to update an existing reminder for a specific event by sending a request with the updated reminder details as the request body. The endpoint would return the updated reminder object as the response.
    - DELETE /events/{id}/reminders/{reminder_id}: This endpoint would allow clients to delete a reminder for a specific event by sending a request with the reminder ID as the URL parameter. The endpoint would return a success or error response to indicate whether the reminder was successfully deleted.


Overall, the requirements and frontend component design for a Google Calendar application would involve a combination of forms, views, controls, and notifications to enable users to manage and interact with their calendar events in a user-friendly and intuitive manner.

### System Design : Chat Application






