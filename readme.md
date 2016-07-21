# Elm

- only ==
- check all conditions and find errors like typos even in an unmet condition
- disallow/warn about mixed type comparison like 1 == « 1 » , this won’t never happen in Elm so he tells you with a MISMATCH TYPE error
- Elm uses Virtual DOM natively
- If a dispatched action is not handled inside the model update function, Elm throws an error
- a lot of runtime errors disappears with Elm compiler
- a lot of functional tests in pure JS becomes irrelevant in Elm
- Elm compile to pure basic JS compatible IE8+. has not been tested, just against a large codebase.

Syntax for updating model (Immutability is key in Elm):
```Elm
-- actionType switch case has been skip in this example.
reducer action model =
  { model | key = model.key }
```

- Elm do not use function callback. It sends instead, the new data the user wants.

This is awesome. For Elm, `[]` is an empty List. He doesn't know anything about what it contains.
```Elm
elm > []
-- prints: [] : List a
```
"a" meaning “whatever" for Elm.
If it happens that we need to filter an empty List in our application like this :
```Elm
List.filter (\str -> str /= "a") []
```
Elm will know that it's a list of Strings because we are filtering list elements against a String. This also happens with any used Primitive.


You can add indications above functions to specify each arguments types + type of returned value:
```Elm
myMethod : String -> String -> Int
myMethod firstname lastname = 5
```
This is also useful for doc I guess.
What is awesome is that Primitives used as indications don't have to be known Primitive.
This is legit :
```Elm
myMethod : foo -> foo -> Int
myMethod firstname lastname = 5
```
Elm doesn't know `foo`, he doesn't have to, but he does know that you want _consistency_ between these arguments.
`foo` cannot be used as returned type value has Elm always know the true type of the end value

- when publishing packages on elm packages plateform, semantic versionning is enforced. Plus, Elm compiler will tell if your changes are breaking changes.

- for side effects, you describe Tasks. Every functions doing  side effect have to return Task type. This helps compiler to find which function could possibly initiate the error.

- function defintions order doesn't matter

## Observation
Awesome tools exists to debug JS application. But because of the flexible nature of JS and the countless ways developers write code, it's hard for these tools to anticipate runtime errors.
When you know what the Elm compiler is capable of, you come to think that all these cool tools won't ever be able to catch every exception. Flow for instance, throws __possible__ runtime errors.

It's easy to say to a type checker "let me handle this, i know what this function returns" and put `any` has returned value's type. But if you do this once, you may end up doing this a lot later, gradually losing what this tool offers and confronted back to the real nature of JS.

As André Staltz said in a blog post, when you use Elm, you use the Elm language and the Elm architecture. You don't have to decide how your data travels inside your app, neither how to manage its state: Elm is here to back you up because he _knows_. You just have to focus on delivering your feature, the good path.

## Resources
- https://www.youtube.com/watch?v=zBHB9i8e3Kc
- https://www.youtube.com/watch?v=txxKx_I39a8
- http://staltz.com/some-problems-with-react-redux.html
