# GridManager

## Overview
GridManager is a nifty little sprite component that allows sprites to have some
structure. Sprites can be added to other sprites' grids, and the grid manager
resolves position relative to the parent sprite.

## General Usage
The GridManager is accessed via the Grid property of a sprite.
```coffeescript
mySprite = new Torch.Sprite(game, 0, 0)
mySprite.Grid.Align("left")
parentSprite.Grid.Append(mySprite)

```

## Public Methods

### Position(?plane, ?optionalArgument)

### Align(positionTags...)

`positionTags...` Strings, the alignment properties to enable (`left`, `right`, `top`,`bottom`)

Returns: `self (Torch.GridManager)`

Sets the sprite's alignment within the parent

### Center(?turnOn)

`turnOn` Bool, should centering be turned on, default is true

Returns: `self (Torch.GridManager)`

Centers the sprite horizontally within the parent

### CenterVertical(?turnOn)

`turnOn` Bool, should centering be turned on, default is true

Returns: `self (Torch.GridManager)`

Centers the sprite vertically within the parent

### Apend(sprite)

`sprite` Torch.Sprite, sprite to add to grid

Returns: `self (Torch.GridManager)`

Adds a sprite to the grid

### Parent()

Returns: `Torch.Sprite` or `NULL`

Gets the sprites' parent if it exists

### Children(?matcher)

`matcher` Object, match children who share properties with matcher

Returns: `Array (Torch.Sprite)`

Gets all the children of the sprite grid, if matcher is provided, only children
who match the matcher are returned

### Ancestors(?matcher)

`matcher` Object, match children who share properties with matcher

Returns: `Array (Torch.Sprite)`

Gets all the ancestors of the sprite grid, if matcher is provided, only ancestors
who match the matcher are returned

## Internal Methods

### constructor(sprite)

`sprite` Torch.Sprite, sprite which owns the GridManager component

Returns: `GridManager`

Initializes the GridManager, is internal because GridManagers should not be
created from outside of Torch

### ApplyCentering(point)

`point` Torch.Point, point being transformed to center

Returns `Torch.Point`

Used to transform the sprite's position to center either vertically, horizontally,
or both.

### ApplyAlignment(point)

`point` Torch.Point, point being transformed to alignment

Returns `Torch.Point`

Used to transform the sprite's position to align left, right, top, or bottom

### ResolveAbosolutePosition()

Returns: `Torch.Point`

Transforms relative positioning into absolute positioning for the game world

### Update()

Returns: `Torch.Point`

Runs the logic of the GridManager

## Public Properties

### position `Torch.Point`
relative position of sprite in grid

## Internal Properties

### sprite `Torch.Sprite`
the sprite that owns the GridManager component

### parent `Torch.Sprite`
the parent sprite that the sprite is positioned in

### children `Torch.Sprite[]`
the children sprites of the sprite

### centered `BOOL`
control switch for horizontal centering

### centerVertical `BOOL`
control switch for vertical centering

### alignLeft `BOOL`
control switch for left alignment

### alignRight `BOOL`
control switch for right alignment

### alignBottom `BOOL`
control switch for bottom alignment

### alignTop `BOOL`
control switch for top alignment
