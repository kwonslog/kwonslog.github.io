---
published: true
layout: single
title: "React 용어"
excerpt: "용어 단순 정리"
date: 2025-08-19
last_modified_at: 2025-08-20
categories: [front-end]
tags: [react, glossary]
toc: true
---

## 헤드리스 컴포넌트(Headless Component)
UI(화면 모양)는 직접 제공하지 않고, 로직과 상태만 제공하는 컴포넌트.

## Props(Properties)
- 부모 -> 자식 방향으로 데이터를 전달하는 읽기 전용 프로퍼티.
- 자식은 전달받은 Props에 대한 수정이 가능하지만 `**상태 관리나 데이터 변경 추적이 어려워 수정하면 안된다.**`
- 변경이 필요한 경우에는 부모가 넘겨준 setter 함수를 호출하는 방식으로 처리.

## JSX(JavaScript XML)
JavaScript 안에서 HTML 문법처럼 UI를 표현할 수 있는 문법 확장
```jsx
function Hello() {
  return <h1>Hello World</h1>;
}
```

## TSX(TypeScript XML)
TypeScript에서 JSX를 사용할 수 있도록 확장한 문법
```tsx
type HelloProps = { name: string };

function Hello({ name }: HelloProps) {
  return <h1>Hello {name}</h1>;
}
```

## 하이드레이션(hydration)
서버에서 렌더링된 HTML에 클라이언트 측 React 이벤트 핸들러와 상태를 연결해 상호작용 가능하게 만드는 과정.

## 라우트 핸들러 (Route Handler)
- 위치: app/api/*/route.ts 또는 app/api/*/route.js
- 역할: API 엔드포인트를 정의하는 것
- 예시: 클라이언트나 외부에서 fetch("/api/posts") 같은 요청을 보낼 때 응답을 반환
- 특징: Express의 라우트와 비슷하며 GET, POST, PUT, DELETE 등 HTTP 메서드별로 함수를 정의

## 서버 액션 (Server Action)
- 위치: 일반적으로 app/* 내부의 서버 컴포넌트 파일 안
- 역할: 폼 제출이나 특정 함수 호출을 서버에서 직접 실행하게 하는 것
- 예시: 클라이언트에서 onSubmit 시 서버로 데이터를 보내지 않고, 마치 함수 호출처럼 서버 코드를 실행
- 특징: use server 지시어를 붙여 정의

