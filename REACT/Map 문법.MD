### Map()함수
-여러 개의 HTML 엘리먼트를 표시 할 때 map()함수를 이용!


### 하드코딩 했을 때
```
const posts = [
  { id: 1, title: "Hello World", content: "Welcome to learning React!" },
  { id: 2, title: "Installation", content: "You can install React via npm." },
  { id: 3, title: "Practice", content: "Practice React via npm run start" }
];

export default function Blog() {
  return (
    <div>
      <div>
        <h3>{posts[0].title}</h3>
        <p>{posts[0].content}</p>
      </div>
      <div>
        {/* TODO : 배열 메소드 map을 이용하여 포스트를 화면에 보여주세요. */}
      </div>
    </div>
  );
}


```
### Map을 사용해서 간단하게 사용 시 
주의 사항 : React에서 map 메소드 사용 시, key 속성을 넣지 않으면 아래와 같이
리스트의 각 항목에 key를 넣어야 한다는 경고가 표시됩니다
key 속성의 위치는 map 메소드 내부에 있는 엘리먼트 즉, 첫 엘리먼트에 넣어주세요.
```
export default function Blog() {
  return (
    <div>
         {
          posts.map((el) =>(
            <div>
            <div key={el.id}></div>
            <h2>{el.title}</h2>
            <p>{el.content}</p>
            </div>
          ))
        }
     
    </div>
  );
}


```