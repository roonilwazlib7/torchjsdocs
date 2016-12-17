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

### Draw()

Returns: `VOID`

Runs the core draw logic and can be overridden if `super` is called

### Hide()

Returns: `self (Torch.Sprite)`

Prevents the sprite from being drawn

### Show()

Returns: `self (Torch.Sprite)`

Allows the sprite to be drawn

### Clone(x,y)

`x` Number, x position of new sprite

`y` Number, y position of new sprite

Returns: `Torch.Sprite`

Copies the sprite

### NotSelf(otherSprite)

`otherSprite` Torch.Sprite, some other sprite

Returns: `BOOL`

determines if otherSprite is different from self

### Velocity(?plane, ?optionalArgument)

`plane` String, what plane of the velocity to get/modify

`plane` Object, sets all planes of the velocity

`optionalArgument` Number, value to set plane to

Returns: `self (Torch.Sprite)` or `NUMBER` or `Torch.Point`

if plane is an object, the velocity is set to it and `self` is returned. If
plane is a valid string (x or y) and optionalArgument is null, the plane velocity is
returned. If optionalArgument is set with plane, the velocity is set and `self` is
returned

### Position(?plane, ?optionalArgument)

`plane` String, what plane of the position to get/modify

`plane` Object, sets all planes of the position

`optionalArgument` Number, value to set plane to

Returns: `self (Torch.Sprite)` or `NUMBER` or `Torch.Point`

if plane is an object, the position is set to it and `self` is returned. If
plane is a valid string (x or y) and optionalArgument is null, the plane position is
returned. If optionalArgument is set with plane, the position is set and `self` is
returned

## Internal Methods

### UpdateEvents()

Returns: `VOID`

Runs event logic against sprite and handles emitting of events.

### UpdateBody()

Returns: `VOID`

Runs simple built-in physics logic against the sprite.

### GetCurrentDraw()

Returns: `object`

Gets the appropriate image to be drawn on the sprite
