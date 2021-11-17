# Section 1: Getting started

## 왜 next.js일까?: react와 비교했을 떄 next.js의 장점과 특징

-   Automatic page pre-rendering : 첫 렌더링 시 빈 html이 아니기 때문에 SEO(검색 엔진 최적화)에 좋고 첫 로딩 속도(initial load)가 빠르다.
-   Blending client-side and server-side rendering : 두 가지 장점을 모두 가져왔다
-   File-based routing : react-router 와 같이 코드 작성에 번거로움 없이 파일/폴더로 라우팅이 가능하다.
-   Fullstack capabilities : 밴엔드 코드를 쉽게 넣을 수 있다

## next.js 시작하기 with TypeScript

-   설치

```
npx create-next-app (폴더명) --typescript
```

-   public : index.html 파일 없다. request가 server에 도달하기 전에 pre-render되므로
-   개발 서버 열기 : npm run dev <-index.js 파일이 pre-rendered 된 상태로 열림

<br />

# Pages & File-based Routing

## File-based Routing instead of Code-based Routing

next.js에서는 react-router가 필요 없다.

경로별 예시는 다음과 같다.

1.  /pages/index.tsx: 시작 페이지. `/`
2.  /pages/about.tsx: `/about`
3.  /pages/products/index.tsx: `/product`
4.  /pages/products/list.tsx: `/product/list`
5.  /pages/products/[id].tsx: detail 페이지. `/product/:id`

### 동적 라우팅(Dynamic Routing)

-   동적 라우팅 파일을 찾는 원리: 어떤 id로 접근 시 next 자체에서 같은 폴더 내의 id 이름과 동일한 파일을 찾고, 없으면 [id].tsx 파일을 보여준다.
-   물론 [] 안에 들어가는 변수명은 아무거나 상관없다.
-   Path segment data 가져오기: `useRouter()`

```tsx
import { useRouter } from "next/dist/client/router";

const DetailPage = () => {
    const router = useRouter();

    console.log(router.query); // { id: value }
    console.log(router.query.id); // 우리가 원하는 값
    //...
};
```

-   중첩 동적 라우팅(Nested Dynamic Routing) -> **n개의 id**를 모두 얻을 수 있다.

    예시 /pages/products/[productId]/[userId].tsx: `/products/:productId/:userId`

    ```tsx
    import { useRouter } from "next/dist/client/router";

    const DetailPage = () => {
        const router = useRouter();

        console.log(router.query); // { productId: value1, userId: value2 }
        console.log(router.query.productId); // value1
        console.log(router.query.userId); // value2
        //...
    };
    ```

    <br />

-   Catch-All Routing: `/some/thing`와 같이 "/"로 나뉜 url 값들을 모두 가져오고 싶을 때

    파일 혹은 폴더명: **spread 연산자**로 작성

    ```
    [...datas].tsx
    [...datas]/index.tsx
    ```

    예시

    ```tsx
    import { useRouter } from "next/dist/client/router";

    const DetailPage = () => {
        const router = useRouter();

        console.log(router.query); // { datas: [some, thing] }
        console.log(router.query.datas[0]); // some
        console.log(router.query.datas[1]); // thing
        //...
    };
    ```
