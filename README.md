# WatchParty

WatchParty is a real-time collaborative video-watching platform that enables multiple users to join a shared room and watch videos in synchronized playback. The system ensures consistent video state across all participants, including play, pause, and seek actions, controlled by a designated host.

---

## Overview

WatchParty addresses the challenge of asynchronous media consumption in shared environments. It provides a seamless experience for users to watch videos together in real time, regardless of their location.

The platform maintains synchronization through event-driven communication and ensures that new participants joining a session are aligned with the current playback state. Integrated room-based chat allows participants to communicate while watching together.

## Features

- Real-time room creation and joining using unique identifiers
- Host-controlled playback for synchronized viewing
- Automatic synchronization for late-joining users
- Real-time communication using WebSockets
- Integrated chat functionality within rooms
- Responsive user interface across devices

## Tech Stack

### Frontend
- React.js
- CSS

### Backend
- Node.js
- Express.js
- Socket.IO

### Database
- MongoDB Atlas

### Deployment
- Vercel (Frontend)
- Render (Backend)

## Deployment Instructions

### Backend on Render

1. Add `render.yaml` to the repository root. The repository already includes a `render.yaml` file for the backend service.
2. Connect the repository to Render and select the `main` branch.
3. Configure the following environment variables:
   - `MONGO_URI` = Your MongoDB Atlas connection string
   - `CLIENT_URL` = Your deployed Vercel frontend URL, such as `https://your-app.vercel.app`
4. Configure the service with:
   - **Build command:** `npm install`
   - **Start command:** `npm start`
   - **Working directory:** `server`

If the previous Render deployment was deleted, create a new service from the repository or redeploy using the existing `render.yaml` configuration.

### Frontend on Vercel

1. Create a new Vercel project using the repository.
2. Set the root directory to `client`.
3. Configure the following environment variable:
   - `REACT_APP_BACKEND_URL` = Your deployed Render backend URL
4. Configure the build settings:
   - **Build command:** `npm run build`
   - **Output directory:** `build`

## Environment Variables

### Frontend

```env
REACT_APP_BACKEND_URL=https://your-backend.onrender.com
```

### Backend

```env
MONGO_URI=your_mongodb_connection_string
CLIENT_URL=https://your-app.vercel.app
```

Replace the example URLs and database credentials with your actual deployment values.

## Local Setup

### 1. Clone the Repository

```bash
git clone <your-repository-url>
cd <your-repository-name>
```

### 2. Install Dependencies

Install the frontend dependencies:

```bash
cd client
npm install
```

Install the backend dependencies:

```bash
cd ../server
npm install
```

### 3. Configure Environment Variables

Create the required environment files and configure the MongoDB connection string and frontend/backend URLs for local development.

### 4. Run the Application

Start the backend from the `server` directory:

```bash
npm start
```

Start the frontend from the `client` directory in a separate terminal:

```bash
npm start
```

## Key Implementation Details

- **Playback synchronization:** Uses event-driven communication through Socket.IO to synchronize playback events across connected clients.
- **Host-controlled playback:** Host actions trigger updates that are propagated to other participants in the room.
- **Late-join synchronization:** New participants receive the current playback state and timestamp when joining an active session.
- **Authoritative state management:** The backend maintains the room's playback state to help ensure consistency across clients.
- **Real-time chat:** Enables participants to communicate within shared viewing rooms.

## Future Enhancements

- Support for additional media platforms
- Improved reconnection and error-handling strategies
- Enhanced user interface and interaction feedback
- Scalability improvements for larger concurrent rooms

## Authors

Developed collaboratively by a team of two.

- **Contributor 1:** [Aryan Kanas]
- **Contributor 2:** [Harguneet Kaur]

## License

This project is intended for educational and demonstration purposes. Add an explicit open-source license, such as the MIT License, if you intend to distribute it under those terms.
