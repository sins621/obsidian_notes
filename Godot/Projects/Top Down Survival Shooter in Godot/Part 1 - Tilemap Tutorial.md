# Tile Map Node:
Create a Tile Map Node and rename it to "World" with `F2`.
![](Pictures/Create%20Tile%20Map%20Node.png)
# Import Grass Asset:

## 1. Find the Asset inside your Asset Browser.
![](Pictures/Import%20Grass%20Asset.png)
## 2. Set the Tile Map Texture to the Grass Asset.
![](Pictures/Set%20Tilemap%20Texture.png)
Important!!!!!!!!!!!!
When creating a new tileset be be sure to specify the correct size.
![](Pictures/Drag%20Grass%20into%20Tileset.png)
![](Pictures/Tile%20Split.png)

Create Grass Layer:
![](Pictures/Create%20Grass%20Layer.png)

Create Second Bushes Layer:
![](Pictures/Add%20Layer%20Element.png)
Return to Tilemap and Now Layers are Accessible.
![](Pictures/Select%20Layer%20in%20Tilemap.png)

Paint Tile Area.
![](Pictures/Add%20Tilesets%20to%20Scene.png)

Increase Tilemap Scale:
![](Pictures/Scale%20Tilemap.png)
## 3. Add border with Bushes.

Select the bush layer, select the push tile, select the draw tool and lay in the border.
![](Pictures/Add%20Bush%20Border.png)
![](Pictures/Bush%20Border.png)

## 4. Add Randomization to the grass Tileset.

First go back to the grass layer, then select all grass tiles, select the rectangular tool, enable randomization, set scattering to 5 and finally paint over the desired area.
![](Pictures/Randomized%20Tileset.png)
## 5. Save the Scene.

Create a new folder named scenes.
![](Pictures/Create%20Scenes%20Folder.png)

## 6. Adjust Game Window to Match the Tilemap Size.

Navigate to `Project` > `Project Settings` then `Window` and Adjust the `Viewport Width` and `Viewport Height`.
![](Pictures/Change%20Window%20Size.png)

# Add Physics Collisions

Click on the `Tile Set` dropdown to display the `Physics Layer` menu, then add a physics element.
![](Pictures/Set%20Tilemap%20Collision.png)
Give Layers names so that it's easier to keep track of which collision layer corresponds to the relevant gameplay element. Navigate to `Project Settings` > `Layer Names` > `2D Physics`.
![](Pictures/Collision%20Names.png)
Go back to the TileSet Menu, select the grass asset and then with the `Select` tool enabled click on the bush.
![](Pictures/Select%20Bush%20Tile%20to%20add%20Collision.png)
Navigate to the `Physics` tab, then `Physics Layer`, then the 3 dot option menu and select `Reset to default tile shape` to create a collision box around the tile.
![](Pictures/Add%20Bush%20Collision%20Box.png)

# Create a `Main` scene to pull everything together.

Add a new tab to the project, select `Create Node`, select the basic `Node` and press `Create`. Rename your Node to `Main`.
![](Pictures/Create%20Main%20Scene.png)
Instantiate the `World` scene into the `Main` scene by clicking on the link icon, selecting the `World` scene and pressing `Open`.
![](Pictures/Instantiate%20Child%20Scene.png)
