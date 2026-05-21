# Namma Vastra - Weaver to Market Mobile Application

> **"Namma Vastra" means "Our Fabric" in Kannada.**
> An Android application that connects handloom weavers of Ilkal and Molakalmuru, Karnataka directly to urban buyers — no middlemen, fair prices, and AI-assisted marketing.

---

## Project Overview

**Namma Vastra** is a native Android application built in **Kotlin** as part of the **MindMatrix Industry Readiness Programme — Android Internship (Project 03)**.

The app digitally empowers handloom weavers by giving them:
- A **public digital storefront** (Loom Gallery) to showcase their sarees
- A **fair price calculator** so they never undersell
- **AI-generated product descriptions** (Gemini API) for professional listings
- **Direct WhatsApp contact** with urban buyers — zero middlemen
- A **Trend Board** showing what colours and patterns are in demand in cities
- A **Weaver's Story** section documenting the cultural heritage of Ilkal and Molakalmuru craft

---

## Problem Statement

Ilkal and Molakalmuru weavers create world-class handloom sarees, but:

| Problem | Impact |
|---------|--------|
| Middlemen take 40–60% of retail value | Weavers earn far below fair price |
| No urban trend visibility | Slow-moving inventory, unsold stock |
| Zero digital presence | Urban buyers cannot discover them |
| No pricing knowledge | Weavers undersell without knowing it |
| Undocumented heritage | Reduced premium brand value |

**Namma Vastra solves all five problems in one simple Android app.**

---

## Screenshots

> Add screenshots of your running app here.
> Suggested: Splash Screen, Home/Trend Board, Loom Gallery, Saree Detail, Price Calculator, Weaver's Story, Upload Screen.

```
[ Splash Screen ]    [ Trend Board ]    [ Loom Gallery ]
[ Saree Detail  ]    [ Calculator  ]    [ Weaver Story ]
```

---

## Features

### Must Have (Implemented)
- [x] **Splash Screen** — Branded 2.5s launch screen
- [x] **Trend Board** — 5 curated fashion trends + 8 colour palette swatches
- [x] **Loom Gallery** — 2-column RecyclerView grid of saree listings
- [x] **Saree Detail Screen** — Full details with WhatsApp and Call buttons
- [x] **WhatsApp Direct Inquiry** — Pre-filled message opens directly in WhatsApp
- [x] **Direct Call Button** — One-tap phone dial to weaver
- [x] **Price Calculator** — Yarn type + zari type + labour cost formula with 35% profit margin
- [x] **Upload Saree** — Image picker + form with validation + Coil preview
- [x] **Weaver's Story** — 4 real weaver profiles from Ilkal and Molakalmuru
- [x] **Bottom Navigation** — 4-tab navigation with Jetpack Navigation Component

### Good to Have (Planned)
- [ ] Firebase Live Gallery (real Firestore data)
- [ ] Firebase Storage image upload
- [ ] Firebase Authentication (Email/Password login)
- [ ] Gemini AI auto-description generator
- [ ] Smart Price Tag (Fair Price / Low Price / Warning)
- [ ] Search and filter gallery
- [ ] Kannada language toggle

---

## Tech Stack

| Technology | Role |
|-----------|------|
| **Kotlin** | Primary programming language |
| **Android Studio** | IDE for development and debugging |
| **XML Layouts** | UI design (ConstraintLayout, CardView) |
| **View Binding** | Type-safe view references |
| **RecyclerView** | Gallery list, Trend list, Story list |
| **Jetpack Navigation** | Fragment navigation + BottomNavigationView |
| **Firebase Auth** | Email and Password authentication |
| **Firebase Firestore** | NoSQL cloud database |
| **Firebase Storage** | Saree image storage |
| **Coil 2.x** | Async image loading with crossfade |
| **Google Gemini API** | AI product description generator |
| **WhatsApp Deep Link** | wa.me buyer-weaver direct contact |
| **Git + GitHub** | Version control |
| **Gradle** | Build system and dependency management |
| Min SDK | **API 24 (Android 7.0)** |
| Target SDK | **API 34 (Android 14)** |

---

## Project Structure

```
NammaVastra/
├── app/
│   ├── src/
│   │   └── main/
│   │       ├── java/com/nammaVastra/app/
│   │       │   ├── adapter/
│   │       │   │   ├── ColorTrendAdapter.kt      # Colour palette grid adapter
│   │       │   │   ├── SareeAdapter.kt           # Loom Gallery RecyclerView adapter
│   │       │   │   ├── TrendAdapter.kt           # Trend Board list adapter
│   │       │   │   └── WeaverStoryAdapter.kt     # Weaver Story list adapter
│   │       │   ├── model/
│   │       │   │   ├── Saree.kt                  # Saree data class
│   │       │   │   ├── Trend.kt                  # Trend data class
│   │       │   │   └── WeaverStory.kt            # Weaver profile data class
│   │       │   └── ui/
│   │       │       ├── MainActivity.kt           # Navigation host with BottomNav
│   │       │       ├── SplashActivity.kt         # Splash screen (2.5s)
│   │       │       ├── loomgallery/
│   │       │       │   ├── LoomGalleryFragment.kt     # 2-column saree grid
│   │       │       │   ├── SareeDetailActivity.kt     # Detail + WhatsApp + Call
│   │       │       │   └── UploadSareeActivity.kt     # Upload form with image picker
│   │       │       ├── pricecalculator/
│   │       │       │   └── PriceCalculatorFragment.kt # Cost-plus price formula
│   │       │       ├── trendboard/
│   │       │       │   └── TrendBoardFragment.kt      # Trends + colour palette
│   │       │       └── weaverstory/
│   │       │           └── WeaverStoryFragment.kt     # Weaver heritage profiles
│   │       └── res/
│   │           ├── layout/                        # All 8 XML screen layouts
│   │           ├── drawable/                      # Icons and drawable assets
│   │           ├── navigation/
│   │           │   └── nav_graph.xml              # Navigation graph
│   │           ├── menu/
│   │           │   └── bottom_nav_menu.xml        # Bottom navigation menu
│   │           └── values/
│   │               ├── colors.xml                 # App colour palette
│   │               ├── strings.xml                # All string resources
│   │               └── themes.xml                 # App theme
│   ├── build.gradle                               # App-level dependencies
│   └── google-services.json                       # Firebase configuration
├── build.gradle                                   # Project-level build file
├── settings.gradle                                # Project settings
└── README.md                                      # This file
```

---

## Price Calculator Formula

The Price Calculator uses a detailed cost-plus formula designed specifically for handloom weavers:

```
Yarn Cost    = Length (metres) × Cost per metre (based on yarn type)
Zari Cost    = Fixed cost based on zari type selected
Labour Cost  = Weaving days × ₹350 per day (fair wage)
Overhead     = (Yarn + Zari + Labour) × 10%
Total Cost   = Yarn + Zari + Labour + Overhead
Profit       = Total Cost × 35%
Final Price  = Total Cost + Profit
```

**Yarn Types and Costs per Metre:**
| Yarn Type | Cost/Metre |
|-----------|-----------|
| Pure Silk | ₹180 |
| Cotton-Silk Blend | ₹90 |
| Pure Cotton | ₹45 |
| Art Silk | ₹60 |

**Zari Options:**
| Zari Type | Fixed Cost |
|-----------|-----------|
| No Zari | ₹0 |
| Light Zari Border | ₹400 |
| Heavy Zari Border | ₹900 |
| Full Zari Work | ₹2,000 |

---

## WhatsApp Integration

When a buyer taps **"Contact via WhatsApp"** on the Saree Detail screen:

```kotlin
val message = "Hello! I'm interested in purchasing your *$sareeName* saree 
               listed on Namma-Vastra app for ₹$price. 
               Could you please share more details?"

val url = "https://wa.me/$cleanPhone?text=${Uri.encode(message)}"
```

WhatsApp opens with this message pre-filled, directed to the weaver's number.

---

## Setup and Installation

### Prerequisites
- Android Studio (latest stable version)
- Android device or emulator running API 24+
- Firebase project (google-services.json already included)
- Internet connection

### Steps to Run

**Step 1 — Clone the repository**
```bash
git clone https://github.com/YOUR_USERNAME/NammaVastra.git
cd NammaVastra
```

**Step 2 — Open in Android Studio**
```
File -> Open -> Select the NammaVastra folder
```

**Step 3 — Sync Gradle**
```
Android Studio will prompt "Gradle files have changed" -> Click "Sync Now"
Wait for BUILD SUCCESSFUL
```

**Step 4 — Run on device**
```
Connect Android phone via USB
Enable USB Debugging (Settings -> Developer Options -> USB Debugging ON)
Click the green Run button in Android Studio
Select your device
```

**Step 5 — Run on emulator**
```
Tools -> Device Manager -> Create Device
Select Pixel 4 -> API 34
Click Run
```

### Firebase Setup (if using your own Firebase project)

1. Go to [Firebase Console](https://console.firebase.google.com)
2. Create a new project or use existing
3. Add Android app with package name: `com.nammaVastra.app`
4. Download `google-services.json` and replace in `app/` folder
5. Enable Firebase Authentication (Email/Password)
6. Create Firestore Database (Mumbai region)
7. Set up Firebase Storage

---

## Dependencies

All dependencies are in `app/build.gradle`:

```groovy
// Firebase
implementation platform('com.google.firebase:firebase-bom:32.6.0')
implementation 'com.google.firebase:firebase-auth-ktx'
implementation 'com.google.firebase:firebase-firestore-ktx'
implementation 'com.google.firebase:firebase-storage-ktx'

// Navigation
implementation 'androidx.navigation:navigation-fragment-ktx:2.7.5'
implementation 'androidx.navigation:navigation-ui-ktx:2.7.5'

// Image Loading
implementation 'io.coil-kt:coil:2.5.0'

// UI
implementation 'com.google.android.material:material:1.10.0'
implementation 'androidx.recyclerview:recyclerview:1.3.2'
implementation 'androidx.cardview:cardview:1.0.0'
implementation 'androidx.constraintlayout:constraintlayout:2.1.4'

// Lifecycle
implementation 'androidx.lifecycle:lifecycle-viewmodel-ktx:2.6.2'
implementation 'androidx.lifecycle:lifecycle-livedata-ktx:2.6.2'
```

---

## Screens Overview

| Screen | Class | Description |
|--------|-------|-------------|
| Splash | `SplashActivity` | 2.5s branded launch screen |
| Trend Board | `TrendBoardFragment` | Fashion trends + colour palette grid |
| Loom Gallery | `LoomGalleryFragment` | 2-col saree grid with FAB upload |
| Saree Detail | `SareeDetailActivity` | Full detail + WhatsApp + Call |
| Upload Saree | `UploadSareeActivity` | Image picker + form + validation |
| Price Calculator | `PriceCalculatorFragment` | Detailed cost-plus formula |
| Weaver's Story | `WeaverStoryFragment` | 4 real weaver heritage profiles |
| Navigation Host | `MainActivity` | BottomNav + NavHostFragment |

---

## Sample Data

The app includes pre-loaded sample data for demonstration:

**Sample Sarees (6 listings):**
- Ilkal Kasuti Silk — ₹4,500 (Ramaiah M, Ilkal)
- Molakalmuru Pure Silk — ₹6,200 (Kavitha D, Molakalmuru)
- Ilkal Cotton Blend — ₹2,800 (Shivanna K, Ilkal)
- Molakalmuru Bridal — ₹12,000 (Girija R, Molakalmuru)
- Ilkal Geometric Design — ₹3,800 (Manjunath S, Ilkal)
- Molakalmuru Pastel — ₹8,500 (Sumathi P, Molakalmuru)

**Trending Styles (5 trends):**
- Earthy Tones Revival (Summer 2024)
- Geometric Borders (All Season)
- Pastel Zari Work (Wedding Season)
- Nature-Inspired Motifs (Festive 2024)
- Indigo and White Contrast (Year Round)

---

## Impact

| Stakeholder | Benefit |
|------------|---------|
| **Weavers** | 40–60% more income by eliminating middleman |
| **Weavers** | Fair pricing knowledge via cost-plus calculator |
| **Weavers** | Professional AI descriptions without English skills |
| **Buyers** | Authentic handloom at fair prices |
| **Buyers** | Direct artisan contact via WhatsApp |
| **Society** | Karnataka's Ilkal and Molakalmuru craft heritage preserved digitally |

---

## Developer

| Field | Details |
|-------|---------|
| **Name** | Abuzar Yaseen |
| **USN** | 1NH22EC004 |
| **Institute** | New Horizon College of Engineering |
| **Programme** | MindMatrix Industry Readiness Programme |
| **Internship** | Android App Development using Generative AI |
| **Project** | Project 03 — Namma Vastra |
| **Year** | 2026 |

---

## Acknowledgements

- **MindMatrix** — Industry Readiness Programme mentorship and guidance
- **Google Firebase** — Backend infrastructure (Auth, Firestore, Storage)
- **Google Gemini API** — Generative AI for product description
- **Ilkal and Molakalmuru Weavers** — The real heroes this app is built for

---

## License

This project is developed as part of an internship programme at MindMatrix.
All rights reserved — New Horizon College of Engineering, 2026.

---

*Namma Vastra — Every saree has a story. Now the world can hear it.*
