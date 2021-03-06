#### ORM-MVC

#### Part1 
1. sequelize를 사용하기 위해선 패키지를 설치해야 합니다.

```
설치방법
npm install --save sequelize mysql2 //mysql과 시퀄라이즈를 이어주는 드라이버 개념입니다.
npm install --save-dev sequelize-cli //시퀄라이즈 명령어를 실행하기 위한 패키지 입니다.

npx sequelize-cli init // 프로젝트 초기단계를 자동으로 설정 해줍니다. 
```
#### 2. sequelize 사용법
npx sequelize-cli init을 입력하면 config, migrations,models,seeders 폴더가 생긴다.

1.Config 설정하기
/config/config.json 파일을 보면 delvelopment, test, production 세 개의 목록 이있는데 말 그대로 개발환경, 테스트목적, Production(운영환경) 으로 나누어 지는데 자기가 사용할 필드의 SQL 환경에 따라 수정하면 됩니다. 

2.모델 정의하기
모델은 SQL 테이블에 대응하는 개념입니다. 시퀄라이즈는 모델과 SQL 의 테이블을 연결시켜주는 역할을 합니다.
시퀄라이즈로 모델을 정의하는 방법
```
npx sequelize-cli model:generate --name User --attributes firstName:string,lastName:string,email:string

```
이 명령어를 사용하게 되면 파일명이 User이며 , firstName(String타입),lastName(String타입),email(String타입) 을 필드로 가진 테이블이 생성을 할 수 있습니다.

3.migration(마이그레이션)
모델 정의하기가 끝났다면 정의한 모델에 따라 실제 테이블을 제작하는 단계가 필요합니다.
이 단계를 migration이라고 합니다. 
```
npx sequelize-cli db:migrate //끝!
```

4.초기값 설정
이미 만들어진 models 폴더에 url.js가 시퀄라이즈 명령어로 통해 만들어져있습니다.
visits에 초기값을 지정을 해줘야 하므로 
```
url.init({
    url: DataTypes.STRING,
    title: DataTypes.STRING,
    visits: {
     type: DataTypes.INTEGER,
     defaultValue : 0
    }
  }, 
```
type : , defaultValue : 0 을 써주면 초기값이 설정이 되어집니다. 

5.Controller 만들기
Get, Post, get/:id 로 해당하는 요청에 대한 응답 콘트롤러를 지정을하고 로직을 작성해야합니다.

밑에 코드는 해당요청에 대한 정답코드입니다.
```
const models = require('../../models/index');
const {getUrlTitle} = require('../../modules/utils');
module.exports = {
    get: async (req, res)=>{
        const urls = await models.url.findAll()
        res.status(200).json(urls)
    },
    getId: async(req, res)=>{
        const id = req.params.id;
        const urlPk = await models.url.findByPk(id);
        await urlPk.increment('visits',{by:1})
        res.redirect(302, urlPk.url)
    },
    post:(req, res)=>{
        const url = req.body.url;
        getUrlTitle(url, async(err, title)=>{
        const makeUrl = await models.url.create({
            url,
            title
        });
        res.status(201).json(makeUrl)
        })
    }
}
```
6.router 연결 
controller를 만들어 주었으니 이제 라우터를 연결을 해서 
작동이 잘 되게 연결을 해주면 끝!
```
const express = require('express');
const router = express.Router();

const controller = require('../controllers/links/index')

/* post link */
router.post('/', controller.post);

// get link
router.get('/', controller.get);

// get link /:id
router.get('/:id', controller.getId);


module.exports = router;
```


