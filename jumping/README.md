<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

### Jumping Animation

<sub>[previous](../falling-ii/README.md#user-content-falling-animation-ii) • [home](../README.md#user-content-ue4-animations) • [next](../jumping-ii/README.md#user-content-jumping-animation-ii)</sub>

<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

Lets add the ability for the player to jump around the level and tune this to our liking.

<br>

---


##### `Step 1.`\|`ITA`|:small_blue_diamond:

Before we start lets set this level as the default boot up level. Go to **Edit | Project Settings** and navigate to the **Maps & Modes** section. Change the **Editor Startup Map** to `AnimTestLevel`.

![add TestLevel to startup map in project settings](images/ProjectSettingTestLevel.png)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

Now we need to add a controller event for jumping. Go to the **Engine | Input** section and press the **+** button next to the **Action Mappings** heading.

![go to input in project settings and add a action mapping](images






:small_blue_diamond:

Call this new action `Jump`. Press the **+** button next to the **Jump** setting and add a **Keyboard | Space Bar** to the controls.

![add jump action and assign space bar](images/JumpSpaceBar.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 4.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Open up the **BP_AJ_Character** blueprint and go to the **Event Graph**. *Right click* and add a **Action Events | Jump** to the graph.

![open BP_AJ_Character bp and add a Jump event](images/RightClickForJumpAction.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 5.`\|`ITA`| :small_orange_diamond:

Pull off of the **Jump** node's **Pressed** execution pin and select the **Jump** node.

![select Jump node](images/PressedToJump.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 6.`\|`ITA`| :small_orange_diamond: :small_blue_diamond:

Add a **comment** around these two nodes called `Jump`.

![add code comments](images/AddJumpComment.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 7.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

*Press** the <kbd>Compile</kbd> button and *run* the game and press the jump button <kbd>space bar</kbd>. Now you should be jumping around the level.

https://user-images.githubusercontent.com/5504953/132988110-e708986d-8dd4-46f1-9d40-b92ad8b8015f.mp4

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 8.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now we could leave it like this as it looks ok. We will add a jump start just to show how it is done. Go back to the [Mixamo](https://www.mixamo.com/#/) site and look for the start of a jump animation. Make sure you speed it up as we want it to be very fast. Also clip just the very begining of the jump. Pick one that will work from jump from stand and from run.

https://user-images.githubusercontent.com/5504953/132995968-f2f3999a-bd91-400e-9bec-c9564ca3beb6.mp4

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 9.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Remember to set **Skin** to `Without Skin` when *downloading*:

![set without skin when downloading](images/DownloadJumpStartWithoutSkin.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 10.`\|`ITA`| :large_blue_diamond:

*Add/Import* the **Jump Start** animation into the jump start folder.

![import jump start to animation](images/ImportJumpStartAnimFolder.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 11.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: 

In the **FBX Import Options** select the *skeleton* for the character. *Press* the <kbd>Import</kbd> button.

![select skeleton and import](images/JumpStartFBXSettings.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>


##### `Step 12.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

*Rename* the animation `Jump_Start` and *run* it to confirm you are happy with the animation.

![rename jump start animation](images/RenameJumpStart.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 13.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

*Open* the **aj_AnimBlueprint** and go to the **Anim Graph | Core Locomotion** page. Right click and select **Add State**.

![add state to animation blueprint core locomotion](images/AddStateToTree.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 14.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Call this state `Jump` and *connect* a transition from **IdleWalkRun** to **Jump to Falling**. There will be a different path to just running off a platform and jumping.

![call state jump and connect from idlewalkrun](images/StateJumpConnect.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 15.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: 

Now the animation blueprint needs to know when the jump button is pressed. Go to **BP_AJ_Character** blueprint and add a **Boolean** variable called `bIsJumping`. Keep it **Public** (**Private** set to `false`) because we need to access it in the animation blueprint.

![add boolean bIsJumping](images/IsJumpingPlayerBPVar.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 16.`\|`ITA`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

*Enlarge* the comment section for jumping. *Drag and drop* a **Set IsJumping** variable next to the **Jump** node.

![add set is jumping node](images/SetIsJumpingForJump.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 17.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

*Set* the execution pin from the **Jump** node to the **Set Is Jumping** node. *Set* **Is Jumping** to `true`.

![set is jumping to true](images/image_02.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 18.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

We need to reset this **boolean** when you are touching the ground. Under the **Jump** nodes *right click* on the graph and add a **Get Movement Component** node. Pull of its pin and look for a **Is Falling** node.

![add get movement component and is falling nodes](images/SetToIsJumpingFalse.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 19.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Pull off* of the **Is Falling** node's pin and select a **Branch** node.

![add branch node](images/BranchFromIsFalling.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 20.`\|`ITA`| :large_blue_diamond: :large_blue_diamond:

*Pull off* of the **False** execution pin from this **Branch** node and select a **Set IsJumping** node and leave it as `false`:

![add set is jumping and connect to false of branch node and leave false](images/BranchFalseIsJumpingFalse.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 21.`\|`ITA`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond:

*Surround* these nodes with a **comment** saying `Reset IsJumping When On Ground`. Now notice there are no execution pins that run every frame (Tick Event).

![add cnode comments](images/ResentIsJumpingCommnet.jpg)

___


<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

<img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Jumping Animation II">

<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

| [previous](../falling-ii/README.md#user-content-falling-animation-ii)| [home](../README.md#user-content-ue4-animations) | [next](../jumping-ii/README.md#user-content-jumping-animation-ii)|
|---|---|---|
