# Getting Started With Naming

One of the important things in starting to create a React Component, is knowing how to name anything that complies to our agreed standards and best practices.

### 1. Naming Folders and Files Containing React Code

Example: create a folder `Register` and inside create a file `index.tsx` in the directory `src/modules/`

```
|- src
|   |- modules
|   |   |- Register
|   |   |   |- index.tsx
```

Note:

- Use PascalCase in naming folders and files containing a React component. Except for `index.tsx`

```js
// Example:

Home.tsx;
Layout.tsx;
```

### 2. Naming React Functional Component

```js
import React, { FC } from "react";

const Register: FC = () => {
  return (
    <section className="register-section">
      <h1 className="register-title">Register</h1>
      <div className="register-form-container">
        <input className="input email" placeholder="Email" />
        <input className="input password" placeholder="Password" />
        <button className="signup-button">Sign up</button>
      </div>
    </section>
  );
};

export default Register;
```

Note:

- Naming functional component should be in PascalCase
- Define the react component as Functional Component or FC

```js
import React, { FC } from 'react';

const Register: FC = () => {
```

- Name the react elements using className
- ClassName should be in lower-kebab-case

```js
<section className="register-section">
  <h1 className="register-title">Register</h1>
  <div className="register-form-container">
    <input className="input name" placeholder="Name" />
    <input className="input email" placeholder="Email" />
    <input className="input password" placeholder="Password" />
    <button className="signup-button">Sign up</button>
  </div>
</section>
```

### 3. Naming Event Handlers

```js
const handleNameChange = () => {};
const handleEmailChange = () => {};
const handlePasswordChange = () => {};
const handleSignupClick = () => {};

return (
  <section className="register-section">
    <h1 className="register-title">Register</h1>
    <div className="register-form">
      <input
        className="input name"
        placeholder="Name"
        onChange={handleNameChange}
      />
      <input
        className="input email"
        placeholder="Email"
        onChange={handleEmailChange}
      />
      <input
        className="input password"
        placeholder="Password"
        onChange={handlePasswordChange}
      />
      <button className="signup-button" onClick={handleSignupClick}>
        Sign up
      </button>
    </div>
  </section>
);
```

Note:

- Prefix `on` is describing what actual event this will be tied to
- Prefix `handle` is describing what will be called when that event fires
- Follow the pattern below:

```js
<RegisterForm onSubjectEvent={handleSubjectEvent} />
```

### 4. Naming Variables and States

```js
const [name, setName] = useState("");
const [email, setEmail] = useState("");
const [password, setPassword] = useState("");

const isSignupDisabled = !name || !email || !password;
```

Note:

- Naming variable should be descriptive
- Naming variable should not be general, specify the name as much as possible
- Boolean variable should have prefix `is`, `has`, `have` or `should` ex:

```js
const isSignupDisabled = !name || !email || !password;
const hasName = !isEmpty(name); // using lodash/isEmpty
const isPhotoCropperVisible = true;
```

- Variable storing collections like array should be in plural term ex:

```ts
const countries = ["Philippines", "Singapore", "Thailand", "Indonesia"];
```

- Using abbreviation or short terminologies is not being fully descriptive ex:

```js
const handlePrevClick = () => {}; // bad
const handlePreviousClick = () => {}; // good

const isETValid = false; // bad
const isEstimatedTimeValid = true; // good
```

- Make sure the variables and states are in correct spelling

```
Review codes by reading them. If the code is hard to read, then there might be better version to write it.
```

### 5. TypeScript naming Interface, Type and Enums

```ts
// Interface

interface RegisterFormValues {
  email: string;
  name: string;
  password: string;
}

interface RegisterProps {
  onRegisterFormSubmit: (values: RegisterFormValues) => void;
}
```

Note:

- For object modeling, using Interface is more powerful than Type
- Interface name is written in PascalCase

```ts
// Type

type Photo = ArrayBuffer | string | null;

interface PhotoCropperProps {
  onPhotoSave: (croppedPhoto: Photo) => void;
  photo?: Photo;
}
```

Note:

- Use Type aliases to create a new name for a type. This will keep your type maintainable and simplified
- Type name is written in PascalCase
- Do not use Type for object modeling, use Interface instead

```ts
// Enums

enum Step {
  PersonalInformation = 1,
  Addresses = 2,
  Hobbies = 3,
}

const [step, setStep] = useState<Step>(1);

setStep(Step.PersonalInformation);
```

Note:

- Enums allow us to define a set of named constants
- Using enums can make it easier to document intent, or create a set of distinct cases.
- Enum name is written in PascalCase
- If Enum able to work on it, therefore avoid using object

### 6. Naming Graphql Query and Mutation

```js
// GraphQL Tag

const SIGNUP = gql`
  mutation SignUp($name: String!, $email: String!, $password: String!) {
    signUp(name: $name, email: $email, password: $password) {
      name
      email
      password
    }
  }
`;

const GET_USER = gql`
  query GetUser($email: String!) {
    user(email: $email) {
      email
      name
      password
    }
  }
`;
```

Note:

- `SIGNUP` and `GET_USER` is written in UPPER_SNAKE_CASE. It is storing an important constant graphql tag.
- `SignUp` and `GetUser` is written in PascalCase. It is an alias for the mutation and query.

```js
// Apollo Client Hooks

interface SignUpVars {
  email: string;
  name: string;
  password: string;
}

const [signUp, { loading, error, data }] = useMutation<SignUpVars>(SIGNUP, {
  onCompleted: data => {},
  onError: error => {},
  update(cache, { data: { signUp } }) {}
});

interface UserVars {
  email: string;
}

interface UserData {
  email: string;
  name: string;
  password: string;
}

const { data, loading, error } = useQuery<UserData, UserVars>(GET_USER, {
  variables: { email: EMAIL }
});
```

Note:

- `useMutation` should be declare above the `useQuery` to avoid reaching maximum count of hooks rendered
- Variable `data` or any variable with `Data` suffix should only be define and use for useMutation and useQuery `results`. At first glace, all variables with word data is known to be from useMutation and useQuery.
- Using `update` in `option` of `useMuatation` is a must, to avoid refetching that caused to another network request
- Renaming `useMutation` and `useQuery` `results` should follow descriptive naming ex:

```js
// useQuery
const { data: userData, loading: isUserLoading, error: userError } = useQuery();
// useMutation
const [signup, { loading: isSigningUp, error: signUpError, data: signUpData }] =
  useMutation();
```
