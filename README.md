# [<img src="https://cdn.rawgit.com/lennonjesus/jasmine2-cheatsheet/master/images/jasmine-cheatsheet-logo.svg" width="400px" />](http://jasmine.github.io)


```javascript
describe("Jasmine Cheatsheet", function() {
  it("is your Swiss Army knife!", function() {
    expect(helpYou).toUseJasmineLikeAPro();
  });

  describe("Credits", function () {
    it("is based on the Official Jasmine Documentation", function () {
      expected("[http://jasmine.github.io/edge/introduction.html](http://jasmine.github.io/edge/introduction.html)").shouldBeVisited();
    });
  });

  describe("Contribution", function () {
    it("is free to fork and contribute", function () {
      expected(forks).and.pullRequests();
    });
  });

  afterAll(function() {
    var author = "Lennon Jesus";
  });
});
```

##### Current Jasmine version:
[![npm version](https://badge.fury.io/js/jasmine.svg)](http://badge.fury.io/js/jasmine)

### Basic Structure

```javascript
describe("A basic Jasmine structure", function() {

  var trueValue = false;

  beforeEach(function() {
    // initialization code...
    // mocks...
    // spies...

    trueValue = true;
  });

  it("should be true", function() {
      expect(trueValue).toBe(true);
  });

  afterEach(function() {
    // tear down...
    // good bye...
    // finish him...
    trueValue = false;
  });
});
```

### Spies how to...

**...create a spy**

```javascript
spyOn(obj, 'method');

jasmine.createSpy('optional name');

jasmine.createSpyObj('name', ['fnct1', 'fnct2', ..., 'fnctN']);
```

**...modify the behavior of a spy**

```javascript
spyOn(obj, 'method').returnValue(val); // all calls to the function will return a specific value

spyOn(obj, 'method').returnValues(val1, val2); // all calls to the function will return specific values in order until it reaches the end of the return values list, at which point it will return undefined for all subsequent calls

spyOn(obj, 'method').callFake(fn); //all calls to the spy will delegate to the supplied function

spyOn(obj, 'method').callThrough(); // it will delegate to the actual implementation

spyOn(obj, 'method').throwError(err); //all calls to the spy will throw the specified value as an error

spyOn(obj, 'method').stub(); // the original stubbing behavior can be returned at any time with and.stub
```

**...verify interactions**

```javascript
obj.method.calls.count(); //returns the number of times the spy was called

obj.method.calls.any(); //returns false if the spy has not been called at all, and then true once at least one call happens

obj.method.calls.reset(); // clears all tracking for a spy
```

**...inspect calls**

```javascript
obj.method.calls.first(); // returns the context (the this) and arguments for the first call

obj.method.calls.mostRecent();

obj.method.calls.all();
```


**...call description object**

```javascript
{
  object: {...},  // 'this' object
  args: []        // the arguments
}
```

### Matchers

**toBe**

```javascript
expect(obj).toBe(null);M
```

**toEqual**

```javascript
expect(obj).toEqual({id: 7});
```

**toMatch**

```javascript
expect(msg).toMatch(/abc/);
```

**toBeDefined**

```javascript
expect(obj).toBeDefined();
```

**toBeUndefined**

```javascript
expect(obj).toBeUndefined();
```

**toBeTruthy**

```javascript
expect('a').toBeTruthy();
```

**toBeFalsy**

```javascript
expect(obj).toBeFalsy();
```

**toContain**

```javascript
expect(arr).toContain();
```

**toBeLessThan**

```javascript
expect(21).toBeLessThan(42);
```

**toBeGreaterThan**

```javascript
expect(42).toBeGreaterThan(21);
```

**toBeCloseTo**

```javascript
expect(1.2).toBeCloseTo(1.23, 1);
```

**toThrow**

```javascript
expect(fnct).toThrow();
```

**toThrowError**

```javascript
expect(obj).toThrowError();
```

**toBeNull**

```javascript
expect(obj).toBeNull();
```
