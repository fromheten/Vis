# VIS LANG

Computers don't run ASCII. They run binary code, derived from syntax trees. When implementing Lisp I saw that it's written form is just a thin layer between the programmer and the syntax tree because of s-expressions. I want to make a purely functional programming environment where you assemble your program tree by composing functions. All functions are pure, and they create values that float to the main function.

Programming in Vis is tree construction (planting?). It can be done with a visual tree editor, or in a textual s-expression format. They are equal and have no difference, except that one has zero syntax errors.

## What is a Vis function?
Vis functions are labeled with a type annotation. They take arguments and return data. Functions are a data type that can be returned. Pretty standard Lisp/ML-style things that you have seen before.

Every function has a unique ID, that is a hash of the function. Since functions are pure and uniquely identifiable (from their unique hash), they can be shared freely in a hyperlinking way, similar to the world wide web. Part of the function body is a human-readable name, so don't worry about refering to them as some random hex number...

## Side effects - needs more thought
Since all functions are pure they can be shared. But what fun is software if you can't change the world with it? Side effects are why we do what we do.

### Possible solutions to having pure functions and still doing side effects
* Have 2 function types - one `Function` for pure functions and `Procedure` for side-effects. A `Procedure` can call functions, but a `Function` can not take a `Procedure` as argument.
* ????
* なんだけ　なんだけ

## Type safety
Vis functions are annotated with types - and can be checked for correctness. This makes for less bugs, but even more importantly that let's your programming environment display all possible functions you can insert at any point

``` ascii art
 ---------------------------------------------------------------------------------------------------
| (defun increase-account-balance     | Suggestions                                                 |
|   [Account acc Num num]             | ===========                                                 |
|   (update acc :balance num))        | account (Str name Str title Num initial-balance) -> Account |
|                                     | change-title (Account acc Str title)                        |
| (increase-account-balance ▊)        | ...                                                         |
|                                     | ...                                                         |
|                                     | ...                                                         |
|                                     | ...                                                         |
 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
```

This illustrations shows one possible way to do this - when focus is in the argument list for the `increase-account-balance` function, suggestions of function returning the expected type are shown. That can be nice, and very fun :).

With types and graphical programming,

## How is Vis edited?
Vis is programs represented as trees. Nothing new. The tree can be generated from parsing a text file or text input to a repl. It can also be made in a graphical program, maybe where users drag things into the argument list like you assemble a puzzle from pieces that fit. Graphical and Textual representation - it's just trees!

## Compilation targets
Compilation is turning a tree into something the computer can run. You can turn it into binary code, some bytecode or transpile into another language.
It would make a lot of sense to compile to JS and have it run seamlessly on the web. Another option is LLVM bytecode - great for efficiency but I don't know much about it.

If functions and procedures are different things, maybe having functions be cross-platform and procedures needing to be ported can be a good way. Then the function can compile into whatever.
