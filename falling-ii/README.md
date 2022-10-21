![](../images/line3.png)

### Falling Animation II

<sub>[previous](../falling/README.md#user-content-falling-animation) • [home](../README.md#user-content-ue4-animations) • [next](../jumping/README.md#user-content-jumping-animation)</sub>

![](../images/line3.png)

Falling animation continued...

<br>

---


##### `Step 1.`\|`ITA`|:small_blue_diamond:

Attach the two only pins in this graph.

ADD SCREENSHOT 

![attach pins for falling](images/ADD SCREENSHOT.jpg)

![](../images/line2.png)

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

Lets put the animation inside the falling state. *Double click* the **Falling** state node.

![double click falling state](images/DoubleClickFallingState.png)

![](../images/line2.png)

##### `Step 3.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Drag and drop* the **Falling_Loop** animation onto the graph. *Connect* the animation pins together.

![add falling loop and connect animation pins](images/PlayFallingLoopAnim.png)

![](../images/line2.png)

##### `Step 4.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Go back to the **Anim Graph | Core Locomotion** screen and *double click* the transition button between **Falling** and **Landing** state nodes:

![enter falling to falling end state](images/FallingToFallingEndTransition.png)

![](../images/line2.png)

##### `Step 5.`\|`ITA`| :small_orange_diamond:

We switch to this animation when we hit the ground. *Drag* a **Get Are We in Air** node to the graph.

![drag a get are we in air variable to graph](images/GetAreWeInAirNOT.png)

![](../images/line2.png)

##### `Step 6.`\|`ITA`| :small_orange_diamond: :small_blue_diamond:

*Pull off* of the **Are We in Air?** node and select a **NOT Boolean** node as we want to find out if the player is not in the air.

![add NOT node](images/PullOffNOTBool.png)

![](../images/line2.png)

##### `Step 7.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Connect the output of the **NOT** node to the **Result** node.

![connect NOT to Result node](images/ConnectNotToEnterTransition.png)

![](../images/line2.png)

##### `Step 8.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Lets assign the falling end animation. Go back to the **Anim Graph | CBasicore Locomotiion** screen and *double left-click* on **Landing**.

![go to falling end animation in core locomotion](images/DoubleClickFallingEnd.png)

![](../images/line2.png)

##### `Step 9.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Drag and drop* the **FallingToLanding** animation onto the graph. *Connect* the animation pin to the **Output Animation Pose**.

![add falling to landing animatoin and connect pin](images/FallingToLandingConnectAnim.png)

![](../images/line2.png)

##### `Step 10.`\|`ITA`| :large_blue_diamond:

*Double click* on the transition button from **Landing** to **IdleWalkRun**.

![go to falling end to idlewalkrun transition](images/DoubleClickTransitionToEnd.png)

![](../images/line2.png)

##### `Step 11.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: 

We want this animation to play once then blend back to the **IdleWalkRun** state. There is a node for this. *Right click* on the graph and select a **Time Remaining (ratio)(FallingToLanding)** node.

![add Time Remaining (ratio)(Falling_To_Landing) node](images/TimeRemainingRatioFallEnd.png)

![](../images/line2.png)


##### `Step 12.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

*Pull off* of the **Return Value** pin from the **Time Remaining** node and select a **<** node. Set the bottom value for the **<=** node to `0.2`. Then *connect* the output to the input of the **Result** node. Why do we start the transition with 20% left?  Because we need room to blend out of this animation into the next (overlap).

![add a less or equal node](images/LessEqualTimeRemaining.png)

![](../images/line2.png)

##### `Step 13.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

*Run* the game and the player should fall on the cube. Walk off the cube and the player should fall on the floor. We should have our states working correctly for falling. Now the only issue is that it is jerky at the end the blend is not working properly.  It is either getting cut off or is not long enough.

https://user-images.githubusercontent.com/5504953/197184951-0242aace-dfa2-4b7d-97ff-100400cfcf7f.mp4

![](../images/line2.png)

##### `Step 14.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

It takes too long to blend from landing back to running again.  Look at **FallingToLanding** and scrub in the timeline to pick a better blend point.  I think about half way through might be best.

![add a less or equal node](images/lookAtBlend.png)

![](../images/line2.png)

##### `Step 15.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: 


*Double click*  on the transition from **Landing** to **IdleWalkRun** on the transition and change the value in the **<** node to `0.5` to start blend at 50% complete (roughly a quarter second left in anim at this point).

![adjust falling to landing blends](images/AdjustBlend.png)

![](../images/line2.png)

##### `Step 16.`\|`ITA`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

*Run* the game and the player should fall on the floor and the blend works perfectly!

![](../images/line2.png)

##### `Step 17.`\|`ITA`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: :small_blue_diamond: 


![](../images/line2.png)

##### `Step 18.`\|`ITA`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: 


![](../images/line2.png)

##### `Step 19.`\|`ITA`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: 



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




