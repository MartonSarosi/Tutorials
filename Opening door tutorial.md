# Opening door tutorial

This tutorial will show you how to make a door open on trigger by using a script and animations.

## 1. Setting up the scene

Assuming we a player controller in the scene, first we will create a simple door object. Of course you should use your own prefab.
We will create a couple cubes and a door object in our scene.

![image](https://user-images.githubusercontent.com/79841064/205897528-287d487a-6c03-4e64-a71b-bdec584b3eda.png)

It is important to also create a Door_Hinge empty gameobject. The door itself will sit on this so we can rotate it when we want the door to open. Don't forget to set the point of the Door_Hinge as pivot and not centre in the top right corner of the scene window. We will also add a Box Collider to Door_Hinge, we will use this collider to detect the player and open the door if we walk into the collider. We need to set this collider to trigger and make it about this big:

![image](https://user-images.githubusercontent.com/79841064/205898169-4f2efadb-1c88-4540-9394-a4127f4645b7.png)

## 2. Creating the animations

Now we will need to create an animation controller for the Door_Hinge object, and three animations. One where the door is closed, one where it is opens, and one where it stays open. First we will create the one where it opens. I called this animation Door_Opening. Press the record button in the animation window, go to the 1 minute mark on the timeline and set the Y rotation to 110. It should look like this:

![image](https://user-images.githubusercontent.com/79841064/205899221-dfc75276-8590-4bdb-a16d-e6045c7a3071.png)

Now we will create a new animation, call it Door_Open, and copy the keyframe from the Door_Opening animation at the 1 minute mark, and paste it in for the Door_Open animation at the 0 second mark.

![image](https://user-images.githubusercontent.com/79841064/205899887-80134735-a6d2-40b2-a8c3-04a0ba0a2675.png)

We will do the same thing for the last animation, Door_Closed. For this we copy the first keyframe from Door_Opening, and paste it in for Door_Closed.

In the animator window we need to set the Door_Closed animation as the default state, and make transitions from one to another like so:

![image](https://user-images.githubusercontent.com/79841064/205900440-1848aea5-3779-48ac-90a0-16000c8c2bc7.png)

We will also create a new parameter, a bool, and called it PlayerOpen.

![image](https://user-images.githubusercontent.com/79841064/205900666-63038cf5-693e-4544-bd78-ddd5bf079a80.png)

We need to add this parameter as a condition to the first, third transition. For the one between Door_Closed and Door_Opening we leave it on true.

![image](https://user-images.githubusercontent.com/79841064/205901115-647a9d1f-f174-41ee-b579-2aaa8544aede.png)

For the one between Door_Open and Door_Closed, we set it to false.

![image](https://user-images.githubusercontent.com/79841064/205901250-641de0b9-f057-4b71-9e2e-3cf886798db3.png)

## 3. Writing the script

First we will need