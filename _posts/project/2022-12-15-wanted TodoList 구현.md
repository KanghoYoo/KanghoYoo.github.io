---
title: wanted TodoList 구현 사전 과제 후기
date: 2022-12-15 +/-TTTT
categories: [Project, Toy Project - wanted Project]
tags: [project, toy-project] # TAG names should always be lowercase
---

# 🖥️ wanted TodoList 구현 사전 과제 후기

## `✏️ 이런 저런 이야기`

취업 준비를 하다가 원티드 프리온보딩 프론트엔드 인턴십 프로그램에 대해 알게 되어 지원을 하고자 사전과제를 만들기 시작하였다. 12월 12일날 알게되었는데 알고보니 신청 마감날짜가 15일 목요일이였다. 시간이 얼마 남지 않았다고 생각했던 나는 컴포넌트를 나눌 생각도 없이 우선 생각나는 대로 코드를 구성하고 리팩토링을 하자라고 생각하여 급하게 만들어 나갔다. 만약 개발 기간이 늦어 참가하지 못한다고 하여도 내가 만들었던 프로젝트를 토대로 배울 점도 있고 하면서 에러 대응 능력또한 향상할 수 있을 것이라고 생각하였다. 



### 라이브러리

라이브러리는  `typescript,axios,fontawesome,styled-components,git-pages,npm,npx create-react-app,react-router-dom` 을 사용하였다. 평소 자주쓰던 자바스크립트가 아닌 한번 사용한 경험이 있는 타입스크립트로 개발하려는 이유는 자바스크립트와 달리 내가 모르고 있던 기능들도 있을 것이고, 응용 또한 능숙하지 않기 때문에 학습을 통해 정적 언어인 타입스크립트로 작성을 하고 싶었기때문이다.



### 로그인 컴포넌트 / 회원가입 컴포넌트 기능 (`/`)

로그인과 회원가입 기능을 구현을 하기전에 페이지 이동을 하지 않고 같은 컴포넌트로 두 기능 모두를 구현하고 싶었기 때문에 하나의 컴포넌트에서 회원가입과 로그인 기능 두가지를 처리할 수 있게 하였다. 로그인페이지는 간단하게 아이디와 비밀번호 입력칸, 로그인버튼과 회원가입버튼으로 구성하였다.

로그인과 회원가입에서 아이디 `input`에 입력을 하면 로그인 버튼 상단에 이메일을 검증하여 상태를 알려준다. 비밀번호 `input`도 마찬가지로 동작한다.

로그인 버튼은 위에 `input` 아이디가 "@"을 포함한 이메일형식이고 `input` 비밀번호가 8자이상일때, 활성화가 되게 만들었다. 로그인 버튼을 클릭하면 `window.alert()` 함수를 통하여 상태를 알려준다. 회원가입이 되어있는 상태라면 `useNavigate`를 통해 `(/todo)`페이지로 이동한다. 회원가입이 안되어 있거나 아이디나 비밀번호가 틀린 경우라면 로그인창 그대로 있고 "다시 확인해주세요."라는 문구를 띄어주었다.

기존 컴포넌트를 재사용하기 때문에 회원가입버튼을 클릭하면 상단에 "Login"텍스트가 "SignUp"이라는 텍스트로 바뀌고 "로그인" 버튼과 "회원가입" 버튼이 "가입하기" 버튼, "로그인화면으로 돌아가기" 버튼으로 텍스트와 함수기능을 다르게 하였다. 

로그인과 회원가입에 필요한 텍스트와 불린값들을 저장하기 위해 객체를 각각 선언하여 안에 있는 프로퍼티들은 동일하게 만들었다. 그후 조건부 렌더링을 통해 기능과 텍스트를 다르게 만든 것이다.



### Todo 컴포넌트 기능 (`/todo`)

로그인에 성공하면 `/todo`페이지로 이동하게 된다. 토큰이 없다면 `/todo`페이지를 직접 이동해도 다시 `/`로 이동하게된다.

우측 상단 로그아웃 버튼을 클릭하면 localstorage에 있는 토큰을 제거하여 로그인 화면으로 돌아가게 하였다.

Todo 에 필요한 기능들은 할일 추가기능(`input`,`button`), 체크기능(`input-checkbox`), 수정기능(`button`, `input`), 삭제기능(`button`)이 기본적으로 있어야한다.

서버로부터 데이터를 받아오기 때문에 axios의 get을 사용하여 useEffect로 감싸 데이터를 표시하게 하였다.

추가 버튼을 누르면 `input`의 값을 post를 통해 서버에 데이터를 생성하고 get을 통해 데이터를 다시 받아와 추가된 할일을 볼 수 있다.

수정 버튼을 누르면 텍스트가 텍스트를 입력할 수 있는`input`으로 변환되고 버튼들도 ["수정", "삭제"]가 아닌 ["확인", "취소"]로 텍스트와 기능이 바뀌게 된다. `input`에 원하는 텍스트를 입력하고 확인 버튼을 누르면 서버에 put요청을 하여 서버에 저장되어있는 텍스트가 업데이트되어 다시 get으로 반환한다. 취소버튼을 누르면 기존에 저장되었던 텍스트로 돌아가게된다.

체크박스를 클릭하면 수정버튼을 누르면 나오는 확인버튼과 동일하게 작동을 한다. 다만 checked 상태를 업데이트를 한다.

overflow 속성을 통해 TodoList 박스안에서 스크롤이 되도록 구현을 하였다.



### 폴더와 컴포넌트 구성

`page` 폴더에 `login`폴더와 `todo`폴더를 만들었고 `login` 폴더안에는 css을 저장하는 `LoginStyles`와 인터페이스와 타입을 저장하기 위한 `LoginInterface`, login화면을 구성하는 `Login`컴포넌트, login에 대한 API로 구성되어 있는 `LoginAPI`로 파일을 구성하였다. `todo`폴더에도 마찬가지로 비슷하게 구성하였다.



### 코드 구현을 하면서 접했던 에러

#### 400 error

서버에 요청을 하면서 `400`에러가 발생하였다. `400`에러는 내가 작성했던 api함수중 요청하는 형식이나 값들이 잘못되었기 때문에 코드를 하나씩 보면서 다시 수정하고 에러를 해결하였다.



#### map is not a function

이 에러는 map에 함수로 전달받았을 때 나오는 에러이다. todo에 아무런 데이터가 없을 때 발생하는 데 이것을 해결하려면 렌더링 화면에서 todos데이터가 존재할 때 map을 실행하게 하면된다. 즉, 논리곱연산자를 통해 map함수를 사용하면된다.

```tsx
 {todos &&
        todos.map((todoItem: TodoType) => (
          <TodoListItem
            todoItem={todoItem}
            onRemove={onRemove}
            onChangeTodo={onChangeTodo}
            onToggle={onToggle}
            key={todoItem.id}
          />
        ))}
```



### 사전과제 후기

사전과제를 하면서 재미있게 코드를 구성하고 생각했던 것 같다. 우선 any를 사용하여 코드를 구현하고 기능이 잘 작동되는 것을 확인하고 파일을 여러개 나누어 가독성과 코드관리를 편하게 하였다. 그다음 type과 interface를 사용하여 재사용되는 타입들을 적용시켰고 any를 사용하는 타입으로 명시적타입선언하여 에러발생률을 줄인 것 같다. 자바스크립트에는 없는 다형성(오버로드)를 사용하여 하나의 함수에 다른 타입의 인수를 넣어 코드를 줄이고 동작하는 코드도 구현을 해보았는데 확실히 타입스크립트의 장점이 더 느껴진 것 같았다. 타입을 적용시키다보니 "타입을 코드 전체를 적용시켜야하는 것일까? 아니면 필요한 부분에만 적용시켜야할까?"라는 궁금점도 생겨 찾아보게 되었다. 

todo 컴포넌트에서 todoItem, todoItemList에 props를 통해 함수를 전달해 주고 state를 관리하기 불편하다는 점을 알았다. 이것이 여러 개 반복되면 관리하기 더욱 어려울 뿐더러 에러 또한 발생할 수 있겠다고 생각했다. 이것이 아마 전역상태관리 라이브러리 contextAPI 또는 redux를 사용하는 이유인것 같았다. 아직은 학습이 부족하다고 판단되어 이해가 될 때 리팩토링을 통해 구현을 해보면 좋을 것같다고 생각하였다. 

3일이란 시간동안 하루종일 코드에 대한 생각만 하게 된 것 같았다. 코드를 어떻게 작성해야 가독성이 좋아보이고 메모리 비용이나 로딩속도를 빠르게할까를 생각하게 되었으며 생각한 만큼은 적용은 하지 못하였지만 어느정도만 진행이 된점이 아쉬웠다.

## `🌃 구현된 화면 및 코드`

https://github.com/KanghoYoo/wanted-pre-onboarding-frontend

위에 링크를 접속하여 구현한 코드와 화면을 볼수 있다.



## `❓ 궁금한 내용이나 잘 이해되지 않는 내용`

- 타입스크립트에서 서버로부터 받은 response의 타입

  - API는 promise로 받기 때문에 Promise로 감싸주고 그 안에 AxiosResponse를 사용한다.

  - 그 안에 정의했던 interface를 가져와 적용한다.

  - ```tsx
    import axios, { AxiosResponse } from "axios";
    interface CovidSummaryResponse {
      Countries: any[];
      // {Country: "Afghanistan", CountryCode: "AF", Slug: "afghanistan", NewConfirmed: 241}
      Date: string;
      Global: any;
      Message: string;
    }
    
    // api axios response 정의
    function fetchCovidSummary(): Promise<AxiosResponse<CovidSummaryResponse>> {
      const url = "https://api.covid19api.com/summary";
    
      return axios.get(url);
    }
    
    // 위 response interface 정의로 타입 추론
    fetchCovidSummary().then(res => res.data.Message);
    ```

  - 출처: https://kyounghwan01.github.io/blog/TS/fundamentals/basic/#union

- Type과 Interface 차이

  - **Type**: 새로운 속성을 추가하기 위해 같은 이름 선언 불가능, 어디든 사용 가능, `&`를 사용하여 확장

  - **Interface**: 항상 선언적 확장이 가능, 객체만 사용가능, 성능에 더 유리, `extends`를 사용하여 확장

  - > 한가지로 통일하여 사용하는 것을 권장(성능과 선언적확장이 가능한 인터페이스 추천, 공식문서에도 인터페이스 권장)

  - ```tsx
    // Interface 선언
    interface PeopleInterface {
      name: string
      age: number
    }
    // 선언적 확장 가능
    interface PeopleInterface {
    	gender: string
    }
    
    // Type 선언
    type PeopleType = {
      name: string
      age: number
    }
    // 선언적 확장 불가능
    // Error: Duplicate identifier 'Window'.
    type PeopleType = {
    	gender: string
    }
    ```

    

- 자바스크립트를 타입스크립트의 Type 을 어디까지 적용시켜야 할까? (범위)
  - 기능적인 변경은 절대 하지 않을 것
  - 테스트 커버리지가 낮을 땐 함부로 타입스크립트를 적용하지 않을 것
  - 처음부터 타입을 엄격하게 적용하지 않을 것 (점진적으로 strict 레벨을 증가)
