## 1. Truthiness:

Sometimes we need to distinguish undefined, null, falsy, and truthy values for different treatment. Jest also provides corresponding matches like:

• *`toBeNull`* compares to null.

• *`toBeUndefined`* compares to the value undefined.

• *`toBeDefined`* is the function that returns toBeUndefined.

• *`toBeTruthy`* compares to true.

• *`toBeFalsy`* compares to false.

For example:

test('null', () => {
const n = null;
```
expect(n).toBeNull();
expect(n).toBeDefined();
expect(n).not.toBeUndefined();
expect(n).not.toBeTruthy();
expect(n).toBeFalsy();
});

test('zero', () => {
const z = 0;
expect(z).not.toBeNull();
expect(z).toBeDefined();
expect(z).not.toBeUndefined();
expect(z).not.toBeTruthy();
expect(z).toBeFalsy();
});
```

## 2. Equality:

`toBe()` uses === `(Object.is)` comparison to compare and output the result.
And to check if the fields of an object or an array are the same, we use toEqual() instead of toBe().

```
test('object assignment', () => {
const data = {one: 1};
data['two'] = 2;
expect(data).toEqual({one: 1, two: 2});
});
```

## 3. Numbers:

|toBeGreaterThan()|greater than|
| :-: | :-: |
|toBeGreaterThanOrEqual()|greater than or equal to|
|toBeLessThan()|less than|
|toBeLessThanOrEqual()|less than or equal|

For example:
```
test('two plus two', () => {*
const value = 2 + 2;*
expect(value).toBeGreaterThan(3);*
expect(value).toBeGreaterThanOrEqual(3.5);*
expect(value).toBeLessThan(5);*
expect(value).toBeLessThanOrEqual(4.5);
// toBe and toEqual are equivalent for numbers
expect(value).toBe(4);
expect(value).toEqual(4);
});
```

## 3. String:
You can check strings against regular expressions with `toMatch()`:
```
test('there is no I in team', () => {
expect('team').not.toMatch(/I/);
});
test('but there is a "stop" in Christoph', () => {
`  `*expect('Christoph').toMatch(/stop/);
});
```

## 4. Array:
To check the value of an array, you can use `toContain()`.
```
const shoppingList = [
'diapers',
'kleenex',
'trash bags',
'paper towels',
'milk',
];

test('the shopping list has milk on it', () => {
expect(shoppingList).toContain('milk');
expect(new Set(shoppingList)).toContain('milk');
});
```


## 5. Exception:

To check if a particular function throws an error when it is called, use `toThrow()`.
```
function compileAndroidCode() {
throw new Error('you are using the wrong JDK');
}
test('compiling android goes as expected', () => {
expect(() => compileAndroidCode()).toThrow();
expect(() => compileAndroidCode()).toThrow(Error);
// You can also use the exact error message or a regexp
expect(() => compileAndroidCode()).toThrow('you are using the wrong JDK');
expect(() => compileAndroidCode()).toThrow(/JDK/);*
});
```
