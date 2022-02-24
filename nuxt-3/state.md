## State

- [useState](#useSate)

---

### useSate

`useState` is a native Vue `ref` upgrade and is SSR friendly. The returned value is a reactive `ref`:

```js
const counter = useState("key", initialValue);
```

#### Composables and global state

We can create `/composables/states.js` to make shared data easily available throughout an application.

`/composables/states.js`:

```js
export const useCounter = () => useState < number > ("counter", () => 0);
export const useColor = () => useState < string > ("color", () => "pink");
```

Then easily access them within components (within the `setup` script tags):

```ts
const color = useColor(); // Same as useState('color')
```
