## 1. Repeating Setup For Many Tests:
**`beforeEach +  afterEach`**: 
>If you need to do iteratively for multiple checks. It can handle asynchronous code in the same way that tests can handle asynchronous code
```
beforeEach(() => {
  initializeCityDatabase();
});

afterEach(() => {
  clearCityDatabase();
});

test('city database has Vienna', () => {
  expect(isCity('Vienna')).toBeTruthy();
});

test('city database has San Juan', () => {
  expect(isCity('San Juan')).toBeTruthy();
});
```

## 2. One time setup:
**`beforeAll +  afterAll`**: 
>When you only need to set it up once and it's at the beginning of the file or at the end of the file. The settings can be out of sync, so you can't do it inline.

## 3. Scoping:
>You can also group test cases together using a description block. Internally, the before and after block are applied to the tests in that described block.
```
describe('matching cities to foods', () => {
  // Applies only to tests in this describe block
  beforeEach(() => {
    return initializeFoodDatabase();
  });

  test('Vienna <3 sausage', () => {
    expect(isValidCityFoodPair('Vienna', 'Wiener Schnitzel')).toBe(true);
  });

  test('San Juan <3 plantains', () => {
    expect(isValidCityFoodPair('San Juan', 'Mofongo')).toBe(true);
  });
});
```

__Note:__ top-level beforeEach will be executed before beforeEach inside description block. It can help illustrate the execution order of all the hooks.
```
beforeAll(() => console.log('1 - beforeAll'));
afterAll(() => console.log('1 - afterAll'));
beforeEach(() => console.log('1 - beforeEach'));
afterEach(() => console.log('1 - afterEach'));
test('', () => console.log('1 - test'));
describe('Scoped / Nested block', () => {
  beforeAll(() => console.log('2 - beforeAll'));
  afterAll(() => console.log('2 - afterAll'));
  beforeEach(() => console.log('2 - beforeEach'));
  afterEach(() => console.log('2 - afterEach'));
  test('', () => console.log('2 - test'));
});

// 1 - beforeAll
// 1 - beforeEach
// 1 - test
// 1 - afterEach
// 2 - beforeAll
// 1 - beforeEach
// 2 - beforeEach
// 2 - test
// 2 - afterEach
// 1 - afterEach
// 2 - afterAll
// 1 - afterAll
```

*Reference source:  [Setup and Teardown - Jest.io](https://jestjs.io/docs/setup-teardown)*
