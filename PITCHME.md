## What is this thing? Why do I care?

+++

## ☠ complexity ☠

Note:

Where OO

Not like Haskell! You won't see arcane runes that are painful to search for

---

## no $Digest cycle

---

## What's wrong with C-style languages?

+++

They're flexible and powerful.

Who doesn't want a flexible and powerful language?

+++

_Too_ flexible.

_Too_ powerful.

+++

```c#
var result = Rooms.GetBoardingAllocations(people, allocations);
```

Does it mutate its arguments?

Does it mutate _something else_?

Does it call external services?

What happens if it's called twice? Or more?

How does it handle null or default properties?

Does it throw exceptions?

__Does it only "Get"?__

+++

## We can't tell from here.

Except by reading __and understanding__ the code, including everything it calls.

+++

## So what, that's just how it is.

It doesn't have to be!

---

## What about Typescript?

+++

TypeScript is great, and makes JavaScript bearable.

But, it doesn't protect anything at runtime.

+++

```typescript
interface Person {
    name: String
    age: Number
} 

function fetchPeople(): Promise<Person[]> {
    // ... call to external service ...
}

const peeps = await fetchPeople();
```

@[7](Has the external service changed what it returns?)

Note:

(TypeScript 3 introduces the `unknown` type which _can_ alleviate the runtime thing, but 
only if everyone remembers to use it and makes the effort to!)


+++

## ☣ type casting ☣

```typescript
function fetchPerson(id: number): Person | null {
    // ... call to external service ...
}

// This call will always produce the result I expect
const duder = fetchPeople(42) as Person;

send
console.log(`Dude's name is ${duder.name}`)


function doSomethingThatNeedsAPerson(p: Person): void {
    // ... explode with byzantine error ...
    // ... maybe straight away, maybe later ...
}
```

@[5-6](O RLY?)

---

## Do we...

start with the View and work downwards

-or-

start with the Model and work upwards

---?code=src/sample1.elm&lang=elm

@[8](These are __the__ only things that can change our Model)

@[10-17](Here's __exactly__ what happens when we get one of those messages)

+++

## It seems a little verbose?

Yes! Elm steers away from \[implicit|magic\], towards \[explicit|obvious\]

In an unfamiliar codebase, this is helpful!

---

## Making impossible states impossible

---

Code quality is almost automatic in Elm

(elm-format)

---

Packages are encouraged to have useful names

---

JS encourages many modules

Elm suggests there should be one great package that solves the problems

---

Babel • Webpack • TypeScript • Redux • ...


You don't need half a dozen different tools to write Elm

---

Elm encourages us to think up-front about the design

---

Things don't get forgotten

_I'll implement this later_ (i.e., never)

---

You have to really go out of your way to write underhanded tricks

It's a pleasure to read Elm code

---

Tree shaking?

Dead code elimination.

---

Upcoming targets like WebAssembly will be free

---

Entire classes of bugs just don't exist in Elm

---

## Future proof

New hires can get up to speed rapidly, and start fearlessly modifying the code

Compare AngularJS / React / Knockout ― much higher WTFs/minute rate

---

Much harder to inadvertently break non-local code
(especially if you make impossible states impossible)

---

## It's fast

+++

### Fast compiler

+++ 

### Fast code

+++ 

### Fast delivery
(small assets)

+++

### Fast refactoring

+++

### Fast testing

- you don't need so many tests

- you don't have to mock a bazillion things

