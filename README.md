# Aid-Link 🤝

**Aid-Link** is an Android application designed to connect **volunteers** with **organizations** that need assistance.

The platform allows organizations to publish volunteering opportunities, while volunteers can browse available opportunities, search for relevant posts, and register for events.

---

## 📱 Overview

Aid-Link provides a centralized platform for managing volunteering opportunities and connecting volunteers with organizations.

The application supports two types of users:

* 👤 **Volunteers** – Browse and search for volunteering opportunities and register for events.
* 🏢 **Organizations** – Create and manage volunteering opportunities and review registered volunteers.

The application uses **Firebase** for authentication, cloud data storage, file storage, and notifications.

---

## ✨ Features

### 🔐 Authentication

* Email & password authentication
* Google Sign-In
* Remember Me functionality
* Password reset via email
* User session management
* Automatic redirection for remembered users

### 👤 Volunteer

Volunteers can:

* Create a volunteer account
* Browse available volunteering opportunities
* Search posts by:

  * Title
  * Description
  * Category
  * Organization
* View additional opportunity details
* Register for volunteering opportunities
* Unregister from opportunities
* Receive registration notifications

### 🏢 Organization

Organizations can:

* Create an organization account
* Upload organization images
* Upload supporting PDF documents
* Create volunteering opportunities
* Edit existing posts
* Delete posts
* View registered volunteers
* Select/approve volunteers
* Deactivate opportunities after volunteers are approved
* Send notifications to approved volunteers

### 📢 Notifications

The application includes a notification system using Firebase:

* Registration confirmation notifications
* Volunteer approval notifications
* Firebase Cloud Messaging (FCM) token management
* Notifications stored in Firestore

### 📱 User Interface

The application uses:

* Android Activities
* Android Fragments
* RecyclerView
* Material Design components
* Bottom navigation
* Search functionality
* Role-based UI behavior

---

## 🏗️ Architecture

The project is structured around Android Activities, Fragments, model classes, and Firebase services.

### Main application flow

```text
                    ┌─────────────────┐
                    │   Aid-Link App  │
                    └────────┬────────┘
                             │
                     ┌───────▼───────┐
                     │   Login Page  │
                     └───────┬───────┘
                             │
                ┌────────────┴────────────┐
                │                         │
        ┌───────▼───────┐       ┌────────▼────────┐
        │    Volunteer  │       │   Organization  │
        └───────┬───────┘       └────────┬────────┘
                │                         │
                └────────────┬────────────┘
                             │
                     ┌───────▼───────┐
                     │   Dashboard   │
                     └───────┬───────┘
                             │
              ┌──────────────┼──────────────┐
              │              │              │
        ┌─────▼─────┐  ┌─────▼─────┐  ┌────▼─────┐
        │   Home    │  │  Profile  │  │ Settings │
        └─────┬─────┘  └───────────┘  └──────────┘
              │
        ┌─────▼─────┐
        │   Posts   │
        └───────────┘
```

---

## 🔥 Firebase

Aid-Link uses several Firebase services:

### Firebase Authentication

Used for:

* Email/password authentication
* Google authentication
* Account creation
* Password reset
* Sign-out

### Cloud Firestore

Used to store application data such as:

```text
users
organizations
posts
notifications
```

Posts contain information such as:

* Title
* Description
* Date
* Location
* Category
* Organization
* Image URL
* Registered volunteers
* Active status

### Firebase Storage

Used for organization-related files, including:

* Images
* PDF documents

### Firebase Cloud Messaging

FCM is used to manage notification tokens and deliver notifications to users.

---

## 🧩 Main Components

### Activities

| Activity                           | Purpose                                       |
| ---------------------------------- | --------------------------------------------- |
| `MainActivity`                     | Login and authentication                      |
| `RegistrationTypeActivity`         | Select volunteer or organization registration |
| `VolunteerRegistrationActivity`    | Volunteer registration                        |
| `OrganizationRegistrationActivity` | Organization registration                     |
| `ForgotPasswordActivity`           | Password reset                                |
| `DashboardActivity`                | Main application dashboard                    |
| `PostActivity`                     | Create/edit volunteering posts                |

### Fragments

| Fragment           | Purpose                                       |
| ------------------ | --------------------------------------------- |
| `HomeFragment`     | Display and search volunteering opportunities |
| `ProfileFragment`  | User profile                                  |
| `SettingsFragment` | Application settings and sign-out             |

### Models

| Class         | Purpose                                  |
| ------------- | ---------------------------------------- |
| `User`        | Represents an application user           |
| `Post`        | Represents a volunteering opportunity    |
| `UserSession` | Manages the current user's local session |

### Adapters

`PostAdapter` manages the display and interaction of volunteering posts inside the RecyclerView.

---

## 🔄 Example User Flow

### Volunteer

```text
Register
   ↓
Login
   ↓
Dashboard
   ↓
Browse Opportunities
   ↓
Search / View Details
   ↓
Register
   ↓
Receive Notification
```

### Organization

```text
Register
   ↓
Upload Organization Information
   ↓
Login
   ↓
Dashboard
   ↓
Create Opportunity
   ↓
Receive Volunteer Registrations
   ↓
Review Volunteers
   ↓
Approve Volunteers
   ↓
Opportunity Becomes Inactive
   ↓
Approved Volunteers Receive Notification
```

---

## 🛠️ Technologies

* **Android**
* **Java**
* **Kotlin**
* **XML**
* **Firebase Authentication**
* **Cloud Firestore**
* **Firebase Storage**
* **Firebase Cloud Messaging (FCM)**
* **Google Sign-In**
* **Material Components**
* **RecyclerView**
* **SharedPreferences**
* **Gson**

---

## 📂 Project Structure

A simplified view of the project structure:

```text
app/
└── src/
    └── main/
        ├── java/
        │   └── com/example/welcom/
        │       ├── MainActivity.java
        │       ├── DashboardActivity.java
        │       ├── PostActivity.java
        │       ├── RegistrationTypeActivity.java
        │       ├── VolunteerRegistrationActivity.java
        │       ├── OrganizationRegistrationActivity.kt
        │       ├── ForgotPasswordActivity.java
        │       │
        │       ├── HomeFragment.java
        │       ├── ProfileFragment.java
        │       ├── SettingsFragment.java
        │       │
        │       ├── Post.java
        │       ├── PostAdapter.java
        │       ├── User.java
        │       └── UserSession.java
        │
        └── res/
            ├── layout/
            ├── menu/
            ├── drawable/
            └── values/
```

---

## 🚀 Getting Started

### Prerequisites

Before running the project, make sure you have:

* Android Studio
* Android SDK
* A Firebase project
* A configured Android application in Firebase

### Installation

1. Clone the repository:

```bash
git clone https://github.com/<your-username>/Aid-Link.git
```

2. Open the project in **Android Studio**.

3. Connect the project to Firebase.

4. Add the required Firebase configuration file:

```text
google-services.json
```

to:

```text
app/
```

5. Sync the Gradle project.

6. Build and run the application on an Android device or emulator.

---

## 🔒 Security Note

Firebase configuration and authentication credentials should **not** be committed to a public repository.

Before publishing the project, make sure that:

* API keys and credentials are handled appropriately.
* Firebase Security Rules are configured correctly.
* Server-side credentials are never stored directly in the Android application.
* Sensitive FCM credentials are not hardcoded in client-side code.

---

## 🔮 Future Improvements

Potential improvements include:

* Improved profile management
* Full notification center
* Push notification architecture improvements
* Better post creation UI
* Image previews for posts
* Location/map integration
* Volunteer history
* Organization dashboards
* Improved role-based permissions
* Better Firebase security rules
* Improved error handling
* UI/UX improvements
* Migration toward a cleaner architectural pattern such as MVVM

---

## 🎯 Project Goal

Aid-Link aims to make volunteering more accessible by providing a simple platform where organizations can publish opportunities and volunteers can discover and participate in them.

**Connect. Volunteer. Make an impact. 🤝**
