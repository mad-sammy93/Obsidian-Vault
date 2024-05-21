****Business Case Study: Room Reservation Management System****

  
  

**Document versions:-**

|sr.no   |  test |   |   |   |
|---|---|---|---|---|
|1   |  Sambert |   |   |   |
|2|Name|---|---|---|
    
|**Version Number**|**Purpose/Change**|**Section**|**Author**|**Date**|
|0.1|Initial draft|-|Sambert Rodrigues, Ruchira Vaze|12/05/2024|

  
  

**Introduction:**

The Room Reservation Management System aims to streamline the process of reserving, scheduling, and utilizing meeting rooms efficiently. To tackle this challenge, we're implementing a modern and scalable solution that will allow users to check availability of meeting rooms, book rooms, managing meetings, etc.

  
  

**Technical Requirements:**

1. Include a proper Readme for easy local setup of project.
    
2. Utilize TypeScript with proper typing for enhanced code maintainability.
    
3. Write clean and understandable code, with comments where complex logic is involved.
    
4. Validate all inputs on both the API and frontend to ensure data integrity.
    
5. Prioritize security considerations throughout the development process.
    
6. Follow industry standard coding.
    
7. Minimize external library usage to maintain control over dependencies.
    

  
  

Implement docker into the project

  
  

  
  

**Key** **Requirements****:**

1. **Third-Party Authentication Integration:**
    
    1. Enable users to log in/sign up using Google along with existing log in/sign up.
        
    2. Provide a backdoor for registration/login with our system's endpoints/utilities if third-party authentication isn't preferred.
        
2. **Two-Factor Authentication:**
    
    1. Integrate a second step of authentication with any third-party authenticator app. For example,Gooogle Authenticator App, Duo Authenticator App.
        
3. **Meeting Room Booking Module:**
    
    1. Integrate the room booking with API.
        
    2. Utilize WebSockets to provide real-time updates on booking/data.
        
4. **Integrated Notifications:**
    
    1. Implement a notification system within the application to alert users about upcoming meetings, booking confirmations, and any changes to their reservations.
        
5. **Real-time Updates****(Optional)****:**
    
    1. Leverage state management, and WebSockets to deliver seamless real-time updates on ra proper Readme for easy local setup, etcoom availability and booking status.
        
6. **Seamless Backend Integration:**
    
    1. Utilize a store(Pinia, vuex)a proper Readme for easy local setup, etc for managing the application state, facilitating easy integration with existing backend services like authentication, database management, and calendar systems.
        

**User Interface:**

1. Integrate JavaScript frontend frameworks for building user interfaces.
    
2. State management library for managing state.
    
3. Design a sleek and intuitive UI to simplify room reservation processes.  
    ([https://www.figma.com/design/BzpXMXhwTqgJZM0hdNF7Ji/Office-meeting-room-management](https://www.figma.com/design/BzpXMXhwTqgJZM0hdNF7Ji/Office-meeting-room-management)).
    

5. Allow users to easily view room availability, schedule meetings, and manage bookings effortlessly.
    
6. WebSocket: Integrated framework for real-time communication.
    

**Acceptance Criteria:**

  
  

**External References:  
Figma:** [https://www.figma.com/design/BzpXMXhwTqgJZM0hdNF7Ji/Office-meeting-room-management](https://www.figma.com/design/BzpXMXhwTqgJZM0hdNF7Ji/Office-meeting-room-management)

**Swagger APIs:**
















1. ** Creation of Recurring Meetings:**
    
    - The system should allow users to create recurring meetings with customizable recurrence patterns (daily, weekly, monthly).
    - Users should be able to specify the start date and time for the recurring meetings.
2. **Recurrence Patterns:**
    
    - Users should have the option to choose different recurrence patterns such as daily, weekly, or monthly.
    - For weekly recurrence, users should be able to select specific weekdays.
3. **End Date and Indefinite Recurrence:**
    
    - Users should be able to specify an end date for recurring meetings.
    - The system should provide an option for indefinite recurrence if no end date is specified.
4. **Validation and Conflicts:**
    
    - The system should validate the recurrence pattern and end date to prevent conflicts with existing bookings.
    - If a conflict arises with an existing booking during the recurrence period, users should be notified and prompted to resolve the conflict.
5. **Modification and Cancellation:**
    
    - Users should be able to modify or cancel individual instances of a recurring meeting without affecting the entire series.
    - Changes made to a recurring meeting instance should be reflected in the system and notifications should be sent to affected participants.
6. **Visibility and Management:**
    
    - Recurring meetings should be clearly distinguishable from one-time meetings in the user interface.
    - Users should have the ability to view and manage all instances of a recurring meeting series from a centralized location.
7. **Testing:**
    
    - The functionality should undergo thorough testing to ensure reliability and accuracy in generating recurring meetings according to the specified patterns.
    - Unit tests and integration tests should cover all aspects of the recurring meeting creation, modification, and cancellation processes.
8. **User Feedback:**
    
    - Solicit feedback from users during the testing phase to identify any usability issues or improvements needed in the recurring meeting functionality.