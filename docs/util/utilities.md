# Utilities

## Overview
Utilities encompasses a bunch of algorithmic goodies for strings, objects, functions
and arrays. Inside the Torch code, an instance of Utilites called Util is defined
for use by torch. This same instance is exported as Torch.Util.

## class Utilities [private]

## Public Methods

### constructor()

### String(str)

`str` String, the string to be manipulated

Returns: `StringUtility`

Sets up a string manipulation

### Array(array)

`array` Array, the array to be manipulated

Returns: `ArrayUtility`

Sets up an array manipulation

### Function(func)

`func` Function, the function to be manipulated

Returns: `FunctionUtility`

Sets up a function manipulation

### Object(obj)

`obj` Object, the object to be manipulated

Returns: `ObjectUtility`

Sets up an object manipulation

### Type(obj)

`obj` Any, the item whose type will be checked

Returns: `string`

Gets the proper type of something, examples:
```coffeescript
    util = new Utilities()

    util.Type("")
    # => "string"

    util.Type(null)
    # => "null"

    util.Type({})
    # => object
```

### Enum(args...)

`args...` String[], the list of enum properties

Returns: `object`

creates a psudeo enum with an object, for example:
```coffeescript
util = new Utilities()

colors = util.Enum("Red", "Yellow", "Blue")

colors.Red
# => 1

colors.Yellow
# => 2

colors.Blue
# => 3
```
