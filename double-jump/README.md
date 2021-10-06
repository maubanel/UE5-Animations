<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

### Double Jump

<sub>[previous](../walk-sprint/README.md#user-content-slow-walk--sprint) • [home](../README.md#user-content-ue4-animations) • [next](../double-jump-ii/README.md#user-content-double-jump-ii)</sub>

<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

Since I have downloaded this cartoon character, I would like to implement double jump which is not an option in the character controller. We will have to add this to the game by ourselves. We will do this now.

<br>

---


##### `Step 1.`\|`ITA`|:small_blue_diamond:

Go back to [Mixamo](https://www.mixamo.com/#/) and look for a good animation for a double jump. I am going with a foreward roll. Make sure it is set to **In Place** if there is translation and trim it to just the spin. We don't don't want any foot on ground bits in our final exported animation. **Export** the file without the skin.

https://user-images.githubusercontent.com/5504953/133075815-ad64f111-a297-4ef0-a9f6-eda8f01a2e3b.mp4

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

Go to the **Animations** folder and press the <kbd>Add/Import</kbd> button. *Select* the latest animation you just downloaded.

![import double jump animation](images/ImportDoubleJumpAnim.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 3.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

In the **FBX Import Options** assign the **Skeleton** that you are using. *Press* the <kbd>Import</kbd> button.

![assign skeleton and import](images/AssignSkeletonToDoubleJumpImport.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 4.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Call* this animation `Double_Jump`. *Double click* it to open it in the editor.

![call animmation Double_Jump and open](images/CallItDoubleJump.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 5.`\|`ITA`| :small_orange_diamond:

Confim that the animation is correct.

https://user-images.githubusercontent.com/5504953/133076270-248aec90-4c4a-48f9-bb38-4e35994bc19d.mp4

![alt_text](images/.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 6.`\|`ITA`| :small_orange_diamond: :small_blue_diamond:

Open **BP_AJ_Character** blueprint and go to the **Jump** section. Make some room in this comment box to add some more nodes for double jumps.

![open up ajcharacter blueprint and go to jump section](images/MakeSpaceInJumpPlayerBP.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 7.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Right click and add a **DoN** node. This node will repeat n number of times. We will set it to two for double jump.

![add a DoN nuode](images/AddDoNNode.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 8.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

We are going to now switch on the integer coming from the **DoN** node. Add a **Switch on Int** node. Set the **N** number to start at `2` as the player will be starting by falling and can't jump at the very begining of pressing play (like they are coming down from a double jump).

![add switch on int node and set n to 2](images/AddSwitchOnIntNode.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 9.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Connect* the **Counter** pin from the **DoN** node to the **Switch on Int** node's **Selection** pin:

![connect Counter to Selection pin](images/CounterToSelectionPin.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 10.`\|`ITA`| :large_blue_diamond:

*Connect* the **DoN** execution pin to the **Switch on Int** node:

![connect DoN to Switch on Int](images/ConnectDoNExecutionPins.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 11.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: 

*Disconnect* the execution pin coming out of the **Jump** node

![disconnect pin from jump node](images/DisconnectExecutionPin.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>


##### `Step 12.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

*Connect* the **Jump** node's execution pin to the **DoN** node.

![connet jump to DoN node](images/ConnectJumpToDoNNode.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 13.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Now we need a variable to know that we have pressed this button. *Right click* on the **bIsJumping** variable and select **Duplicate** to make another copy.

![duplicate bIsJumping](images/DuplicateIsJumpingVariable.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 14.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

*Call* this new Variable `bIsDoubleJumping`.

![name variable bIsDoubleJumping](images/CallItDoubleJumping.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 15.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: 

*Press* the **+** button three times on the **Switch On Int** node. Even though we only need two pins the **DoN** node starts counting at `1` and the **Switch On Int** node starts on `0`. Connect the output pin **1** from the **Switch on Int** node to the **Jump** node:

![connect switch on int to jump node](images/SwitchOnIntToJump.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 16.`\|`ITA`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

*Pull* from the **Switch on Int | 2** node's execution pin and select a **Launch Character** node.

![add a launch character node](images/Pin2ToLaunchCharacter.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 17.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

We want to launch the characer upwards, or positive along the **Z** axis. *Change* the **Launch Velocity | Z** to `700.0`. *Pull off* the execution pin and select **Set Is Double Jumping** variable.

![set up set is double jumping](images/SetDoubleJumping.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 18.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Set the **Is Double Jumping** setting to `true`.

![set is double jumping to true](images/SetIsDoubleJumpingToTrue.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 19.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Right click* under the **Action Event Jump** node and select an **Event On Landed**. This will run when the player lands.

![add event on landed node](images/ResetWhenPlayerLands.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 20.`\|`ITA`| :large_blue_diamond: :large_blue_diamond:

*Connect* the output execution pin from the **Event On Landed** node and put it on the **Reset** pin on the **DoN** node. This means that each time the player lands he will be able to jump then double jump again!

![connect on landed to reset](images/ConnectOnLandedToReset.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 21.`\|`ITA`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond:

To test our work lets print on screen. *Add* two **Print String** nodes. *Add* to the **InString** in the top one `Single Jump` then in the bottom one `Double Jump`. *Connect* the **Is Jumping** output to the top **Print String** node and the **Is Double Jumping** to the bottom **Print String** node.

![print single and double jump to test logic](images/AddTwoPrintNodesDoubleJump.jpg)

___


<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

<img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Double Jump II">

<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

| [previous](../walk-sprint/README.md#user-content-slow-walk--sprint)| [home](../README.md#user-content-ue4-animations) | [next](../double-jump-ii/README.md#user-content-double-jump-ii)|
|---|---|---|
