## What is this thing? Why do I care?

+++

## ☠ complexity ☠

Note:

Where OO

Not like Haskell! You won't see arcane runes that are painful to search for

---

## no $Digest cycle

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
