# Collider

### Description

The collider is an interface used by [Sprite2D](Sprite2D.md) and [Shape2D](Shape2D.md), you will not need it to develop you game except if you want to create a custom GameObject class which supports collision.

### Variable Implementations
| Variable Name    | Description | Type | Get/Set |
| :---        |    :----   | :----: | :---:
| isColliderDisabled | If the collider is disabled no collision detection should be possible even if a collision checking method is called |bool| Both |

<br></br>

### Method Implementations

| Method     | Description | Return Type |
| :---        |    :----   | :----   | 
| isColliding(out GameObject collide) | Returns true if it is colliding and false if it isn't. It also sets the collide variable to the GameObject class of the collide | bool |
| isColliding  | Returns true if it is colliding and false if it isn't | bool |
| isCollidingWith(GameObject gameObject) | Returns true if it is colliding with the specified GameObject | bool |
