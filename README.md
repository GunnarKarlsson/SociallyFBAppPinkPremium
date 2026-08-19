# Socially Pink Premium

This is the **paid, ads-free Android app** for **Socially Pink**, a pink-themed third-party Facebook client. Socially let users restyle the app with interchangeable skins and themes (backgrounds, action bar colors, sliding-menu colors, fonts, and a custom color picker) instead of using Facebook’s default look.

This listing shipped a custom pink theme pack that was not in the main Socially apps. It was a separate Google Play listing from the free, ad-supported Socially build and from the paid non-pink Socially build.

Package: `com.bluebitapps.sociallypinkpremium`  
Type: Eclipse ADT / Ant Android application  
Min SDK: 14 · Target SDK: 17  
Store version: `1.00050` (`versionCode` 50)

Live on Google Play **2012–2014**.

## How this project relates to the library

`socially_base_lib` (`com.bluebitapps.fbclientbase`) holds Graph API access, the navigation shell, theming engine, and all feature screens (news feed, photos, chat, notifications, events, groups, and so on). See that project’s README for the full feature list.

This app:

- Depends on `socially_base_lib` as an Android library (`android.library.reference.2=../socially_base_lib`)
- Sets `isPremiumVersion` to **true**, which hides AdMob banners and the “Remove ads” menu item
- Sets `isPinkVersion` to **true**, so store links and version-specific behavior target the Pink listing
- Provides **100 pink-focused themes** (numbered pink pack, named skins, custom, kawaii, and set5)
- Has **no Java sources of its own** — `FBClientApplication`, `LaunchActivity`, and the rest come from the library

The free Socially app is a separate project (`com.bluebitapps.fbclient`). A paid non-pink counterpart existed as `com.bluebitapps.sociallypremium`.

## What this app adds

### Premium / pink flags

- `res/values/config_version.xml` — `isPremiumVersion=true` and `isPinkVersion=true` (Facebook app id and AdMob unit ids are not included)
- No Google Play billing permission (this listing was sold as a paid app)
- Overlay layouts in `res/layout/` that omit the `AdView` banners used by the library’s list screens

### Skins and themes

This project includes **100 pink-focused themes**. They are declared in `res/xml/app_themes.xml` and applied by the library’s `ThemeFactory`. The app ships the drawable backgrounds, preview icons, and action-bar / menu colors: numbered pink themes, named skins such as Pink, Hearts, Pink Skull, Pink Fur, and Purple Rain, plus custom, kawaii, and set5 packs.

The themes are copyright Gunnar Karlsson and are not covered by the MIT License.

### Fonts

Bundled typefaces in `assets/fonts/`: Arial, Roboto, Verdana, Garamond, Gill, BM Solid, Cute. The library uses these for the in-app text-appearance settings.

### Preferences overlay

`res/xml/preferences.xml` overlays notification delivery, news-feed refresh, and text appearance settings on top of the library defaults.

## Project layout

```
AndroidManifest.xml     Application id, library activities/services
res/xml/app_themes.xml  Skin catalog
res/values/             Premium / pink flags, theme colors
res/drawable*/          Theme backgrounds and icons
res/layout/             List-screen overlays without ad banners
res/xml/preferences.xml Settings overlay
assets/fonts/           Bundled typefaces
libs/                   android-support-v4.jar
```

External Eclipse library references (not all in this repo): `socially_base_lib`, Facebook Android SDK, Google Play services.

## License

Source code is licensed under the MIT License. See [LICENSE](LICENSE).

The themes (including artwork in `res/drawable*` and the catalog in `res/xml/app_themes.xml`) are copyright Gunnar Karlsson and are not covered by the MIT License.
