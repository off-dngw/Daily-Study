### useState 문법
State는 컴포넌트 내부에서 변할 수 있는 값입니다.
한마디로 어플리케이션의 상태라고 볼 수가 있습니다.
실제 어플리케이션 에서는 무엇이 상태라고 정의가 되어질까요?

밑에 예시 처럼 한번 보시죠!


### useState 사용법

### 주의 할 점!
React 컴포넌트는 state가 변경되면 새롭게 호출되고 리렌더링이 됩니다.
즉, 컴포넌트의 상태가 변경 될 때 마다 새롭게 호출하고 
리렌더링이 됩니다.

```
//useState를 사용하기 위해서는 import를 사용해서 useState라는 객체를 불러와야 합니다.
import React, { useState } from "react";
import "./styles.css";

function CheckboxExample() {
// 새로운 변수를 하나 선언하고 useState() 괄호안에 초기값을 넣어 줄수 있습니다. 그래서 false라는걸 지정을 해주어 볼게요!
  const [isChecked, setIsChecked] = useState(false);
  // const [state 저장 변수, state 갱신 함수] = useState(state 초기 값);

//체크박스를 클릭하는 핸들링을 만들어 주겠습니다.
  const handleChecked = (event) => {
    setIsChecked(event.target.checked);
  };
  return (
    <div className="App">
      //input type 에 checkbox의 값을 주었기 때문 체크를 할 수있는 박스의 모양이 나올것이고
      //사용자가 체크박스 값을 변경하면 onChange 이벤트가 이벤트 핸들러 함수인 handleChecked 를 호출하고, 이 함수가 setIsChecked 를 호출하게 됩니다. setIsChecked 가 호출되면 호출된 결과에 따라 isChecked 변수가 갱신되며, React는 새로운 isChecked 변수를 CheckboxExample 컴포넌트에 넘겨 해당 컴포넌트를 다시 렌더링 합니다.
      <input type="checkbox" checked={isChecked} onChange={handleChecked} />

      //JSX에서는 if문 대신 삼항연산자를 사용해야합니다!
      //isChecked의 값이 위에서 지정해준 상태 값으로 true면 문자가 Checked!! 라고 나옵니다.
      //isChecked의 값이 false 이면 초기값과 같은 상태니 Unchecked!! 라고 나올 것이죠!
      <span>{isChecked ? "Checked!!" : "Unchecked"}</span>
    </div>
  );
}

export default CheckboxExample;


```
