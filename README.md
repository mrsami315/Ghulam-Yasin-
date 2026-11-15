# Haider School Staff Attendance

Firebase-backed staff attendance web app for Haider Model Computerized Public Boys School, Haiderabad Thall (PEF code 9-BHK-0002).

## Status
The app interface and Firebase client integration are prepared. **It is not live-connected until the project owner adds the Firebase Web App config, enables Email/Password Authentication, creates Firestore, publishes the rules, and tests with dummy accounts.**

## Owner setup
1. In Firebase Console, register a Web App in the correct project.
2. Copy the Web App config into `firebase-config.js`. It is not a password. Never put service-account keys or private credentials in this repository.
3. Enable Authentication > Email/Password.
4. Create a Cloud Firestore database.
5. Publish `firestore.rules` in Firestore > Rules.
6. Create each account in Authentication. Then create a Firestore document at `users/{AUTH_UID}` with fields `name` (string) and `role` (string: `staff` or `admin`). Set admin role only for the authorized school administrator.
7. Test using dummy accounts before entering real staff records.

## Data model
- `users/{uid}`: name, role (profiles are admin-managed).
- `attendance/{uid_YYYY-MM-DD}`: uid, staffName, date, checkIn, checkOut, status, createdAt.

Staff can read their own records and mark their own check-in/check-out. Admins can read all attendance records and delete records. Staff cannot edit roles or profiles.

Monthly report supports CSV export. Firestore may ask for a composite index; use the index-creation link shown by Firebase Console if prompted.
