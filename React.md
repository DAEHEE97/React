# React

---

### install node.js

React 앱을 만들기 위해 먼저 Node.js가 설치되어 있어야 합니다. 


### npx create-react-app 

npx create-react-app은 React 앱을 빠르게 생성하기 위한 명령어입니다.


설치된 상태에서 터미널 또는 명령 프롬프트에서 `npx create-react-app [app-name]`을 실행하면, 지정한 `[app-name]` 폴더에 새로운 React 프로젝트가 생성됩니다.


React 앱 개발을 위한 초기 설정과 프로젝트 구조를 자동으로 생성해주기 때문에, 개발자들은 이를 활용하여 바로 개발에 착수할 수 있습니다.

---

## 배포

- 빌드 (배포판 을 만드는 과정) : `npm run build`


- build 폴더 안에 있는 index.html 파일을 서비스 하는 웹 서버가 실행 됨 : `px serve -s build`

    - npx - node js, 
    - serve - 서비스
    - 웹 서버가 -s라는 옵션을 주면 어떤 경로로 들어오든 index.html 파일을 서비스 + build로 지정하면, 그 bulid 폴더에 있는 index.html 파일을 쓰겠다는 의미


---

## Componet 

- 사용자 정의 태그 

1. function name은 반드시 대문자로 시작해야 합니다. : Header(), Nav(), Article()

2. Return 값으로 html 코드를 return



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

---

## props

props는 컴포넌트의 외부에서 사용하는 입력값 입니다.  


- < img src width height /> 와 같은 Component 의 속성 


- 객체로 전달 받음 > 컴포넌트의 속성으로 props 입력값 처리 가능


- 전달 받은 객체 `{}` 중괄호 처리



---

```.jsx

import './App.css';


function Header(props){
  console.log(props.title)
  return <header>
    <h1><a href="/">{props.title}</a></h1>
  </header>
}

function Nav(props){

  const lis = []

  for(let i=0; i<props.topics.length; i++){
    
    let t = props.topics[i]; // 0 1 2 

    lis.push(<li key={t.id}><a href={'/read/'+t.id}>{t.title}</a></li>)

  }

  return <nav>
    <ol>
      {lis}
    </ol>
  </nav>
}

function Article(props){
  return <article>
    <h2>{props.title}</h2>
    {props.body}
  </article>
}


function App() {

  const topics = [
    {id:1, title:'html', body:'html is ...'},
    {id:2, title:'css', body:'css is ...'},
    {id:3, title:'javascript', body:'javascript is ...'}
  ] 

  return (
    <div>
      <Header title = 'REACT'></Header>
      <Nav topics={topics}></Nav>
      <Article title = 'Hello' body = 'React'></Article>
    </div>

  );
}

export default App;

```

---

## 컴포넌트 이벤트 처리


- `onChangeMode = `

onChangeMode 이벤트는, 주로 사용자의 입력값이 변경될 때 발생하는 이벤트로, 예를 들어 input 요소의 값이 변경될 때 발생합니다.

따라서, onChangeMode는 input 요소에서 발생하는 이벤트를 처리하거나, 부모 컴포넌트로부터 전달받은 상태를 변경하는 등의 역할을 수행할 수 있습니다. 



- `event.preventDefault();` 

기본 동작 비활성화 page reload 방지


- `props.onChangeMode();`

onChangeMode function 함수 실행 

---

```.jsx
//import logo from './logo.svg';
import './App.css';


function Header(props){
  console.log(props, props.title)
  return <header>
    <h1> <a href="/" onClick={function(event){
      event.preventDefault();
      props.onChangeMode();
    }}> {props.title} </a> </h1>
  </header>
} 

function Nav(props){

  const lis = []
  for(let i=0; i<props.topics.length; i++){
    
    let t = props.topics[i]; // 0 1 2 

    lis.push(<li key={t.id}>
      <a id = {t.id} href={'/read/'+t.id} onClick={event=>{
        
        event.preventDefault();
        props.onChangeMode(event.target.id);
        
    }}>{t.title}</a></li>)

  }

  return <nav>
    <ol>
      {lis}
    </ol>
  </nav>
}

function Article(props){
  return <article>
    <h2>{props.title}</h2>
    {props.body}
  </article>
}


function App() {

  const topics = [
    {id:1, title:'html', body:'html is ...'},
    {id:2, title:'css', body:'css is ...'},
    {id:3, title:'javascript', body:'javascript is ...'}
  ] 

  return (
    
    <div>

      <Header title = 'REACT' onChangeMode = {function(){alert('Header Click');} }></Header>

      <Header title = 'REACT' onChangeMode = {()=>{alert('Header');}}></Header>
      
      <Nav topics = {topics} onChangeMode = {(id)=>{alert(id);}}></Nav>
      
      <Article title = 'Hello' body = 'React'></Article>

    </div>

  );
}

export default App;
```

---

## 정리

```.jsx

function Header(){
  return <header>
    <h1><a href="/">WEB</a></h1>
  </header>
}

```

---

```.jsx
function Header(props){
  console.log(props.title)
  return <header>
  
    <h1><a href="/">{props.title}</a></h1>
    
  </header>
}
```

---


```.jsx
function Header(props){
  console.log(props, props.title)
  return <header>
  
    <h1> <a href="/" onClick={function(event){
      event.preventDefault();
      props.onChangeMode();
    }}> {props.title} </a> </h1>
    
  </header>
} 
```

---

### a 태그 클릭했을시 이벤트 처리, a 태그 id 처리 ( id = {t.id} ), 이벤트 속성안에서 a태그에 id 값 처리 (event.target.id)

```.jsx

<li><a href="/read/1">html</a></li>

```

---

```.jsx
<li key={t.id}><a href={'/read/'+t.id}>{t.title}</a></li>
```

---

```.jsx
<li key={t.id}><a id = {t.id} href={'/read/'+t.id} 
    onClick={event=>{
        event.preventDefault();
        props.onChangeMode(event.target.id);
        }
      }>{t.title}</a></li>)
      
```


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



- `npm start` :  Starts the development server.


- `npm run build` : Bundles the app into static files for production.


- `npm test` : Starts the test runner.

 
- `npm run eject` : Removes this tool and copies build dependencies, configuration files and scripts into the app directory. If you do this, you can’t go back!

---

props와 state는 React에서 컴포넌트의 데이터를 관리하는 두 가지 메커니즘입니다.

props는 컴포넌트 간 데이터를 전달하는 데 사용되며, 일반적으로 부모 컴포넌트가 자식 컴포넌트로 데이터를 전달할 때 사용됩니다.

props는 읽기 전용이므로, 자식 컴포넌트에서 변경할 수 없습니다. 

예를 들어, 부모 컴포넌트에서 title이라는 prop을 자식 컴포넌트에 전달하고, 자식 컴포넌트에서 이를 사용하여 제목을 렌더링할 수 있습니다.


state는 컴포넌트 내부의 데이터를 관리하는 데 사용됩니다. 

state는 읽기와 쓰기가 모두 가능합니다. 

컴포넌트 내부에서 상태를 변경하면, React는 자동으로 변경된 상태를 사용하여 UI를 업데이트합니다. 

state는 setState 메서드를 사용하여 변경합니다. 예를 들어, 버튼을 클릭할 때마다 숫자를 증가시키는 카운터 컴포넌트를 다음과 같이 구현할 수 있습니다.
