## What is this thing? Why do I care?

---

Have you ever gotten elbow deep into a codebase...

...and _not_ regretted it?

---

## ☠ accidental¹ complexity ☠

- Costs time
- Costs features
- Costs sanity

Footnote : ¹ as opposed to essential complexity

+++

It's hard to avoid.

Almost inevitable in large projects.

+++

We can buckle down, use grit and discipline to fight against it.

+++

But how often do we win when we go against human nature?

+++

Elm steers us away from the quick fixes, asks us to think about the
repercussions of the code we write.

---




+++

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

Programmers using functional languages get paid more, regardless of experience level

https://discourse.elm-lang.org/t/elm-feedback-in-the-state-of-javascript-2018/2560/10?u=rkb

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

---

## What's wrong with C-style languages?

+++

They're flexible and powerful.

Who doesn't want a flexible and powerful language?

+++

## 👣 🔫

+++

_Too_ flexible.

_Too_ powerful.

+++

```c#
var result = Rooms.GetBoardingAllocations(people, allocations);
```

@[1](Does it mutate its arguments?)

@[1](Does it mutate _something else_?)

@[1](Does it call external services?)

@[1](What happens if it's called twice? Or more?)

@[1](How does it handle null or default properties?)

@[1](Does it throw exceptions?)

@[1](__Does it only "Get"?__)

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

## Make impossible states impossible


---

## What does it look like?

Not like Haskell! You won't see arcane runes that are painful to search for

---
