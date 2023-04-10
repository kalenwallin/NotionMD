# Godot Game Level Demo

Author: Kalen Wallin
Created: April 1, 2023 10:53 PM
Featured: No
Last Updated: April 2, 2023 4:08 PM
Public: Yes
Published: February 14, 2022
Tags: Game Dev, Godot, Graphic Design, School

This is a game level demo for my Game Engineering Architecture course (GEDE-637) at Reykjavik University. 

[Level demo created in Godot. [Play in fullscreen here](https://games.kalenwallin.com/godotdemo/html/godot-demo.html).](https://games.kalenwallin.com/godotdemo/html/godot-demo.html)

Level demo created in Godot. [Play in fullscreen here](https://games.kalenwallin.com/godotdemo/html/godot-demo.html).

## Background

I used the game engine Godot v3.2. I had already used Godot to create a small city building game called [Minieval](https://frie.dev/minieval) in 2021, which is why I decided to use Godot. I worked mostly on UI design in that game, so I thought this would be a good opportunity to learn how to create character art and program it.

I forked this project from this repository:

[youtube-tutorials/Action RPG at master · uheartbeast/youtube-tutorials](https://github.com/uheartbeast/youtube-tutorials/tree/master/Action%20RPG)

Which is from [Heartbeast's Make an Action RPG in Godot 3.2](https://www.youtube.com/watch?v=mAbG8Oi-SvQ&list=PL9FzW-m48fn2SlrW0KoLT4n5egNdX-W9a) tutorial series. It is a massive 23 video tutorial series that includes assets for the player, the bat enemy, effects such as hit damage and death, as well as the world assets like grass, bushes, trees, dirt, etc.

# Game Overview

Using the existing assets, I created a tutorial level, a transition scene, a boss fight level, a death scene and a victory scene. The tutorial scene introduces the movement and attacking system. After the tutorial, I introduce the final boss in a transition scene. Then the player loads into the boss fight, where they take on Evil Hannes. After beating Evil Hannes, the player is rewarded with a victory scene where they have the option to play again or exit the game.

# Paint.net Art

Most of my creative effort was put into making and programming the new models. These include Evil Hannes and the projectiles he shoots. I used paint.net, a graphics editing program, to create pixel models of each of the assets. This took a bit of time because I had to create a new model for each frame of the asset to be animated. Otherwise, the gameplay looked too stale. I ended up with four different models of Evil Hannes, where he is facing in each of the cardinal directions, 64 models for the projectiles, eight for each of the cardinal and ordinal directions.

![Projectile sprite sheet in paint.net.](Godot%20Game%20Level%20Demo%20ec2750346a974afaaae04160393be097/Untitled.png)

Projectile sprite sheet in paint.net.

![Character sprite sheet in paint.net.](Godot%20Game%20Level%20Demo%20ec2750346a974afaaae04160393be097/Untitled%201.png)

Character sprite sheet in paint.net.

# Godot Sprites

To prepare the pixel models for in game use, I used the sprite node, which is used to display the character art I created. The sprite node takes a PNG file, called a sprite sheet, that has all the different model frames laid out. Godot automatically picks out the frames from the PNG sheet based on how many horizontal and vertical frames you want to use. For example, with the projectile sheet that has 64 model frames in an 8x8 layout, I set both the horizontal and vertical frames to 8, so that each model frame is one game frame. It is important to split up the frames evenly in paint.net, otherwise the game frames contain parts of other model frames.

![Sprite sheet of Evil Hannes in png format.](Godot%20Game%20Level%20Demo%20ec2750346a974afaaae04160393be097/HannesSheet.png)

Sprite sheet of Evil Hannes in png format.

![Sprite sheet of projectiles in png format.](Godot%20Game%20Level%20Demo%20ec2750346a974afaaae04160393be097/ProjectileSheet.png)

Sprite sheet of projectiles in png format.

# Godot Animation

Once I converted the pixel models into Godot sprites, I was able to animate the sprites using the animation player. For Evil Hannes, this was simply making a hover animation, where I set key frames on his Y position, for each of the four directions and then mapping his movement to the animations using an animation tree. For the projectiles, I already had the frames I needed to make an animation. Godot has a nice system already in place, so it was as simple as setting key frames on changing the frame's property in the sprite node.

![Evil hannes head hovering animation in Godot Editor.](Godot%20Game%20Level%20Demo%20ec2750346a974afaaae04160393be097/hannes.gif)

Evil hannes head hovering animation in Godot Editor.

# Godot Scripting

Once animated, I used Godot’s scripting language, GDScript, to make Evil Hannes follow the player, shoot his projectiles, and attack the player. I used the script that Heartbeast made for the bat enemy’s AI detection of the player to make Evil Hannes chase the player and attack him with a headbutt. But I had to create my own script to make Evil Hannes shoot projectiles. I altered some stats of the bat script to make Evil Hannes slower and heavier, since he is much bigger than the bat. Furthermore, I made a health bar for Hannes, so the player knows how much health he has. I also made new scripts to make the game flow from scene to scene, such as when a player finishes the tutorial or dies during the boss fight.

![Code snippet of projectile attack from [Hannes.gd](http://Hannes.gd) written in GDScript.](Godot%20Game%20Level%20Demo%20ec2750346a974afaaae04160393be097/Hannes.gd.svg)

Code snippet of projectile attack from [Hannes.gd](http://Hannes.gd) written in GDScript.

# Gameplay

The player has 5 hit points, Evil Hannes has 20 hit points, and each bat has 2 hit points. All attacks do 1 damage. During the boss fight, Evil Hannes shoots out projectiles, alternating between cardinal and ordinal directions, every 2 seconds and also attacks the player with a headbutt if they get too close. If the player reaches 0 hit points, they die and have to restart the level.

![gameplay.gif](Godot%20Game%20Level%20Demo%20ec2750346a974afaaae04160393be097/gameplay.gif)