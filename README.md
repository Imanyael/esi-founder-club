# esi-founder-club
E.S.I Founder Club
# App Release Checklist

**Everything you need to get your app live on the web and the stores!**

So, you've vibe‑coded something cool for your phone with Bolt.new. What's next? How do I get this to the app stores? Let's talk about that.

> **How to use:** Do whatever works for you, but I like to copy this markdown into a new Issue in my app’s GitHub repo. That way, I can check it off as I go!

---

## 1. Finishing touches to your code in Bolt

> You could technically do these after downloading your project, but might as well knock them out here—especially the parts Bolt can generate for you.

* CLICK INTEGRATION
* Add Github
* Add Supabase
  

* **App Icon & Splash Screen**

  1. Follow the guide: [https://docs.expo.dev/develop/user-interface/splash-screen-and-app-icon/](https://docs.expo.dev/develop/user-interface/splash-screen-and-app-icon/)
  2. Use our Figma template for layout and export: [https://docs.google.com/document/d/1OOiwZNy15OgLzkz4T-KrAfQd4\_0badRvh1sVXVdENYw/edit?usp=sharing](https://docs.google.com/document/d/1OOiwZNy15OgLzkz4T-KrAfQd4_0badRvh1sVXVdENYw/edit?usp=sharing)
  3. Draw your own icon, use Figma tools or ask ChatGPT to generate a logo with a transparent background.
  4. In Bolt → **Project Settings → App Icon & Splash** → upload each PNG.

* **Privacy Policy page** (`/privacy`)

  ```txt
  Bolt → create a `/privacy` route. Summarize: "This app uses only local data, does not collect or transmit your location or personal info."  
  ```

* **(Optional) About page** (`/about`)

  ```txt
  Describe your app’s features, link to `/privacy`, include a contact button if desired.
  ```

* **(Optional but recommended) Connect to GitHub**

  * In Bolt: **Project Settings → GitHub** → connect your repo for two‑way sync.

---

## 2. Sign up as a developer for the stores

> You’ll need accounts with Google and Apple to publish. These can take some time to activate, so sign up as soon as your app is at least feature‑complete.

* **Apple Developer Program**: \$99 USD / year → [https://developer.apple.com/](https://developer.apple.com/)
* **Google Play Console**: \$25 USD one‑time → [https://play.google.com/console/u/0/signup](https://play.google.com/console/u/0/signup)

---

## 3. Build, Deploy & Test

Download your project to your computer (via Bolt’s file export or GitHub) and run the commands below.
If any features won’t run in Expo Go (camera, in‑app purchases, custom native code), add them locally and create a **Development Build** first:
[https://docs.expo.dev/develop/development-builds/introduction/](https://docs.expo.dev/develop/development-builds/introduction/)

### iOS

```sh
# Build & submit to TestFlight
npx testflight
```

* Logs you into Apple, handles certificates/profiles, uploads a build.
* Check your email for the TestFlight invite code.
* Install TestFlight app, redeem code, and test.

### Android

```sh
# Build Play‑ready AAB
eas build --profile production --platform android
```

* For quick local testing, use the `preview` profile to produce an APK you can sideload.
* Go to Play Console → create or open your app → **Internal testing** → upload APK/AAB → install via link.
* Note: New Google accounts may require a short pre‑release testing period.

### Web

```sh
# Export & deploy to web
npx expo export --platform web
npx eas-cli deploy --prod
```

* Publishes to your-project.expo.app by default.

**Optional:** Integrate [EAS Update](https://docs.expo.dev/eas-update/introduction/) to push JS bug‑fixes instantly without a full store release.

---

## 4. Prepare your store assets & copy

You’ll need images and text for your store listings. Create them now so you can paste them in order.

### Screenshots

**Recommendation:** Use [https://app-mockup.com/](https://app-mockup.com/) (free) to generate properly sized device mockups.

* **iOS**

  * 1 screenshot at **1320 × 2868 px** (iPhone 16 Pro Max)
  * (Optional) 1 screenshot at **2048 × 2732 px** (13″ iPad)
* **Android**

  * 2 screenshots at a ≥ 9:16 ratio (any tall Android phone)

### Store Listing Copy

* **Store description**: Ask Bolt or ChatGPT to generate from your app’s feature list.
* **Icon for Play Store**: Resize your 1024×1024 PNG to 512×512 (Preview or Paint).
* **Feature graphic (Play)**: 1024×500 px → prompt ChatGPT to match your icon.
* **Short description (80 chars max)**: pithy one‑liner.

---

## 5. Submit to the stores

### App Store (iOS)

1. Go to App Store Connect → your app entry.
2. In **1.0 Release**, add screenshots, description, and pick the build uploaded via `npx testflight`.
3. Under **App Information**, set a unique name, category, and age rating.
4. Under **App Privacy**, add your `/privacy` URL, declare collected data, and **Publish**.
5. Click **Add for Review** on the main page to submit.

### Play Store (Android)

1. Open your app in Play Console.
2. On the **Dashboard**, click through each setup task:

   * Privacy policy URL
   * Content rating questionnaire
   * Required disclosures (news, government, …)
   * Contact details
   * Store listing (screenshots, graphic, icon, descriptions)
3. **Select countries and regions** at the bottom of Dashboard.
4. Under **Testing → Internal**, choose your build and **Promote to Production**.
5. Back on Dashboard, **Submit for review**.

---

## Appendix: Tools & Accounts

* GitHub account → [https://github.com/](https://github.com/)
* GitHub Desktop → [https://desktop.github.com/](https://desktop.github.com/)
* Visual Studio Code → [https://code.visualstudio.com/](https://code.visualstudio.com/)
* Expo account → [https://expo.dev/](https://expo.dev/)
* Expo CLI & EAS CLI → `npm install -g eas-cli`
* Figma (for template) → [https://www.figma.com/](https://www.figma.com/)
* App Mockup → [https://app-mockup.com/](https://app-mockup.com/)

Good luck—ship it! 🚀
