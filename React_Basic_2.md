# React_Basic_2

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

  console.log('props',props,props.title)

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

## src



Header 함수 컴포넌트 는 `<h1>` 태그 안에 링크를 생성, props를 인자로 받아서 prop.title 값을 처리한다.


Nav 함수 컴포넌트 는 props를 인자로 받아서 prop.topics 의 값을 사용하여 각각의 topic에 대한 링크를 생성한다. 

lis 배열 우선 생성, for 루프를 사용하여 props.topics 배열을 순회하고, 각각의 topic에 대한 링크를 생성하여 lis 배열에 추가한 후, lis 배열을 `<ol>` 태그 안에 렌더링한다.

Article 함수 컴포넌트 는 props를 인자로 받아서 prop.title 의 값을 사용하여 제목을 생성하고, prop.body 의 값을 사용하여 본문을 생성한다.


App 함수 컴포넌트 는 topics라는 배열을 선언하고, `<Header>`, `<Nav>`, `<Article>` 컴포넌트를 사용하여 화면을 구성한다. 



이렇게 props를 이용하여 데이터를 전달하면, Header, Nav, Article 컴포넌트에서는 전달된 데이터를 사용하여 UI를 생성할 수 있다.

마지막으로, export default 문을 사용하여 App 구성 요소를 내보내고, 다른 파일에서 가져올 수 있도록 합니다.



---
