## What is this thing? Why do I care?

---

Have you ever gotten elbow deep into a big codebase...

...and _not_ regretted it?

---

## accidental complexity¹

☠ ☠ ☠

- Costs time
- Costs features
- Costs sanity

@snap[south]
@size[0.6em](¹ as opposed to _essential_ complexity)
@snapend

+++

It's hard to avoid.

Almost inevitable in large projects.

+++

Or is it?

+++

Discipline!

😠

Note:
We can buckle down, use grit and discipline to fight against it.

+++

But, how often do we win when we go against human nature?

😩

Note:
Especially when it's so easy to do the hacky thing, or
introduce some magic that makes sense at the time.

+++

Elm steers us away from the quick fixes, asks us to think about the
repercussions of the code we write.

---

## Why would my business use Elm?

---

Elm encourages us to think up-front about the design

Note:
It's common to start with the model and work our way up to the 
view, rather than starting with the view and working backwards.

When we think like that, architectural problems get caught early,
and are much cheaper to fix. 

---

New hires can get up to speed rapidly, and start fearlessly modifying the code

Note:
Compare AngularJS / React / Knockout / etc:

- much higher WTFs/minute rate
- Need discipline to avoid 'magic' / obtuse code
- TypeScript helps, but still leaves many choices up to individuals

---

Elm brings potentially costly corner cases to our attention early on

Note:
Much cheaper to find & fix defects early on, than in production

---

Code quality is almost automatic in Elm

Note:
`elm-format` means less back-and-forth bikeshedding

and almost all the Elm code in existence is formatted consistently

---

We can make impossible states **impossible**

Note:
Richard Feldman has a great video on this! The gist of it is that
if you pick the right model to represent the application, it becomes
impossible to ever get into states that shouldn't be possible. 

+++

![Video](https://www.youtube.com/embed/IcgmSRJHu_8)


---

## Why would a dev choose Elm?

---

Elm's type system is very safe

+++

## There are no
## runtime errors

Note:
In languages with exceptions, all functions have an extra, hidden return type.

Throw / Catch are basically a `GOTO` statement. How 

+++

## There are no
## null values

Note:
The "billion dollar mistake" ― when we use a type in Elm, we know 
__unconditionally__ that we have that type, and not a `null` value.

TypeScript allows us to pretend we have that safety - but it's built
in sand - TypeScript cannot protect you at runtime.

+++

Control statements are forced to deal with all possibilities

+++

```elm
type Msg
    = Increment
    | Decrement


update : Msg -> Model -> Model
update msg model =
    case msg of
        Increment ->
            { model | count = model.count + 1 }
```

+++

```
This `case` does not have branches for all possibilities:

24|>    case msg of
25|>        Increment ->
26|>            { model | count = model.count + 1 }

Missing possibilities include:

    Decrement

I would have to crash if I saw one of those. Add branches for them!

Hint: If you want to write the code for each branch later, use `Debug.todo` as a
placeholder. Read <https://elm-lang.org/0.19.0/missing-patterns> for more
guidance on this workflow.
```


---

Simplicity from start to end

Note:
Elm is helpful, from the day you start a project
through to the last time it's worked on.

---

It's a pleasure to read Elm code

Note:
We don't need to rely on discipline to avoid complexity-multiplying mutations and side effects

You have to really go out of your way to write underhanded tricks

It's even helped developers with ADHD

+++

![Video](https://www.youtube.com/embed/wpYFTG-uViE)

---

> Programmers using functional languages get paid more, regardless of experience level

+++

![paid more](https://cdn.sstatic.net/insights/Img/Survey/2018/salary_language-1.svg?v=3f273db9f512)

footnote : https://insights.stackoverflow.com/survey/2018/#work-salary-and-experience-by-language

Note:
https://discourse.elm-lang.org/t/elm-feedback-in-the-state-of-javascript-2018/2560/10?u=rkb

---

## Short feedback loop

+++

↱   think → type → compile → test   ↲ 

---

Upcoming targets like WebAssembly will be free

---

Entire classes of bugs just don't exist in Elm

Note:
mutations, unexpected `null`s, etc...

---

Much harder to inadvertently break non-local code
(especially if you make impossible states impossible)

Note:


+++

```c#
public class Startup
{
    // ...

    public void Configure(IApplicationBuilder app, IHostingEnvironment env)
    {
        /// ...

        app.UseStaticFiles();
        app.UseSpaStaticFiles();

        // ...
    }
}
```

@[10](What the heck does this do? What changes if it present, or missing?)

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

You don't need half a dozen different tools to write Elm

+++

Babel • Webpack • TypeScript • Redux
Redux-Loop • Redux-Saga • Create-React-App
...etc...

---

Packages are encouraged to have useful names

+++

Compare some of the [top packages on npm](https://www.npmjs.com/browse/depended):

_lodash bluebird axios minimist
through2 inquirer q_

 

With some [from Elm](http://elm-skimmer.com/):

_elm-css elm-plot elm-test elm-sortable-table
elm-route-url elm-decode-pipeline elm-graphql_

---

Choice paralysis

+++

JS encourages many packages

-vs-

Elm says there should be one great package that solves the problem

---

Tree shaking?

Dead code elimination.

Note: tree shaking is risky in js and typescript; it relies
on assumptions that don't always hold. 
when there are problems with it, they might only 
manifest in production mode.


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

LMW examples

Note:
<https://lmw.demo.envoyat.com/about-lmw/our-people/>
<https://www.lmw.com.au/about-lmw/our-people/>
<https://lmw.demo.envoyat.com/request-a-quote/>
<https://www.lmw.com.au/request-a-quote/>

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
