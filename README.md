# ChatBot

A Gemini-powered chatbot built with the Google AI client SDK for Android, written in Java.

## Features

- Requests sent through the `generativeai` client SDK
- Asynchronous responses delivered via a `ResponseCallback` interface
- Chat UI backed by a RecyclerView

## Tech stack

- **Language:** Java
- **UI:** XML layouts with View binding
- **SDK:** min 24, target 34
- **Package:** `com.example.chatbot`
- **Libraries:** Google AI (Gemini) SDK

<sub>6 source files · 192 lines of code · 3 layouts</sub>

## Getting started

```bash
git clone https://github.com/rajabbov/ChatBot.git
```

Open the folder in Android Studio, let Gradle sync, and run the `app` configuration on a device or emulator.

### Configuration

Set `GEMINI_API_KEY` in `local.properties`. The key is exposed to the app through `BuildConfig` and is never committed.

## License

MIT
