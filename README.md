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
    
