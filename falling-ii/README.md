<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

### Falling Animation II

<sub>[previous](../falling/README.md#user-content-falling-animation) • [home](../README.md#user-content-ue4-animations) • [next](../jumping/README.md#user-content-jumping-animation)</sub>

<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

Falling animation continued...

<br>

---


##### `Step 1.`\|`ITA`|:small_blue_diamond:

Attach the two only pins in this graph.

![attach pins for falling](images/AttachPinsForFalling.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

Lets put the animation inside the falling state. *Double click* the **Falling** state node.

![double click falling state](images/DoubleClickFallingState.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 3.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Drag and drop* the **Falling_Loop** animation onto the graph. *Connect* the animation pins together.

![add falling loop and connect animation pins](images/PlayFallingLoopAnim.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 4.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Go back to the **Anim Graph | Core Locomotion** screen and *double click* the transition button between **Falling** and **Falling End** state nodes:

![enter falling to falling end state](images/FallingToFallingEndTransition.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 5.`\|`ITA`| :small_orange_diamond:

We switch to this animation when we hit the ground. *Drag* a **Get Are We in Air?** node to the graph.

![drag a get are we in air variable to graph](images/GetAreWeInAirNOT.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 6.`\|`ITA`| :small_orange_diamond: :small_blue_diamond:

*Pull off* of the **Are We in Air?** node and select a **NOT Boolean** node as we want to find out if the player is not in the air.

![add NOT node](images/PullOffNOTBool.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 7.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Connect the output of the **NOT** node to the **Result** node.

![connect NOT to Result node](images/ConnectNotToEnterTransition.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 8.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Lets assign the falling end animation. Go back to the **Anim Graph | Core Locomotiion** screen and *double left-click* on **Falling End**.

![go to falling end animation in core locomotion](images/DoubleClickFallingEnd.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 9.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Drag and drop* the **Falling_To_Landing** animation onto the graph. *Connect* the animation pin to the **Output Animation Pose**.

![add falling to landing animatoin and connect pin](images/FallingToLandingConnectAnim.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 10.`\|`ITA`| :large_blue_diamond:

*Double click* on the transition button from **Falling End** to **IdleWalkRun**.

![go to falling end to idlewalkrun transition](images/DoubleClickTransitionToEnd.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 11.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: 

We want this animation to play once then blend back to the **IdleWalkRun** state. There is a node for this. *Right click* on the graph and select a **Time Remaining (ratio)(Falling_To_Landing)** node.

![add Time Remaining (ratio)(Falling_To_Landing) node](images/TimeRemainingRatioFallEnd.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>


##### `Step 12.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

*Pull off* of the **Return Value** pin from the **Time Remaining** node and select a **<=** node:

![add a less or equal node](images/LessEqualTimeRemaining.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 13.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Set the bottom value for the **<=** node to `0.2`. Then *connect* the output to the input of the **Result** node. Why do we start the transition with 20% left?  Because we need room to blend out of this animation into the next (overlap).

![set bottom value of <= to .2](images/LessThanPointSevenFive.png)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 14.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Go back to the game editor and select the **Floor** object in the **World Outliner**. Copy it multiple times to create a **6 x 6** grid centered in the world.  You should have 36 ground pieces.  Put them in a folder called `Ground` and lock them in place by turning on **Transform | Lock Actor Movement**.

![scale floor by 10](images/MakeFloorBigger.png)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 15.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: 

Add a cube under the **Player Start** so that the player will land on the cube. Scale the cube to a size that makes sense to you. Raise the **Player Start** so it is above this platform.

![add cube under player start in level](images/AddCubeUnderPlayerStart.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 16.`\|`ITA`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

*Run* the game and the player should fall on the cube. Walk off the cube and the player should fall on the floor. We should have our states working correctly for falling. Press **Save All** and update **Github** by **committing** and **pushing** all the changes made. Next up we will be adding jumping to the game.

https://user-images.githubusercontent.com/5504953/132987892-ec21b82f-c6eb-4190-a7e7-e52882d3baa4.mp4
___


<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

<img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Jumping Animation">

<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

| [previous](../falling/README.md#user-content-falling-animation)| [home](../README.md#user-content-ue4-animations) | [next](../jumping/README.md#user-content-jumping-animation)|
|---|---|---|
