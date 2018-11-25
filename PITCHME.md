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

