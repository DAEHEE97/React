# React_Basic_4


---

# state

useState() 함수는 React에서 제공하는 Hook 중 하나로, 함수 컴포넌트에서 상태를 관리하기 위해 사용됩니다. 

이 함수를 사용하면, state 변수와 해당 변수를 변경할 수 있는 함수를 쌍으로 생성할 수 있습니다.

예를 들어, mode와 같은 상태 변수가 변경되면, useState() 함수에 전달된 해당 상태 변수에 대한 새 값을 반환하고, 이 값은 App() 함수 컴포넌트에서 사용됩니다. 

이렇게 새로운 값을 반환함으로써, React는 자동으로 App() 함수 컴포넌트를 재실행하여 새로운 state 값을 반영합니다. 

따라서 useState() 함수는 React의 렌더링 시스템에서 컴포넌트의 상태 변경을 추적하고 새로운 UI를 렌더링하도록 만들어주는 역할을 합니다.


- `useState('1')` 배열 반환
    - [0]. '1' : 상태 값
    - [1]. $f()$ : 처리 함수
    

---

## mode 에 따른 논리 출력, 직접 입력 단점

- if, onChangeMode 로 클릭시, Mode 변경 처리시 작동 x,
- because mode 변수 값은 변경되지만 ,App() 함수 컴포넌트는 다시 실행하지 않기 때문에

```.jsx
function App() {

  const mode = 'asd';

  const topics = [
    {id:1, title:'html', body:'html is ...'},
    {id:2, title:'css', body:'css is ...'},
    {id:3, title:'javascript', body:'javascript is ...'}
  ] 

  let content = null;
  if (mode === 'welcome'){
    content = <Article title = 'Hello' body = 'welcome'></Article>

  }
  else{
    content = <Article title = 'Hello' body = 'else'></Article>
  }

  return (
    
    <div>

      {/* <Header title = 'REACT' onChangeMode = {function(){alert('Header Click');} }></Header> */}
      <Header title = 'REACT' onChangeMode = {()=>{alert('Header');}}></Header>
      <Nav topics = {topics} onChangeMode = {(id)=>{alert(id);}}></Nav>
      {content}

    </div>

  );
}

export default App;

```

---

## mode state

mode  값이 바뀌면서,  App() 함수 컴포넌트가 재실행 되도록, 새로운 리턴값을 반환하여 ui 반영 처리 

---



```.jsx
//import logo from './logo.svg';
import './App.css';
import { useState } from 'react';


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
        props.onChangeMode(Number(event.target.id));
        
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


  // const _mode = useState('1');
  // const mode = _mode[0];
  // const setMode = _mode[1];

  const [mode,setMode] = useState('1')

  console.log(mode,setMode);


  const topics = [
    {id:1, title:'html', body:'html is ...'},
    {id:2, title:'css', body:'css is ...'},
    {id:3, title:'javascript', body:'javascript is ...'}
  ] 

  let content = null;
  if (mode === '1'){
    content = <Article title = 'Hello' body = 'state 1'></Article>

  }
  else{
    content = <Article title = 'Hello' body = 'state 0'></Article>
  }



  return (
    
    <div>
      
      <Header title = 'REACT' onChangeMode = {()=>{
        alert('Header');
        // mode = 'state 1';
        setMode('1')

        }}></Header>

      <Nav topics = {topics} onChangeMode = {(id)=>{
        alert(id);
        // mode = 'state 0';
        setMode('0')

      }}></Nav>

      {content}

    </div>

  );
}

export default App;

```




---

## id state 처리 


- topic.id 랑 id(state) 랑 같으면, title, body 반영

- id(state) 는 문자형, id 는 setId 로 옴, setId는 _id 로 반영, 

- props.onChageMode(event.target.id) 로 입력 받은 걸 -> `<a id = {t.id} </a>` 처리 됨 t.id 반영 그러므로 

- event.target.id (str) >  Number(event.target.id) 정수형 변환


---

```.jsx

import './App.css';
import { useState } from 'react';


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
        props.onChangeMode(Number(event.target.id));
        
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


  // const _mode = useState('1');
  // const mode = _mode[0];
  // const setMode = _mode[1];

  const [mode,setMode] = useState('1')
  const [id, setId] = useState(null);

  const topics = [
    {id:1, title:'html', body:'html is ... state 0'},
    {id:2, title:'css', body:'css is ... state 0'},
    {id:3, title:'javascript', body:'javascript is ... state 0'}
  ] 

  let content = null;
  if (mode === '1'){
    content = <Article title = 'React' body = 'React is ... state 1'></Article>

  }
  else{

    let title, body = null;

    for(let i=0; i<topics.length; i++){
      console.log(topics[i].id, id);

      if(topics[i].id === id){
        title = topics[i].title;
        body = topics[i].body;
      }

    content = <Article title = {title} body = {body}></Article>
    
    }
  }

  return (
    
    <div>
      
      <Header title = 'REACT' onChangeMode = {()=>{
        alert('Header');
        // mode = 'state 1';
        setMode('1');

        }}></Header>

      <Nav topics = {topics} onChangeMode = {(_id)=>{
        alert(_id);
        // mode = 'state 0';
        setMode('0');
        setId(_id);

      }}></Nav>

      {content}

    </div>

  );
}

export default App;
```

---

## Src


React 앱이 실행될 때, 먼저 App() 컴포넌트가 실행됩니다.

App 컴포넌트 내부에서는 다음과 같은 일들이 수행됩니다.

1. useState Hook을 사용하여 mode와 id 상태 변수를 선언하고 초기값을 설정합니다. mode 변수의 초기값은 '1'로 설정되어 있습니다.

2. topics라는 배열 변수를 선언하고, 객체들을 요소로 하는 배열을 생성합니다.



3. App 컴포넌트에서 content 변수를 선언하고, 현재 mode가 '1'인 경우와 그렇지 않은 경우의 렌더링 결과를 할당합니다.

4. 'mode' 값에 따라 렌더링할 컨텐츠가 달라집니다. mode가 '1'이면 'React'라는 제목과 'React is ... state 1'이라는 내용이 들어있는 Article 컴포넌트가 content 변수에 할당됩니다.


5. mode가 '1'이 아니면 topics 배열을 순회하면서 id 값이 일치하는 title과 body를 찾습니다. 찾으면 Article 컴포넌트를 title과 body 값을 전달하여 생성하고, content 변수에 할당합니다.

6. Header 컴포넌트와 Nav 컴포넌트를 렌더링하면서 title, topics, onChangeMode 등의 props를 전달합니다.

7. Header 컴포넌트에서는 전달받은 title과 onChangeMode를 사용하여 제목과 링크를 렌더링합니다. 링크 클릭 시 props.onChangeMode() 함수를 호출하여 App 컴포넌트의 mode 값을 변경합니다.

8. Nav 컴포넌트에서는 topics 배열을 순회하면서 각각의 주제에 대한 링크를 생성합니다. 링크 클릭 시 props.onChangeMode() 함수를 호출하여 App 컴포넌트의 mode 값을 변경하고, 선택된 주제의 id 값을 setId 함수를 통해 id 상태로 설정합니다.

9. 마지막으로, content 변수에 저장된 컴포넌트를 렌더링하여 해당하는 내용이 표시됩니다.





---

Header 컴포넌트는 페이지 상단에 위치하며, props로 전달받은 제목(title)과 onChangeMode 함수를 출력합니다. onChangeMode 함수는 a 태그를 클릭할 때 호출되며, 이벤트를 중지하고 App 컴포넌트의 mode 상태를 변경합니다.

Nav 컴포넌트는 페이지 상단의 메뉴를 출력합니다. props로 전달받은 주제(topics)를 이용하여 메뉴를 동적으로 생성합니다. 메뉴 항목을 클릭할 때 호출되는 onChangeMode 함수는 이벤트를 중지하고 App 컴포넌트의 mode와 id 상태를 변경합니다.

Article 컴포넌트는 페이지의 내용을 출력합니다. props로 전달받은 제목(title)과 내용(body)을 출력합니다.

App 컴포넌트는 Header, Nav, Article 컴포넌트를 렌더링합니다. 또한, mode와 id 상태를 관리하고, 이들 상태에 따라 Article 컴포넌트의 내용을 동적으로 변경합니다. 이벤트 핸들러를 정의하여 상태를 변경할 수 있도록 하고, 이벤트 핸들러에서는 alert 함수를 호출하여 이벤트가 제대로 동작하는지 확인할 수 있도록 합니다.

또한, useState를 사용하여 mode와 id 상태를 정의하고 초기값을 설정합니다. 이들 상태는 컴포넌트의 렌더링에 영향을 미치는 중요한 역할을 합니다. 렌더링 결과는 content 변수에 저장되며, mode 상태에 따라 다른 내용이 출력됩니다. content 변수는 App 컴포넌트의 반환값으로 사용됩니다.




---
