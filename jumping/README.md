![](../images/line3.png)

### Jumping Animation

<sub>[previous](../falling-ii/README.md#user-content-falling-animation-ii) • [home](../README.md#user-content-ue4-animations) • [next](../jumping-ii/README.md#user-content-jumping-animation-ii)</sub>

![](../images/line3.png)

Lets add the ability for the player to jump around the level and tune this to our liking.

<br>

---


##### `Step 1.`\|`ITA`|:small_blue_diamond:

Now we need to add a controller event for jumping. Go to the **Engine | Input** section and press the **+** button next to the **Action Mappings** heading.

![go to input in project settings and add a action mapping](images/ActionMap.png)

![](../images/line2.png)

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

Call this new action `Jump`. Press the **+** button next to the **Jump** setting and add a **Keyboard | Space Bar** to the controls.

![add jump action and assign space bar](images/JumpSpaceBar.png)

![](../images/line2.png)

##### `Step 4.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Open up the **AnimBP_AJ** blueprint and go to the **Event Graph**. *Right click* and add a **Character | Jump** to the graph.

![open BP_AJ_Character bp and add a Jump event](images/RightClickForJumpAction.png)

![](../images/line2.png)

##### `Step 5.`\|`ITA`| :small_orange_diamond:

Pull off of the **Jump** node's **Pressed** execution pin and select the **Action Events | Jump** node. Add a **comment** around these two nodes called `Jump`.

![select Jump node](images/PressedToJump.png)

![](../images/line2.png)

##### `Step 6.`\|`ITA`| :small_orange_diamond: :small_blue_diamond:

*Press** the <kbd>Compile</kbd> button and *run* the game and press the jump button <kbd>space bar</kbd>. Now you should be jumping around the level.

https://user-images.githubusercontent.com/5504953/197189065-bafc020b-5773-4957-98c6-2901a6fa7518.mp4

![](../images/line2.png)

##### `Step 7.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Now we could leave it like this as it looks ok. We will add a jump start just to show how it is done. Go back to the [Mixamo](https://www.mixamo.com/#/) site and look for the start of a jump animation. Make sure you speed it up as we want it to be very fast. Also clip just the very begining of the jump. Pick one that will work from jump from stand and from run.

https://user-images.githubusercontent.com/5504953/132995968-f2f3999a-bd91-400e-9bec-c9564ca3beb6.mp4


![](../images/line2.png)

##### `Step 8.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Remember to set **Skin** to `Without Skin` when *downloading*:

![set without skin when downloading](images/DownloadJumpStartWithoutSkin.jpg)

![](../images/line2.png)

##### `Step 9.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Drag and drop* the **Jumping Up** animation into the **Animations** folder.

![import jump start to animation](images/ImportJumpStartAnimFolder.png)

![](../images/line2.png)

##### `Step 10.`\|`ITA`| :large_blue_diamond:

In the **FBX Import Options** select the *skeleton* for the character. *Press* the <kbd>Import</kbd> button.

![select skeleton and import](images/JumpStartFBXSettings.png)

![](../images/line2.png)

##### `Step 11.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: 

*Rename* the animation `JumpingUp` and *run* it to confirm you are happy with the animation.

![rename jump start animation](images/RenameJumpStart.png)

![](../images/line2.png)


##### `Step 12.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

Open up the **JumpingUp** animation and make sure it is very short. On its own it should look like this:

https://user-images.githubusercontent.com/5504953/197190409-b9021428-7b22-4fe3-ac72-fb8fa5abb3ec.mp4

![](../images/line2.png)

##### `Step 13.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

*Open* the **aj_AnimBlueprint** and go to the **Anim Graph | Basic Locomotion** page. Right click and select **Add State**. Call this state `Jumping`.

![add state to animation blueprint core locomotion](images/AddStateToTree.png)

![](../images/line2.png)

##### `Step 14.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

*Connect* a transition from **IdleWalkRun** to **Jumping** and **Jumping** to **Falling**.  There will be a different path to just running off a platform and jumping.

![call state jump and connect from idlewalkrun](images/StateJumpConnect.png)

![](../images/line2.png)

##### `Step 15.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: 

Now the animation blueprint needs to know when the jump button is pressed. Go to **BP_AJ_Character** blueprint and add a **Boolean** variable called `IsJumping`. Keep it **Public** (**Private** set to `false`) because we need to access it in the animation blueprint. Set the **Category** to `Player Physics`.

![add boolean bIsJumping](images/IsJumpingPlayerBPVar.png)

![](../images/line2.png)

##### `Step 16.`\|`ITA`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

*Enlarge* the comment section for jumping. *Drag and drop* a **Set IsJumping** variable next to the **Jump** node.

![add set is jumping node](images/SetIsJumpingForJump.png)

![](../images/line2.png)

##### `Step 17.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

*Set* the execution pin from the **Jump** node to the **Set Is Jumping** node. *Set* **Is Jumping** to `true`.

![set is jumping to true](images/image_02.png)

![](../images/line2.png)

##### `Step 18.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

We need to reset this **boolean** when you are touching the ground. Under the **Jump** nodes *right click* on the graph and add a **Get Movement Component** node. Pull of its pin and look for a **Is Falling** node.

![add get movement component and is falling nodes](images/SetToIsJumpingFalse.jpg)

![](../images/line2.png)

##### `Step 19.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Pull off* of the **Is Falling** node's pin and select a **Branch** node.

![add branch node](images/BranchFromIsFalling.jpg)

![](../images/line2.png)

##### `Step 20.`\|`ITA`| :large_blue_diamond: :large_blue_diamond:

*Pull off* of the **False** execution pin from this **Branch** node and select a **Set IsJumping** node and leave it as `false`:

![add set is jumping and connect to false of branch node and leave false](images/BranchFalseIsJumpingFalse.jpg)

![](../images/line2.png)

##### `Step 21.`\|`ITA`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond:

*Surround* these nodes with a **comment** saying `Reset IsJumping When On Ground`. Now notice there are no execution pins that run every frame (Tick Event).

![add cnode comments](images/ResentIsJumpingCommnet.jpg)

___


![](../images/line1.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Jumping Animation II"> -->
![next up next tile](images/banner.png)

![](../images/line1.png)

| [previous](../falling-ii/README.md#user-content-falling-animation-ii)| [home](../README.md#user-content-ue4-animations) | [next](../jumping-ii/README.md#user-content-jumping-animation-ii)|
|---|---|---|
