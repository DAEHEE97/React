# React_Basic_1

---

- install node.js

React 앱을 만들기 위해 먼저 Node.js가 설치되어 있어야 합니다. 


- `npx create-react-app` 

npx create-react-app은 React 앱을 빠르게 생성하기 위한 명령어입니다.


설치된 상태에서 터미널 또는 명령 프롬프트에서 `npx create-react-app [app-name]`을 실행하면, 지정한 `[app-name]` 폴더에 새로운 React 프로젝트가 생성됩니다.


React 앱 개발을 위한 초기 설정과 프로젝트 구조를 자동으로 생성해주기 때문에, 개발자들은 이를 활용하여 바로 개발에 착수할 수 있습니다.

---

### App.css

React 앱에서 사용할 스타일을 정의하는 파일입니다. 

CSS 문법을 사용하여 스타일을 작성할 수 있으며, 이 파일에서 작성한 스타일은 App.js 파일에서 import하여 사용할 수 있습니다.

### App.js

React 앱의 루트 컴포넌트입니다. 이 파일에서는 React 컴포넌트를 정의하고, 해당 컴포넌트가 렌더링할 JSX 코드를 작성합니다. 또한, 이 파일에서는 import 문을 사용하여 App.css 파일을 불러와서 스타일을 적용할 수 있습니다.

### App.test.js

App.js 컴포넌트의 유닛 테스트를 위한 파일입니다. 

Jest 프레임워크를 사용하여 컴포넌트의 동작을 검증할 수 있습니다.

### index.css

React 앱 전반에 걸쳐 사용할 스타일을 정의하는 파일입니다. 

이 파일에서는 App.css와 마찬가지로 CSS 문법을 사용하여 스타일을 작성할 수 있습니다.

### index.js

React 앱의 진입점 역할을 수행하는 파일입니다. 

이 파일에서는 ReactDOM.render() 함수를 사용하여 React 앱을 실제 DOM에 렌더링합니다.

### logo.svg

React 앱에서 사용하는 로고 이미지 파일입니다.

App.js 컴포넌트에서 import하여 사용할 수 있습니다.

### reportWebVitals.js

Web Vitals API를 사용하여 React 앱의 성능을 모니터링하는 파일입니다. 

이 파일에서는 reportWebVitals() 함수를 정의하여 사용자 경험 측면에서 중요한 성능 지표를 측정합니다.

### setupTests.js

Jest 프레임워크에서 유닛 테스트 실행 전에 실행할 설정 파일입니다. 

이 파일에서는 유닛 테스트를 위한 환경 설정 등을 수행할 수 있습니다.

---

## 배포

- 빌드 (배포판 을 만드는 과정) : `npm run build`


- build 폴더 안에 있는 index.html 파일을 서비스 하는 웹 서버가 실행 됨 : `npx serve -s build`


    - npx - node js, 
    - serve - 서비스
    - 웹 서버가 -s라는 옵션을 주면 어떤 경로로 들어오든 index.html 파일을 서비스 + build로 지정하면, 그 bulid 폴더에 있는 index.html 파일을 쓰겠다는 의미


---

## Componet 

- 함수 컨포넌트 (사용자 정의 태그) 

    1. function name은 반드시 대문자로 시작해야 합니다. : Header(), Nav(), Article()

    2. Return 값으로 html 코드를 return


함수 컴포넌트는 함수를 정의하여 React element를 반환하는 것입니다. 

이러한 함수 컴포넌트는 React의 기본적인 구성 요소 중 하나로, 특히 재사용 가능한 UI 구성 요소를 작성하는 데 유용합니다.

반면, 일반적인 함수는 React 컴포넌트가 아닙니다. 함수는 특정한 컴포넌트를 정의하거나 렌더링하는 데 사용되지 않습니다. 

그러나 함수는 컴포넌트의 일부 기능을 수행하는 데 사용될 수 있습니다. 예를 들어, 코드에서 console.log()를 호출하는 데 사용되는 함수는 컴포넌트가 아니며 React와는 관련이 없습니다.




---

```.jsx


function Header(){
  return <header>
    <h1><a href="/">WEB</a></h1>
  </header>
}

function Nav(){
  return <nav>
    <ol>
      <li><a href="/read/1">html</a></li>
      <li><a href="/read/2">css</a></li>
      <li><a href="/read/3">js</a></li>
    </ol>
  </nav>
}

function Article(){
  return <article>
    <h2>Welcome</h2>
    Hello, WEB
  </article>
}


function App() {
  return (
    
    <div>
      <Header></Header>
      <Nav></Nav>
      <Article></Article>
    </div>

  );
}

export default App;



```

## src

React를 사용하여 간단한 웹 페이지의 구조를 만든 예시입니다.

React에서, Component들은 각각의 독립적인 기능을 수행하며, 이러한 Component들을 모아 하나의 완전한 UI를 만들어내는 것이 일반적인 패턴입니다.


App() 함수는 JSX 문법을 사용하여 React 엘리먼트를 반환합니다. ( Component들을 모아하나의 완전한 UI를 만들어내는 역할)




이 함수는 JSX(JSX는 JavaScript XML의 약자)를 반환하는데, 이 JSX는 여러 개의 Component들을 조합하여 만들어진 완전한 UI를 나타냅니다.

위 코드에서는 `<div>` 태그를 사용하여 Header, Nav, Article Component들을 하나의 요소로 묶어주고 있습니다. 



따라서, App() 함수는 여러 개의 Component들을 조합하여 하나의 UI를 만들어내는 중요한 역할을 합니다.
    



마지막으로, export default App; 구문을 통해 App() 함수를 내보냅니다. 이를 통해, 해당 코드를 사용하는 다른 코드에서 App() 함수를 import하여 사용할 수 있습니다.

---

### JSX

JSX는 JavaScript XML의 약자로, React에서 UI를 작성하기 위해 사용되는 문법입니다. 

JSX는 HTML과 유사한 문법을 가지고 있지만, 이는 JavaScript 확장 문법으로 처리됩니다. 따라서 JSX에서는 JavaScript의 모든 기능을 사용할 수 있습니다.
 

예를 들어, 다음은 App 컴포넌트에서 JSX를 사용하여 UI를 정의한 예시입니다.


```.jsx

function App() {
  return (
    <div className="App">
      <h1>Hello, world!</h1>
      <p>Welcome to my React app.</p>
    </div>
  );
}

 
```

위 코드에서 `<div`, `<h1>`, `<p>`와 같은 태그들은 JSX를 통해 정의된 React 컴포넌트를 나타냅니다. 



이러한 React에서 JSX 코드를 실행하면, 컴파일러가 JSX 코드를 JavaScript 코드로 변환하여 화면에 출력합니다.

이 과정에서 React.createElement() 함수가 자동으로 호출됩니다.


---



JSX 코드는 일종의 JavaScript 확장 문법으로, React 엘리먼트를 생성하기 위해 사용됩니다. 

하지만, 브라우저에서는 JSX를 이해하지 못하기 때문에, JSX 코드는 React.createElement() 함수를 통해 JavaScript 코드로 변환됩니다. 

이 함수는 JSX에서 생성하려는 React 엘리먼트의 타입, 속성, 자식 엘리먼트 등을 인자로 받아, 이를 기반으로 JavaScript 객체 형태로 React 엘리먼트를 생성합니다. 

이후, 생성된 React 엘리먼트는 브라우저에서 렌더링됩니다. 즉, JSX 코드는 최종적으로 JavaScript 코드로 변환되어 실행되는 것입니다.



JSX는 컴파일되면 React.createElement() 함수를 호출하여 React 엘리먼트를 생성하므로, 사실상 JSX를 반환하는 것과 React 엘리먼트를 반환하는 것은 같은 의미를 갖습니다. 따라서 JSX를 반환하는 것이라고 말해도 되고, React 엘리먼트를 반환하는 것이라고 말해도 되는 것입니다.


---

### `export default`

JavaScript에서, `export default`는 파일에서 하나의 기능을 내보낼 때 사용하는 문법입니다. 

위의 코드에서는 App Component를 내보내는 것이므로, export default App; 구문이 사용되었습니다.

이를 통해, 다른 파일에서 이 App Component를 불러와 사용할 수 있게 됩니다. 

예를 들어, 다른 파일(index.js)에서 import App from './App'; 구문을 사용하여 이 파일에서 내보낸 App Component를 불러와 사용할 수 있습니다.

export default 구문은 다음과 같은 형식으로 사용됩니다.

`export default [기능];' : 이 때, [기능]은 하나의 함수, 변수, 클래스, 객체 등이 될 수 있습니

---

```index.jsx

import React from 'react';
import ReactDOM from 'react-dom/client';
import './index.css';
import App from './App';
import reportWebVitals from './reportWebVitals';

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);

// If you want to start measuring performance in your app, pass a function
// to log results (for example: reportWebVitals(console.log))
// or send to an analytics endpoint. Learn more: https://bit.ly/CRA-vitals
reportWebVitals();



```



---

### `<div>`
    
HTML에서 `<div>` 태그는 구역을 설정하는 데 사용되는 블록 수준 요소(block-level element)입니다.

`<div` 태그는 주로 CSS를 사용하여 해당 구역을 스타일링하거나, 자바스크립트를 사용하여 해당 구역을 조작하는 데에 사용됩니다. 

또한, 여러 개의 다른 요소를 그룹화하여 하나의 요소로 만들기도 합니다.

예를 들어, 위의 React 코드에서는 `<div>` 태그를 사용하여 Header, Nav, Article Component들을 하나의 요소로 묶어주고 있습니다. 

이를 통해, 해당 UI의 구조를 잘 정리하고 유지보수하기 용이하게 만들 수 있습니다.

---

---

### npm

- `npm start` :  Starts the development server.


- `npm run build` : Bundles the app into static files for production.


- `npm test` : Starts the test runner.

 
- `npm run eject` : Removes this tool and copies build dependencies, configuration files and scripts into the app directory. If you do this, you can’t go back!


npm은 Node.js를 기반으로 하는 JavaScript 패키지 관리자입니다. 

이 패키지 관리자를 통해 다른 개발자들이 만든 JavaScript 패키지를 손쉽게 설치하고, 관리할 수 있습니다.

위에서 나열된 명령어들은 npm을 통해 React 앱을 개발할 때 자주 사용되는 명령어들입니다.

npm start : 개발 서버를 시작합니다. 개발 중인 앱을 빠르게 테스트하고 확인할 수 있습니다.

npm run build : 앱을 프로덕션 환경에서 사용할 수 있도록 정적 파일로 번들링합니다.

npm test : 테스트 실행기를 시작합니다. Jest와 같은 테스트 프레임워크를 사용하여 앱의 단위 테스트를 실행할 수 있습니다.

npm run eject : Create React App에서 생성한 환경을 밖으로 내보냅니다. 이 작업을 하면 개발 환경을 직접 구성할 수 있으나, 이후에 Create React App에서 제공하는 기능을 사용할 수 없게 됩니다. 따라서, 이 작업은 신중하게 진행해야 합니다.

이러한 명령어들은 React 앱을 개발하는 데 있어서 매우 중요한 역할을 합니다.


---

### npx

npx는 npm 5.2.0 버전부터 추가된 도구입니다. npx를 사용하면 로컬에 설치하지 않은 커맨드를 실행할 수 있습니다. 

즉, 로컬에 설치하지 않고, npm registry에서 다운로드하여 실행할 수 있습니다.

npx를 사용하면, 프로젝트의 node_modules 디렉토리에 설치하지 않아도 패키지를 실행할 수 있기 때문에, 환경을 깨끗하게 유지할 수 있습니다. 

또한, 프로젝트 내에 설치된 패키지들을 쉽게 사용할 수 있습니다.

예를 들어, create-react-app을 사용하여 새로운 React 프로젝트를 만들 때, npx create-react-app my-app와 같이 npx를 사용하여 create-react-app을 실행할 수 있습니다. 

이렇게 하면, create-react-app을 전역적으로 설치하지 않고도 프로젝트를 시작할 수 있습니다.
