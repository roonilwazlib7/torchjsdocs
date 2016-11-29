# Sprites

## Overview
Sprites. Sprites are your things. If you think about adding something to your game,
it's probably a Sprite. Sprites have events that can be listened to, collision detection,
and even a hierchal system of children Sprites. Sprites is where stuff goes down.

## General Usage
Before we get down to the nitty-gritty of documenting everything about the sprite,
lets take a look at how to use them.

Sprites can be used as-is, like so:
```coffeescript
mySprite = new Torch.Sprite(game, 0, 0)
```
`game` being an instance of `Torch.Game`. See [Games](games.md)

Or they can by inherited from:
```coffeescript
class MyCustomSprite extends Torch.Sprite
    constructor: (game, x, y)->
        @InitSprite(game, x, y)

    Update: ->
        super()
        # do stuff..
```
When inherting Sprite, make sure you call `@InitSprite` in the constructor
Also, make sure `@InitSprite` is always the first call in the constructor and
that `super` is the first call in any overridden method.

## Public Methods

### constructor(game, x, y)

`game` Torch.Game, the game that the sprite will be added to

`x` Number, the initial x position of the sprite

`y` Number, the initial y position of the sprite

Returns:
`Torch.Sprite`

Initializes the Sprite

### InitSprite(game, x, y)

`game` Torch.Game, the game that the sprite will be added to

`x` Number, the initial x position of the sprite

`y` Number, the initial y position of the sprite

Returns: `VOID`

Initializes the sprite. Should be called inside of any class' constructor that
inherits from Sprite

### Fixed(tog)

`tog` Bool, false turns on fixing, true turns it off

Returns: `self (Torch.Sprite)`

Makes the sprite independent of camera position. Any sprite that is 'fixed' would
not move with the camera

### UpdateSprite()

Returns: `VOID`

Runs the core update logic of the sprite. Should only be used in a javascript
environment as a replacement for `super`

### Update()

Returns: `VOID`

Runs the core update logic and can be overridden if `super` or `@UpdateSprite` is
called

## Internal Methods

### UpdateEvents()

Returns: `VOID`

Runs event logic against sprite and handles emitting of events.

### UpdateBody()

Returns: `VOID`

Runs simple built-in physics logic against the sprite.
