# 🎨 Android Design System with Dynamic Theming  

## 📖 Overview  
This project is a **modular, scalable Design System** built with **Jetpack Compose**, supporting **dynamic theme switching** (Light/Dark) and **brand-based theming via flavors**.  

The system is divided into four modules:  
1️⃣ **Design System Tokens (`design-system-token`)** – Stores **color, typography, dimensions, and font tokens** per brand/flavor.  
2️⃣ **Design System (`design-system`)** – Provides **custom UI components** mapped to token values.  
3️⃣ **Theme Provider (`theme-provider`)** – Manages **dynamic theme switching** and applies token mappings.  
4️⃣ **Main Application (`app`)** – Consumes **UI components and theming** from the design system.  

---

## 📂 **Project Structure**

           ┌──────────────────────────────────────┐
           │          Main Application            │
           │  (Consumes Design System .aar)      │
           └──────────────────────────────────────┘
                         ▲
                         │
          ┌──────────────────────────┐
          │     Theme Provider       │
          │ (Provides Dynamic Theme) │
          └──────────────────────────┘
                         ▲
                         │
    ┌───────────────────────────┐         ┌──────────────────────────────┐
    │    Design System (.aar)   │◄────────┤   Design System Tokens (.aar)│
    │ (Contains Custom UI)      │         │ (Provides Tokens via .aar)   │
    └───────────────────────────┘         └──────────────────────────────┘


## 🛠️ Key Features:
✅  **Modular Architecture**: Clean separation between tokens, UI, theming, and the app.
✅  **Dynamic Theme Switching**: Supports light & dark mode without app restart.
✅  **Brand-Based Theming**: Allows multiple brands via flavors.
✅  **Reusable UI Components**: Custom buttons, text styles, loaders, etc.
✅  **Token-Based Theming**: Color, typography, and dimensions are centralized and scalable.
✅  **.aar Distribution**: Both design-system and design-system-token are distributed via .aar for easy consumption.

##📌 **Final Token Flow**

┌────────────────────────────┐
│  Main Application          │
│  - Uses AppTheme()         │
│  - Calls ThemeSwitcher()   │
└────────────────────────────┘
           ▲
           │
┌──────────────────────────────┐
│  Theme Provider              │
│  - Provides Dynamic Theme    │
│  - Uses TokenProviderFactory │
└──────────────────────────────┘
           ▲
           │
┌───────────────────────────┐
│  Design System (.aar)     │
│  - Uses UI Components     │
│  - Fetches Token Values   │
└───────────────────────────┘
           ▲
           │
┌──────────────────────────────┐
│  Design System Tokens (.aar) │
│  - Provides Tokens via .aar  │
└──────────────────────────────┘

##🛠 **Implementation Plan**
Create Token Module (design-system-token)

Define tokens (colors, dimensions, typography, fonts)
Support multiple flavors
Generate .aar
Create UI Components Module (design-system)

Consume .aar from design-system-token
Implement AppLoader using mapped token values
Create Theme Provider (theme-provider)

Provide LightTokensMapper & DarkTokensMapper
Support dynamic theme switching
Integrate into the Main App (app)

Consume .aar files
Use AppTheme for dynamic theme switching




📦 android-design-system
 ├── 📁 design-system-token         # Stores design tokens (.aar file)
 │   ├── 📁 color
 │   ├── 📁 dimensions
 │   ├── 📁 fonts
 │   ├── 📁 typography
 │   └── 📝 build.gradle
 ├── 📁 design-system               # Contains UI components (.aar file)
 │   ├── 📁 components
 │   ├── 📁 themes
 │   ├── 📁 utils
 │   └── 📝 build.gradle
 ├── 📁 theme-provider              # Manages dynamic themes
 │   ├── 📁 token-mapper
 │   ├── 📁 theme-switching
 │   └── 📝 build.gradle
 ├── 📁 app                         # Main application consuming the design system
 │   ├── 📁 ui
 │   ├── 📁 viewmodel
 │   ├── 📁 data
 │   └── 📝 build.gradle
 ├── 📝 settings.gradle
 ├── 📝 README.md                   # Project Documentation
 └── 📝 LICENSE

