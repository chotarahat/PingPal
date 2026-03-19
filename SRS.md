# PingPal Messaging App — Software Requirements Specification

**Prepared by:** Muhammad Neamatullah Rahat
---

## 1. Introduction

### 1.1 Purpose
This SRS outlines requirements for a retro-styled real-time messaging 
web application. The system enables users to register, authenticate, 
send direct messages, create group chats, manage a friends list, 
and share images — all within a nostalgic AIM-era interface.

### 1.2 Scope
The application serves:
- **Registered users** who can send/receive messages, manage 
  profiles, and add friends
- **Group members** who can participate in multi-user chat rooms

### 1.3 Definitions
- **JWT:** JSON Web Token — used for stateless authentication
- **DM:** Direct Message between two users
- **Socket.io:** Library for real-time bidirectional communication
- **ORM:** Object-Relational Mapper (Prisma)

---

## 2. Overall Description

### 2.1 Product Features
1. OTP/JWT Authentication & Authorization
2. Real-time direct messaging via Socket.io
3. Group chat creation and management
4. Friends list with online/offline status
5. User profile customization (avatar, bio, status)
6. Image sharing in chat
7. Message history persistence

### 2.2 User Classes
- **Guest:** Can view login/register pages only
- **Authenticated User:** Full access to messaging, friends, groups
- **Admin (future):** User management

### 2.3 Operating Environment
- Web browsers: Chrome, Firefox, Edge, Safari
- Mobile responsive
- Backend: Node.js + Express on Railway/Render
- Database: PostgreSQL via Prisma on Supabase/Railway
- Frontend: React + Vite on Netlify/Vercel

---

## 3. System Requirements

### 3.1 Functional Requirements

#### 3.1.1 Authentication
- FR-1: Users shall register with username, email, and password
- FR-2: Passwords shall be hashed with bcrypt (min 10 salt rounds)
- FR-3: Login shall return a signed JWT (1 hour expiry)
- FR-4: Protected routes shall reject requests without a valid JWT
- FR-5: Users shall be able to log out (token cleared client-side)

#### 3.1.2 Messaging
- FR-6: Users shall send direct messages to any other user
- FR-7: Message history shall persist in the database
- FR-8: New messages shall appear in real-time via Socket.io
- FR-9: Users shall see a "typing..." indicator when the other 
  party is composing
- FR-10: Users shall be able to send images as messages

#### 3.1.3 Friends & Online Status
- FR-11: Users shall send, accept, and decline friend requests
- FR-12: The friends list shall show online/away/offline status
- FR-13: Online status shall update in real-time via Socket.io
- FR-14: Users shall see a list of all registered users to 
  find friends

#### 3.1.4 Group Chats
- FR-15: Users shall create group chats with a name
- FR-16: Group creators shall add members by username
- FR-17: Group messages shall be delivered to all members 
  in real-time
- FR-18: Users shall be able to leave a group

#### 3.1.5 Profile
- FR-19: Users shall update their display name, bio, 
  and status message
- FR-20: Users shall upload a profile avatar (stored via Cloudinary)

### 3.2 Non-Functional Requirements
- NFR-1: All API communication over HTTPS in production
- NFR-2: Passwords never stored in plain text
- NFR-3: Page load under 3 seconds on standard connection
- NFR-4: Application shall be mobile-responsive

---

## 4. Technology Stack

| Layer | Technology |
|---|---|
| Frontend | React 18, Vite, React Router v6 |
| Styling | CSS Modules (retro AIM aesthetic) |
| HTTP Client | Axios |
| Real-time | Socket.io client |
| Backend | Node.js, Express.js |
| Auth | JWT, bcrypt |
| Real-time | Socket.io server |
| ORM | Prisma |
| Database | PostgreSQL |
| File Upload | Multer + Cloudinary |
| Deployment (FE) | Netlify |
| Deployment (BE) | Railway |

---

## 5. Development Plan (Agile Sprints)

| Sprint | Weeks | Features |
|---|---|---|
| Sprint 1 | 1–2 | Repo setup, auth (register/login/JWT) |
| Sprint 2 | 3–4 | Direct messaging + Socket.io real-time |
| Sprint 3 | 5–6 | Friends list + online status |
| Sprint 4 | 7 | Group chats + image sharing |
| Sprint 5 | 8–9 | Profile customization + deployment |

---

## 6. Acceptance Criteria
- All FR-1 through FR-20 are implemented and manually tested
- Application is deployed and publicly accessible
- README includes setup instructions and live demo link
