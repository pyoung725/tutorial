# Collection Game Sprites Tutorial
## Introduction 
In this tutorial you will make a game where the player needs to collect 20 items while staying away from the enemy

Learning goals  
+ *use* **conditional container blocks** to program game events   
+ *create* **sprites** and *apply* **sprite properties**  
+ *create* **visual** and **sound effects**

Let's get started!

## Container Blocks
A **container block** is a block that holds other blocks inside it

**container blocks** have:  
- a flat edge at the top and bottom  
    - they do not link to other blocks  
    - place them in an empty workspace area  
- a space in the middle, like a mouth  
    - relevant blocks go inside the mouth space  
- a **condition** that tells when the blocks inside will run  
    - blocks with **conditions** are called **conditionals**   
    - **container blocks** are examples of **conditionals**  

The block shown, ``||loops(noclick):on start||``, is a **container block**    

It runs on the **condition** that the game starts 

## Set the Scene  
In **``||scene:Scene||``** find  
``||scene(noclick): set background color||``  
drag it inside the ``||loops(noclick):on start||`` container  
  -click on the gray oval to change the background color  
    - gray is transparent or no color  
    - it appears black, not gray  

find ``||scene(noclick):  start screen confetti▼ effect||``  
add it to the ``||loops(noclick):on start||`` container  
- click on *confetti▼* to change screen effects.  
- click on ***᪠*** to make the effect last only for a set amount of time
- after looking at the effects, you can remove the effect block if you don't want any screen effects  
  - drag the block to the left until you see a trash can  
  - when dragging a block make sure to click on the outermost part, not the inserts
  - click on the block and hit backspace or delete  
  - right click or 2-finger click on chromebook and select delete block  

```blocks
scene.setBackgroundColor(0)
effects.confetti.startScreenEffect()
```

## Let's talk Sprites    
A **sprite** is a game character or object

When creating sprites, you need to specify:  
- a variable *name* to store the sprite 
  - each variable *name* can only store one specific sprite
- an *image* for what the sprite looks like  
  - you can't import images into MakeCode Arcade
  - there is a gallery you can pick an image from 
  - you can edit a gallery image or draw your own  
- a *kind*  
  - like a role-- is it a player?  enemy?  food?  projectile?
  - you can create new kinds  

In **``||sprites:Sprites||``** find    
``||variables(noclick): set mySprite▼ to sprite of kind Player▼||``  
add it to the ``||loops(noclick):on start||`` container     
- click on *mySprite▼* to change the name to myplayer  
- click on the gray square to assign an image to the sprite  
  - click on gallery to select a pre-made image
  - wait until *__AFTER YOU FINISH THE TUTORIAL__* to edit/create your own images

Create a total of 3 **sprites**:
1. *myplayer* of kind Player  
    - should already be created in the tutorial steps above
2. *myenemy* of kind Enemy  
    - right click or 2-finger click the word *set* on ``||variables(noclick): set myplayer▼ to sprite of kind Player▼||``    
    - duplicate the block and add it to ``||loops(noclick):on start||``    
    - click on *myplayer▼* and make a ***new variable*** *myenemy*  
    - click on *Player▼* to change the kind   
3. *myfood* of kind Food   

```blocks
scene.setBackgroundColor(0)
effects.bubbles.startScreenEffect()
let myplayer = sprites.create(img`
    .............ccfff..............
    ...........ccddbcf..............
    ..........ccddbbf...............
    ..........fccbbcf...............
    .....fffffccccccff.........ccc..
    ...ffbbbbbbbcbbbbcfff....ccbbc..
    ..fbbbbbbbbcbcbbbbcccff.cdbbc...
    ffbbbbbbffbbcbcbbbcccccfcdbbf...
    fbcbbb11ff1bcbbbbbcccccffbbf....
    fbbb11111111bbbbbcccccccbbcf....
    .fb11133cc11bbbbcccccccccccf....
    ..fccc31c111bbbcccccbdbffbbcf...
    ...fc13c111cbbbfcddddcc..fbbf...
    ....fccc111fbdbbccdcc.....fbbf..
    ........ccccfcdbbcc........fff..
    .............fffff..............
    `, SpriteKind.Player)
let myenemy = sprites.create(img`
    . . . . 5 . . . . . . . . . . . 
    . . . 5 . . 5 . . . . . . . . . 
    . . 5 2 2 5 . . . . . . . 5 5 . 
    . 5 2 5 5 2 2 . . . . . 5 5 . . 
    . 2 2 5 . . 2 2 . . . 5 5 2 2 . 
    . . . . . . 2 2 . . 5 5 2 2 2 2 
    . . . . . 2 2 2 . 2 2 2 2 2 2 2 
    . . . . . 2 5 2 . 2 2 2 . 2 2 2 
    . . . 5 5 2 5 5 . 2 2 . . . 2 2 
    . . 5 5 2 2 2 5 . 2 2 . . . 2 2 
    . . . 2 2 2 . 5 2 2 2 . . 2 2 2 
    . . 2 2 2 . . . 2 2 . . 2 2 2 . 
    . . 2 2 . . 1 . 2 2 . . 5 2 . . 
    . . 2 2 . . . 2 2 2 . . 5 5 5 5 
    . . 2 2 2 2 2 2 2 2 . . . 5 5 . 
    . . . 2 2 2 2 2 2 . . . . . 5 5 
    `, SpriteKind.Enemy)
let myfish = sprites.create(img`
    . . . . . . . . . . . . . . . . 
    . . . . . . . . c c c c . . . . 
    . . . . . . c c d d d d c . . . 
    . . . . . c c c c c c d c . . . 
    . . . . c c 4 4 4 4 d c c . . . 
    . . . c 4 d 4 4 4 4 4 1 c . c c 
    . . c 4 4 4 1 4 4 4 4 d 1 c 4 c 
    . c 4 4 4 4 1 4 4 4 4 4 1 c 4 c 
    f 4 4 4 4 4 1 4 4 4 4 4 1 4 4 f 
    f 4 4 4 f 4 1 c c 4 4 4 1 f 4 f 
    f 4 4 4 4 4 1 4 4 f 4 4 d f 4 f 
    . f 4 4 4 4 1 c 4 f 4 d f f f f 
    . . f f 4 d 4 4 f f 4 c f c . . 
    . . . . f f 4 4 4 4 c d b c . . 
    . . . . . . f f f f d d d c . . 
    . . . . . . . . . . c c c . . . 
    `, SpriteKind.Food)
```

## Sprite Properties

**scale**
in a lot of games, enemies and boss characters are bigger than other characters  
the property to change size is called *scale*  

in **``||sprites:Sprites|``** find  
``||sprites(noclick):set mySprite▼ scale||``  
add it to the ``||loops(noclick):on start||`` container  
  - put it *below* ``||variables(noclick):set myenemy▼ to sprite||``  
  - if you need to move one block, press ctrl while clicking and dragging the block  
  - you cannot set the scale of a sprite that does not exist yet
  - change the *name* to *myenemy▼*  
  - fill in a number greater than 1 to make the sprite bigger  

set the *scale* of any other sprites you want to change size
  - if ou want to make the sprite smaller, fill in a number less than 1  

**position**  
by default ALL sprites will spawn in the center of the screen  
to make sprites appear somewhere else you must set its position  

in **``||sprites:Sprites||``** find  
``||sprites(noclick):set mySprite position||`` 
add it to the ``||loops(noclick):on start||`` container  
  - put it *below* ``||variables(noclick):set myenemy▼ to sprite||``  
  - if you need to move one block, press ctrl while clicking and dragging the block  
  - change the *name* to *myenemy▼*
  - click on a *0* next to x or y
  - click on the popup where you want the enemy to spawn  
  - you can also type the coordinates or use the slider  

duplicate ``||sprites(noclick): set myenemy▼ position||``  
add it to the ``||loops(noclick):on start||`` container  
  - make sure it is *below* ``||variables(noclick):set myfood▼ to sprite||``  
  - if you need to move one block, press ctrl while clicking and dragging the block  
  - change the *name* to *myfood▼*  

in **``||math:Math||``** find  
``||math(noclick):pick random||``
put it in place of the *0* afer x  
  - line up the left side of the block with the left side of the slot
  - ``||math(noclick):pick random 10 to 150||``  

duplicate ``||math(noclick):pick random||``  
put it in place of the *0* after y  
  - ``||math(noclick):pick random 10 to 110||``  

```blocks  
scene.setBackgroundColor(0)
effects.bubbles.startScreenEffect()
let myplayer = sprites.create(img`
    .............ccfff..............
    ...........ccddbcf..............
    ..........ccddbbf...............
    ..........fccbbcf...............
    .....fffffccccccff.........ccc..
    ...ffbbbbbbbcbbbbcfff....ccbbc..
    ..fbbbbbbbbcbcbbbbcccff.cdbbc...
    ffbbbbbbffbbcbcbbbcccccfcdbbf...
    fbcbbb11ff1bcbbbbbcccccffbbf....
    fbbb11111111bbbbbcccccccbbcf....
    .fb11133cc11bbbbcccccccccccf....
    ..fccc31c111bbbcccccbdbffbbcf...
    ...fc13c111cbbbfcddddcc..fbbf...
    ....fccc111fbdbbccdcc.....fbbf..
    ........ccccfcdbbcc........fff..
    .............fffff..............
    `, SpriteKind.Player)
let myenemy = sprites.create(img`
    . . . . 5 . . . . . . . . . . . 
    . . . 5 . . 5 . . . . . . . . . 
    . . 5 2 2 5 . . . . . . . 5 5 . 
    . 5 2 5 5 2 2 . . . . . 5 5 . . 
    . 2 2 5 . . 2 2 . . . 5 5 2 2 . 
    . . . . . . 2 2 . . 5 5 2 2 2 2 
    . . . . . 2 2 2 . 2 2 2 2 2 2 2 
    . . . . . 2 5 2 . 2 2 2 . 2 2 2 
    . . . 5 5 2 5 5 . 2 2 . . . 2 2 
    . . 5 5 2 2 2 5 . 2 2 . . . 2 2 
    . . . 2 2 2 . 5 2 2 2 . . 2 2 2 
    . . 2 2 2 . . . 2 2 . . 2 2 2 . 
    . . 2 2 . . 1 . 2 2 . . 5 2 . . 
    . . 2 2 . . . 2 2 2 . . 5 5 5 5 
    . . 2 2 2 2 2 2 2 2 . . . 5 5 . 
    . . . 2 2 2 2 2 2 . . . . . 5 5 
    `, SpriteKind.Enemy)
myenemy.setScale(2.5, ScaleAnchor.Middle)
myenemy.setPosition(140, 10)
let myfish = sprites.create(img`
    . . . . . . . . . . . . . . . . 
    . . . . . . . . c c c c . . . . 
    . . . . . . c c d d d d c . . . 
    . . . . . c c c c c c d c . . . 
    . . . . c c 4 4 4 4 d c c . . . 
    . . . c 4 d 4 4 4 4 4 1 c . c c 
    . . c 4 4 4 1 4 4 4 4 d 1 c 4 c 
    . c 4 4 4 4 1 4 4 4 4 4 1 c 4 c 
    f 4 4 4 4 4 1 4 4 4 4 4 1 4 4 f 
    f 4 4 4 f 4 1 c c 4 4 4 1 f 4 f 
    f 4 4 4 4 4 1 4 4 f 4 4 d f 4 f 
    . f 4 4 4 4 1 c 4 f 4 d f f f f 
    . . f f 4 d 4 4 f f 4 c f c . . 
    . . . . f f 4 4 4 4 c d b c . . 
    . . . . . . f f f f d d d c . . 
    . . . . . . . . . . c c c . . . 
    `, SpriteKind.Food)
myfish.setPosition(randint(10, 150), randint(10, 110))  
```

## Sprite Movement
in most games players are controlled using a keyboard, mouse, controller, or joystick  
in **``||controller:Controller||``** find  
``||controller(noclick):move mySprite▼ with buttons||``  
add it to the ``||loops(noclick):on start||`` container  
  - put it *below* ``||variables(noclick):set myplayer▼ to sprite||``  
  - if you need to move one block, press ctrl while clicking and dragging the block  
  - change the *name* to *myplayer▼*  
  - on the  keyboard use *WASD* or *arrows ↑←↓→*  

if you try the game in the simulator, the player disappears off screen
in **``||sprites:Sprites||``** find  
``||sprites(noclick):set mySprite▼ stay in screen||``  
add it to the ``||loops(noclick):on start||`` container  
  - put it *below* ``||variables(noclick):set myplayer▼ to sprite||``  
  - if you need to move one block, press ctrl while clicking and dragging the block  
  - change the *name* to *myplayer▼*  
  - make sure the toggle is on  

in this game, the enemy sprite is chasing the player sprite
in **``||sprites:Sprites||``** find  
``||sprites(noclick):set myenemy▼ follow mySprite▼||``
add it to the ``||loops(noclick):on start||`` container  
  - make sure it's placed *lower than* both ``||variables(noclick):set myenemy▼ to sprite||`` and ``||variables(noclick):set myplayer▼ to sprite||``  
  - if you need to move one block, press ctrl while clicking and dragging the block  
  - change *both names* so that *myenemy▼* is following *myplayer▼*  
  - click on ***᪠*** to reduce the speed of myenemy  

the food sprite will be bouncing around the screen  
in **``||sprites:Sprites||``** find
``||sprites(noclick):set mySprite▼ bounce on wall||``
add it to the ``||loops(noclick):on start||`` container  
  - put it *below* ``||variables(noclick):set myfood▼ to sprite||``
  - if you need to move one block, press ctrl while clicking and dragging the block    
  - change the *name* to *myfood▼*  
  - make sure the toggle is on  

the food sprite won't bounce on the wall unless it first moves and hits the wall  
**velocity** is speed in a specific direction  
for example, 60mph is a speed; 60 mph North is a velocity  
in **``||sprites:Sprites||``** find  
``||sprites(noclick):set mySprite▼ velocity||``  
add it to the ``||loops(noclick):on start||`` container  
  - put it *below* ``||variables(noclick):set myfood▼ to sprite||``  
  - if you need to move one block, press ctrl while clicking and dragging the block  
  - vx(velocity x) negative = left; positive = right     
  - vy(velocity y) negative = up; positive = down  
  - diagonal movement is a combination of vx and vy  
  - put numbers for vx and vy to make *myfood▼* move diagonally

```blocks
scene.setBackgroundColor(0)
effects.bubbles.startScreenEffect()
let myplayer = sprites.create(img`
    .............ccfff..............
    ...........ccddbcf..............
    ..........ccddbbf...............
    ..........fccbbcf...............
    .....fffffccccccff.........ccc..
    ...ffbbbbbbbcbbbbcfff....ccbbc..
    ..fbbbbbbbbcbcbbbbcccff.cdbbc...
    ffbbbbbbffbbcbcbbbcccccfcdbbf...
    fbcbbb11ff1bcbbbbbcccccffbbf....
    fbbb11111111bbbbbcccccccbbcf....
    .fb11133cc11bbbbcccccccccccf....
    ..fccc31c111bbbcccccbdbffbbcf...
    ...fc13c111cbbbfcddddcc..fbbf...
    ....fccc111fbdbbccdcc.....fbbf..
    ........ccccfcdbbcc........fff..
    .............fffff..............
    `, SpriteKind.Player)
controller.moveSprite(myplayer)
myplayer.setStayInScreen(true)
let myenemy = sprites.create(img`
    . . . . 5 . . . . . . . . . . . 
    . . . 5 . . 5 . . . . . . . . . 
    . . 5 2 2 5 . . . . . . . 5 5 . 
    . 5 2 5 5 2 2 . . . . . 5 5 . . 
    . 2 2 5 . . 2 2 . . . 5 5 2 2 . 
    . . . . . . 2 2 . . 5 5 2 2 2 2 
    . . . . . 2 2 2 . 2 2 2 2 2 2 2 
    . . . . . 2 5 2 . 2 2 2 . 2 2 2 
    . . . 5 5 2 5 5 . 2 2 . . . 2 2 
    . . 5 5 2 2 2 5 . 2 2 . . . 2 2 
    . . . 2 2 2 . 5 2 2 2 . . 2 2 2 
    . . 2 2 2 . . . 2 2 . . 2 2 2 . 
    . . 2 2 . . 1 . 2 2 . . 5 2 . . 
    . . 2 2 . . . 2 2 2 . . 5 5 5 5 
    . . 2 2 2 2 2 2 2 2 . . . 5 5 . 
    . . . 2 2 2 2 2 2 . . . . . 5 5 
    `, SpriteKind.Enemy)
myenemy.setScale(2.5, ScaleAnchor.Middle)
myenemy.setPosition(140, 10)
myenemy.follow(myplayer, 30)
let myfish = sprites.create(img`
    . . . . . . . . . . . . . . . . 
    . . . . . . . . c c c c . . . . 
    . . . . . . c c d d d d c . . . 
    . . . . . c c c c c c d c . . . 
    . . . . c c 4 4 4 4 d c c . . . 
    . . . c 4 d 4 4 4 4 4 1 c . c c 
    . . c 4 4 4 1 4 4 4 4 d 1 c 4 c 
    . c 4 4 4 4 1 4 4 4 4 4 1 c 4 c 
    f 4 4 4 4 4 1 4 4 4 4 4 1 4 4 f 
    f 4 4 4 f 4 1 c c 4 4 4 1 f 4 f 
    f 4 4 4 4 4 1 4 4 f 4 4 d f 4 f 
    . f 4 4 4 4 1 c 4 f 4 d f f f f 
    . . f f 4 d 4 4 f f 4 c f c . . 
    . . . . f f 4 4 4 4 c d b c . . 
    . . . . . . f f f f d d d c . . 
    . . . . . . . . . . c c c . . . 
    `, SpriteKind.Food)
myfish.setPosition(randint(10, 150), randint(10, 110))
myfish.setVelocity(50, 50)
myfish.setBounceOnWall(true)
```

## Game Stats(Info)  


## Overlap conditionals
