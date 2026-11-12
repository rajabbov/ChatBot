# ChatBot

![Java](https://img.shields.io/badge/Java-ED8B00?logo=openjdk&logoColor=white) ![Android](https://img.shields.io/badge/Android-3DDC84?logo=android&logoColor=white) ![minSdk 24](https://img.shields.io/badge/minSdk_24-555)

**AIBrain** — a chatbot powered by Google **Gemini**, written in **Java** with the official Google AI client SDK. Unlike a single question-answer call, it opens a **chat session**, so Gemini remembers the earlier messages in the conversation.

## Features

- **Multi-turn conversation** — `startChat()` keeps context between messages
- Model **`gemini-1.5-flash`** with tuned generation settings (temperature 0.9, topK 16, topP 0.1)
- **Safety setting** — harassment content blocked at high threshold
- **Floating action button** opens a message dialog; a progress bar shows while Gemini thinks
- Chat bubbles with avatars for *You* and *Brain*

## How it works

The SDK returns a Guava `ListenableFuture`, which `GeminiResp` turns into a simple callback interface:

```java
Futures.addCallback(chatModel.sendMessage(userMessage), new FutureCallback<GenerateContentResponse>() {
    public void onSuccess(GenerateContentResponse result) { callback.onResponse(result.getText()); }
    public void onFailure(Throwable t)                   { callback.onError(t); }
}, executor);
```

`MainActivity` only implements `ResponseCallback` — it never sees futures or SDK types, which keeps the UI code short.

## Project structure

```
com.example.chatbot
├── GeminiResp.java
├── MainActivity.java
└── ResponseCallback.java
```

<sub>3 source files · 153 lines of code · 3 layouts</sub>

## Tech stack

| | |
|---|---|
| **Language** | Java |
| **UI** | XML layouts |
| **Min / Target SDK** | 24 / 34 |
| **Google AI SDK** | Gemini API |
| **Guava** | Futures |

## Getting started

```bash
git clone https://github.com/rajabbov/ChatBot.git
```

1. Open the folder in **Android Studio** (Ladybug or newer).
2. Let Gradle sync.
3. Complete the configuration below, then run the `app` configuration.

### Configuration

Get a free key from [Google AI Studio](https://aistudio.google.com/) and add it to `local.properties` (git-ignored):

```properties
GEMINI_API_KEY=AIza...
```
It is exposed to the app as `BuildConfig.apiKey`.

## Known limitations

- Messages are added to a `LinearLayout`; switching to a RecyclerView would scale better for long chats.

---

Made by **Ibrohimjon Rajabboyev** · [@rajabbov](https://github.com/rajabbov)
