## Elm

- only ==
- check all conditions and find errors like typos even in an unmet condition
- disallow/warn about mixed type comparison like 1 == « 1 » , this won’t never happen in Elm so he tells you with a MISMATCH TYPE error
- Elm uses Virual DOM natively
- If a dispatched action is not handled inside the model update function, Elm throws an error
- a lot of runtime errors disappeares with Elm compiler
- a lot of functional tests in pure JS becomes irrelevant in Elm
- Elm compile to pure basic JS compatible IE8+. has not been tested, just against a large codebase.

Syntaxe for updating model (Immutability is key in Elm):
```Elm
-- actionType switch case has been skip in this example.
reducer action model =
  { model | key = model.key }
```

- Elm do not use function callback. It sends instead, the new data the user wants.

This is awesome.
```Elm
-- For Elm, this, is empty list. It doesn't know anything about what it contains :
[]

-- prints: [] : List a
-- "a" meaning “whatever" for Elm.
-- If it happens that we need to filter an empty List in our 
-- application like this :
List.filter (\str -> str /= "a") []
-- Elm will know that it's a list of Strings because we are
-- filtering list elements against a String.
-- This also happens with any used Primitive.
```
