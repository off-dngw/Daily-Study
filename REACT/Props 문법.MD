### Props 문법
- 컴포넌트의 속성을 의미합니다
- 부모컴포넌트(상위컴포넌트)로 부터 전달 받은 값입니다.
- React 컴포넌트는 JavaScript 함수와 클래스로 props를 전달 인자(argument)처럼 전달 받습니다.
- 객체 형태이며 props는 읽기 전용 입니다.


### Props 사용 예시
props로 전달 할때 
예시 하나를 들자면
프롭스전달1 = {부모1}
부모1은 프롭스에 전달 될 값
프롭스전달1 은 props.을 사용해 가져올 변수명을 사용하면 된다.

```
import "./styles.css";

const App = () => {
  const 부모1 = "안녕하세요";
  const 부모2 = "리액트입니다";

  return (
    <div className="App">
      {/* Learn 컴포넌트에 itemOne 과 itemTwo 를
      props 로 전달하세요 */}
      <Learn 프롭스전달1={부모1} 프롭스전달2={부모2}/>
    </div>
  );
};

const Learn = (props) => {

return(
  <>
  <h2 className="Learn">
    {props.프롭스전달1}
  </h2>
  <h3>{props.프롭스전달2}</h3>

  </>
  ) 
  
  ;

};

export default App;

```