# BDD against TDD spaghetti code effect

Presentation draft

We first define TDD before BDD to well understand differences and how the BDD approach can resolve tests complexity.

## Firstly, what is TDD ?

TDD stands for Test Driven Development

For each unit of code (function, class, module, etc) you must follow this process:

```
Add test -> Test fails -> Write implementation -> Run test -> Test succeeds
   ^                                 ^              |            |
   |                                 |______________|            |
   |_____________________________________________________________|
```

### Example: decimal to roman numerals converter

__First try__

```javascript
it('test if exists', () => {
  assert.equal('function', typeof fct)
})

-> AssertionError: expected 'function' to equal 'undefined'
```

__Second try__

```javascript
const decToRom = () => {
}

it('test if exists', () => {
  assert.equal('function', typeof fct)
})

-> OK
```

__Third try__

```javascript
const decToRom = () => {
}

it('test if 1 is converted to I', () => {
  assert.equal('I', decToRom(1))
})

-> AssertionError: expected 'I' to equal undefined
```

__Fourth try__

```javascript
const decToRom = () => {
  return 'I'
}

it('test if 1 is converted to I', () => {
  assert.equal('I', decToRom(1))
})

-> OK
```

## What are advantages of TDD ?

* Help you to write reliable code
* Prevent overkill, you code only that you need
* Cover 100% of the code without any efforts
* Each test is independant each others, tests can be isolated.

## What are disavantages of TDD ?

* It is difficult to write tests first if you do not know how to resolve a problem
* Huge amount of tests can involve loss of sense
* __A well covered program can have a poor value if it does not follow customer needs (Acceptance)__
* __It is difficult to maintain__:
    * __Tests should be independant, but in practice dependances exist (it is bad) and it is a hell to untangle them__
    * __Too close to implementation, refactoring or evolutions will cost many tests rewriting__

# Secondly, what is ATDD and how it can help me ?

A is for Acceptance, and TDD is same as below.
This is TDD with Acceptance approach, with customer goals focus.
It is not a test automation, it is a vision.
It is used to group tests by customer needs.

## Example: decimal to roman numerals converter for headlines in a word processor

```javascript
describe('As such writer, I need headlines with roman numerals betwween 1 and 5', () => {
  it('assert if 1 is converted to I', () => {
  })
  it('assert if 2 is converted to II', () => {
  })
  it('assert if 3 is converted to III', () => {
  })
  it('assert if 4 is converted to IV', () => {
  })
  it('assert if 5 is converted to V', () => {
  })
})
```

## What the main advantages of ATDD ?

* __Focus to the customer needs__
* __No off topic__
* __Better than TDD to prevent overkill__

# Finally, how BDD should improve testing process ?

B if for Behavior.
It is the evolution after ATTD, it is a new test automation approach with a new framework, not only an Acceptance focus.

Acceptance -> Feature -> Behaviors

* __Acceptance:__ As such user, I can recover my password
* __Feature:__ Password recovering by email with page to create new one
* __Behaviors:__ 
    * It should send email with password recovery link page inside
    * It should create new password if token and new passord are correct
    * It should expire token after 15 minutes

## Example: decimal to roman numerals converter

```javascript
describe('As such writer, I need headlines with roman numerals betwween 1 and 5', () => {
  it('should couvert 1 to I', () => {
      romanHeadline('1. The first chapter').should.equal('I. The first chapter');
      expect(romanHeadline('1. The first chapter')).to.equal('I. The first chapter');
  })
  it('should couvert 2 to II', () => {
  })
  it('should couvert 3 to III', () => {
  })
  it('should couvert 4 to IV', () => {
  })
  it('should couvert 5 to V', () => {
  })
})
```
## What are advantages of BDD ?

* __See ATDD__
* __It is easy to maintain__
  * __Test only behaviors not implementation__
  * __Do not need to change tests if implementation change__
  * __Amount of tests is acceptable__

## What are disadvantages of BDD ?

* Sometimes it is difficult to guess behavior tests before implementation
* Composition dependencies against TDD principle

