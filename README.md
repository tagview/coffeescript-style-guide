# Tagview Coffeescript Style Guide

## White Space

Use soft tabs with 2 spaces.

```coffeescript
# Bad
hello = (names) ->
∙∙∙∙for name in names
∙∙∙∙∙∙∙∙alert name

hello = (names) ->
∙for name in names
∙∙alert name

# Good
hello = (names) ->
∙∙for name in names
∙∙∙∙alert name
```

Don't put spaces between parentheses.

```coffeescript
# Bad
triangle = -> ( base, height ) base * height / 2

# Good
triangle = -> (base, height) base * height / 2
```

Put a space after a comma and operator signs.

```coffeescript
# Bad
user = new User "Bruce","Lee"
numbers = [1,2,3]
sum = 1+2

# Good
user = new User "Bruce", "Lee"
numbers = [1, 2, 3]
sum = 1 + 2
```

Put a space after an asignment.

```coffeescript
# Bad
hello = (name="Joe") alert "Hello #{name}"

# Good
hello = (name = "Joe") alert "Hello #{name}"
```

Don't put spaces before `:`.

```coffeescript
# Bad
user = 
  name : "Sasha"
  age : 25

# Good
user = 
  name: "Sasha"
  age: 25
```

## Naming

Use camelCase for objects, functions and primitives.

```coffeescript
# Bad
User = name: "Sasha"
check-power-level = -> "Over 9 thousands"
powerfull_user = name: "Vegeta"
power_level = 9000

# Good
user = name: "Sasha"
checkPowerLevel -> "Over 9 thousands"
powerfullUser = name: "Vegeta"
powerLevel = 9000
```

Use [PascalCase](http://c2.com/cgi/wiki?PascalCase) for classes.

```coffeescript
# Bad
class user extends human
  constructor: (@name)

bad = new user "Noooooo"

# Good
class User extends Human
  constructor: (@name)

good = new User "Yeah"
```

Use uppercase with underscores for constants.

```coffeescript
HI_I_AM_A_CONSTANT = 42
```

Prefix jQuery/zeptojs objects with a `$`.

```coffeescript
# Bad
header = $(".header")

# Good
$header = $(".header")
```

Prefix booleans with `is` or `has`.

```coffeescript
user.isActive
user.hasPosts()
```

## Strings

Use double `""` quotes.

```coffeescript
# Bad
name = 'Vegeta'

# Good
name = "Vegeta"
```

Use interpolation instead of contatenation.

```coffeescript
# Bad
"Hello " + name + ", how are you?"

# Good
"Hello #{name}, how are you?"
```

## Arrays

Always use array literals.

```coffeescript
# Bad
names = new Array

# Good
names = []
```

When you need to transform an array-like object into an array, use Array#slice.

```coffeescript
test = ->
  args = Array::slice.apply(arguments)
```

## Objects

Always use object literals.

```coffeescript
# Bad
obj = new Object

# Good
obj = {}
```

Don't use strings as keys.

```coffeescript
# Bad
var obj = 
  "name": "Sasha"
  "age": 23

# Good
var obj =
  name: "Sasha"
  age: 23
```

Put each key-value pair on its own line.

```coffeescript
# Bad
var obj =
  name: "Sasha", age: 23,
  rating: 10

# Good
var obj = 
  name: "Sasha"
  age: 23
  rating: 10
```

Don't use commas when creating multiline objects.

```coffeescript
# Bad
var obj = 
  name: "Sasha",
  age: 23,
  rating: 10

# Good
var obj = 
  name: "Sasha"
  age: 23
  rating: 10
```

## Functions

Don't use parentheses when declaring functions that take no arguments.

```coffeescript
# Bad
hello = () -> alert "Hello"

# Good
hello = -> alert "Hello"
```

When the function has arguments, put a space after the parentheses.

```coffeescript
# Bad
hello = (name)-> alert "Hello #{name}"

# Good
hello = (name) -> alert "Hello #{name}"
```

## Classes and Constructor Functions

Don't open the parentheses when creating objects from classes that don't accept arguments.

```coffeescript
# Bad
user = new User()

# Good
user = new User
```

Use `::` to access the function prototype.

```coffeescript
# Bad
Array.prototype.slice([1, 2])

# Good
Array::slice([1, 2])
```

Prefer `@` over `this.property`.

```coffeescript
# Bad
class User
  fullName: ->
    this.firstName + this.lastName

# Good
class User
  fullName: ->
    @firstName + @lastName
```

Avoid the use of a standalone `@`.

```coffeescript
# Bad
class UsersView extends Backbone.View
  initiliaze: -
    @collection.on "reset", @render, @

  render: ->
    $("body").html("Hi")
    @

# Good
class UsersView extends Backbone.View
  initiliaze: -
    @collection.on "reset", @render, this

  render: ->
    $("body").html("Hi")
    this
```

## Conditionals

Don't use `unless...else`, use `if...else`

```coffeescript
# Bad
unless isLogged
  login()
else
  "Hello"

# Good
if isLogged
  "Hello"
else
  login()
```

## Comments

Always put a newline above a comment.

```coffeescript
# Bad
isActive = true
# The admin
user = new Admin

# Good
isActive = true

# The admin
user = new Admin
```

When using multiline comments, use a empty `#` to separate paragraphs.

```coffeescript
# This is a block comment. Note that if this were a real block
# comment, we would actually be describing the proceeding code.
#
# This is the second paragraph of the same block comment. Note
# that this paragraph was separated from the previous paragraph
# by a line containing a single comment character.
```

## Semicolons

Nope

```coffeescript
# Bad
user = new User;

# Good
user = new User
```
