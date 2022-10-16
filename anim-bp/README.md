![](../images/line3.png)

### Our First Animation Blueprint

<sub>[previous](../animation-blend/README.md#user-content-animation-blend-space) • [home](../README.md#user-content-ue4-animations) • [next](../second-idle/README.md#user-content-time-out-for-second-idle)</sub>

![](../images/line3.png)

There is a special kind of blueprint used as a state machine for animations. It is an animation blueprint. Lets create one for our character.

<br>

---


##### `Step 1.`\|`ITA`|:small_blue_diamond:

We are now going to start to set up a state machine for our character. Go to the **AJ** folder and *press* the <kbd>Add/Import</kbd> button and *select* **Animation | Animation Blueprint**. Make sure it is of type **AnimInstance** and the correct skeleton is selected. Press the <kbd>Create</kbd> button.

![add animation blueprint to aj folder](images/AddNewAnimationBlueprint.png)

![](../images/line2.png)

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

Name it `AnimBP_AJ`.

![namne file AJ_AnimBlueprint](images/CallItAJAnimBP.png)

![](../images/line2.png)

##### `Step 3.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Open the animation blueprint and go to the **AnimGraph** tab. If it is not there you can double click it in the **AnimGraph** menu item on the left hand side.

![open animgraph](images/GoToAnimGraphTabAnimBP.png)

![](../images/line2.png)

##### `Step 4.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Right click* on the anim graph and select a **Add New State Machine** node.

![add state machine node](images/RightClickAddNewStateMachine.png)


![](../images/line2.png)

##### `Step 5.`\|`ITA`| :small_orange_diamond:

Name this node `BasicLocomotion`.

![name node basic locomotion](images/NameStateMachineBasicLocomotion.png)

![](../images/line2.png)

##### `Step 6.`\|`ITA`| :small_orange_diamond: :small_blue_diamond:

*Connect* the animation pins from the **Basic Locomotion** node to the **Final Animation Pose** node. *Double click* on the **Basic Locomotion** node to enter its state machine.

![connect pin from basic locomotion to final animatoin pose](images/ConnectGoToGraphForLoco.png)

![](../images/line2.png)

##### `Step 7.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

This gets us to the entrance of the Basic Locomotion animation tree. It has an **Entry** node that is what it plays when it enters this state (the only state we are calling for the moment)

![entry node](images/EntranceToBasicLocomotion.png)


![](../images/line2.png)

##### `Step 8.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Right click* on the anim graph and select **Add State.**

![add state](images/AddStateToTree.png)

![](../images/line2.png)

##### `Step 9.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Name* this state **IdleWalkRun** and *attach* the node from **Entry** to this new **State**. *Double click* on **IdleWalkRun** to enter this state.

![name state IdleWalkRun and attach to Entry state](images/NameIdleWalkRunDC.png)

![](../images/line2.png)

##### `Step 10.`\|`ITA`| :large_blue_diamond:

Now we need to play the blend space we created. Drag and drop the **IdleWalkRun_BlendSpace** onto the graph.

![drag blend space to graph](images/DragBlendSpaceToGraph.png)

![](../images/line2.png)

##### `Step 11.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: 

*Connect* the animation pins so that this **blendspace** runs and gets sent to the **state machine**.

![connect blendspace to state machine](images/ConnectAnimPins.png)

![](../images/line2.png)


##### `Step 12.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

Now this blend space requires an input float to represent the speed of the player. *Right click* on **None** and select **Promote to Variable**.

![promote none to variable](images/PromoteToVariableSpeed.png)

![](../images/line2.png)

##### `Step 13.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Name this variable `Speed` and set **Private** to `true`. *Press* the <kbd>Compile</kbd> button.

![name variable speed and make private](images/VariableSpeedPrivate.png)

![](../images/line2.png)

##### `Step 14.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Now there is no begin play in animation blueprints but there is a **Event Blueprint Initialize Animation** which runs once when adding an animation to the game.  Lets add this event type by right clicking on the graph and selecting **Event Blueprint Initialize Animation**.  Next we need access to the blueprint that holds our playable character **BP_AJ** so we will add a **Get Owning Actor** node which gets access to the current playable character.

![add initialize animatoin and get owning actor nodes](images/getOwningActorInit.png)


![](../images/line2.png)

##### `Step 15.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: 

Pull off of the **Get Owning Actor** pin and select a **Cast to Character** node.  This will cast the class from **Pawn** to **Character**.  Right click on the **As Character** and select **Promote to Variable**.  Connect the execution pin from **Cast to Character** to **Set Character** node. Set **Private** to `true` and add a **Category** `References` to the animation blueprint.

![Get owning actor cast to character and set character as promoted var](images/getReference.png)


![](../images/line2.png)

##### `Step 16.`\|`ITA`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

Connect the execution pin from **EventBlueprint Initialize Annimation** to **Cast to Character**.

![connect execution pins](images/finishCharRef.png)

![](../images/line2.png)

##### `Step 17.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Now drag a **Get** for the **Character** variable next to the **EventBlueprint Update Animation** which will tick every frame like the tick node in a normal blueprint as long as this animation is active.  Now we need to make sure that the character still exists in the game (could have died for example and have been remoted) so we *right click* on the node and select **Convert to Validated Get** which will stop the game from crashing if we access a null reference.

![Get owning actor cast to character and set character as promoted var](images/validatedGet.png)

![](../images/line2.png)

##### `Step 18.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Drag* off the **GET | Is Valid** execution pin and select a **Sequence** node. the *Drag off* of the **Character** from the **GET** node and select **Get Velocity** to get the velocity vector of the player pawn. 

![add get velocity node](images/GetVelocityFromPawn.png)

![](../images/line2.png)

##### `Step 19.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

We forgot to clean up above so go back to the **Intialize Animation** and place a comment box around the nodes saying `Get Reference`.

![add get reference comment](images/getReferencesComment.png)

![](../images/line2.png)

##### `Step 20.`\|`ITA`| :large_blue_diamond: :large_blue_diamond:

Connect the execution pin from **Event Blueprint Update Animation** to **? Is Valid** nodes.
We need to get access to the **Speed** of the player. We do this in the **Event Graph** of the animation blueprint. *Click on* the **Event Graph** tab (or *double click* it from the Graphs menu on the left) and you should see two *greyed* out nodes. If you don't see the **Try Get Pawn Owner** then add it. *Drag off* of the **Return Value** pin from the **Try Get Pawn Owner** node and selecdt a **? Is Valid** node. We want to make sure that this pawn is active in game.

![add try get pawn owner and check if valid](images/PawnOwnerValid.jpg)

Now a **Velocity** (or any vector for that matter) has a *direction* and a *magnitude*. All we care about here is the *magnitude*. *Drag off* of the **Return Value** pin from the **Get Velocity** node and select **Vector Length** (I typed in Magnitude in the search window and it still points to this node!). This returns a float with the length of the vector (magnitude).

![get velocity magnitude](images/GetVelocityMagnitude.jpg)

*Drag and drop* the **Speed Variable** and select **Set Speed**:

![add set speed variable](images/DragAndDropSetSpeed.jpg)

Connect the execution pins between the three nodes and *press* the <kbd>Compile</kbd> button.

![connect execution pins and compile](images/ConnectExecPinsCompile.jpg)

Add a comment called `Get Speed From Player` to these nodes:

![add code comment](images/AddCommentSpeedNodes.jpg)

![](../images/line2.png)

##### `Step 21.`\|`ITA`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond:

Now we need to assign this animation blueprint to our skeletal mesh. *Open* the **BP_AJ_Character** blueprint. *Go* to the **Viewport** tab. We notice our character is in a *T-Pose*. *Select* the **Animation Class** on the Details panel and pick the animation blueprint we just made **AJ_AnimBlueprint**. You will notice that the player should enter the idle state. *Press* the <kbd>Compile</kbd> button.

![add anim blueprint to player blueprint](images/SelectAnimBPOnCharacterMesh.jpg)

![](../images/line2.png)

##### `Step 22.`\|`ITA`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:

We want the player to face the direction we are moving in as opposed to always looking forward. Go to the top level component on the blueprint and under **Pawn** *set* the **Use Controller Rotation Yaw** to `false`.

![set Use Controller Rotation Yaw to false](images/NoControllerYaw.jpg)

![](../images/line2.png)

##### `Step 23.`\|`ITA`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:


Now *select* the **Spring Arm** component and in **Camera Settings** *set* **Use Pawn Control Rotation** to `true`.

![set use pawn control rotation to true](images/SpringArmRotationTrue.jpg)

![](../images/line2.png)

##### `Step 24.`\|`ITA`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now press the <kbd>Compile</kbd> button and go into the game and press *play*. You will notice that the player does animate but doesn't change directions.

https://user-images.githubusercontent.com/5504953/132985178-71262496-6c39-4202-a0d0-55974a03eb39.mp4

![](../images/line2.png)

##### `Step 25.`\|`ITA`| :large_blue_diamond: :large_blue_diamond: :small_orange_diamond:

Now go back to the **BP_AJ_Character** blueprint and *select* the **CharacterMovement** component. *Scroll* in the **Details** panel down to C**haracter Movement (Rotation Settings)** tab. Open it up and look for **Orient Rotation to Movement**. Set this to *true*.

![set orient rotation to movement to true](images/OrientRotationToMovement.jpg)

![](../images/line2.png)

##### `Step 26.`\|`ITA`| :large_blue_diamond: :large_blue_diamond: :small_orange_diamond: :small_blue_diamond:

Now press the <kbd>Compile</kbd> button and go back into the game. Now the player should animate and turn correctly. Select the **File | Save All** then press the <kbd>Source Control</kbd> button and select **Submit to Source Control...**.  Enter a **Changelist Description** and then press <kbd>Submit</kbd>.  Open up **GitHub Desktop** and select **Push origin** to update the server with the latest changes.

https://user-images.githubusercontent.com/5504953/132985183-13aeb172-0a84-40e7-8033-d30f3ec22ca1.mp4

![save, commit and push to github](images/GitHub.png)

___

![](../images/line1.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Time Out for Second Idle"> -->
![next up next tile](images/banner.png)

![](../images/line1.png)

| [previous](../animation-blend/README.md#user-content-animation-blend-space)| [home](../README.md#user-content-ue4-animations) | [next](../second-idle/README.md#user-content-time-out-for-second-idle)|
|---|---|---|
