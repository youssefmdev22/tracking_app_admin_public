# 📊 Tracking App Admin

## 🚀 1. Project Overview

**Tracking App Admin** is a comprehensive, enterprise-grade Flutter application built for administrators and managers. It provides a centralized dashboard to track staff attendance, manage shifts, handle leave requests, and oversee organizational branches and departments. Built with scalability and maintainability in mind, this project strictly adheres to **Clean Architecture** principles and the **MVI (Model-View-Intent)** presentation pattern.

## 🛠️ 2. Tech Stack

- **Framework**: Flutter (SDK ^3.10.0)
- **Language**: Dart
- **Architecture**: Clean Architecture + Model-View-Intent (MVI)
- **State Management**: `flutter_bloc` (Cubit)
- **Dependency Injection**: `get_it` & `injectable`
- **Routing**: `go_router` (with `StatefulShellRoute` for nested navigation)
- **Backend & Database**: `supabase_flutter` for networking/database, `flutter_secure_storage` for local secure storage
- **Push Notifications**: `firebase_messaging` & `flutter_local_notifications`
- **Location Services**: `geolocator`, `google_maps_flutter`, `geocoding` (for location sync and tracking)
- **UI & Styling**: `flutter_screenutil` (responsive sizing), `toastification` (alerts), `flutter_svg`
- **Data Serialization**: `json_annotation` & `json_serializable`
- **Localization**: `flutter_intl` (Multilingual support including English & Arabic)

## 🏗️ 3. Architecture

This project is built from the ground up prioritizing separation of concerns, utilizing **Clean Architecture** combined with the **MVI (Model-View-Intent)** pattern:

1. **Domain Layer**: The innermost pure Dart layer completely isolated from Flutter dependencies. Formed by Entities, UseCases (Callable Classes), and Repository Interfaces.
2. **Data Layer**: Implements Domain repositories. It contains Models (which implement `toEntity()`), DataSources (Remote/Local), and API interactions wrapped in elegant safe data calls returning `DataResult<T>`.
3. **Presentation Layer**: Handles UI and State, implementing strictly the MVI pattern:
   - `{Feature}ViewModel` (Cubit class): Processes intents via a single public method `doIntent()`.
   - `{Feature}Events`: Sealed classes defining user interactions.
   - `{Feature}State`: Immutable state management using `Equatable`.
4. **Core Layer**: Shared utilities, Dependency Injection setup (`@injectable`), context Theme Extensions (avoiding raw `Theme.of(context)` arrays), and Constant mappings (`ConstKeys`, `AppImages`).

## ✨ 4. Features

- **🛡️ Secure Authentication**: Custom unified login flow tailored for managers and admins.
- **👥 Staff & User Management**: Add, update, and closely track employees, system users, and managers.
- **🏢 Branch & Department Control**: Organize the company hierarchy effortlessly with full CRUD capabilities.
- **📅 Shift Management**: Allocate, configure, and schedule working hours for distinct roles seamlessly.
- **📝 Leave Requests**: Streamlined inbox format to review, approve, or reject employee leave requests.
- **📊 Detailed Reports**: Generate and view comprehensive attendance and activity overview logs.
- **📍 Location & Tracking Sync**: Background location sync integration communicating reliably with Supabase endpoints.
- **🔔 Real-time Notifications**: Keep administrators quickly alerted regarding critical staff updates.
- **⚙️ Application Settings**: In-depth app configurations inclusive of regional localization.

## 📁 5. Folder Structure

```text
lib/
├── core/                   # Shared logic, DI config, extensions, and styling
├── data/                   # API logic, local storage, Models, and Repository Impls
├── domain/                 # Pure business logic: Entities, UseCases, and Repo Interfaces
├── presentation/           # UI and State Management module implementations
│   ├── branch/
│   ├── department/
│   ├── home/
│   ├── leave_requests/
│   ├── login/
│   ├── manager/
│   ├── notification/
│   ├── overview/
│   ├── reports/
│   ├── settings/
│   ├── shift/
│   ├── splash/
│   ├── staff/
│   └── user/
├── generated/              # Auto-generated outputs (Localization, DI logic)
├── l10n/                   # Translation dictionaries (ARB files)
└── main.dart               # Core application entry point
```

## 🚀 6. How to Run the Project

1. **Clone the repository**:
   ```bash
   git clone https://github.com/youssefmdev22/tracking_app_admin_public.git
   cd tracking_app_admin_public
   ```

2. **Install dependencies**:
   ```bash
   flutter pub get
   ```

3. **Generate code (for DI, JSON serialization, and localization)**:
   ```bash
   flutter pub run build_runner build --delete-conflicting-outputs
   ```

4. **Environment Setup**:
   Ensure you have configured your Supabase environment variables and included `google-services.json` (Android) / `GoogleService-Info.plist` (iOS) in respective project folders to enable Firebase services.

5. **Run the App**:
   ```bash
   flutter run
   ```

## 📸 7. Screenshots Section

### 📱 Mobile

| Login & Overview | Staff & Profile | Branches & Departments |
| :---: | :---: | :---: |
| <img src="screenshots/login.png" width="220" alt="Login"/> | <img src="screenshots/staff.gif" width="220" alt="Staff"/> | <img src="screenshots/branches.gif" width="220" alt="Branches"/> |
| <img src="screenshots/overview.gif" width="220" alt="Overview"/> | <img src="screenshots/staff_profile.gif" width="220" alt="Staff Profile"/> | <img src="screenshots/departments.gif" width="220" alt="Departments"/> |

| Shifts & Leaves | Managers & Reports | Settings & More |
| :---: | :---: | :---: |
| <img src="screenshots/shifts.gif" width="220" alt="Shifts"/> | <img src="screenshots/managers.gif" width="220" alt="Managers"/> | <img src="screenshots/settings.gif" width="220" alt="Settings"/> |
| <img src="screenshots/leave_requests.gif" width="220" alt="Leave Requests"/> | <img src="screenshots/reports.gif" width="220" alt="Reports"/> | <img src="screenshots/language_feature.gif" width="220" alt="Language"/> |
| <img src="screenshots/notifications.png" width="220" alt="Notifications"/> | <img src="screenshots/reports_excel.gif" width="220" alt="Export Reports"/> | |

### 💻 Web

| Login & Overview | Staff & Profile |
| :---: | :---: |
| <img src="screenshots/web/login.png" width="400" alt="Login"/> | <img src="screenshots/web/staff.gif" width="400" alt="Staff"/> |
| <img src="screenshots/web/overview.gif" width="400" alt="Overview"/> | <img src="screenshots/web/staff_profile.png" width="400" alt="Staff Profile"/> |

| Branches & Departments | Shifts & Leaves |
| :---: | :---: |
| <img src="screenshots/web/branches.gif" width="400" alt="Branches"/> | <img src="screenshots/web/shifts.gif" width="400" alt="Shifts"/> |
| <img src="screenshots/web/departments.gif" width="400" alt="Departments"/> | <img src="screenshots/web/leave_requests.gif" width="400" alt="Leave Requests"/> |

| Managers & Reports | Settings & More |
| :---: | :---: |
| <img src="screenshots/web/managers.gif" width="400" alt="Managers"/> | <img src="screenshots/web/settings.png" width="400" alt="Settings"/> |
| <img src="screenshots/web/reports.gif" width="400" alt="Reports"/> | <img src="screenshots/web/language_feature.gif" width="400" alt="Language Feature"/> |
| <img src="screenshots/web/reports_excel.gif" width="400" alt="Export Reports"/> | <img src="screenshots/web/notifications.png" width="400" alt="Notifications"/> |

## 👨‍💻 Contributors
* [Youssef Mohamed](https://github.com/youssefmdev22)
* [Moaz Osama](https://github.com/moazosama1)
* [Mohamed Hossam El-Bably](https://github.com/Bablu521)
