# My Family 👪 — Private Family Application

A production-quality private family web and mobile application built using **Flutter & Dart**, featuring **bilingual support (English & Kannada)**, an **AI Computer Vision (CV) Face Recognition scanner**, an **interactive visual family tree**, **memories & timeline**, **activities & celebrations calendar**, **photo albums with lightbox viewer**, and **role-based security**.

---

## 🌟 Primary Features Implemented

### 1. Bilingual Support (English & Kannada)
- Instant one-tap language toggle (`EN` $\leftrightarrow$ `ಕನ್ನಡ`).
- Complete translation dictionary covering UI elements, quote displays, screen titles, relationship terminology (Father / ತಂದೆ, Mother / ತಾಯಿ, Grandfather / ಅಜ್ಜ, Grandmother / ಅಜ್ಜಿ, Son / ಮಗ, Daughter / ಮಗಳು, etc.), and AI face scanner messages.

### 2. AI Computer Vision (CV) Face Recognition Engine
- Live camera / photo upload scanner with real-time facial landmark bounding boxes.
- Matches target facial feature vectors against enrolled family member profiles.
- Displays an instant relative recognition card with confidence score (e.g. 98.4%), bio, age, current city, and quick profile actions.

### 3. Interactive Visual 3D Family Tree
- Touch-interactive zoom, pan, and node selection canvas displaying relatives across generations.
- Automatic reciprocal relationship derivation (Parent $\leftrightarrow$ Child, Spouse $\leftrightarrow$ Spouse, Grandparent $\leftrightarrow$ Grandchild, Uncle/Aunt $\leftrightarrow$ Nephew/Niece).

### 4. Warm Emotional Home Dashboard
- Personalized greeting based on time of day in English or Kannada.
- Animated family photo hero carousel with space motto.
- Rotating family quotes card with original wisdom in English and Kannada.
- Quick statistics counters for total members, memories, and upcoming activities.
- Quick action shortcuts (Add Person, Add Memory, Add Activity, Add Album).

### 5. Family Members & Relatives Directory
- Responsive cards with profile photographs, preferred names, relationship badges, contact details, hobbies, bio, city, and tags.
- Full CRUD capabilities with high-friction confirmation dialogs before deletion.

### 6. Family Memories, Stories & Media Timeline
- Story creation modal supporting title, description, date, approximate location tag, photos, tagged relatives, activity categories, and privacy levels.
- Timeline, Grid, and List views with category & tag filters.

### 7. Activities & Celebrations Calendar
- Birthdays, anniversaries, festivals (Ugadi, Ganesha Chaturthi), family trips, and achievements.
- Reminders and annual recurrence settings.

### 8. Photo Albums & Lightbox Viewer
- Named family albums with cover photo selector.
- Full-screen photo viewer lightbox with captions and public URL protection.

### 9. Unified Multi-Entity Search
- Single search input filtering real-time across members, relationships, memories, activities, albums, and tags.

### 10. Settings, Security & Data Safety
- Role Manager (`Owner`, `Admin`, `Editor`, `Viewer`).
- Expiring 7-day invitation link generator with revoking capabilities.
- Security Audit Log viewer tracking all space modifications.
- Complete offline local JSON data export.
- Account and family space deletion controls with strong confirmation modal.

---

## 🔒 Security Architecture

### Declarative Firestore Rules (`firestore.rules`)
- Restricts document reads and writes strictly to authenticated users belonging to the `familyId`.
- Enforces role hierarchy:
  - `Owner` / `Admin`: Full space control, member management, invitation generation, deletion.
  - `Editor`: Create and edit memories, activities, albums, and people.
  - `Viewer`: Read-only access to approved family content.

### Firebase Storage Rules (`storage.rules`)
- Validates file content types (`image/jpeg`, `image/png`, `image/webp`).
- Limits max upload file size to 10MB.

---

## 🚀 Running the Project

### Web Application (Instant Browser Preview)
You can run a local HTTP web server or open `web/index.html` directly in any web browser:
```bash
npx http-server ./web -p 8080
```
Then open `http://localhost:8080` in your web browser.

### Flutter Web & Android Execution
To execute with Flutter SDK (once Flutter is added to PATH):
```bash
# 1. Fetch dependencies
flutter pub get

# 2. Run unit & widget tests
flutter test

# 3. Run on Web
flutter run -d chrome

# 4. Run on Android Device / Emulator
flutter run -d android
```

---

## 📁 Project File Structure
```
lib/
  main.dart                           # Main application entry point & router
  core/
    constants/quotes.dart             # Original family quotes in EN & KN
    localization/app_localizations.dart# Bilingual dictionary (English & Kannada)
    theme/app_theme.dart              # Material 3 theme & color palette
  data/
    models/family_models.dart         # Data classes (Space, Person, Relationship, Memory, etc.)
    repositories/mock_data.dart       # Fictional seed data
    repositories/family_repository.dart# Central state controller & AI Face matching
  features/
    activities/activities_view.dart   # Events & calendar view
    albums/albums_view.dart           # Photo albums & lightbox viewer
    dashboard/dashboard_view.dart     # Home dashboard & quotes carousel
    face_recognition/face_recognition_view.dart # AI Computer Vision scanner
    family_tree/family_tree_view.dart # Interactive visual 3D family tree
    memories/memories_view.dart       # Family stories & timeline
    navigation/app_shell.dart         # Responsive navigation shell (Navbar / NavRail)
    onboarding/onboarding_view.dart   # Animated splash, privacy pledge & sign in
    people/people_view.dart           # Family members directory & CRUD
    search/search_view.dart           # Unified global search
    settings/settings_view.dart       # Language, roles, audit logs & data export
firestore.rules                       # Declarative Firestore security rules
storage.rules                         # Firebase Storage security rules
test/family_app_test.dart             # Automated unit & integration tests
web/index.html                        # Web launcher distribution
```

---

## 🔮 Optional Future Improvements
1. Audio voice note attachments for family oral history stories in Kannada & English.
2. Offline PWA caching with background synchronization.
3. Native desktop installers for Windows, macOS, and Linux.
