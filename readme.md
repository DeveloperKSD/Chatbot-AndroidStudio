# Gemini API Compose Starter - MAD Experiment 6

An Android app built with Kotlin and Jetpack Compose. It combines image features (camera, gallery, image loading libraries, caching) with a Gemini-powered chatbot that saves your conversations.

## Pictures
<img width="263" height="596" alt="image" src="https://github.com/user-attachments/assets/cd81e23d-9644-44e0-8425-4fb736829007" />


<img width="327" height="736" alt="image" src="https://github.com/user-attachments/assets/4486eeaa-7ef7-4449-8906-e190c3816361" />



<img width="324" height="704" alt="image" src="https://github.com/user-attachments/assets/a2be2dbb-2a72-44d9-ab25-34387312d480" />



<img width="268" height="588" alt="image" src="https://github.com/user-attachments/assets/0bfc7729-4639-4aad-af52-0232f2f0e16a" />






## Features

The home screen has five buttons:

| Screen | What it does |
|---|---|
| **Camera** | Opens the phone's camera app, takes a photo and shows it in the app. No camera permission needed. |
| **Gallery** | Lets you pick an image from the device and displays it using Coil. |
| **Glide / Coil** | Loads the same online image with Coil and Glide side by side. |
| **Caching & Preloading** | **Preload** downloads a set of images into both libraries' caches so they show instantly. **Clear caches** empties memory and disk caches so you can compare load speed. |
| **Gemini Chat** | The chatbot, described below. |

### Gemini Chat

- **Chat bubbles:** your messages on the right, Gemini's replies on the left, with a "Thinking..." indicator while it waits.
- **Saved history:** every chat is stored on the device, so it is still there after closing or restarting the app. The latest chat reopens automatically.
- **Side menu (☰):** start a **New chat**, reopen an older chat, or delete one.
- **Conversation memory:** Gemini gets the earlier messages of the chat, so follow-ups like "another one" make sense.
- **Settings (⚙):** a Dark mode switch. The choice is remembered.
- **Voice input (🎤):** speak your prompt using Android's speech recognizer (needs a speech service on the device).
- **Error handling:** if Gemini is busy (503), the app retries up to 3 times. Other errors show a short message instead of raw JSON.

## Setup

1. Get a free API key from [Google AI Studio](https://aistudio.google.com).
2. Open `local.properties` in the project root and add:
   ```
   GEMINI_API_KEY=your_key_here
   ```
   (no quotes, no spaces around `=`)
3. Open the project in Android Studio and wait for Gradle sync to finish.
4. Start an emulator (Tools -> Device Manager) or plug in a phone, then press **Run**.

`local.properties` is git-ignored, so your key is not committed.

## Tech used

- Kotlin, Jetpack Compose, Material 3
- MVVM with `StateFlow` and ViewModels
- Gemini API through the `generativeai` Android SDK (model `gemini-3.6-flash`)
- Coil 3 and Glide for image loading and caching
- Chat history stored as a JSON file, and the dark-mode setting in SharedPreferences

## Project layout

```
app/src/main/java/com/fahim/geminiApiComposeStarter/
  MainActivity.kt          home menu
  CameraActivity.kt        camera demo
  GalleryActivity.kt       gallery demo
  ImageLoaderActivity.kt   Coil vs Glide
  CacheDemoActivity.kt     caching and preloading
  ChatActivity.kt          hosts the chatbot
  data/                    Gemini repository, chat models, ChatStore (saving)
  ui/chat/                 chat screen and ViewModel
  utils/ImageLoaderManager.kt   preload and cache helpers
```

## Limitations

- The API key is built into the app, so this is fine for a class project but not for a production app.
- The `generativeai` SDK is deprecated by Google in favour of Firebase AI Logic.
- Chats are stored only on the device, with no cloud sync.
