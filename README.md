# ShelfChef

**Your AI-powered kitchen companion — manage your pantry, import recipes, and cook smarter with what you already have.**

ShelfChef is a native Android cooking companion app that helps users take control of their kitchen. It combines pantry management, intelligent recipe importing, grocery list organization, and a suite of kitchen tools into a single, cohesive experience. Built with Kotlin and Jetpack Compose following Clean Architecture principles.

> Built for the [RevenueCat Mobile App Hackathon](https://www.revenuecat.com/)

---

## Table of Contents

- [Written Proposal](#written-proposal)
  - [Problem Statement](#problem-statement)
  - [Target Audience](#target-audience)
  - [Solution](#solution)
  - [Monetization Strategy](#monetization-strategy)
- [Features](#features)
- [Screenshots](#screenshots)
- [Technical Documentation](#technical-documentation)
  - [Tech Stack](#tech-stack)
  - [Architecture](#architecture)
  - [Project Structure](#project-structure)
  - [Data Flow](#data-flow)
  - [Database Schema](#database-schema)
  - [RevenueCat Implementation](#revenuecat-implementation)
  - [API Integrations](#api-integrations)
  - [Notification System](#notification-system)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Setup](#setup)
  - [Build Commands](#build-commands)
- [Configuration](#configuration)
- [Contributing](#contributing)
- [License](#license)

---

## Written Proposal

### Problem Statement

Home cooks face a fragmented and frustrating kitchen experience. The average household wastes approximately 30-40% of the food they purchase, largely because people lose track of what they already have in their pantry, buy duplicate items, or let ingredients expire before they can be used. Meanwhile, recipe discovery is disconnected from what people actually have on hand — users browse recipes online, save them across dozens of bookmarks and apps, and then realize they are missing half the ingredients.

The core problems ShelfChef addresses:

1. **Food waste from poor pantry visibility.** People forget what they have, where they stored it, and when it expires. Items get buried in the back of the fridge or pantry and go to waste.

2. **Disconnected recipe management.** Recipes are scattered across bookmarks, screenshots, social media saves, and physical cookbooks. There is no single place to collect, organize, and act on recipes.

3. **Inefficient grocery shopping.** Without knowing what is already at home, people overbuy. Without organized lists tied to recipes, trips to the store are inefficient and lead to impulse purchases.

4. **The "what can I cook?" dilemma.** The most common question at mealtime — "What can I make with what I have?" — has no good answer without manually cross-referencing pantry contents against recipe ingredients.

5. **Lack of kitchen utility tools.** Home cooks frequently need measurement conversions, cooking timers, rice-to-water ratios, and ingredient substitutions, but switch between multiple apps or Google searches to find them.

### Target Audience

ShelfChef is designed for three primary user segments:

**1. Busy Home Cooks (Primary)**
- Ages 25-45, cooking 3-7 meals per week at home
- Juggling work, family, and meal planning
- Want to reduce food waste and save money on groceries
- Value convenience and time-saving tools
- Comfortable with smartphone apps but not necessarily tech-savvy

**2. Budget-Conscious Households**
- Families and individuals actively trying to reduce grocery spending
- Want to maximize the use of ingredients they already own
- Interested in meal planning around existing pantry stock
- Motivated by the financial impact of reduced food waste

**3. Cooking Enthusiasts**
- Passionate about trying new recipes from the web, social media, and video platforms
- Collect recipes from many sources and want a single organized repository
- Appreciate tools that enhance the cooking experience (timers, converters, substitutions)
- Willing to pay for premium features that support their hobby

### Solution

ShelfChef solves these problems by creating a unified kitchen management platform that connects pantry tracking, recipe management, grocery shopping, and cooking tools into one intelligent system:

- **Pantry Inventory** with expiration tracking and categorized storage locations eliminates the "what do I have?" problem.
- **Smart Recipe Import** from any URL using web scraping and AI-powered parsing lets users consolidate recipes from across the internet into one place.
- **"What Can I Cook?"** matches saved recipes against current pantry inventory, showing match percentages and missing ingredients, and suggests substitutions for near-matches.
- **AI-Powered Recipe Suggestions** go beyond saved recipes to generate entirely new recipe ideas based on available ingredients.
- **Integrated Grocery Lists** with barcode scanning, store section organization, and one-tap checkout to pantry close the loop between shopping and inventory.
- **Built-In Kitchen Tools** (timers, converters, rice calculator, substitution guides) eliminate the need to leave the app during cooking.

### Monetization Strategy

ShelfChef employs a **freemium subscription model** powered by RevenueCat, designed to let users experience core value before committing financially.

#### Free Tier

The free tier provides enough functionality for users to understand the app's value and build habits around it:

| Feature | Free Limit |
|---|---|
| Saved recipes | Up to 10 |
| URL recipe imports | Up to 5 |
| Pantry management | Unlimited |
| Grocery lists | Unlimited |
| Kitchen timer | Unlimited |
| Recipe matching ("What Can I Cook?") | Available (saved recipes only) |

#### Pro Tier (ShelfChef Pro)

The Pro tier unlocks the full experience with three subscription options:

| Plan | Billing | Value Proposition |
|---|---|---|
| **Monthly** | Recurring monthly | Low commitment entry point |
| **Yearly** | Recurring annually | ~17% savings (2 months free) |
| **Lifetime** | One-time purchase | Best value for long-term users |

**Pro features include:**
- **Unlimited recipes and URL imports** — no caps on saving or importing
- **AI-powered smart suggestions** — recipe ideas generated from pantry contents using GPT-4o-mini
- **Full kitchen tools suite** — measurement converter, rice calculator, ingredient substitutions, recipe scaler, temperature guide
- **Recipe scaling** — adjust serving sizes with automatic ingredient recalculation
- **Cloud sync** — back up and sync data across devices via Firebase

#### Why This Model Works

1. **Low barrier to entry.** The free tier is genuinely useful — unlimited pantry management, grocery lists, and timers ensure users get value from day one.
2. **Natural upgrade triggers.** Users hit recipe/import limits organically as they invest in the app, making the upgrade feel like a natural next step rather than an arbitrary gate.
3. **Multiple price points.** Monthly, yearly, and lifetime options accommodate different spending preferences and commitment levels.
4. **High retention features.** Once users build a pantry inventory and recipe collection, switching costs are high — their data lives in the app.

---

## Features

### Pantry Management
- Add, edit, and delete pantry items with detailed categorization
- **Categories:** Dairy, Produce, Meat & Seafood, Pantry Staples, Frozen, Beverages, Snacks, Condiments, Baking, and more
- **Storage locations:** Pantry, Fridge, Freezer
- Expiration date tracking with dashboard alerts for items nearing expiry
- Search and filter by category or location

### Recipe Management
- **URL Import:** Paste any recipe URL and ShelfChef extracts the title, ingredients, instructions, cook times, and images using Schema.org parsing with an AI fallback (GPT-4o-mini)
- **Manual Entry:** Add recipes by hand with full detail support
- **Favorites:** Mark and filter favorite recipes
- **Cook Tracking:** Track how many times you have cooked each recipe
- **Cook Time Filters:** Quick (<30 min), Medium (30-60 min), Long (60+ min)
- **Recipe Details:** Full view with ingredients, step-by-step instructions, and source attribution

### What Can I Cook?
- **Recipe Matching:** Cross-references saved recipes against current pantry inventory
- **Match Percentages:** See how closely your pantry matches each recipe's ingredient list
- **Missing Ingredients:** Instantly see what you would need to buy
- **Substitution Suggestions:** For 60-99% matches, the app suggests ingredient swaps so you can still cook the meal
- **AI Smart Suggestions (Pro):** GPT-4o-mini generates entirely new recipe ideas tailored to your available ingredients

### Grocery Lists
- Add items manually or directly from recipe ingredient lists
- **Store Sections:** Produce, Dairy, Meat, Frozen, Pantry, Bakery, Beverages, Snacks, Household, and more
- **Barcode Scanning:** Scan product barcodes using ML Kit + CameraX to auto-populate item details via Open Food Facts API
- **Item Photos:** Attach photos from camera or gallery
- Mark items as purchased with animated strikethrough
- Swipe-to-delete functionality
- **Checkout to Pantry:** One-tap transfer of purchased items into your pantry inventory
- Search and filter by section

### Kitchen Tools
- **Multi-Timer (Free):** Run multiple simultaneous cooking timers with foreground notifications and completion alerts
- **Measurement Converter (Pro):** Convert between cups, tablespoons, grams, ounces, milliliters, temperatures (F/C), and more
- **Rice Calculator (Pro):** Calculate precise water-to-rice ratios for different rice varieties
- **Ingredient Substitutions (Pro):** Quick reference for common ingredient swaps
- **Recipe Scaler (Pro):** Adjust serving sizes with automatic ingredient recalculation
- **Temperature Guide (Pro):** Reference for common cooking temperatures

### Subscription & Paywall
- Integrated RevenueCat native paywall UI with remote configuration
- Subscription management and plan selection
- Restore purchases support
- Customer center for managing active subscriptions

### Additional Features
- **Dark Mode:** Full Material 3 dark theme support
- **Onboarding Flow:** Guided introduction for new users
- **Splash Screen:** Native Android 12+ splash screen API
- **Offline-First:** Room database ensures full functionality without internet
- **Cloud Sync (Pro):** Firebase Firestore backup and cross-device sync

---

## Screenshots

*Coming soon — screenshots of key app screens will be added here.*

<!--
| Home | Pantry | Recipes | Grocery | Tools |
|:---:|:---:|:---:|:---:|:---:|
| ![Home](screenshots/home.png) | ![Pantry](screenshots/pantry.png) | ![Recipes](screenshots/recipes.png) | ![Grocery](screenshots/grocery.png) | ![Tools](screenshots/tools.png) |
-->

---

## Technical Documentation

### Tech Stack

| Category | Technology |
|---|---|
| **Language** | Kotlin |
| **UI Framework** | Jetpack Compose with Material 3 |
| **Architecture** | Clean Architecture + MVVM |
| **Dependency Injection** | Hilt (with KSP annotation processing) |
| **Local Database** | Room (SQLite) |
| **Networking** | Retrofit 2 + OkHttp |
| **JSON Parsing** | Gson |
| **Image Loading** | Coil (Compose integration) |
| **Web Scraping** | Jsoup (HTML + Schema.org parsing) |
| **AI/LLM** | OpenAI API (GPT-4o-mini) |
| **Subscriptions** | RevenueCat SDK + RevenueCat UI |
| **Authentication** | Firebase Auth + Credential Manager (Google Sign-In) |
| **Cloud Database** | Firebase Firestore |
| **Cloud Storage** | Firebase Storage |
| **Barcode Scanning** | Google ML Kit + CameraX |
| **Product Database** | Open Food Facts API |
| **Async/Reactive** | Kotlin Coroutines + Flow + StateFlow |
| **Preferences** | Jetpack DataStore |
| **Navigation** | Compose Navigation |
| **Min SDK** | 26 (Android 8.0) |
| **Target SDK** | 35 (Android 15) |
| **JVM Target** | 17 |

### Architecture

ShelfChef follows **Clean Architecture** with the **MVVM (Model-View-ViewModel)** presentation pattern, ensuring separation of concerns, testability, and maintainability.

```
┌─────────────────────────────────────────────────────────┐
│                   PRESENTATION LAYER                     │
│  ┌─────────────┐    ┌──────────────┐    ┌────────────┐  │
│  │   Screens   │───▶│  ViewModels  │───▶│ UI State   │  │
│  │  (Compose)  │◀───│  (StateFlow) │    │ (Data Classes)│
│  └─────────────┘    └──────┬───────┘    └────────────┘  │
│                            │                             │
├────────────────────────────┼─────────────────────────────┤
│                   DOMAIN LAYER          │                 │
│  ┌──────────────┐   ┌──────┴───────┐                     │
│  │    Models    │   │   Use Cases  │                     │
│  │ (PantryItem, │   │(FeatureGate  │                     │
│  │  Recipe, etc)│   │  Manager)    │                     │
│  └──────────────┘   └──────────────┘                     │
│                            │                             │
├────────────────────────────┼─────────────────────────────┤
│                    DATA LAYER           │                 │
│  ┌──────────────┐   ┌──────┴───────┐   ┌─────────────┐  │
│  │ Repositories │──▶│   Room DAOs  │   │  API Services│  │
│  │              │   │   Entities   │   │  (Retrofit)  │  │
│  └──────────────┘   └──────────────┘   └─────────────┘  │
│                            │                   │         │
│                     ┌──────┴───────┐   ┌───────┴──────┐  │
│                     │   Room DB    │   │  Remote APIs  │  │
│                     │  (SQLite)    │   │(OpenAI, RevCat│  │
│                     │              │   │ Firebase, OFF)│  │
│                     └──────────────┘   └──────────────┘  │
└─────────────────────────────────────────────────────────┘
```

### Project Structure

```
app/src/main/java/com/shelfchef/
│
├── ShelfChefApp.kt                  # Application class (Hilt, RevenueCat init, notification channels)
│
├── data/                            # DATA LAYER
│   ├── api/                         # Remote API services
│   │   ├── OpenAiApiService.kt      # OpenAI GPT-4o-mini for recipe parsing & suggestions
│   │   ├── OpenAiModels.kt          # Request/response data classes for OpenAI
│   │   ├── OpenFoodFactsApiService.kt  # Barcode product lookup
│   │   └── SmartSuggestionService.kt   # AI recipe suggestion orchestration
│   ├── local/                       # Local persistence
│   │   ├── dao/                     # Room Data Access Objects
│   │   │   ├── PantryDao.kt         # CRUD for pantry items
│   │   │   └── RecipeDao.kt         # CRUD for recipes
│   │   ├── entity/                  # Room entities
│   │   │   ├── PantryItemEntity.kt  # Pantry item table definition
│   │   │   └── RecipeEntity.kt      # Recipe table definition
│   │   ├── converter/               # Room type converters (JSON, enums)
│   │   └── database/                # Room database definition & migrations
│   │       └── ShelfChefDatabase.kt
│   ├── repository/                  # Repository implementations
│   │   ├── PantryRepository.kt
│   │   ├── RecipeRepository.kt
│   │   ├── SubscriptionRepository.kt
│   │   └── ...
│   ├── scraping/                    # Web scraping
│   │   └── RecipeScrapingService.kt # Schema.org + Jsoup recipe extraction
│   └── preferences/                 # DataStore preferences
│       ├── ThemePreferencesRepository.kt
│       └── OnboardingPreferencesRepository.kt
│
├── di/                              # DEPENDENCY INJECTION
│   ├── AppModule.kt                 # Hilt module (repos, services, networking)
│   └── FirebaseModule.kt            # Firebase instance providers
│
├── domain/                          # DOMAIN LAYER
│   ├── model/                       # Domain models
│   │   ├── PantryItem.kt
│   │   ├── Recipe.kt
│   │   ├── SubscriptionState.kt
│   │   ├── SubscriptionType.kt
│   │   ├── SubscriptionPackage.kt
│   │   └── ...
│   └── usecase/                     # Business logic
│       └── FeatureGateManager.kt    # Subscription-based feature gating
│
└── presentation/                    # PRESENTATION LAYER
    ├── navigation/                  # Navigation
    │   ├── Screen.kt                # Route definitions (sealed class)
    │   └── ShelfChefNavHost.kt      # NavHost composable with all routes
    ├── screens/                     # Feature screens (each has ViewModel + Composables)
    │   ├── home/                    # Dashboard
    │   ├── pantry/                  # Pantry management
    │   ├── recipes/                 # Recipe collection & import
    │   ├── grocery/                 # Grocery lists & barcode scanning
    │   ├── tools/                   # Kitchen tools (timer, converter, etc.)
    │   ├── whatcanicook/            # Recipe matching & AI suggestions
    │   ├── subscription/            # Paywall, plans, customer center
    │   ├── auth/                    # Login, register, forgot password
    │   ├── onboarding/              # First-launch onboarding
    │   ├── profile/                 # User profile
    │   └── settings/                # App settings
    ├── components/                  # Shared UI components
    │   ├── UpgradeBanner.kt         # Pro upgrade prompt banner
    │   └── ProFeatureDialog.kt      # Feature-locked dialog
    └── theme/                       # Material 3 theming
        ├── Color.kt
        ├── Theme.kt
        ├── Type.kt
        └── Shape.kt
```

### Data Flow

```
User Interaction
       │
       ▼
┌─────────────┐   State observation    ┌──────────────┐
│   Screen     │◀──────────────────────│  ViewModel   │
│  (Compose)   │───── user action ────▶│  (StateFlow) │
└─────────────┘                        └──────┬───────┘
                                              │
                                     calls repository
                                              │
                                              ▼
                                       ┌──────────────┐
                                       │  Repository   │
                                       └──────┬───────┘
                                              │
                              ┌───────────────┼───────────────┐
                              ▼               ▼               ▼
                       ┌──────────┐   ┌────────────┐   ┌───────────┐
                       │ Room DAO │   │ API Service│   │  Firebase  │
                       │ (Local)  │   │ (Remote)   │   │  (Cloud)   │
                       └──────────┘   └────────────┘   └───────────┘
```

**Key patterns:**
- ViewModels expose `StateFlow` for reactive UI updates
- Repositories abstract data sources (local DB, remote APIs, Firebase)
- Domain models are mapped from Room entities via extension functions
- Coroutines + Flow handle all asynchronous operations
- Hilt provides constructor injection throughout the dependency graph

### Database Schema

ShelfChef uses Room (SQLite) with KSP annotation processing. Schema exports are stored in `app/schemas/`.

**Current version:** 3

#### `pantry_items` Table

| Column | Type | Description |
|---|---|---|
| `id` | TEXT (PK) | Unique identifier |
| `user_id` | TEXT | Owner user ID |
| `name` | TEXT | Item name |
| `quantity` | REAL | Amount |
| `unit` | TEXT | Unit of measurement |
| `category` | TEXT | Enum: Dairy, Produce, Meat, Pantry Staples, Frozen, etc. |
| `expiration_date` | TEXT | ISO date string |
| `location` | TEXT | Enum: Pantry, Fridge, Freezer |
| `added_at` | INTEGER | Timestamp |
| `updated_at` | INTEGER | Timestamp |

#### `recipes` Table

| Column | Type | Description |
|---|---|---|
| `id` | TEXT (PK) | Unique identifier |
| `user_id` | TEXT | Owner user ID |
| `title` | TEXT | Recipe title |
| `description` | TEXT | Recipe description |
| `ingredients` | TEXT (JSON) | List of ingredients with name, amount, unit |
| `instructions` | TEXT (JSON) | Ordered list of instruction steps |
| `servings` | INTEGER | Number of servings |
| `prep_time` | INTEGER | Prep time in minutes |
| `cook_time` | INTEGER | Cook time in minutes |
| `image_url` | TEXT | Recipe photo URL |
| `source_url` | TEXT | Original recipe URL |
| `source_type` | TEXT | Enum: URL, Manual, AI |
| `author` | TEXT | Recipe author |
| `cookbook_id` | TEXT | Associated cookbook ID |
| `is_favorite` | INTEGER | Boolean flag |
| `tags` | TEXT (JSON) | List of tags |
| `times_cooked` | INTEGER | Cook counter |
| `created_at` | INTEGER | Timestamp |
| `updated_at` | INTEGER | Timestamp |

**Type Converters:** Room type converters handle JSON serialization of `List<String>`, `List<Ingredient>`, and enum-to-string mappings for `PantryCategory`, `PantryLocation`, `RecipeSource`, and `StoreSection`.

### RevenueCat Implementation

ShelfChef integrates RevenueCat for subscription management, providing a complete in-app purchase flow with server-side receipt validation and entitlement management.

#### SDK Initialization

RevenueCat is initialized in `ShelfChefApp.kt` (the Hilt `@HiltAndroidApp` Application class) during `onCreate()`:

```kotlin
Purchases.logLevel = LogLevel.DEBUG  // Debug builds only
Purchases.configure(
    PurchasesConfiguration.Builder(this, BuildConfig.REVENUECAT_API_KEY).build()
)
```

The API key is loaded from `local.properties` (gitignored) and injected via `BuildConfig`.

#### Entitlement Model

| Entitlement | ID | Description |
|---|---|---|
| ShelfChef Pro | `"ShelfChef Pro"` | Unlocks all premium features |

#### Subscription Packages

RevenueCat offerings are configured remotely and loaded at runtime. The app supports three package types:

| Package | Identifier Pattern | Display |
|---|---|---|
| Monthly | Contains `"monthly"` | Recurring monthly billing |
| Yearly | Contains `"yearly"` | ~17% savings badge, "2 months free" messaging |
| Lifetime | Contains `"lifetime"` | One-time purchase, "Best Value" badge |

#### Feature Gating Architecture

Feature access is controlled by `FeatureGateManager`, a singleton injected via Hilt:

```kotlin
@Singleton
class FeatureGateManager @Inject constructor(
    private val subscriptionRepository: SubscriptionRepository
) {
    val isProUser: Flow<Boolean>

    suspend fun canSaveRecipe(currentRecipeCount: Int): Boolean
    suspend fun canUseUrlParser(currentImportCount: Int): Boolean
    suspend fun canUseSmartSuggestions(): Boolean
    suspend fun hasToolsAccess(): Boolean
    suspend fun canScaleRecipes(): Boolean
    suspend fun hasCloudSync(): Boolean
    suspend fun getRemainingRecipeSlots(currentRecipeCount: Int): Int?
    suspend fun getRemainingUrlImports(currentImportCount: Int): Int?
}
```

**Free tier limits (constants):**
- `FREE_RECIPE_LIMIT = 10` — Maximum saved recipes
- `FREE_URL_IMPORT_LIMIT = 5` — Maximum URL imports

**How gating works:**
1. ViewModels inject `FeatureGateManager` and check access before executing gated operations.
2. If access is denied, the UI shows either an `UpgradeBanner` (passive) or `ProFeatureDialog` (blocking) prompting the user to subscribe.
3. `SubscriptionRepository` wraps the RevenueCat SDK, exposing `subscriptionState` as a `Flow<SubscriptionState>` that the gate manager observes.
4. `SubscriptionState` contains `isProUser`, `subscriptionType`, and `expirationDate`.

#### Paywall Implementation

ShelfChef implements **two paywall experiences**:

1. **Custom Paywall (`SubscriptionScreen`):**
   - Hero banner with feature highlights
   - Package cards with pricing, savings badges, and free trial detection
   - Feature comparison list (4 key benefits)
   - Restore purchases button
   - Legal auto-renewal disclaimer

2. **RevenueCat Native Paywall (`RevenueCatPaywallScreen`):**
   - Uses `PaywallDialog` from `com.revenuecat.purchases.ui`
   - Remotely configurable templates — update the paywall without shipping an app update
   - Requires `"ShelfChef Pro"` entitlement identifier
   - Handles purchase completion, restoration, errors, and cancellation via `PaywallListener`

#### Customer Center

`CustomerCenterScreen` provides subscription management (cancel, change plan, request refund) using RevenueCat's Customer Center UI component.

#### User Identity

- On Firebase Auth login, the RevenueCat user is identified via `Purchases.sharedInstance.logIn(firebaseUid)`
- On logout, `Purchases.sharedInstance.logOut()` resets to anonymous
- This links subscription entitlements to the authenticated user across devices

### API Integrations

#### OpenAI (GPT-4o-mini)

- **Purpose:** Fallback recipe parsing when Schema.org extraction fails; AI-powered recipe suggestion generation
- **Base URL:** `https://api.openai.com/`
- **Model:** `gpt-4o-mini`
- **Authentication:** Bearer token from `BuildConfig.OPENAI_API_KEY`
- **Usage:**
  - `RecipeScrapingService` sends raw HTML to GPT-4o-mini when structured data extraction fails, asking it to extract recipe fields
  - `SmartSuggestionService` sends pantry inventory to GPT-4o-mini and receives generated recipe suggestions

#### Open Food Facts

- **Purpose:** Product lookup from barcode scans
- **Base URL:** `https://world.openfoodfacts.org/`
- **Authentication:** None (public API)
- **Usage:** `OpenFoodFactsApiService` fetches product name, brand, image, and category from scanned barcodes to auto-populate grocery items

#### Firebase Suite

- **Firebase Auth:** Email/password and Google Sign-In (via Credential Manager)
- **Firestore:** Cloud sync for pantry items, recipes, and grocery lists (Pro feature)
- **Storage:** Recipe and grocery item image uploads

### Notification System

ShelfChef creates three notification channels in `ShelfChefApp.kt`:

| Channel ID | Name | Importance | Purpose |
|---|---|---|---|
| `timer_channel` | Timer Updates | LOW (silent) | Active timer countdown updates |
| `timer_completed_channel` | Timer Completed | HIGH (vibrate, badge) | Timer completion alerts |
| `general_channel` | General | DEFAULT | General app notifications |

The `TimerService` runs as a foreground service to ensure timers continue when the app is backgrounded. Timer completion triggers a high-priority notification with vibration.

---

## Getting Started

### Prerequisites

- **Android Studio** Ladybug (2024.2.1) or newer
- **JDK 17**
- **Android SDK** with API level 35 installed
- **Kotlin** 2.0+

### Setup

1. **Clone the repository:**
   ```bash
   git clone https://github.com/your-username/ShelfChef.git
   cd ShelfChef
   ```

2. **Configure API keys** — create or edit `local.properties` in the project root:
   ```properties
   # OpenAI API key for recipe parsing fallback and AI suggestions
   OPENAI_API_KEY=your_openai_api_key_here

   # RevenueCat API key for subscription management
   REVENUECAT_API_KEY=your_revenuecat_api_key_here
   ```

3. **Configure Firebase** (optional — required for auth and cloud sync):
   - Create a Firebase project at [console.firebase.google.com](https://console.firebase.google.com)
   - Add an Android app with package name `com.shelfchef`
   - Download `google-services.json` and place it in `app/`
   - Enable Email/Password and Google Sign-In providers in Firebase Auth
   - Create a Firestore database
   - Enable Firebase Storage

4. **Sync and build:**
   ```bash
   ./gradlew assembleDebug
   ```

### Build Commands

```bash
# Build debug APK
./gradlew assembleDebug

# Build release APK
./gradlew assembleRelease

# Run all unit tests
./gradlew test

# Run a single test class
./gradlew test --tests "com.shelfchef.ExampleTest"

# Run instrumented tests
./gradlew connectedAndroidTest

# Clean build
./gradlew clean

# Check for lint issues
./gradlew lint
```

---

## Configuration

| File | Purpose |
|---|---|
| `local.properties` | API keys (OPENAI_API_KEY, REVENUECAT_API_KEY) — gitignored |
| `app/google-services.json` | Firebase configuration — gitignored |
| `gradle/libs.versions.toml` | Dependency version catalog |
| `app/build.gradle.kts` | App-level build configuration |
| `app/schemas/` | Room database schema exports for migration validation |
| `app/proguard-rules.pro` | ProGuard rules for release builds |

---

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/your-feature`)
3. Commit your changes (`git commit -m "Add your feature"`)
4. Push to the branch (`git push origin feature/your-feature`)
5. Open a Pull Request

---

## License

This project was built for the RevenueCat Mobile App Hackathon.

---

**ShelfChef** — Cook smarter with what you already have.
