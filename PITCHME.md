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

They're flexible and powerful, yes.

_Too flexible._

_Too powerful._

+++

```c#
var result = Rooms.GetBoardingAllocations(people, allocations);
```

Does it mutate its arguments?

Does it call external services?

What happens if it's called twice? Or more?

How does it handle null or default properties?

Does it throw exceptions?

__Does it only "Get"?__

+++

We can't tell except by reading __and understanding__ the code, including everything it calls.

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
