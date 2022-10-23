![](../images/line3.png)

### Double Jump II

<sub>[previous](../double-jump/README.md#user-content-double-jump) • [home](../README.md#user-content-ue4-animations) • [next](../ramps/README.md#user-content-speed-up--down-ramps)</sub>

![](../images/line3.png)

Finish setting up the double jump ability to the player. 

<br>

---


##### `Step 1.`\|`ITA`|:small_blue_diamond:

Now lets set pressed jump to true for the first jump and reset the double jump in case it is true.  So drag a **Set Pressed Jump** and **Set Pressed Double Jump** to the right of the **Branch** node.  Set **Pressed Jump** to `true` and **Pressed Double Jump** to `false`. Connect them both to the **Branch | True** execution pin.

![delete print string nodes](images/setPressedDoubleFalse.png)

![](../images/line2.png)

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

Drag off the **Jump Count** pin and select a **==** node.  This will now check to see if it is the second jump so set the second pin in the **==** node to `2`. This will run when we are at the second jump.

![delete print string nodes](images/checkSecondJump.png)

![](../images/line2.png)

##### `Step 3.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Pull off the second **==** nodes and select a new **Branch** node.  Connect it to the **Branch | False** pin from the first jump.

![duplicate pressed jump](images/secondBranch.png)

![](../images/line2.png)

##### `Step 4.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Add* a **Set Pressed Double Jump** and set it to `true`.  Then add a **Set Pressed Jump** and set it to `false`. Connect both of them to the second **Branch** true node on the second jump.

![add is double jumping node](images/connectPins.png)

![](../images/line2.png)

##### `Step 5.`\|`ITA`| :small_orange_diamond:

*Pull off* the **As BP_AJ** pin and select a **Set Jump Count** node and make it `3`.  Otherwise the player will keep spinning in the second jump spin.  This resets it so it doesn't call any jumping again until the player lands on the ground. Connect the **Execution** pin to the **Set Pressed Jump** node.

![add set pressed double jump node](images/setJumpCountTo3.png)

![](../images/line2.png)

##### `Step 6.`\|`ITA`| :small_orange_diamond: :small_blue_diamond:

Now after the jump count is set to `3` we then set both **Pressed Jump** and **Pressed Double Jump** to false.  Add one more **Set Pressed Jump** and **Set Pressed Double Jump** to `false`.  Connect to the **Branch | False** pin from the second jump.

![connect set pressed jump to set pressed double jump](images/addFinalSettings.png)

![](../images/line2.png)

##### `Step 7.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Go to the **Anim Graph | Core Locomotion** screen. To the right of the **Fall** node right click and select **Add State**.

![add state to anim graph](images/addState.png)

![](../images/line2.png)

##### `Step 8.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Call* this new state `Double Jump`.

![call state Double Jump](images/CallItDoubleJumpState.png)

![](../images/line2.png)

##### `Step 9.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Connect* the **Double Jump** node to and from the **Falling** node. We are double jumping while in the **Falling** state. *Double click* on the **Double Jump** node to assign the animation to this state.

![connect double jump to falling](images/AddLinkToAndFromDoubleJump.png)

![](../images/line2.png)

##### `Step 10.`\|`ITA`| :large_blue_diamond:

Drag and drop the **Double Jump** animation onto the animation graph.

![add double jump to anim graph](images/PlayDoubleJump.png)

![](../images/line2.png)

##### `Step 11.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: 

*Connect* the **Play Double Jump** node to the **Final Animation Pose**.

![connect double jump animation](images/ConnectDoubleJumpAnim.png)

![](../images/line2.png)


##### `Step 12.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

*Double click* the transition from the **Falling** node to the **Double Jump** node.

![open falling to double jump state](images/DoubleClickFallingToDoubleJump.png)

![](../images/line2.png)

##### `Step 13.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

*Drag and drop* a **Get Pressed Double Jump** node onto the graph.

![add Get Pressed Double Jump node](images/PressedDoubleJumpDragAndDrop.png)

![](../images/line2.png)

##### `Step 14.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Connect the **Pressed Double Jump** node to the **Can Enter Transition** node. This will be triggered when in air and the **Pressed Double Jump** node is true.

![connect pressed double jump to can enter transition](images/ConnectJumpToTransition.png)

![](../images/line2.png)

##### `Step 15.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: 

Go back to the **Core Locomotion** screen. *Double click* on the **Double Jump to Falling** transition button. *Right click* on the graph and select a **Time Remaining (ratio) (Double Jump)** node.

![go to double jump to falling transition and add a Time Remaining (ratio) node](images/DoubleJumpToFallingTrans.jpg)

![](../images/line2.png)

##### `Step 16.`\|`ITA`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

*Pull off* of the **Return Value** from this node and select a **float <= float** node:

![add <= float node](images/PullOffLessThan.jpg)

![](../images/line2.png)

##### `Step 17.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Set the value in the **<=** node to `0.2` and *connect* the output to the **Result** node.

![set <= to 0.2](images/LessThanPointOne.jpg)

![](../images/line2.png)

##### `Step 18.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

One thing we haven't done is turn off the double jump state. If we run the game the player will just keep rolling. Go back to the **BP_AJ_Character** blueprint and go to the **Event Graph**. *Pull off* of the **Set Is Double Jumping** node's execution pin and add a **Delay** node.

![add delay not to AJ_Character bp](images/DelayAfterDoubleJump.jpg)

![](../images/line2.png)

##### `Step 19.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Set the **Duration** of the **Delay** node to `0.1`. *Pull off* of the **Execution** pin and add a **Set Is Double Jumping** node and make sure it is set to `false`.

![set delay to .1 and add set is double jumping node](images/IsJumpingFalse.jpg)

![](../images/line2.png)

##### `Step 20.`\|`ITA`| :large_blue_diamond: :large_blue_diamond:

*Run* the game and a double jump animation should now run during the second jump.Select the **File | Save All** then press the <kbd>Source Control</kbd> button and select **Submit to Source Control...**. Enter a **Changelist Description** and then press <kbd>Submit</kbd>. Open up **GitHub Desktop** and select **Push origin** to update the server with the latest changes.

https://user-images.githubusercontent.com/5504953/133079769-07e7d1f1-2ae2-4cb1-bb11-9be5d719a054.mp4

![save, commit and push to github](images/GitHub.png)
___


![](../images/line1.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Speed Up / Down Ramps"> -->
![next up next tile](images/banner.png)

![](../images/line1.png)

| [previous](../double-jump/README.md#user-content-double-jump)| [home](../README.md#user-content-ue4-animations) | [next](../ramps/README.md#user-content-speed-up--down-ramps)|
|---|---|---|
