# Section 1: Getting started

## 왜 next.js일까?: react와 비교했을 떄 next.js의 장점과 특징

-   Automatic page pre-rendering : 첫 렌더링 시 빈 html이 아니기 때문에 SEO(검색 엔진 최적화)에 좋고 첫 로딩 속도(initial load)가 빠르다.
-   Blending client-side and server-side rendering : 두 가지 장점을 모두 가져왔다
-   File-based routing : react-router 와 같이 코드 작성에 번거로움 없이 파일/폴더로 라우팅이 가능하다.
-   Fullstack capabilities : 밴엔드 코드를 쉽게 넣을 수 있다

## next.js 시작하기

-   설치 : npx create-next-app (폴더명)
-   public : index.html 파일 없다. request가 server에 도달하기 전에 pre-render되므로
-   개발 서버 열기 : npm run dev <-index.js 파일이 pre-rendered 된 상태로 열림

## next.js 초기화하기

-   index.js의 wrapper만 남기고 모든 태그 제거
