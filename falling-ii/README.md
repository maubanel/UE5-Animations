![](../images/line3.png)

### Falling Animation II

<sub>[previous](../falling/README.md#user-content-falling-animation) • [home](../README.md#user-content-ue4-animations) • [next](../jumping/README.md#user-content-jumping-animation)</sub>

![](../images/line3.png)

Falling animation continued...

<br>

---


##### `Step 1.`\|`ITA`|:small_blue_diamond:

Attach the two only pins in this graph.

![attach pins for falling](images/AttachPinsForFalling.jpg)

![](../images/line2.png)

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

Lets put the animation inside the falling state. *Double click* the **Falling** state node.

![double click falling state](images/DoubleClickFallingState.png)

![](../images/line2.png)

##### `Step 3.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Drag and drop* the **Falling_Loop** animation onto the graph. *Connect* the animation pins together.

![add falling loop and connect animation pins](images/PlayFallingLoopAnim.jpg)

![](../images/line2.png)

##### `Step 4.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Go back to the **Anim Graph | Core Locomotion** screen and *double click* the transition button between **Falling** and **Falling End** state nodes:

![enter falling to falling end state](images/FallingToFallingEndTransition.jpg)

![](../images/line2.png)

##### `Step 5.`\|`ITA`| :small_orange_diamond:

We switch to this animation when we hit the ground. *Drag* a **Get Are We in Air?** node to the graph.

![drag a get are we in air variable to graph](images/GetAreWeInAirNOT.jpg)

![](../images/line2.png)

##### `Step 6.`\|`ITA`| :small_orange_diamond: :small_blue_diamond:

*Pull off* of the **Are We in Air?** node and select a **NOT Boolean** node as we want to find out if the player is not in the air.

![add NOT node](images/PullOffNOTBool.jpg)

![](../images/line2.png)

##### `Step 7.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Connect the output of the **NOT** node to the **Result** node.

![connect NOT to Result node](images/ConnectNotToEnterTransition.jpg)

![](../images/line2.png)

##### `Step 8.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Lets assign the falling end animation. Go back to the **Anim Graph | Core Locomotiion** screen and *double left-click* on **Falling End**.

![go to falling end animation in core locomotion](images/DoubleClickFallingEnd.jpg)

![](../images/line2.png)

##### `Step 9.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Drag and drop* the **Falling_To_Landing** animation onto the graph. *Connect* the animation pin to the **Output Animation Pose**.

![add falling to landing animatoin and connect pin](images/FallingToLandingConnectAnim.jpg)

![](../images/line2.png)

##### `Step 10.`\|`ITA`| :large_blue_diamond:

*Double click* on the transition button from **Falling End** to **IdleWalkRun**.

![go to falling end to idlewalkrun transition](images/DoubleClickTransitionToEnd.jpg)

![](../images/line2.png)

##### `Step 11.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: 

We want this animation to play once then blend back to the **IdleWalkRun** state. There is a node for this. *Right click* on the graph and select a **Time Remaining (ratio)(Falling_To_Landing)** node.

![add Time Remaining (ratio)(Falling_To_Landing) node](images/TimeRemainingRatioFallEnd.jpg)

![](../images/line2.png)


##### `Step 12.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

*Pull off* of the **Return Value** pin from the **Time Remaining** node and select a **<=** node:

![add a less or equal node](images/LessEqualTimeRemaining.jpg)

![](../images/line2.png)

##### `Step 13.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Set the bottom value for the **<=** node to `0.2`. Then *connect* the output to the input of the **Result** node. Why do we start the transition with 20% left?  Because we need room to blend out of this animation into the next (overlap).

![set bottom value of <= to .2](images/LessThanPointSevenFive.png)

![](../images/line2.png)

##### `Step 14.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Go back to the game editor and select the **Floor** object in the **World Outliner**. Copy it multiple times to create a **6 x 6** grid centered in the world.  You should have 36 ground pieces.  Put them in a folder called `Ground` and lock them in place by turning on **Transform | Lock Actor Movement**.

![scale floor by 10](images/MakeFloorBigger.png)

![](../images/line2.png)

##### `Step 15.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: 

Add a cube under the **Player Start** so that the player will land on the cube. Scale the cube to`3.0` to triple its size. Raise the **Player Start** so it is above this platform.

![add cube under player start in level](images/AddCubeUnderPlayerStart.jpg)

![](../images/line2.png)

##### `Step 16.`\|`ITA`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

*Run* the game and the player should fall on the cube. Walk off the cube and the player should fall on the floor. We should have our states working correctly for falling. Now the only issue is that it is jerky at the end the blend is not working properly.  It is either getting cut off or is not long enough.

https://user-images.githubusercontent.com/5504953/135755418-1e18c62b-d315-4f3e-a452-ef280803120b.mp4

![](../images/line2.png)

##### `Step 17.`\|`ITA`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: :small_blue_diamond: 

So open up the **Falling_To_Landing** animation and scroll to the end.  You will see that is is **16** frames long or **0.53** seconds (remember we exported these animations from Mixamo at 30 FPS).  So we should start the blend at about half way (.5) and blend for .25 seconds.

![falling to landing is wrong](images/FallingToLanding.png)

![](../images/line2.png)

##### `Step 18.`\|`ITA`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

Click on the tarnsition from **Falling End** to **IdleWalkRun** and change the **Details | Duration** to `0.25` to increase the blend time to a quarter of a second.  *Double click* on the transition and change the value in the **<** node to `0.5` to start blend at 50% complete (roughly a quarter second left in anim at this point).

![adjust falling to landing blends](images/AdjustBlend.png)

![](../images/line2.png)

##### `Step 19.`\|`ITA`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

*Run* the game and the player should fall on the floor and the blend works perfectly!

https://user-images.githubusercontent.com/5504953/135755444-752e994b-c9e0-4aed-89d1-3ec14d008eae.mp4

![](../images/line2.png)

##### `Step 20.`\|`ITA`| :large_blue_diamond: :large_blue_diamond:

Press **Save All** and update **Github** by **committing** and **pushing** all the changes made. Next up we will be adding jumping to the game.

![save, commit and push to github](images/GitHub.png)
___


![](../images/line1.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Jumping Animation"> -->
![next up next tile](images/banner.png)

![](../images/line1.png)

| [previous](../falling/README.md#user-content-falling-animation)| [home](../README.md#user-content-ue4-animations) | [next](../jumping/README.md#user-content-jumping-animation)|
|---|---|---|




