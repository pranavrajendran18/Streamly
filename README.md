# Streamly - Music Streaming Application

Streamly is a music streaming application developed as a part of the project course AppDev2 Project for the Diploma Level of IT Madras BS Online Degree in Data Science and Application. The project utilizes Flask for the backend and Vue.js for the frontend.

## Models

### User Model
Represents users with attributes like first name, last name, email, password, role, and timestamps for creation and last login. Contains a one-to-many relationship with the Playlist model.

### Playlist Model
Represents playlists with attributes like name, user ID (foreign key), art URL, and a many-to-many relationship with the Song model. The many-to-many relationship with the Song model is defined through the `playlist_song_association` table.

### Genre Model
Represents music genres with attributes like an ID and name. Linked to the Song model through a many-to-many relationship using the `song_genre_association` table.

### Song Model
Represents individual songs with attributes like name, lyrics, file path, cover path, artist name, user ID (foreign key), album ID (foreign key), creation timestamp, play count, and ratings. Includes relationships with User, Album, Genre, and Rating models.

### Rating Model
Represents ratings given by users to songs and albums with attributes like rating value, user ID (foreign key), song ID (foreign key), and album ID (foreign key). Provides relationships with User, Song, and Album models.

### Artist Model
Represents artists with attributes like name and a one-to-one relationship with the User model.

### Album Model
Represents albums with attributes like name, artist ID (foreign key), art URL, and a one-to-many relationship with Song and Rating models.

## Overall System Design

### API Endpoints
The system has different endpoints for various functionalities, including user authentication, admin operations, and user-specific actions such as creating playlists, rating songs, and searching.

### Authentication and Authorization
JWT tokens are used for user authentication and authorization. Endpoints like `/login`, `/refresh`, and `/signup` handle user authentication, while specific endpoints like those under `/admin` and `/artist` are protected for authorized users.

### File Uploads
Endpoints like `/upload/album` and `/upload/song` handle file uploads for album covers and song files, respectively.

### Admin Operations
Endpoints under `/admin` provide functionalities like retrieving admin dashboard statistics, logging in as an admin, and removing albums or songs.

### User and Artist Actions
Endpoints under `/api` and `/artist` provide functionalities like creating playlists, rating albums and songs, searching, and accessing user profiles.

### CDN Endpoint
The `/cdn/{filename}` endpoint serves files from the CDN, facilitating efficient file handling.

### Error Handling
The system provides appropriate error responses for different scenarios, enhancing user experience and aiding in debugging.

### Overall Documentation
The API documentation is structured using Swagger (backend/api/api.yaml), providing clear information about endpoints, parameters, and responses.

## Additional Features

- Redis and Celery have been used for sending scheduled reminders to users.
- Automated monthly reports are sent to artists containing various statistics and performance reports.

## System Environment
The project was developed on a native Linux (Ubuntu 22.04) system.

