![](../images/line3.png)

### Double Jump

<sub>[previous](../walk-sprint/README.md#user-content-slow-walk--sprint) • [home](../README.md#user-content-ue4-animations) • [next](../double-jump-ii/README.md#user-content-double-jump-ii)</sub>

![](../images/line3.png)

Since I have downloaded this cartoon character, I would like to implement double jump which is not an option in the character controller. We will have to add this to the game by ourselves. We will do this now.

<br>

---


##### `Step 1.`\|`ITA`|:small_blue_diamond:

Go back to [Mixamo](https://www.mixamo.com/#/) and look for a good animation for a double jump. I am going with a foreward roll. Make sure it is set to **In Place** if there is translation and trim it to just the spin. We don't don't want any foot on ground bits in our final exported animation. **Export** the file without the skin. Just snip only the roll portion so don't include the legs extending or contracting.

https://github.com/maubanel/UE5-Animations/assets/5504953/b6c5a654-92d5-4ac2-9084-c80c95989705

![](../images/line2.png)

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

Download the animation without a skin. *Drag and drop* the animation to the **Animations** folder. In the **FBX Import Options** assign the **Skeleton** that you are using. *Press* the <kbd>Import All</kbd> button. *Call* this animation `Double_Jump`. 

![download double jump animation](images/ImportDoubleJumpAnim3.png)

![](../images/line2.png)

##### `Step 3.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Open **BP_AJ** blueprint and go to the **Jump** section. Click on the top component and select **Character | Jump max Count** to `2`.

![import double jump animation](images/ImportDoubleJumpAnim.png)

![](../images/line2.png)

##### `Step 4.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Press* the <kbd>Play</kbd> button and double jump.  Notice that you double jump but there are no animations.

https://github.com/maubanel/UE5-Animations/assets/5504953/4bb88dc0-c30a-499b-800c-e4d9552576d3

![](../images/line2.png)

##### `Step 5.`\|`ITA`| :small_orange_diamond:

Open up **ABP_AJ** and *delete* the **Print** nodes as we no lnoger need them.  

![add switch on int node and set n to 2](images/disconnectPrint.png)

![](../images/line2.png)

##### `Step 6.`\|`ITA`| :small_orange_diamond: :small_blue_diamond:

In **ABP_AJ** *add* a new **Boolean** vairable called `bIsDoubleJumping`.  Create a tooltip **Description** with `Is player in air?`. Then *set* **Private** to `true` and **Category** to `PlayerPhysics`.

![add double jump var](images/doubleJump.png)

![](../images/line2.png)

##### `Step 7.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Open up **BP_AJ** and lets add a double jump variable to the character blueprint. *Add* a new **Boolean** vairable called `bIsDoubleJumping`.  Create a tooltip **Description** with `Has Player pressed double jump in the air (Double Jumping)`. Then *set* **Private** to `true` and **Category** to `Player States`.

![duplicate bIsJumping](images/playerCount.png)

![](../images/line2.png)

##### `Step 8.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

First thing we want to check if the player is on the ground, if they are they can't double jump.  Drag a reference to the **Character Movement** component.  Drag off of the pin and get the **Is Moving On Ground** node which outputs a yes or no boolean.  Add a **Branch** node and connect the execution pin from the **Jump** to the **Branch** node.  Pull off the execution pin on the **Branch Node** and select a **Sequence** node.  Take the return value of **Is Moving On Ground** and plae it in the **Branch | Condition** input pin.

![duplicate bIsJumping](images/CheckIfOnGround.png)


![](../images/line2.png)

##### `Step 9.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now here comes the tricky part.  We can't use a flip flop node as we don't want more than two jumps. This is where a **MultiGate** node comes in handy.  It will keep counting up until it resets it.  So the first time it is called it will be a jump. (index 0)  The second time a double jump (index 1).  Then it will keep increasing the index but we will do nothing with it.  When the player hits the ground we will reset the node so they can jump again.  Add a **Sequence** node to the graph. So the **Branch | True** pin (which is the player on ground)  will go to a **Seequence** node input.  Add a **MultiGate** node. Then we feed the **Sequence | Then 0** to the **Multi Game | Reset** pin (so the player can jump again).  The **Then 1** goes to the input of the **MultiGate**.  The **Branch | False** pin is when the player is not on the ground and that will get fed into the **MultiGate** as well.

![duplicate bIsJumping](images/multiGate.png)

![](../images/line2.png)

##### `Step 10.`\|`ITA`| :large_blue_diamond:

Now on the first time through it is a jump so we set the **bIsJumping** to `true`.

![duplicate bIsJumping](images/MultiGateOutput.png)

![](../images/line2.png)

##### `Step 11.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: 

Add **Comments** to the print node to clean up the chart.

![disconnect pin from jump node](images/addComments.png)

![](../images/line2.png)


##### `Step 12.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 



![](../images/line2.png)

##### `Step 13.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 



![](../images/line2.png)

##### `Step 14.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

*Drag* a get **Jump Count** to the **Jumping** area.  Make room to add some nodes before the jump function.

![name variable bIsDoubleJumping](images/jumpCountMakeRoom.png)

![](../images/line2.png)

##### `Step 15.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: 

*Drag* off of the **Jump Count** pin and select a **Increment Int** node.  This will add `1` to the interger value.

![connect switch on int to jump node](images/incrementByOne.png)

![](../images/line2.png)

##### `Step 16.`\|`ITA`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

*Highjack* the execution pins from **InputAction Jump** to **++** to **Jump** node.

![highjack execution node](images/highjackExecutionPins.png)

![](../images/line2.png)

##### `Step 17.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Now we do not want to trigger an animation if the jump is pressed three or more times. *Drag* a get **Jump Count**. Select the pin and select a **<=** node.  Set the bottom value to `2`.

![set up set is double jumping](images/lessThan2.png)

![](../images/line2.png)

##### `Step 18.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Pull off* the **<=** pin and select a **Branch** node.  *Highjack* the execution pin from **Jump** to **Branch** and **Branch | True** to **Set | Is Jupming**.  This will only set is jumping tif the count is 2 or less (so the first or second jump).

![set is double jumping to true](images/jumpIfLess2.png)

![](../images/line2.png)

##### `Step 19.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Below the jumping on the falling node.  Switch setting **Is Jumping** to `false` on the **False** node.  This way when we hit the ground we set **Is Jumping** to `false`.  Also add a **Set Jump Count** variable to the chart and set it to `0`.  Connect it from the **Set | Is Jumping** execution pin.

![set jump count to 0](images/resetJumpCount.png)

![](../images/line2.png)

##### `Step 20.`\|`ITA`| :large_blue_diamond: :large_blue_diamond:

Go back to **AnimBP_AJ** and delete all the nodes after **Cast to BP_AJ** node. 

![connect on landed to reset](images/deleteJumpingNodes.png)

![](../images/line2.png)

##### `Step 21.`\|`ITA`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond:

*Drag* off of the **Cast To BP_AJ | As BP_AJ** pin and select **Get Jump Count**. Pull off the **Jump Count** pin and select **==** node and set the check to `1`. This is the first time it is pressed.  *Pull off* the boolean from the **==** node and select a **Branch** node.  Connect the execution pin to the **Cast to BP_AJ** node.

![add a check for one press](images/jumpCountBranch.png)

![](../images/line1.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Double Jump II"> -->
![next up next tile](images/banner.png)

![](../images/line1.png)

| [previous](../walk-sprint/README.md#user-content-slow-walk--sprint)| [home](../README.md#user-content-ue4-animations) | [next](../double-jump-ii/README.md#user-content-double-jump-ii)|
|---|---|---|
