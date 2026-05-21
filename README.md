# Smart Mess Management Platform

## 📘 Abstract

The Smart Mess Management Platform is a cross-platform Flutter application designed to digitize hostel mess operations. The system supports role-based access for students, staff, and administrators and provides modules for menu management, complaint handling, staff workflows, attendance-related utilities, and billing support. Firebase services are used for authentication, data persistence, and cloud-backed synchronization.

## 🔎 Index Terms

Flutter, Firebase, Firebase Authentication, Cloud Firestore, mess management, role-based access control, attendance tracking, billing, complaint management.

## 1. Introduction 📘

Traditional mess administration often depends on manual recordkeeping, fragmented communication, and delayed issue resolution. This platform addresses those limitations through a digital workflow that centralizes user authentication, menu publishing, complaints, replacements, reports, and administrative operations in a single application.

The repository contains the main Flutter application and supporting modules for face attendance registration and backend processing.

## 2. Project Specifications 🧾

| Specification | Details |
| --- | --- |
| Project Name | Smart Mess Management Platform |
| Primary Frontend | Flutter application |
| Secondary Module | Face attendance app |
| Backend Service | Node.js Express API for face attendance |
| State Management | Provider |
| Authentication | Firebase Authentication, Google sign-in, email/password sign-in |
| Database | Cloud Firestore |
| File Storage | Firebase Storage |
| Supported Platforms | Android, iOS, Web, macOS, Linux, Windows |
| Dart SDK | 3.9.2 |
| Flutter Package Version | 1.0.0+1 |
| Design System | Material UI with custom app theme |

## 3. System Overview 🧩

The application is organized around three primary user roles.

- Student: views the daily menu, raises complaints, submits replacement requests, checks billing and notifications, and uses mess-related services.
- Staff: manages operational tasks, student records, analytics, settings, and mess-related reviews.
- Administrator: oversees approvals, user management, operational dashboards, and system-level reporting.

## 4. Major Modules 🏗️

### 4.1 Main Mess Management App

The root Flutter application located in the `lib/` directory provides:

- Authentication and onboarding flows
- Role-based routing
- Menu publication and menu seeding
- Complaint submission and review
- Food report and replacement workflows
- Billing and payment tracking
- Analytics and operational dashboards

### 4.2 Face Attendance Application

The `face_attendance_app/` package provides a dedicated face registration and attendance workflow. It uses camera capture and face detection to support attendance marking through a separate interface.

### 4.3 Face Attendance Backend

The `face_attendance_backend/` service is an Express-based API that supports face embedding storage, attendance marking, and utility scripts such as attendance backfilling.

## 5. Technology Stack ⚙️

- Frontend: Flutter
- State management: Provider
- Authentication: Firebase Auth and Google Sign-In
- Database: Cloud Firestore
- Storage: Firebase Storage
- Face detection: Google ML Kit face detection
- Backend runtime: Node.js
- API framework: Express

## 6. Project Structure 📂

```text
Mess-Management-Platform/
├── android/                 # Android host project
├── assets/                  # Shared application assets
├── docs/                    # Supporting documentation and scripts
├── face_attendance_app/     # Separate Flutter face attendance app
│   ├── lib/                 # Attendance app source code
│   └── pubspec.yaml         # Attendance app package configuration
├── face_attendance_backend/  # Node.js attendance API
│   └── src/                 # Express server, services, scripts, utilities
├── ios/                     # iOS host project
├── lib/                     # Main Flutter application source code
│   ├── config/              # App and Firebase configuration
│   ├── models/              # Firestore and domain models
│   ├── providers/           # Application state management
│   ├── repositories/        # Data access layer
│   ├── screens/             # UI screens and workflows
│   ├── services/            # Business logic and integrations
│   ├── utils/               # Helper utilities
│   └── widgets/             # Reusable UI components
├── test/                    # Flutter tests
├── web/                     # Web entry point and static assets
├── windows/                 # Windows host project
├── linux/                   # Linux host project
├── macos/                   # macOS host project
├── firebase.json            # Firebase project configuration
├── firestore.indexes.json   # Firestore index definitions
├── firestore.rules          # Firestore security rules
└── pubspec.yaml             # Main Flutter package configuration
```

## 7. Firestore Data Model 🗃️

### 7.1 Core Collections

- `users`: application user profiles and role data
- `mess_menu`: breakfast, lunch, snacks, and dinner menu documents
- `food_reports`: reported meal issues and resolution status
- `mess_bill_payments`: persistent payment status records
- `notifications`: in-app notification records

### 7.2 Face Attendance Collections

- `face_data`: stored face embeddings indexed by student ID
- `attendance`: date-based attendance documents with daily student subcollections

## 8. Prerequisites ✅

- Flutter SDK installed and configured
- Node.js installed for the backend service
- Firebase project access
- Firebase CLI installed
- FlutterFire CLI installed

## 9. Setup Instructions 🚀

### 9.1 Install Firebase Tools

```bash
npm install -g firebase-tools
dart pub global activate flutterfire_cli
```

### 9.2 Authenticate with Firebase

```bash
firebase login
```

### 9.3 Configure the Flutter App

Run Firebase configuration from the repository root and select the Firebase project used by this system.

```bash
flutterfire configure
```

This regenerates `lib/firebase_options.dart` for the selected platforms.

### 9.4 Fetch Dependencies

```bash
flutter pub get
```

## 10. Running the Application ▶️

### 10.1 Main Flutter App

```bash
flutter run
```

### 10.2 Face Attendance Backend

```bash
cd face_attendance_backend
npm install
cp .env.example .env
npm start
```

### 10.3 Face Attendance App

```bash
cd face_attendance_app
flutter pub get
flutter run
```

## 11. Functional Capabilities ✨

- Role-based login for students, staff, and administrators
- Digital menu viewing and menu seeding
- Complaint registration and administrative review
- Food issue reporting with resolution tracking
- Bill generation and payment state persistence
- Student and staff operational dashboards
- Face-based attendance registration and marking

## 12. Configuration Notes ⚠️

- Ensure Firebase rules and indexes are deployed before production use.
- Verify the correct Firebase project is selected during FlutterFire configuration.
- For face attendance locally, the backend may require Google application credentials.
- The Android emulator backend base URL is typically `http://10.0.2.2:3000`.

## 13. Documentation 📄

- `docs/face_attendance_setup.md` describes the face attendance module, API endpoints, and Firestore structure.
- `README.md` provides the primary project overview and setup guide.

## 14. Conclusion

The Smart Mess Management Platform provides a structured digital workflow for hostel mess operations. Its modular architecture, Firebase integration, and dedicated face attendance components make it suitable for operational tracking, student services, and administrative oversight in a single system.
