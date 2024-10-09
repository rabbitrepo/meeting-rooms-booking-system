![Thumbnail](/demo-thumbnail.png)

https://github.com/user-attachments/assets/4ac612fc-8e42-48bc-b2d6-96169999e61d


# Background

One day, I was chatting with a friend who's an HRIS (Data Analyst). He was venting about the chaos in his company over meeting rooms—apparently, it's like a daily battle royale. Their current system is a mess, with no clear way to check if a room's actually booked, so everyone's double-booking and stepping on each other’s toes.

I casually threw out, 'Why not let me build you something better?' A custom solution, tailored exactly to their needs—and I could easily make the pricing more attractive than the usual vendors. So, I decided to dive in and start building a POC. Challenge accepted.

The project is now in the bidding phase.

# Features

## User Portal

https://github.com/user-attachments/assets/4ac612fc-8e42-48bc-b2d6-96169999e61d

- Login
    - [ ]  For an MVP, user can login with email OTP but for production integrated with Azure Auth system they use would be a better option.
- Booking History
    - User can see and managed their bookings.
- Create New Booking
    - User can create new booking.
    - User can select a room within a branch. User designated to only allowed branch (ex. for staff in Chonburi, can only book rooms in Chonburi branches).
    - After picking the room and time, user will see a clear availability of the room on that date as a easy to navigate calendar component.
    - User can add participants for a meeting. There’s full-text search capability. People can be found by nickname, email, and employee Id.
        - [ ]  In actual production, this should be integrated with their directory.
    - After booking is completed, all participants will get an email notification as well as a calendar invitation.

## Live Occupancy

![Occupancy Display](https://github.com/user-attachments/assets/6110bb16-220f-4c00-b705-f62a07ea6833)

- The system displays the real-time availability status of each meeting room, making it easy for users to see which rooms are currently occupied or available.
- The application is meant to be run on a tablet device, which will be mounted at the entrance of each meeting room for convenient access.
- The system provides a way for users to check in using a QR code displayed on the tablet.
- Before the meeting starts 15 minutes, the system will send a confirmation email to all attendees. If no one responds within 5 minutes, the room will be automatically freed up for other users to book.

## Admin Portal

…In Development

- Manage branches, meeting rooms, and permission.

# Architecture

![meeting-rooms-architecture](https://github.com/user-attachments/assets/92af2400-3808-4e7b-af20-a9d10a350e3c)

- Users will interact with the app through a web browser.
- The app is built on a microservice architecture for scalability. 
- Authentication is handled by AppWrite, which offers SDKs for both front-end and back-end, making it a great way to quickly bootstrap the project.    
- We're using MongoDB for storage—nothing too fancy. Each domain has its own database, keeping everything loosely coupled.
- Users' info and calendar invitations are managed using Microsoft Graph API.

# Source Code
- API (All services): https://github.com/rabbitrepo/meeting-rooms-booking-api
- Web Client: https://github.com/rabbitrepo/meeting-rooms-booking-client
