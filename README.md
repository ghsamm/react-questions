# react-questions

A list of React questions, and their explanations. Inspired by lydiahallie/javascript-questions

---

###### 1. What's the output?

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
