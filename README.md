# react-questions

A list of React questions, and their explanations. Inspired by lydiahallie/javascript-questions

---

##### 1. What's the output?

```javascript
function siteHeader() {
  return <h1>Welcome</h1>;
}

ReactDOM.render(<siteHeader />, document.querySelector("#root"));
```

- A: Nothing
- B: `<h1>Welcome</h1>`
- C: Error

<details><summary><b>Answer</b></summary>
<p>

#### Answer: B

The name of our component `siteHeader` is camelCase.
React will treat it as regular HTML tag and ignore our component/function.

If you inspect the output, you'll see that what React actually rendered is the following:

```html
<siteheader></siteheader>
```

The convention is to always to use `UpperCamelCase` instead of `camelCase`. Basically, keep the first letter uppercase.
Only then would react detect we're using our own custom component and not an HTML tag.

</p>
</details>

---

##### 2. What's the output?

```javascript
ReactDOM.render(
  <img src="image.jpg">,
  document.querySelector("#root")
);
```

- A: Nothing
- B: Error
- C: `<img src="image.jpg>`

<details><summary><b>Answer</b></summary>
<p>

#### Answer: B

In HTML, we can have _self-closing_ tags, `img` and `br` are two popular examples.

In React however, all tag (or component) calls must be closed.

The following would have worked (notice the `/` at the end of the self-closing tag)

```html
<img src="image.jpg" />
```

</p>
</details>

---

##### 3. What's the output?

```javascript

const Header = () => {
  return (
    <h1>Welcome</h1>
    <p>to the jungle</p>
  )
}

ReactDOM.render(
  <Header />,
  document.querySelector("#root")
);
```

- A: Nothing
- B: `<h1>Welcome</h1><p>to the jungle</p>`
- C: Error

<details><summary><b>Answer</b></summary>
<p>

#### Answer: C

All react components must return a single element, in this case we returned two!

What we can do instead is wrap the elments inside another enclosing element, like so:

```javascript
const Header = () => {
  return (
    <div>
      <h1>Welcome</h1>
      <p>to the jungle</p>
    </div>
  );
};
```

</p>
</details>

---

##### 4. What's the output?

```javascript
const Header = () => {
  return (
    <>
      <h1>Welcome</h1>
      <p>to the jungle</p>
    </>
  );
};

ReactDOM.render(<Header />, document.querySelector("#root"));
```

- A: WTH!
- B: Error
- C: Noting
- D: `<h1>Welcome</h1><p>to the jungle</p>`

<details><summary><b>Answer</b></summary>
<p>

#### Answer: D

Instead of wrapping the elements inside an element, we have some other alternatives:

1. Return an array of element, be careful about the `,` between elements

```javascript
return [<h1>Welcome</h1>, <p>to the jungle</p>];
```

2. Use `React.Fragment`. The difference from using other elements is when this component gets translated to HTML later on, the `h1` and `p` elements won't be wrapped at all. Feel free to inspect and see for yourself!

```javascript
return (
  <React.Fragment>
    <h1>Welcome</h1>
    <p>to the jungle</p>
  </React.Fragment>
);
```

3. Use the shorthand syntax for `React.Fragment`. `<>` and `</>` are actually synonyms of `<React.Fragment>` and `</React.Fragment>` respectively. Neat trick, right?

</p>
</details>

---

##### 5. What's the output?

```javascript
const Header = () => {
  return <hEADER>Welcome</hEADER>;
};

ReactDOM.render(<Header />, document.querySelector("#root"));
```

- A: `<header>Welcome</header>`
- B: Error
- C: Noting

<details><summary><b>Answer</b></summary>
<p>

#### Answer: A

You might think this will be an infite recursive call, where `Header` calls itself an infinite number of times until the program crashes. You'd be wrong!

Since the first letter in `hEADER` is lowercase, it will be considered as an HTML tag. And btw, HTML tags are case-insensetive.

</p>
</details>

---

##### 6. What's the output?

```javascript
class Course {
  render() {
    return <div>Course content</div>;
  }
}

ReactDOM.render(<Course />, document.querySelector("#root"));
```

- A: Nothing
- B: `<div>Course content</div>`
- C: Error

<details><summary><b>Answer</b></summary>
<p>

#### Answer: C

All class components in React must inherit from the base class `React.Component`.

We can change the first line to the following:

```javascript
  class Course extends React.Component {
```

</p>
</details>
