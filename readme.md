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

## Resources
- https://www.youtube.com/watch?v=zBHB9i8e3Kc
