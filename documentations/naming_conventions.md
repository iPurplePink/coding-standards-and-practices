# Naming Conventions

Are general rules applied when creating text scripts for software programming. They have many different purposes, such as adding clarity and uniformity to scripts, readability for third-party applications, and functionality in certain languages and applications. They range from capitalization and punctuation to adding symbols and identifiers to signify certain functions.

# Types of Naming Conventions

### 1. Pascal Case

is the practice of writing compound words or phrases such that each word or abbreviation in the middle of the phrase begins with a capital letter, with no intervening spaces or punctuation.

### 2. Camel Case

is the practice of writing compound words or phrases such that each word or abbreviation in the middle of the phrase begins with a capital letter except the initial, with no intervening spaces or punctuation.

### 3. Kebab Case

is a type of naming style where a word is separated by a hypen(-) and in a lower (kebab) case or upper (kebab) case.

### 3. Snake Case

is the practice of writing compound words or phrases in which the elements are separated with one underscore character (\_) and no spaces, with each element's initial letter usually lowercased within the compound and the first letter either upper- or lowercase—as in "foo_bar" and "Hello_world".

## Examples:

| Types       |                  Sample                   |
| ----------- | :---------------------------------------: |
| Pascal Case | ProfileComponent or ProfileComponentProps |
| Camel Case  |             handleNameChange              |
| Kebab Case  |     profile-section or CREATE-PROFILE     |
| Snake Case  |            user_id or USER_ID             |

Never mix two types of naming style in naming any variables, classnames, ids, components, folder, and files. It will create confusion in other developers.

# Naming Standards

In order for naming to be more understandable we recommend it to be more descriptive and to prevent confusion with other developers we created a standard for naming.

### For ReactComponent, Interface, Type and Enum:

It is in **PascalCase**

```ts
const Profile: FC = () => {};

interface ProfileProps {}
type Photo = ArrayBuffer | string;
enum Step {}
```

### For Variables and Custom Methods:

It is in **camelCase**.

```js
const cities = ["Manila", "Tokyo", "Denver", "Rio"];
const handleChangeFirstName = () => {};
```

### For Constant and Important Variables:

- it is in **UPPER_SNAKE_CASE**.

```js
const PI = "3.14";
const HOME_PAGE_TITLE = "Home | React App";
const { ID } = useAppContext();
```

### For ClassNames and Ids:

It is in **lower-kebab-case**.

```js
className = "delete-button";
Id = "test-save-button";
```

Note: Except for ids that is being use for robot. ex. id="robot-btn-submit"

### For Folders and Files in component and modules:

- it is the same for variables but the **pascal case in every words is capitalize** except the index files (index.ts, index.tsx, etc.).

#### `Folder: Layout, Files: Header.jsx`
