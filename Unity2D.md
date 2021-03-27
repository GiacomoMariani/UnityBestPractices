# 2D
* Turn off ealtime global illumination
* *PPU* - Pixel Per Unit: determines how many pixel (width and height) correspond to 1 unit in game space. Select a standard and re use it.
* *Avoid Overdraw*: Reduce overlapping pixels, of sprites above another sprite
* Set *Sprite* => *Mesh Type* to _Tight_ to optimize the mask of the image
* Further improve the Mask of the Sprite in the *Sprite Editor*
* Merge sprites after the level is done
* Use the [9-slice](https://docs.unity3d.com/Manual/9SliceSprites.html) approach
* Burst improves Spline and Animations
* Implement an importer template

# Tools
## Tilemap
* Tilemap Chunk mode optimize things if sorting is not required
* Place the tiles in one atlas for each tilemap

## Spline
* Set *Cache Geometry* of the Spline if it won't change at runtime

## 2D Physics
* Combine static 2D colliders as a composite collider

## Pixel Perfect
* Set the sprite Filter mode to point
* Use the same PPU for all sprites
* Add pixel perfect camera

# Links
* [Unity 2D Tools](https://unity.com/unity/features/2dtools)
