##### Formik 튜토리얼 정리용 페이지

회원가입 또는 email등 사용자로부터 데이터를 받을때 정확한 데이터를 받는 것이 중요하다.
그래서, 이러한 기능을 한군대 모아 사용하기 편리하도록 만든 라이브러리(?)가 Formik이다.

이 튜토리얼에서는 webPage에서 작업하는것이 아닌, 개인환경(Local)에서 작업한다.

##1. 작업환경 셋팅

(1). 
```
//기본적인 셋팅
npx create-react-app my-app

//npm을 이용한 Formik 설치
npm i formik --save

//yarn을 이용한 Formik 설치
yarn add formik --save
```

1. 설치후 root/src/[src내에 담겨있는 모든 파일 삭제].
2. src폴더내에 두개의 파일을 생성.
2-1. styles.css, index.js
2-2. 
```
//styles.css
https://codesandbox.io/s/formik-v2-tutorial-start-s04yr?file=/src/styles.css:0-13160

//index.js
import React from "react";
import ReactDOM from "react-dom";
import { useFormik } from "formik";
import "./styles.css";

const SignupForm = () => {
  const formik = useFormik({
    initialValues: { email: "" },
    onSubmit: values => {
      alert(JSON.stringify(values, null, 2));
    }
  });
  return (
    <form onSubmit={formik.handleSubmit}>
      <label htmlFor="email">Email Address</label>
      <input
        id="email"
        name="email"
        type="email"
        onChange={formik.handleChange}
        value={formik.values.email}
      />
      <button type="submit">Submit</button>
    </form>
  );
};

function App() {
  return <SignupForm />;
}

const rootElement = document.getElementById("root");
ReactDOM.render(<App />, rootElement);

```

