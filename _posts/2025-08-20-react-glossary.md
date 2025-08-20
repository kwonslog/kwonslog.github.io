---
published: true
layout: single
title: "React/Next.js 용어"
excerpt: "용어 단순 정리"
date: 2025-08-19
last_modified_at: 2025-08-20
categories: [front-end]
tags: [react, glossary]
toc: true
---

# React

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

---

# Next.js

## 그룹 라우트(group)
- 폴더명에 `()`를 사용해서 작성.
- 개발자가 폴더 구조를 정리하고 싶을 때 사용함. 
- 실제 URL에는 영향을 주지 않음.
- 그룹 라우트는 없어도 되지만 있으면 구조 정리에 좋다는 개념.
- 예시
  
  ```
  src/app/(board)/list/page.tsx   → /list 
  src/app/(board)/[id]/page.tsx   → /:id
  ```

## 동적 라우트(Dynamic Route)
- 폴더명에 `[]`를 사용해서 작성.
- URL 경로에 변수를 매핑.
- App Router 사용시 폴더명만 가능하며 파일명에는 동적 라우트 사용을 할 수 없다.(Pages Router에서만 가능)
- 예시

  ```
  src/app/`[id]`/page.tsx → /123 (params.id = "123")
  ```

## 예약 파일(Reserved Files)
- App Router에서 `폴더 = 경로`, `파일 = 역할` 이라는 원칙에 따라, 파일 이름은 마음대로 정할 수 없고 정해진 이름만 사용 가능.
- 종류

| 파일명               | 설명                                                |
| ----------------- | ------------------------------------------------- |
| **page.tsx**      | 실제 라우트 페이지 컴포넌트 (예: `/about`, `/blog/[id]`).      |
| **layout.tsx**    | 해당 경로 및 하위 경로에 적용되는 레이아웃(공통 UI). 중첩 가능.           |
| **template.tsx**  | layout과 유사하지만, 매번 새로운 인스턴스를 생성 (상태 공유 X).         |
| **error.tsx**     | 하위 라우트에서 에러 발생 시 표시되는 UI. (React error boundary). |
| **not-found.tsx** | `notFound()` 호출 시 또는 존재하지 않는 경로일 때 표시되는 UI.       |
| **loading.tsx**   | 해당 경로 로딩 중일 때 표시되는 UI (React Suspense 기반).        |
| **default.tsx**   | 병렬 라우트(Parallel Routes)에서 fallback UI 정의할 때 사용.   |

## 병렬 라우트(Parallel Routes)
- 일반적으로 app/ 폴더 구조는 경로(URL) = 페이지(page.tsx) 로 1:1 대응.
- 하지만 어떤 경우에는 같은 경로 내에서 여러 화면 조합이 필요할 수 있음.
- 병렬 라우트는 하나의 layout 안에 여러 슬롯(slot) 을 정의하고, 각 슬롯에 다른 UI를 주입할 수 있다.
- 예시

```
app/dashboard/layout.tsx
app/dashboard/@charts/page.tsx
app/dashboard/@news/page.tsx
```

```tsx
// layout.tsx
export default function DashboardLayout({
  charts,
  news,
}: {
  charts: React.ReactNode;
  news: React.ReactNode;
}) {
  return (
    <div>
      <aside>{charts}</aside>
      <section>{news}</section>
    </div>
  );
}

```


  
