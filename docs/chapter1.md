# 1. Create your first app

[공식 문서](https://docs.expo.dev/tutorial/create-your-first-app/)

## Expo와 React-Native

React Native는 JavaScript로 작성한 컴포넌트를 iOS/Android의 실제 네이티브 UI로 렌더링해주는 코어 엔진이다. 앱을 빌드하려면 **Xcode, Android Studio, CocoaPods, Gradle** 같은 네이티브 툴체인을 직접 다뤄야한다.

Expo는 React Native의 부족한 부분들을 대신 처리해주는 React Native 앱이라고 볼 수 있다.

- 개발 실행: npx expo start, Expo Go 앱으로 QR 찍어서 바로 실행
- 네이티브 모듈: expo-camera, expo-notifications, expo-file-system 등 검증된 모듈 세트
- 빌드/배포: EAS Build (클라우드 빌드 — 맥 없이 iOS 빌드 가능), EAS Submit (스토어 자동 제출)
- OTA 업데이트: EAS Update — 스토어 심사 없이 JS 번들만 교체
- 라우팅: expo-router (파일 기반 라우팅)
- 네이티브 설정: config plugin + prebuild로 app.json만 고치면 네이티브 파일 자동 생성

## 설치 방법

```bash
npx create-expo-app@latest StickerSmash

pnpm create expo-app StickerSmash

yarn create expo-app StickerSmash
```

## reset-project

튜토리얼을 시작하기 전에, `reset-project` 스크립트를 실행하여 기본 코드를 제거한다.

```bash
pnpm run reset-project
```

위 명령어를 실행하면 `app` 디렉토리에 `index.tsx` 와 `_layout.tsx` 파일이 남게된다.

## 모바일 및 웹에서 앱 사용

프로젝트 디렉토리에서, 터미널에서 개발 서버를 시작하려면 아래 명령어를 사용한다.

```bash
pnpm expo start
```

위 명령어를 실행한 후:

1. 개발서버가 시작되고, 터미널 창에 QR코드가 표시된다.
2. QR 코드를 스캔하여 해당 기기에서 앱을 실행한다. 안드로이드는 Expo Go > QR 코드 스캔 옵션을 사용한다. iOS에서는 기본 카메라 앱을 사용한다.
3. 웹 앱을 실행하려면 터미널에서 `w`을 입력한다.
