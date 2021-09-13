<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

### Double Jump II

<sub>[previous](../double-jump/README.md#user-content-double-jump) • [home](../README.md#user-content-ue4-animations) • [next](../ramps/README.md#user-content-speed-up--down-ramps)</sub>

<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

Finish setting up the double jump ability to the player.

<br>

---


##### `Step 1.`\|`ITA`|:small_blue_diamond:

Play the game and you should now be able to double jump and the text should reflect the correct state. Next up we will add the animation of the player rolling.

https://user-images.githubusercontent.com/5504953/133078025-b828a1e1-b9a0-49da-8a9e-7413e951ffee.mp4

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

When you have the double jump physics working you can delete the two **Print String** nodes.

![delete print string nodes](images/DeletePrintStringWhenDoubleJumpDone.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 3.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Open* to the **bj_AnimBlueprint** and go to the **Event Graph**. *Duplicate* the **Pressed Jump** variable. Call it `bPressedDoubleJump`.

![duplicate pressed jump](images/DuplicatePressedJumpNode.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 4.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Go to the **Set Is Jumpin**g Section. Pull the As **BP_AJ_Character** pin and select a **Get Is Double Jumping** node.

![add is double jumping node](images/SetDoubleJumpVariableAnimBP.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 5.`\|`ITA`| :small_orange_diamond:

*Drag and drop* a **Set Pressed Double Jump** node. *Connect* it to the **Is Double Jumping** pin.

![add set pressed double jump node](images/SetIsDoubleJump.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 6.`\|`ITA`| :small_orange_diamond: :small_blue_diamond:

*Connect* the execution pin from the **Set Pressed Jump** node to the **Set Pressed Double Jump** node.

![connect set pressed jump to set pressed double jump](images/ConnectExecuteDoubleJumpIs.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 7.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Go to the **Anim Graph | Core Locomotion** screen. To the right of the **Fall** node right click and select **Add State**.

![add state to anim graph](images/AddStateForDoubleJump.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 8.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Call* this new state `Double Jump`.

![call state Double Jump](images/CallItDoubleJumpState.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 9.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Connect* the **Double Jump** node to and from the **Falling** node. We are double jumping while in the **Falling** state. *Double click* on the **Double Jump** node to assign the animation to this state.

![connect double jump to falling](images/AddLinkToAndFromDoubleJump.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 10.`\|`ITA`| :large_blue_diamond:

Drag and drop the **Double Jump** animation onto the animation graph.

![add double jump to anim graph](images/PlayDoubleJump.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 11.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: 

*Connect* the **Play Double Jump** node to the **Final Animation Pose**.

![connect double jump animation](images/ConnectDoubleJumpAnim.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>


##### `Step 12.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

*Double click* the transition from the **Falling** node to the **Double Jump** node.

![open falling to double jump state](images/DoubleClickFallingToDoubleJump.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 13.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

*Drag and drop* a **Get Pressed Double Jump** node onto the graph.

![add Get Pressed Double Jump node](images/PressedDoubleJumpDragAndDrop.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 14.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Connect the **Pressed Double Jump** node to the **Can Enter Transition** node. This will be triggered when in air and the **Pressed Double Jump** node is true.

![connect pressed double jump to can enter transition](images/ConnectJumpToTransition.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 15.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: 

Go back to the **Core Locomotion** screen. *Double click* on the **Double Jump to Falling** transition button. *Right click* on the graph and select a **Time Remaining (ratio) (Double Jump)** node.

![go to double jump to falling transition and add a Time Remaining (ratio) node](images/DoubleJumpToFallingTrans.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 16.`\|`ITA`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

*Pull off* of the **Return Value** from this node and select a **float <= float** node:

![add <= float node](images/PullOffLessThan.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 17.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Set the value in the **<=** node to `0.2` and *connect* the output to the **Result** node.

![set <= to 0.2](images/LessThanPointOne.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 18.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

One thing we haven't done is turn off the double jump state. If we run the game the player will just keep rolling. Go back to the **BP_AJ_Character** blueprint and go to the **Event Graph**. *Pull off* of the **Set Is Double Jumping** node's execution pin and add a **Delay** node.

![add delay not to AJ_Character bp](images/DelayAfterDoubleJump.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 19.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Set the **Duration** of the **Delay** node to `0.1`. *Pull off* of the **Execution** pin and add a **Set Is Double Jumping** node and make sure it is set to `false`.

![set delay to .1 and add set is double jumping node](images/IsJumpingFalse.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 20.`\|`ITA`| :large_blue_diamond: :large_blue_diamond:

*Run* the game and a double jump animation should now run during the second jump. Press Save All and update Github by committing and pushing all the changes made.

https://user-images.githubusercontent.com/5504953/133079769-07e7d1f1-2ae2-4cb1-bb11-9be5d719a054.mp4

___


<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

<img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Speed Up / Down Ramps">

<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

| [previous](../double-jump/README.md#user-content-double-jump)| [home](../README.md#user-content-ue4-animations) | [next](../ramps/README.md#user-content-speed-up--down-ramps)|
|---|---|---|
