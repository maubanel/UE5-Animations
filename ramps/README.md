<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

### Speed Up & Down Ramps

<sub>[previous](../double-jump-ii/README.md#user-content-double-jump-ii) • [home](../README.md#user-content-ue4-animations) • [next](../ramps-ii/README.md#user-content-speed-up--down-ramps-ii)</sub>

<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

Lets make the player run slower when moving up a ramp and faster when moving down.  Lets also have the player lean into the motion so they are perpendicular to the ground.

<br>

---


##### `Step 1.`\|`ITA`|:small_blue_diamond:

Now lets add a ramp to run up and down and see how it feels. We will make adjustments to the physics to get what we would like. Start by *dragging* another **Box** onto the level.

![drag box onto level](images/DragFirstRampIntoRoom.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

Adjust the size to `2000` by `400` by `600` in the **brush size**. And make sure the box is on the ground (press the <kbd>End</kbd> key).

![change box brush to 2000, 400 and 600](images/ResizeBoxForRamp.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 3.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Move player start in front of this box.

![put player start in front of box](images/image_03.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 4.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now select the edit tool in the box. Press the Control key and left click the back top points on the rectangle. Pull them upwards to make a nice slope. Do the same thing for the front two but pull them down to the ground.

https://user-images.githubusercontent.com/5504953/133777427-122eb2bb-866a-47b8-8229-d14d19c88187.mp4

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 5.`\|`ITA`| :small_orange_diamond:

Now run up and down the ramps. Hmmm, doesn't feel right to me. I don't feel an acceleration down the ramp or deceleration running up the ramp. Lets add some debug to confirm.

https://user-images.githubusercontent.com/5504953/133778590-23023748-01da-4a51-a5b9-52663298da88.mp4


<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 6.`\|`ITA`| :small_orange_diamond: :small_blue_diamond:

Open your player blueprint **BP_AJCharacter**. Add a variable called `bShowVelocity` that is type **Boolean**. Set **Instance Editable** and **Private** to `true`. Set the **Category** to `Debug` and the **Tooltip** to `Prints on screen the velociy of the player`.

![add boolean variable bShowVelocity](images/AddShowVelocityPrint.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 7.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

*Drag and drop* a `Get bShowVelocity` node and *pull off* of the pin to add a **Branch** node.

![add get bShowVelocity and branch node](images/AddBranchToVelocity.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 8.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Pull off* of the **True** branch and select a **Print** node. We will be printing the magnitude (length) of the **Velocity** vector of our character.

![print velocity output](images/BranchTrueToPrint.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 9.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Drag and drop* a reference to the **Character Movement** Component in the player blueprint.

![alt_text](images/GetReferenceForCharacterMovement.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 10.`\|`ITA`| :large_blue_diamond:

*Pull off* the **Character Movement** node and select the **Velocity** node.

![add a velocity node](images/GetVelocityNode.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 11.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: 

Now lets get the magnitude (length) of the **Vector** which will return how fast they are moving. *Pull off* of the **Velocity** exit pin and add a **Vector Length** node.

![add vector length node](images/VectorOutputGetLength.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>


##### `Step 12.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

*Take* the ouput of the **Vector Length** node and plug it into the **In String** in the **Print String** node. *Press* the triangle at the bottom to get more options. Set the **Duration** to `0.0`.

![connect output of Vector Length to print node with a duration of 0](images/PrintVelocityLength.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 13.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

*Drag* the pin from **Set Is Jumping** output execution pin and from the **True** pin of the **Branch** node before **Set Is Jumping** to the input pin on the new **Branch** node created. We only care now about the ground speed so this will suffice. Add a comment around these nodes called `Debug Velocity`.

![check if player is jumping as there will be no ground speed up if not](images/DebugVelocityCommentConnectExecPin.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 14.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Set **bShowVelocity** to `True` in the blueprint. *Press* the <kbe>Compile</kbd> button on the blueprint. Go to back to the game.

![set bShowVelocity default to true](images/ShowCharacterVelocity.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 15.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: 

*Run* the game and sprint, run and walk up and down the ramp. Now the player does not lean into the ramps not does the speed change when running on slopes.

https://user-images.githubusercontent.com/5504953/133780569-c4fb10dc-b0cf-4a81-9837-e280e65f18d2.mp4

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 16.`\|`ITA`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

So first we need to find out the slope of the ground under us. How are we going to do this? We need to cast a line from the player straight downwards to the ground. When it collides we will use that to determine the slope (pitch of the surface normal). 

*Right click* under the debug print we just made on the character blueprint then add a **Line Trace By Channel** node.

![add line trace by channel node](images/LineByTraceChannel.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 17.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Make some room to the right of the debug **Print String** nodes and add a **Sequence** node to keep our graph clean.

![add sequence node](images/SequenceBetweenNodes.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 18.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Attach* the execution pin between **Print String** and **Sequence** nodes.

![attach execution pins from print string to sequence nodes](images/HighjackExecutionPinToSequence.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 19.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now we want to only perform this operation if the player is moving. So *grab* the output of the previous **Vector Length** node and add a **Float > Float** node.

![add float > float node](images/OnlyIfPlayerIsMoving.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 20.`\|`ITA`| :large_blue_diamond: :large_blue_diamond:

Add a **Branch** node after checking in seeing if the **Velocity** is greater than **0**. Attach the output of the **Then 1** execution pin to the input of the **Branch** node.

![add branch and connect to Then 1 of sequence node](images/BranchAfterThenOneBeforeLineTrace.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 21.`\|`ITA`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond:

Now we will start the line trace in the center of the character. *Right click* and select a **Get Actor Location** node. *Send* the output of this to the **Start** pin in the **Line Trace By Channel** node. *Connect* the **Then 0** pin of the **Sequence** node to the **Branch** node then select the **True** execution pin from the **Branch** node to the **Line Trace By Channel** node.

![start line trace from center of character](images/StartLineTraceFromCenterOfCharacter.jpg)

___


<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

<img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Speed Up / Down Ramps II">

<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

| [previous](../double-jump-ii/README.md#user-content-double-jump-ii)| [home](../README.md#user-content-ue4-animations) | [next](../ramps-ii/README.md#user-content-speed-up--down-ramps-ii)|
|---|---|---|
