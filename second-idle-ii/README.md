<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

### Time Out for Second Idle II

<sub>[previous](../second-idle/README.md#user-content-time-out-for-second-idle) • [home](../README.md#user-content-ue4-animations) • [next](../falling/README.md#user-content-falling-animation)</sub>

<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

Second idle continued...

<br>

---


##### `Step 1.`\|`ITA`|:small_blue_diamond:

*Connect* the output of the **NOT** node to the **Can Enter Transition** pin in the **Result** node.

![conect not to can enter transition node](images/OutputOfNotToTransition.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

Go back to the **Core Locomotion** state tab. Now we have dealt with the transitions but not the actual animation in this new state. *Double click* the **Alternate Idle** node.

![enter alternate idle graph](images/CoreLocomotionToAlternateIdle.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 3.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Drag a reference to **Idle_Fidget** to the open graph.

![add idle_fidget to graph](images/PlayIdleFidget.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 4.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

**Connect** the animation pins and then *press* the <kbd>Compile</kbd> button. That should do it for the animation blueprint.

![connect animation pins and compile](images/ConnectAnimationPinsAlternateIdle.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 5.`\|`ITA`| :small_orange_diamond:

Now go into the game. After 5 seconds the player should go to the alternate idle. But he/she never leaves this state. We now want to reset the Does Idle Time Out? variable back to false. We need to do this at the end of the alternate animation. We can this using **Notifies**. Open **Idle_Fidget** animation.

![enter idle never leaves the state](images/IdleFidgetPre.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 6.`\|`ITA`| :small_orange_diamond: :small_blue_diamond:

Right click on the **Notifies** timeline near the end and select **Add Notify | New Notify**.

![add notify](images/AddNotifyToIdleTimeline.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 7.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

A box will pop up asking you to enter the **Notify** Name. *Enter* `EndAnim` and press the <kbd>Enter</kbd> key.

![call notify endanim](images/NameNotifyEndAnim.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 8.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Adjust the position after the core movement ends but with room to blend it back to the core idle. I set it at the 80<sup>th</sup> frame.

![call from frame 80](images/GiveItRoomToBlend.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 9.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Go back to the **AJ_AnimBlueprint | Event Graph** and lets add some logic for when this notify event triggers. *Right clic*k on the open graph and select a **Event AnimNotify_EndAnim** node. It should be red with an execution pin.

![add event AnimNotify_EndAnim node to anim blueprint](images/EndAnimAnimEvent.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 10.`\|`ITA`| :large_blue_diamond:

Pull off of the **EndAnim** pin and select a **Set Idle Time Out?** node and set it to `false`. *Pull off* this execution pin and select **Set Idle Timer** and set it to `0.0`.

![add set idle time out and set to false and add set idle timer node set at 0](images/ResetVariables.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 11.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: 

Now add a **comment** around these nodes that says `Reset Idle Timer`. *Press* the <kbe>Compile</kbd> button.

![add comment and compile](images/AddCommentCompile.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>


##### `Step 12.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

We have done enough to test our work. Play the game and move the character then let go of the controls. Let the character idle and see if the idle animation plays. Then make sure it goes back to the normal idle. After playing around there is a clear issue with trying to move while in the alternate idle. It is not switching back to our normal blend IdleWalkRun animation when branching from this state.

https://user-images.githubusercontent.com/5504953/132986162-d782c87f-f7fe-4d03-b94b-6197fbd6dd4a.mp4

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 13.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Now go back to the **aj_AnimBlueprint** to its **Event Graph** tab. Look to see the **Branch** node where we check to see if the **Vector Length** is close to `0.0.` We do not set the **Does Idle Time Out** node back to false. **Add** a **Set Does Idle Time Out?** node to the right of the **Set Idle Timer** node.

![add set does idle time out node to anim blueprint](images/DoesIdleTimeWaitFalse.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 14.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

*Connect* the execution pin from **Set Idle Timer** to **Set Does Idle Time Out?** node.

![connect set idle timer to set does idle time out](images/ConnectTwoSetExecutionPins.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 15.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: 

*Play* the game and transition from the alternate idle. It now snaps back to the regular IdleWalkRun blend sequence. This works great. I don't like the snap back to the idle though and it is rough and jerky. We need to add a bit of a blend here.

https://user-images.githubusercontent.com/5504953/132986290-d633e829-b132-4fec-8d5a-01e9423504ea.mp4

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 16.`\|`ITA`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

Open the **IdleWalkRun_BlendSpace** file and go to the **Asset Details** panel to the **Sample Interpolation | Target Weight Interpolation** setting and *adjust* it to `6.0` (you can play with values between 5 and 10 to see what you like). Now it should be much smoother. Press **Save All** and update **Github** by committing and pushing all the changes made. Next up we will be adding a falling animation.


___


<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

<img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Falling Animation">

<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

| [previous](../second-idle/README.md#user-content-time-out-for-second-idle)| [home](../README.md#user-content-ue4-animations) | [next](../falling/README.md#user-content-falling-animation)|
|---|---|---|
