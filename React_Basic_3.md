# React_Basic_3

---

- Header 컴포넌트가 클릭되었을 때 경고창이 뜨도록 onClick 이벤트 핸들러를 추가하여, Header 컴포넌트에서 onClick 이벤트를 직접 처리

```.jsx
import './App.css';


function Header(props){

  const handleClick = () => {
    alert('Header 클릭됨!');
  };

  return <header onClick={handleClick}>
    <h1><a href="/">{props.title}</a></h1>
  </header>
}

function Nav(props){
  
  const lis = []

  for(let i=0; i<props.topics.length; i++){
    
    let t = props.topics[i]; // 0 1 2 
    lis.push(<li key={t.id}><a href={'/read/'+t.id}>{t.title}</a></li>)
  }

  return <nav><ol>{lis}</ol></nav>
}

function Article(props){
  return <article><h2>{props.title}</h2>
  {props.body}</article>
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
      <Article title = 'React' body = 'is ...'></Article>
    </div>
  );
}

export default App;
```

---

## 컴포넌트 이벤트 처리


onClick 이벤트 핸들러가 props로 전달되고, 이를 호출하도록 처리

따라서, 이번 코드에서는 Header 컴포넌트에서 onClick 이벤트를 직접 처리하는 것이 아니라, 부모 컴포넌트에서 전달된 onChangeMode props를 호출하는 방식으로 동작합니다. 이렇게 하면 부모 컴포넌트에서 Header의 동작을 컨트롤할 수 있게 됩니다.


- `event.preventDefault();` : 기본 동작 비활성화 page reload 방지


- `props.onChangeMode();` : onChangeMode function 함수 실행 

---

```.jsx
import './App.css';

function Header(props){
  console.log(props)

  return <header>
    <h1><a href="/" onClick={(event)=>{
      event.preventDefault();
      props.onChangeMode();
    }}>{props.title}</a></h1>
  </header>
}

function Nav(props){
  
  const lis = []

  for(let i=0; i<props.topics.length; i++){
    
    let t = props.topics[i]; // 0 1 2 
    lis.push(<li key={t.id}><a href={'/read/'+t.id}>{t.title}</a></li>)
  }

  return <nav><ol>{lis}</ol></nav>
}

function Article(props){
  return <article><h2>{props.title}</h2>
  {props.body}</article>
}


function App() {

  const topics = [
    {id:1, title:'html', body:'html is ...'},
    {id:2, title:'css', body:'css is ...'},
    {id:3, title:'javascript', body:'javascript is ...'}
  ] 

  return (
    <div>
      <Header title = 'REACT' onChangeMode = {()=>{alert('Header 클릭됨!');}} ></Header>

      <Nav topics={topics}></Nav>
      <Article title = 'React' body = 'is ...'></Article>
    </div>
  );
}

export default App;

```

## src

App 컴포넌트가 부모 컴포넌트이고, Header, Nav, Article 컴포넌트들은 모두 App 컴포넌트의 자식 컴포넌트입니다. 

이러한 구조에서 App 컴포넌트가 각각의 자식 컴포넌트들에게 props 값을 전달하여, 자식 컴포넌트가 해당 props 값을 사용하여 UI를 렌더링하고, 이벤트 처리 등의 기능을 수행하게 됩니다.


--- 

Header 컴포넌트는 props로 `title`과 `onChangeMode`를 받으며, 이를 `<a>` 요소의 텍스트와 onClick 핸들러에 각각 사용합니다. 


Header 컴포넌트는 단순히 onClick 이벤트 핸들러를 정의하고, 해당 이벤트를 발생시키는 것만 담당합니다. 

부모 컴포넌트에서는 이벤트 핸들러를 props로 전달하고, 필요에 따라 이벤트 핸들러를 수정하거나 다른 핸들러를 전달할 수 있습니다.


따라서 부모 App 컴포넌트가 Header의 동작을 컨트롤할 수 있게 됩니다. 


    


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

## state

React 16.8버전부터는 Hook 중 하나인 useState를 사용해서 함수 Component에서도 state를 사용할 수 있게 되었습니다. 

useState는 state와 그 state를 업데이트하는 함수인 setState를 반환합니다. 

이 함수를 사용하면 state를 업데이트하고, 새로고침 없이 Component를 rendering해줍니다.
