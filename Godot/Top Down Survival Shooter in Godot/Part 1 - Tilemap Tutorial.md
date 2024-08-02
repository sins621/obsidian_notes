# Tile Map Node:
Create a Tile Map Node and rename it to "World" with `F2`.
![[Create Tile Map Node.png]]
# Import Grass Asset:

## 1. Find the Asset inside your Asset Browser.
![[Import Grass Asset.png]]
## 2. Set the Tile Map Texture to the Grass Asset.
![[Set Tilemap Texture.png]]
Important!!!!!!!!!!!!
When creating a new tileset be be sure to specify the correct size.
![[Drag Grass into Tileset.png]]
![[Tile Split.png]]

Create Grass Layer:
![[Create Grass Layer.png]]

Create Second Bushes Layer:
![[Add Layer Element.png]]
Return to Tilemap and Now Layers are Accessible.
![[Select Layer in Tilemap.png]]

Paint Tile Area.
![[Add Tilesets to Scene.png]]

Increase Tilemap Scale:
![[Scale Tilemap.png]]
## 3. Add border with Bushes.

Select the bush layer, select the push tile, select the draw tool and lay in the border.
![[Add Bush Border.png]]
![[Bush Border.png]]

## 4. Add Randomization to the grass Tileset.

First go back to the grass layer, then select all grass tiles, select the rectangular tool, enable randomization, set scattering to 5 and finally paint over the desired area.
![[Randomized Tileset.png]]
## 5. Save the Scene.

Create a new folder named scenes.
![[Create Scenes Folder.png]]

## 6. Adjust Game Window to Match the Tilemap Size.

Navigate to `Project` > `Project Settings` then `Window` and Adjust the `Viewport Width` and `Viewport Height`.
![[Change Window Size.png]]

# Add Physics Collisions

Click on the `Tile Set` dropdown to display the `Physics Layer` menu, then add a physics element.
![[Set Tilemap Collision.png]]
Give Layers names so that it's easier to keep track of which collision layer corresponds to the relevant gameplay element. Navigate to `Project Settings` > `Layer Names` > `2D Physics`.
![[Collision Names.png]]
Go back to the TileSet Menu, select the grass asset and then with the `Select` tool enabled click on the bush.
![[Select Bush Tile to add Collision.png]]
Navigate to the `Physics` tab, then `Physics Layer`, then the 3 dot option menu and select `Reset to default tile shape` to create a collision box around the tile.
![[Add Bush Collision Box.png]]

# Create a `Main` scene to pull everything together.

Add a new tab to the project, select `Create Node`, select the basic `Node` and press `Create`. Rename your Node to `Main`.
![[Create Main Scene.png]]
Instantiate the `World` scene into the `Main` scene by clicking on the link icon, selecting the `World` scene and pressing `Open`.
![[Instantiate Child Scene.png]]
