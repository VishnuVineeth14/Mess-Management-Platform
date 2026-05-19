# Smart Mess Management Platform

A multi-module system for managing hostel mess operations, including a Flutter admin/student/staff app and a face-attendance stack (Flutter client + Node.js backend).

## Project Overview

This repository contains three connected modules:

1. **Main Flutter App (`/`)**
   - Core mess management workflows for Admin, Staff, and Students
   - Firebase Auth + Firestore based data and access control
2. **Face Attendance Mobile App (`face_attendance_app/`)**
   - Captures and validates faces for attendance marking
3. **Face Attendance Backend (`face_attendance_backend/`)**
   - Express API for face embedding storage and attendance updates in Firestore

## Repository Structure

```text
Mess-Management-Platform/
├── lib/                           # Main Flutter app source (models, services, screens, widgets)
├── assets/                        # Main app assets
├── test/                          # Main app tests
├── face_attendance_app/           # Separate Flutter app for face registration/attendance
│   └── lib/
├── face_attendance_backend/       # Node.js backend for face attendance APIs
│   └── src/
├── docs/                          # Documentation and setup notes
├── tool/                          # Utility scripts
├── android/ ios/ web/ macos/ linux/ windows/  # Flutter platform targets
├── firestore.rules                # Firestore security rules
├── firebase.json                  # Firebase project config
└── pubspec.yaml                   # Main app Flutter dependencies and metadata
```

## Main App Features

- Role-based authentication (Admin, Staff, Student)
- Menu display and management workflows
- Complaint submission and tracking
- Replacement food selection
- Billing and pending bill management
- Mess cancellation flow
- Analytics dashboard

## Face Attendance Module

### Face Attendance App (`face_attendance_app`)
- Camera-based face capture
- Face registration workflow
- Attendance marking workflow

### Face Attendance Backend (`face_attendance_backend`)
- `POST /register-face`
- `GET /face-embeddings`
- `POST /mark-attendance`

For full setup and Firestore schema, see:
- `docs/face_attendance_setup.md`

## Technology Stack

- **Frontend:** Flutter (Dart)
- **Backend (face attendance):** Node.js + Express
- **Database/Auth/Storage:** Firebase (Firestore, Auth, Storage)
- **State Management:** Provider

## Prerequisites

- Flutter SDK
- Dart SDK
- Node.js + npm
- Firebase CLI
- FlutterFire CLI

Install CLIs (if needed):

```bash
npm install -g firebase-tools
dart pub global activate flutterfire_cli
```

## Setup

### 1) Configure Firebase for the main Flutter app

From repository root:

```bash
firebase login
flutterfire configure
```

### 2) Run the main Flutter app

From repository root:

```bash
flutter pub get
flutter run
```

### 3) Run face attendance backend

```bash
cd face_attendance_backend
npm install
cp .env.example .env
npm start
```

### 4) Run face attendance Flutter app

```bash
cd face_attendance_app
flutter pub get
flutter run
```

## Useful Documentation

- `docs/face_attendance_setup.md` — face attendance architecture, Firestore schema, API contracts, and local run steps

## Notes

- Main app Firebase configuration is generated in `lib/firebase_options.dart`.
- Face attendance backend defaults to port `3000` (see `face_attendance_backend/.env.example`).
- For Android emulator-to-localhost communication, use `http://10.0.2.2:3000` as backend base URL.
