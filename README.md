## React Hook Form

### ❓ react-hook-form 특징
- Hooks API!
- 제어되지 않는 컴포넌트 기반으로 작동하여 성능이 우수합니다.
- 다른 라이브러리와 다르게 폼을 위한 컴포넌트나 필드를 위한 컴포넌트가 없습니다. 
- form 태그나 input 태그에 ref 를 사용하여 폼을 구성할 수 있습니다.
- 유효성 검증을 위한 내부 기능이 포함되어 있지만, 필요하다면 yup 을 사용할 수 있습니다.
- 타입스크립트로 작성된 프로젝트라서 타입스크립트와 아주 잘 맞습니다 👍 

## 🙋‍♀️ 설치
```
$ yarn add react-hook-form
```

## 사용법

FormContext 라는 컨텍스트를 제외하면 별도의 컴포넌트가 존재하지 않습니다.
```
import useForm from 'react-hook-form';

const Form = () => {
  const { register, handleSubmit } = useForm();

  const onSubmit = data => {
    console.log(data);
  };
  
  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <input type="text" name="name" ref={register} />
      <input type="submit" />
    </form>
  );
};
```
실제 작동 예제는 <a href="https://github.com/react-hook-form/react-hook-form/tree/master/examples">여기</a>에 많이 있습니다. 
    
## 필드 등록하기

- React Hook Form 의 중요 컨셉 중 하나는 register 를 통해 여러분의 비제어 컴포넌트(uncontrolled component)를 Hook 과 연결하여 값이 검사될 수 있도록 만들고 폼을 제출할 때 한꺼번에 모아지도록 하는 것
- 각각의 필드는 등록 과정의 key 로 사용하기 위해 name 속성이 반드시 필요

```
import React from 'react';
import { useForm } from 'react-hook-form';

export default function App() {
  const { register, handleSubmit } = useForm();
  const onSubmit = (data) => console.log(data);

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <input {...register('firstName', { required: true })} />
      <select {...register('gender', { required: true })}>
        <option value='female'>female</option>
        <option value='male'>male</option>
        <option value='other'>other</option>
      </select>
      <input type='submit' />
    </form>
  );
}

```

## Error 핸들링

버전 6.~ 의 예제코드를 그대로 쓰니 <input name="example" ref={register} /> ref 부분에서 오류가 났다.
해당 부분을 {...register( name부분, { required: true })} 이렇게 고치니 오류가 사라졌다.  
