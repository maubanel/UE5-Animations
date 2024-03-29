![](../images/line3.png)

### Falling Animation

<sub>[previous](../second-idle-ii/README.md#user-content-time-out-for-second-idle-ii) • [home](../README.md#user-content-ue4-animations) • [next](../falling-ii/README.md#user-content-falling-animation-ii)</sub>

![](../images/line3.png)

Lets add an animation for when the player is falling to our movement state machine for when the player falls off the edge of a surface.

<br>

---

##### `Step 1.`\|`ITA`|:small_blue_diamond:

Lets go back to [Mixamo](https://www.mixamo.com/#/) and look for some more animations. I am looking for a looping falling animation and for hitting the ground (after falling). Select the character you are using then search for these two animations. First pick the looping falling and make the appropriate adjustments. *Click* the **Download** button.

![go to mixamo and download loop falling animation](images/LoopingFalling.jpg)

![](../images/line2.png)

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

*Download* just the animation with the default settings. *Set* **Skin** to `Without Skin` to avoid bringing in any geometry. *Press* the <kbd>Download</kbd> button again.

![download falling animation without skin](images/DownloadJustAnimationFall.jpg)

![](../images/line2.png)

##### `Step 3.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

I also found an animation from falling to hitting the ground. I sped up the animation as I didn't want it to interupt gameplay too much so I cranked up the **Overdrive**. On the next menu it should be the same settings as previously so you can verify this then *press* <kbd>Download</kbd> again.

![download falling hitting ground anim](images/FallingToLanding.jpg)

![](../images/line2.png)

##### `Step 4.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Go back to the game and go to the **AJ | Animations** folder and *press* the <kbd>Add/Import</kbd> button and *select* these two animations you just downloaded. In the **FBX Import Options** overlay, make sure you select the skeleton you have been using. Then press the <kbd>Import All</kbd> button.

![import animations into unreal](images/ImportFallingAnimation.png)

![](../images/line2.png)

##### `Step 5.`\|`ITA`| :small_orange_diamond:

*Preview* the animations in the editor. *Name* them accordingly. I named them `Falling_Loop` and `Landing`.

![rename animations](images/RenameAndPreviewAnims.png)

![](../images/line2.png)

##### `Step 6.`\|`ITA`| :small_orange_diamond: :small_blue_diamond:

Open the **AnimBP_AJ** animation blueprint and go to the **Anim Graph | Basic Locomotion** tab. *Right click* on the area and add an **Add State** button. Call this new state `Falling`. 

![press add state button in ainmation blueprint](images/AddFallingState.png)

![](../images/line2.png)

##### `Step 7.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

*Right click* again and select another **Add State** node. *Call* this new state `Landing`.

![call state falling and add new state](images/CallItFallingAddAnotherState.png)


![](../images/line2.png)

##### `Step 8.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now we need a boolean to track when we are on the ground or in the air. Add a new **Boolean** Variable and call it `AreWeInAir`. *Make* it **Private** and set the **Tooltip** to `True when player is not on the ground`. Set the **Category** to `Player Physics`.

![add are we in air boolean variable](images/AreWeInAirBooleanDef.png)

![](../images/line2.png)

##### `Step 9.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Go to the **Event Graph** tab and make some space between the **Sequence** node and the **Get Ground Speed** nodes to check to see if we are in air.

![add space to nodes](images/MakeSpaceEventGraphAnimBP.png)

![](../images/line2.png)

##### `Step 10.`\|`ITA`| :large_blue_diamond:

*Drag* a get **Character Movement** variable to the graph. *Pull off* of the **Return Value** pin from the **Movement Component** and select the **IsFalling** node.

![add isfalling node](images/IsFallingVariableGet.png)


![](../images/line2.png)

##### `Step 11.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: 

*Drag* the **Set Are We In Air** variable onto the graph. Connect the **Return Value** pin from the **Is Falling** node to the **Set Are We In Air** node. *Hijack* the execution pin from **Sequence | Then 0** node and *send it* to the **Set Are We In Air** node.  Take the output execution pin from **Set Are We in Air** node to the **Set Speed** node. Select the new nodes and make a **comment** `Set In Air`.

![add set are we in air node](images/SetAreWeInAir.png)

![](../images/line2.png)

##### `Step 12.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

Go back to the **Anim Graph | BasicLocomotion** screen. *Connect* the **IdleWalkRun** state to the **Falling** state to the **Landing** state *back* to the **IdleWalkRun**. This only goes in the single direction.

![connect idlewalkrun to falling to falling end back to idlewalkrun in core locomotion in anim graph](images/ConnectFallingStates.png)

![](../images/line2.png)

##### `Step 13.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Double click the transition from **IdleWalkRun** to **Falling**.

![go to idlewalkrun to falling transition](images/ConditionToFalling.png)

![](../images/line2.png)

##### `Step 14.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

*Drag and drop* the **Get Are We In Air** variable onto the graph. Attach the two only pins in this graph.

![add get are we in air node](images/AreWeInAirGetTransition.png)

![](../images/line2.png)

##### `Step 15.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: 

Lets put the animation inside the falling state. *Double click* the **Falling** state node. *Drag and drop* the **Falling_Loop** animation onto the graph. 

![double click falling state](images/DoubleClickFallingState.png)

![](../images/line2.png)

##### `Step 16.`\|`ITA`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

*Connect* the animation pins together.

![add falling loop and connect animation pins](images/PlayFallingLoopAnim.png)

![](../images/line2.png)

##### `Step 17.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Go back to the **Anim Graph | Core Locomotion** screen and *double click* the transition button between **Falling** and **Landing** state nodes. We switch to this animation when we hit the ground. *Drag* a **Get Are We in Air** node to the graph. *Pull off* of the **Are We in Air?** node and select a **NOT Boolean** node as we want to find out if the player is not in the air.

![enter falling to falling end state](images/FallingToFallingEndTransition.png)

![](../images/line2.png)

##### `Step 18.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Connect the output of the **NOT** node to the **Result** node.

![connect NOT to Result node](images/ConnectNotToEnterTransition.png)

![](../images/line2.png)

##### `Step 19.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Lets assign the falling end animation. Go back to the **Anim Graph | CBasicore Locomotiion** screen and *double left-click* on **Landing**. *Drag and drop* the **Landing** animation onto the graph. *Connect* the animation pin to the **Output Animation Pose**.

![go to falling end animation in core locomotion](images/DoubleClickFallingEnd.png)

![](../images/line2.png)

##### `Step 20.`\|`ITA`| :large_blue_diamond: :large_blue_diamond:

*Double click* on the transition button from **Landing** to **IdleWalkRun**. We want this animation to play once then blend back to the **IdleWalkRun** state. There is a node for this. *Right click* on the graph and select a **Time Remaining (ratio)(FallingToLanding)** node.

![go to falling end to idlewalkrun transition](images/DoubleClickTransitionToEnd.png)

![](../images/line2.png)

##### `Step 21.`\|`ITA`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond:

*Pull off* of the **Return Value** pin from the **Time Remaining** node and select a **<** node. Set the bottom value for the **<=** node to `0.2`. Then *connect* the output to the input of the **Result** node. Why do we start the transition with 20% left?  Because we need room to blend out of this animation into the next (overlap).

![add a less or equal node](images/LessEqualTimeRemaining.png)

___


![](../images/line1.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Falling Animation II"> -->
![next up next tile](images/banner.png)

![](../images/line1.png)

| [previous](../second-idle-ii/README.md#user-content-time-out-for-second-idle-ii)| [home](../README.md#user-content-ue4-animations) | [next](../falling-ii/README.md#user-content-falling-animation-ii)|
|---|---|---|
