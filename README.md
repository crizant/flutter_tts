This repo is forked from [dlutton/flutter_tts](https://github.com/dlutton/flutter_tts) with a little modification to work in Swift 4.2.

# Text To Speech

[![pub package](https://img.shields.io/pub/v/flutter_tts.svg?style=for-the-badge&colorB=green)](https://pub.dartlang.org/packages/flutter_tts)

A flutter text to speech plugin (Swift,Java)

## Features

- [x] Android & iOS
  - [x] speak
  - [x] stop
  - [x] get languages
  - [x] set language
  - [x] is language available
  - [x] set speech rate
  - [x] set speech volume
  - [x] set speech pitch
  - [x] get voices
  - [x] set voice
- [x] Android
  - [x] set Silence

## Usage

## Android

Change the minimum Android sdk version to 21 (or higher) in your `android/app/build.gradle` file.

```java
minSdkVersion 21
```

## iOS

There's a known issue with integrating plugins that use Swift into a Flutter project created with the Objective-C template. [Flutter#16049](https://github.com/flutter/flutter/issues/16049)

[Example](https://github.com/dlutton/flutter_tts/blob/master/example/lib/main.dart)

To use this plugin :

- add the dependency to your [pubspec.yaml](https://github.com/dlutton/flutter_tts/blob/master/example/pubspec.yaml) file.

```yaml
  dependencies:
    flutter:
      sdk: flutter
    flutter_tts:
```

- instantiate a FlutterTts instance

```dart
FlutterTts flutterTts = new FlutterTts();
```

### speak, stop, getLanguages, setLanguage, setSpeechRate, setVolume, setPitch, isLanguageAvailable

```dart
Future _speak() async{
    var result = await flutterTts.speak("Hello World");
    if (result == 1) setState(() => ttsState = TtsState.playing);
}

Future _stop() async{
    var result = await flutterTts.stop();
    if (result == 1) setState(() => ttsState = TtsState.stopped);
}

List<dynamic> languages = await flutterTts.getLanguages;

await flutterTts.setLanguage("en-US");

await flutterTts.setSpeechRate(1.0);

await flutterTts.setVolume(1.0);

await flutterTts.setPitch(1.0);

await flutterTts.isLanguageAvailable("en-US");
```

### Listening for platform calls

```dart
flutterTts.setStartHandler(() {
  setState(() {
    ttsState = TtsState.playing;
  });
});

flutterTts.setCompletionHandler(() {
  setState(() {
    ttsState = TtsState.stopped;
  });
});

flutterTts.setErrorHandler((msg) {
  setState(() {
    ttsState = TtsState.stopped;
  });
});
```

## Getting Started

For help getting started with Flutter, view our online
[documentation](https://flutter.io/).

For help on editing plugin code, view the [documentation](https://flutter.io/platform-plugins/#edit-code).
