# BDD against Spaghetti code effect

Presentation draft

We first define TDD before BDD to well understand differences and how the BDD approach can resolve tests complexity.

# Firstly, what is TDD ?

TDD stand for Test Driven Development

For each unit of code (function, class, module, etc) you must follow this process:

```
Add test -> Test fails -> Write implementation -> Run test -> Test succeed
   ^                                 ^              |            |
   |                                 |______________|            |
   |_____________________________________________________________|
```

# What are advantages of TDD ?

* Help you to write reliable code
* Prevent overkill, you code only that you need
* Cover 100% of the code without any efforts

# What are disavantages of TDD ?

* It is difficult to write tests first if you do not know how to resolve a problem
* Huge amount of tests can involve loss of sense
* __A well covered program can have a poor value if it does not follow customer needs (Acceptance)__
* __Too close to implementation, refactoring or evolutions will cost many tests rewriting__

# Secondly, what is ATDD and how it can help me ?

A is for Acceptance, and TDD is same as below.
This is TDD with Acceptance approach, with customer goals focus.
It is not a test automation, it is a vision.
It is used to group tests by customer needs.

# Finally, how BDD should improve testing process ?

//
