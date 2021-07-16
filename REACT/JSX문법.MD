## JSX 문법 

---
JSX는 JavaScript XML의 줄임말로 문자열도 아니고 HTML도 아닙니다.
React에서 UI를 구성할 때 사용되는 문법으로 JavaScript를 확장한 문법입니다.
하지만 브라우저가 바로 실행할 수 있는 JavaScript 코드가 아니라 
브라우저가 이해할 수 있는 JavaScript코드로 변환을 해주어야 하는데 이때 사용하는 것이 Babel입니다.
Babel은 JSX를 브라우저가 이해할 수 있는 JavaScript로 컴파일 합니다.

---

## JSX 활용과 문법

JSX에서 여러 엘리먼트를 작성하고자 할 때는 반드시 opening tag와 closing tag로 감싸주어야 합니다.

#### 예시

```
틀린 방법
<div>
 <h2>안녕</h2>
</div> 

옳은 방법

<> 
 <div>
  <h2>안녕</h2>
  </div>
  <div>
    <h2>안녕</h2>
  </div>
</>

```
---

### 규칙
### 엘리먼트 사용시 className 으로 표기!
React 에서 class 속성을 지정을 하려면 꼭 className을 사용하여야 합니다.
```
틀린 방법
<div class ="div">
옳은 방법
<div className ="div">

```

### JavaScript 표현식 사용 시 중괄호 {} 를 이용!
JSX에서 JavaScript를 쓰고자 한다면 꼭 중괄호를 사용하여야 합니다.
```
function App(){
    const name = "kdw"
    return(
      <div>
       Hello,{name} <-- 변수명에 중괄호를 사용
      </div>
    )
}

```

```

function hello(){ <-- 틀린 표현
function Hello() <-- 옳은 표현
    return <div>Hello</div>
}
function HelloWorld(){
    return <hello /> <-- 틀린 표현
    return <Hello /> <-- 옳은 표현
}

```

### 조건부 렌더링에는 삼항연산자 사용!
조건부 렌더링에는 if문이 아닌 삼항연산자를 사용해야 합니다.
```
<div>
    {
        (1 + 1 === 2 ) ? (<p>정답</p>) : (<p>오답</p>)
    }
</div>
```






