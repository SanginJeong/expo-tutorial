# 2. Add Navigation

## Expo Router Basics

Expo Router는 React Native 및 웹 앱을 위한 파일 기반의 라우팅 프레임워크이다. 이 프레임워크는 화면 간의 이동을 관리하며, 여러 플랫폼에서 동일한 컴포넌트들을 사용할 수 있도록 해준다.

## 규칙들

- app directory: 루트와 해당 레이아웃만을 포함하는 특별한 디렉토리다. 이 디렉토리에 추가되는 모든 파일은 네이티브 앱 내의 화면이자 웹상의 페이지가 된다.
- Root layout: 이 파일은 헤더나 탭 바와 같은 공통적인 UI 요소들을 정의하여, 다양한 루트 간에 일관된 디자인이 유지되도록 한다.
- 파일명 규칙: index.tsx와 같은 인덱스 파일명은 해당 파일이 속한 디렉토리와 일치하며, 별도의 경로 정보는 추가되지 않는다. 예를들어, app 디렉토리에 있는 index.tsx 파일은 `/` 루트와 연관된다.
- 루트 파일은 React 컴포넌트를 기본 값으로 내보낸다.
- 안드로이드, iOS, 웹은 모두 통일된 네비게이션 구조를 가지고 있다.

## 스택에 새로운 화면 추가

`app/about.tsx` 파일 추가. -> `/about` 루트

```tsx
import { Stack } from "expo-router";

export default function RootLayout() {
  return (
    <Stack>
      <Stack.Screen name="index" options={{ title: "Home" }} />
    </Stack>
  );
}
```

**Stack** 이란 앱 내의 다양한 화면들을 오가는 데 필요한 기반 기능이다. 안드로이드에서는 스택 기반의 네비게이션 효과가 현재 화면 위에 표시된다. iOS에서는 오른쪽에서부터 네비게이션 효과가 나타난다.Expo Router는 새로운 루트를 추가하기 위한 `Stack` 컴포넌트를 제공한다.

> AI 답번
>
> Q. expo-router의 Stack 컴포넌트는 뭐야?
>
> A. `<Stack>`은 "그 경로들이 화면에서 어떻게 전환되고 보이는가" 를 정합니다. `<Stack>`은 이 중 "쌓임(stack) 방식으로 네비게이션한다"를 선언하는 네비게이터입니다. 내부적으로는 React Navigation의 native-stack을 감싼 것이고요.
>
> <Stack>만 쓰면 모든 화면이 같은 옵션을 갖습니다. 개별 화면 설정은 <Stack.Screen>으로 합니다. name은 파일명과 일치해야 합니다.
> <Stack.Screen>은 화면을 만드는 게 아니라 이미 파일로 존재하는 화면에 옵션을 붙이는 역할입니다. 안 써도 화면은 나옵니다.다른 네비게이터로 바꾸면 \_layout.tsx에서 <Stack> 대신 <Tabs>를 쓰면, 파일 하나 안 건드리고 같은 화면들이 하단 탭으로 바뀝니다:
>
> 한 줄 요약: 파일 = 라우트의 존재, `<Stack>` = 라우트의 표현 방식.

## 화면 전환

```tsx
<Link href="/about" style={styles.button}>
  Go to About screen
</Link>
```

Link 컴포넌트를 사용하여 화면 전환 가능

**Link를 눌렀을 때 expo-router가 화면을 만들어둔 stack 위에 push 하기 때문에, 자동으로 back이 생긴다.**

> "밑에 돌아갈 화면이 있네 → 헤더 왼쪽에 back 버튼 넣자"

아래와 같이 뒤로가기를 숨길 수도 있다.

```tsx
<Stack.Screen name="about" options={{ headerBackVisible: false }} />
```

> 새로고침 해야 없어짐 -> Fast Refresh가 네비게이터 옵션까지는 따라가지 못하는 알려진 한계.
