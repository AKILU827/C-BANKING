Paul Lubwika-2025559522                                                                                                     

Tenson Simulunga-2025015922                                                                                   

Christopher Msimuko-2025554164                                                                     

Kabuku Michelo-2025552530

 Rockview University Student Portal & Admin System

A simple web application designed for students and staff to manage and track student fee payments and academic clearance status.

Features

Student Portal (`index.html`)
Secure Authentication: Firebase-based login for students.
Dashboard View:** Displays student profile information (name, student number, program, level).
Payment History:** Section to view past transactions (implied).
Clearance Status: Shows the current academic/financial clearance status.
PDF Generation:** Uses **jsPDF** for generating reports or payment slips (implied by script import).

Admin Dashboard (`admin.html`)
  Secure Authentication: Firebase-based login for staff/administrators.
  Student Management: View a list of all students.
  Search/Filter: Ability to search for students by name, student number, or program.
  Clearance Control: Functionality to view, edit, and update a student's clearance status (pending, approved, rejected).

Login Pages
Student Login (`login.html`): Standard email/password login for students.
  Staff Login (`staff-login.html`): Separate email/password login for staff/administrators.

 Technologies Used

   Frontend: HTML5, Vanilla JavaScript
Styling: Tailwind CSS (via CDN)
Backend/Database/Auth: Firebase (Authentication and Firestore)
Utility: sPDF** (for client-side PDF generation in the student portal)

File Structure

The project consists of four main HTML files:

| File Name | Description | Audience |

| `index.html` | The main Student Portal dashboard. | Students |
| `login.html` | The Login Page for students. | Students |
| `admin.html` | The Admin Dashboard for managing students and clearance. | Staff/Admins |
| `staff-login.html` | The login Page for staff and administrators. | Staff/Admins |

Setup and Installation

This project relies heavily on Firebase for user authentication and data storage.

 1. Firebase Project Setup

1. In order to Create a Firebase Project: Go to the [Firebase Console](https://console.firebase.google.com/) and create a new project.
2.  Enable Services:
    Authentication: Enable the Email/Password sign-in method.
    Firestore Database: Create a new Firestore database.
3.  To get Configuration: In the Firebase project settings, find your Web App configuration snippet. It look like this:

    javascript
    const firebaseConfig = {
      apiKey: "YOUR_API_KEY",
      authDomain: "YOUR_AUTH_DOMAIN",
      projectId: "YOUR_PROJECT_ID",
      storageBucket: "YOUR_STORAGE_BUCKET",
      messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
      appId: "YOUR_APP_ID"
    };
    ```

 2. Update Files with Config

You will need to insert your `firebaseConfig` details into all four HTML files (`index.html`, `admin.html`, `login.html`, and `staff-login.html`). Look for the section where Firebase is initialized and replace the placeholder configuration.

3. Firestore Database Structure

The application expects certain collections to exist in Firestore:
`students`: Stores student data (e.g., `fullName`, `studentNumber`, `program`, `email`, `clearanceStatus`).
`admins`: Stores admin/staff user data. A user needs to exist in this collection to be redirected to `admin.html` after logging in via `staff-login.html`.

 4. Running Locally

Since this is a set of static HTML files, you can simply open them in your web browser:

1.  Open login.html for the student login page.
2.  Open staff-login.html for the admin login page.


 Usage
Staff/Admin Access

1.  Navigate to staff-login.html.
2.  Log in with an email/password that has been registered in **Firebase Authentication** AND has a corresponding document in the **`admins`** Firestore collection.
3.  You will be redirected to the Admin Dashboard (`admin.html`).

Student Access

1.  Navigate to `login.html`.
2.  Log in with a student email/password registered in **Firebase Authentication**.
3.  If the user does not exist in the `students` collection, the system may auto-create a basic record (check the script logic in `login.html`).
4.  You will be redirected to the **Student Portal** (`index.html`).
