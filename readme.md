# Frontend-System-Design
A collection of notes and examples related to Frontend system design. 

## Common Concepts
Most application would always have some common responsibilities no matter what the domain. 

- Authentication and Authorization
- User Profile and Settings
- Search and Recommendation

We will try to create reusable template for all these Concerns so that we can put them into our example System Design questions.

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

#### General Requirements
As a user, I want to be able to create a new account and log in to the chat application so that I can access my conversations and messages.

As a user, I want to be able to create and join conversations with other users so that I can communicate with them in real time.

As a user, I want to be able to send and receive messages in my conversations so that I can have ongoing discussions with other users.

As a user, I want to be able to add and remove participants from my conversations so that I can control who can see and contribute to the conversation.

As a user, I want to be able to search for past conversations and messages so that I can easily find information and continue previous discussions.

As a user, I want to be able to customize my settings and preferences for the chat application so that I can control how the application behaves and looks.


#### API Design 
The API design for a chat application could include the following endpoints:

`POST /users:` Create a new user account.

`POST /users/authenticate:` Authenticate an existing user and generate an access token.

`GET /conversations:` Retrieve a list of the user's conversations.

`POST /conversations:` Create a new conversation with one or more participants.

`GET /conversations/:id:` Retrieve the details and messages for a specific conversation.

`POST /conversations/:id/messages:` Send a message to a specific conversation.

`POST /conversations/:id/participants:` Add one or more participants to a specific conversation.

`DELETE /conversations/:id/participants:` Remove one or more participants from a specific conversation.

`GET /messages:` Search for past messages across all of the user's conversations.

`GET /settings:` Retrieve the user's current settings and preferences.

`PUT /settings:` Update the user's settings and preferences.

`GET /notifications:` Retrieve a list of the user's pending notifications.

#### Component Design 
- LoginForm: A component for the login or signup screen that allows users to authenticate their identity and access the application.

- ConversationList: A component that displays a list of the user's conversations and allows them to create or join new ones.

- Conversation: A component that shows the messages in a given conversation, allows the user to send new messages, and displays the list of participants in the conversation.

- Settings: A component that allows the user to customize their preferences and settings for the chat application.

- Notifications: A component that displays alerts for new messages and other events in the chat application.

- Search: A component that allows the user to search for past conversations and messages.



Overall, these endpoints would provide the necessary functionality for a chat application, allowing users to create and manage accounts, create and participate in conversations, and customize their settings and preferences.


### System Design : Pinterest 

#### Functional Requirements
- User profile and settings: Pinterest allows users to create and customize their profile, including their name, profile picture, and a bio. This component is responsible for storing and managing user profile information, as well as allowing users to update their settings, such as their email and password.

- Boards and pins: The core feature of Pinterest is the ability to save and organize images and videos into boards. This component is responsible for creating, managing, and displaying boards and pins. It must also support features such as pinning, repinning, and commenting on pins.

- Search and recommendation: To help users discover new content, Pinterest uses a search and recommendation engine that indexes and ranks content based on various factors, such as user interests, engagement, and social connections. This component is responsible for providing search and recommendation functionality to users.



#### Non Functional Requirement

#### API Design 

`GET /boards:` This endpoint allows users to retrieve a list of all the boards they have created.

`POST /boards:` This endpoint allows users to create a new board. It accepts a JSON object containing the board name and description as input.

`GET /boards/:board_id:` This endpoint allows users to retrieve the details of a specific board, identified by its board_id.

`PUT /boards/:board_id:` This endpoint allows users to update the details of a specific board, identified by its board_id. It accepts a JSON object containing the updated board name and description as input.

`DELETE /boards/:board_id:` This endpoint allows users to delete a specific board, identified by its board_id.

`GET /boards/:board_id/pins:` This endpoint allows users to retrieve a list of all the pins on a specific board, identified by its board_id.

`POST /boards/:board_id/pins:` This endpoint allows users to add a new pin to a specific board, identified by its board_id. It accepts a JSON object containing the pin URL and description as input.

`GET /boards/:board_id/pins/:pin_id:` This endpoint allows users to retrieve the details of a specific pin on a specific board, identified by the board_id and pin_id.

`PUT /boards/:board_id/pins/:pin_id:` This endpoint allows users to update the details of a specific pin on a specific board, identified by the board_id and pin_id. It accepts a JSON object containing the updated pin URL and description as input.

`DELETE /boards/:board_id/pins/:pin_id:` This endpoint allows users to delete a specific pin on a specific board, identified by the board_id and pin_id.



### System Design: Excalidraw (Drawing Tool)

#### General Requirements
- As a user, I want to be able to create a new drawing by clicking on a "New Drawing" button.

- As a user, I want to be able to select different drawing tools, such as a pen, eraser, and shape tools, to create and edit my drawing.

- As a user, I want to be able to customize the properties of my drawing tools, such as the line thickness and color, to create the desired effect.

- As a user, I want to be able to zoom and pan on the drawing canvas to see and edit my drawing in detail.

- As a user, I want to be able to save my drawing to a local or cloud-based data storage system.

- As a user, I want to be able to load and view my saved drawings from the data storage system.

- As a user, I want to be able to export my drawings in different file formats, such as JPEG, PNG, and SVG.

- As a user, I want to be able to collaborate with other users in real-time on the same drawing.

- As a user, I want to be able to see the changes made by other users on the drawing in real-time.

- As a user, I want to be able to resolve conflicts if two users try to edit the same part of the drawing at the same time.

#### API Design (Excalidraw)



