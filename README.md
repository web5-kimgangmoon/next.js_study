# NEXT.JS 학습시작

## 08/22

### git repository init

npm i react@latest react-dom@latest next@latest

### next 기초

https://nextjs.org/learn/react-foundations

<!-- - 페이지에서의 nextjs와 현재 버전 간에 차이가 있는 것 같다. -->

- user interface - 사용자가 애플리케이션을 사용하고 상호작용하는 방식입니다.
- routing - 사용자가 애플리케이션의 여러 부분 사이를 탐색하는 방식입니다.
- data fetching - 데이터가 어디에 있는지, 그리고 어떻게 가져오는지.
- rendering - 정적 또는 동적 콘텐츠를 언제, 어디에서 렌더링하는지.
- integration - 어떤 타사 서비스를 사용하는지(CMS, 인증, 결제 등)와 이러한 서비스에 어떻게 연결하는지.
- infrastructure - 애플리케이션 코드를 배포, 저장, 실행하는 위치(서버리스, CDN, 엣지 등).
- preformance - 최종 사용자를 위해 애플리케이션을 어떻게 최적화하는가.
- scalability(확장성) - 팀, 데이터, 트래픽이 증가함에 따라 애플리케이션이 어떻게 적응하는지.
- developer experience(개발자 경험) - 애플리케이션을 구축하고 유지 관리하는 팀의 경험입니다.
- DOM - HTML 요소의 객체 표현입니다. 코드와 사용자 인터페이스 사이의 다리 역할을 하며 부모와 자식 관계가 있는 트리와 같은 구조를 가지고 있습니다.
- 네트워크 경계 - 서로 다른 환경을 구분하는 개념적 선입니다.

#### 서버 구성 요소가 렌더링된 후 RSC(React Server Component Payload)라는 특수 데이터 형식이 클라이언트로 전송됩니다. RSC 페이로드에는 다음이 포함됩니다.

- 서버 구성 요소의 렌더링된 결과입니다.

2. 클라이언트 구성 요소를 렌더링해야 하는 위치에 대한 placeholder Data와 해당 JavaScript 파일에 대한 참조입니다.
3. React는 이 정보를 사용하여 서버 및 클라이언트 구성 요소를 통합하고 클라이언트에서 DOM을 업데이트합니다.

## next Adavance

https://nextjs.org/learn/dashboard-app/getting-started

다음을 사용하는 것이 좋습니다. pnpm 패키지 관리자로서 또는 보다 빠르고 효율적입니다. 설치하지 않은 경우 다음을 실행하여 전역적으로 설치할 수 있습니다

```bash
npm install -g pnpm
cd next_advance
npx create-next-app@latest nextjs-dashboard --example "https://github.com/vercel/next-learn/tree/main/dashboard/starter-example" --use-pnpm
cd nextjs-dashboard
pnpm i
```

#### 경로

- /app: 애플리케이션에 대한 모든 경로, 구성 요소 및 논리를 포함하며, 주로 작업할 위치입니다.
- /app/lib: 재사용 가능한 유틸리티 함수 및 데이터 가져오기 함수와 같이 애플리케이션에서 사용되는 함수를 포함합니다.
- /app/ui: 카드, 테이블 및 폼과 같은 애플리케이션의 모든 UI 구성 요소를 포함합니다. 시간을 절약하기 위해 이러한 구성 요소를 미리 스타일링했습니다.
- /public: 이미지와 같은 응용 프로그램의 모든 정적 자산을 포함합니다.
- 구성 파일: 응용 프로그램의 루트와 같은 구성 파일도 확인할 수 있습니다. 이러한 파일의 대부분은 새 프로젝트를 시작할 때 만들어지고 미리 구성됩니다. 이 과정에서는 수정할 필요가 없습니다.(next.config.jscreate-next-app)

Placeholder data

- 사용자 인터페이스를 빌드할 때 몇 가지 placeholder data가 있으면 도움이 됩니다. 데이터베이스 또는 API를 아직 사용할 수 없는 경우 다음을 수행할 수 있습니다.

- placeholder data를 JSON 형식 또는 JavaScript 개체로 사용합니다.
- 제3자 서비스 사용(이 문서에서 예시로 mock 라이브러리를 보여줬다.)

데이터 형식 안정성을 위해 쓸만한 라이브러리

- prisma
- drizzle

pnpm dev 포트에서 Next.js 개발 서버를 시작합니다. 작동하는지 확인해 보겠습니다.3000
http://localhost:3000 브라우저에서. 홈페이지는 다음과 같아야 하며 의도적으로 스타일이 지정되지 않았습니다.

이 파일을 사용하여 CSS 재설정 규칙, 링크와 같은 HTML 요소에 대한 사이트 전체 스타일 등과 같은 CSS 규칙을 애플리케이션의 모든 경로에 추가할 수 있습니다.

- /app/ui/global.css (root layout)

하지만 잠깐만요, CSS 규칙을 추가하지 않으셨는데, 스타일은 어디서 왔나요?  
내부를 살펴보면 몇 가지 지시문을 확인할 수 있습니다.global.css@tailwind

- next.js는 알아서 tailwind 설정을 해준다. (framework), (선언적 프로그래밍)

CSS 스타일은 전역적으로 공유되지만 각 클래스는 각 요소에 개별적으로 적용됩니다. 즉, 요소를 추가하거나 삭제하는 경우 별도의 스타일시트를 유지 관리하거나, 스타일 충돌을 유지하거나, 애플리케이션이 확장됨에 따라 CSS 번들의 크기가 커지는 것에 대해 걱정할 필요가 없습니다.

새 프로젝트를 시작하는 데 사용할 때 Next.js Tailwind를 사용할 것인지 묻습니다. 를 선택하면 Next.js 자동으로 필요한 패키지를 설치하고 애플리케이션에서 Tailwind를 구성합니다.
create-next-app, yes
