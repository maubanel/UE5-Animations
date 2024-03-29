![](../images/line3.png)

### Slow Walk & Sprint

<sub>[previous](../jumping-ii/README.md#user-content-jumping-animation-ii) • [home](../README.md#user-content-ue4-animations) • [next](../double-jump/README.md#user-content-double-jump)</sub>

![](../images/line3.png)

Lets add some speed changes so we can adjust our speed based on a button state change. Lets add a Alt button for slow walk and an Shift button for sprint. Then lets create some platforms to jump around in.

---

##### `Step 1.`\|`ITA`|:small_blue_diamond:

So we need to control the speed of the player. Open the **BP_AJ** blueprint and select the **Character Movement** component. In the detail panel look for **Character Movement: Walking | Max Walk Speed**. My guess is that this is the same value as the magnitude of the velocity vector. Please take note that the word walking means speed on ground and does not imply an animation state. It is used for all ground movement (not flying or swimming). Set **Max Walk Speed** to `450`.

![set max walk speed to 450](images/ShowWalkingSpeed.png)

![](../images/line2.png)

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

Remember we placed this velocity magnitude in the animation blueprint. Open the **AnimBP_AJ | Event Graph** blueprint and add to the bottom of the graph a **Get Speed** node. Add a **Print String** node. *Connect* the output of the **Speed** node to the **In String** of the **Print String** node. Press the arrow at the bottom of the **Print** node and change the **Duration** to `0.0`. *Connect* the execution pin coming from **Set PressedJump** node to the **Print String** node.

![add print string to print velocity](images/PrintVelocityMagnitude.png)

![](../images/line2.png)

##### `Step 3.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Play* the game. You will notice that the running speed is set at 450. So our assumption is correct, this matches the max walking value in the blueprint. Also, it is picking the sprint animation but it doesn't feel like our player is sprinting.  Remember it is the 1D Blend that we have set which animation to run so this is what we would need to adjust to pick a more appropriate animation speed to match the displacement velocity vector we are printing. So we want to sprint at 600 and run at 450, so we will have to adjust our blend.

https://github.com/maubanel/UE5-Animations/assets/5504953/cf1d1663-5e3e-4f35-8f65-547c7aedfcb0

![](../images/line2.png)

##### `Step 4.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Since 450 we are runnning the sprint anim but we are not displacing fast enought lets make a change to our **BlendSpace_IdleWalkRun**. Now lets make some adjustments in our blend space. We want our top sprinting speed to be 600 and our normal run at 450 . Open the **IdleWalkRun_BlendSpace** blend in our **Animations** folder. *Click on* **Axis Settings** and change the **Horizontal Axis | Maximum Axis** Value to `600` to match the top speed in game. Now this opens up a greater range at the end to blend from running to sprtinting.

That rescales our graph. So I want to know the speed of our normal run animation. *Click* on the last animation and change its value to `600.0`, what will be our sprinting speed.

![in blend space change maximum axis value to 600](images/MaxAxisValue.png)

![](../images/line2.png)

##### `Step 5.`\|`ITA`| :small_orange_diamond:

Now we need to set our regular run speed to 450. *Click* on the second to last run animation and it *change* this value to `450.0`.

![run speed should be at 450](images/RunSpeedFourFifty2.png)

![](../images/line2.png)

##### `Step 6.`\|`ITA`| :small_orange_diamond: :small_blue_diamond:

*Play* the game. You will noticed that in the player only runs at 450 and the slower run animation plays.  So you should see the bottom animation and no longer the top one. Notice the player is not as hunched over and leaning when running.

https://github.com/maubanel/UE5-Animations/assets/5504953/fa061515-15f1-4dad-bf2b-014b4ad8a2aa

![](../images/line2.png)

##### `Step 7.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Lets add sprinting to get the speed back up to 600. We will do this when pressing the <kbd>Shift</kbd> key. Now go to **Inputs | Actions** and right click to add a new **Input | Input Action**.  Call it `IA_Sprint`.  Now open it and we will leave it as a **Value Type** `Digital Bool`.  Just like the jump you are either holding the shift for sprinting or not.

![add sprint to project settings input action mapping](images/SprintInputAction.png)

![](../images/line2.png)

##### `Step 8.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Open up **IMC_Default** and press the <kbd>+</kbd> button next to **Mappings** to add another mapping.  Select `IA_SPrint` and assign both the `Left Shift` and `Right Shift` buttons.

![add sprint to project settings input action mapping](images/AddSprintToDef.png)

![](../images/line2.png)

##### `Step 9.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Reopen **BP_AJ** blueprint and go to the **Event Graph**. At the bottom add a **Enhanced Action Events | IA_Sprint** node. *Drag and drop* a reference to the **Character Movement** component.

![add sprint to ajCharacter blueprint](images/SprintActionMappingAdd.png)

![](../images/line2.png)

##### `Step 10.`\|`ITA`| :large_blue_diamond:

 *Pull off* of the **Character Movement** pin and add a **Set Max Walk Speed** node.

![add set max walk speed node](images/SetMaxWalkSpeedForSprint.png)

![](../images/line2.png)

##### `Step 11.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: 

 *Copy and paste* the the **Set Max Walk Speed** node to have a duplicate. *Connect* the execution pin **Triggered** from the **IA_Sprint** node to the **Set Max Walk Speed** node.  *Change* the **Speed** to `600.0` so that the speed increases when pressing the shift key to go to `600` triggering the sprint animation in the blend space. *Connect* the **Completed** (released) execution pin from the **IA_Sprint** node to the second **Set Max Walk Speed** node.  *Change* it back to your regular run speed setting **Speed** to `450.0`. Add a comment with `Sprinting` around these nodes.

![chnage speed to 600 and add another set max walk speed node](images/PressedSetSpeedSprint.png)

![](../images/line2.png)

##### `Step 12.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

*Play* the game. You will noticed that in the player runs at 450 until the <kbd>Shift</kbd> button is held. Then the player runs at a full 600 with the faster animation.

https://github.com/maubanel/UE5-Animations/assets/5504953/b7289530-9efa-491d-a846-cd1c757f84e7

![](../images/line2.png)

##### `Step 13.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

OK, lets work on the slow walk. Open the **BlendSpace_IdleWalkRun** editor. It is the second option on the left. We can see that it is at ~ `40`.

![go to idle walk run blend space](images/SlowWalkSpeedBlendSpace.png)

![](../images/line2.png)

##### `Step 14.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Lets add oru slow creep walk to use when the speed goes down to 40. We will do this when pressing the <kbd>Alt</kbd> key. Now go to **Inputs | Actions** and right click to add a new **Input | Input Action**.  Call it `IA_Creep`.  Now open it and we will leave it as a **Value Type** `Digital Bool`.  Just like the jump you are either holding the alt key for slow walking or not.

![go to idle walk run blend space](images/creepInputAction.png)

![](../images/line2.png)

##### `Step 15.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: 

Open up **IMC_Default** and press the <kbd>+</kbd> button next to **Mappings** to add another mapping.  Select `IA_Creep` and assign both the `Left Alt` and `Right Alt` buttons.

![add sprint to project settings input action mapping](images/AddCreepToDef.png)

![](../images/line2.png)

##### `Step 16.`\|`ITA`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

Go back to the **BP_AJ** blueprint and at the bottom *right click* and add a **Enhanced Action Events | IA_Creep** node.

![add slow walk action to ajcharacter bp](images/AddSlowWalkActionNode.png)


![](../images/line2.png)

##### `Step 17.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

*Copy and paste* the **Character Movement** and two **Set** nodes from sprinting and paste them next to the **Slow Walk** node. *Connect* the execution pins. *Change* the **Max Walk Speed** for the **Pressed** node path to `40.0`. *Leave* the **Released** back to `450.0`. Add a comment `Slow Walk` around these new nodes.

![hook up slow walk](images/HookUpSlowWalk.png)

![](../images/line2.png)

##### `Step 18.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now *run* the game and press the <kbd>Alt</kbd> key. I got *very* luck and my character does not kate across the screen. 

https://github.com/maubanel/UE5-Animations/assets/5504953/b9584046-3f94-4e51-ab65-9c1d69c249c9

![](../images/line2.png)

##### `Step 19.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Go back to the **IdleWalkRun_BlendSpace**. Adjust the location of the animation for the creep walk, walk, run and sprint.  There is no relation between the movement physics and animation.  You need to tweak at what point each of these animations fall without seeing any foot sliding issues (physics running slower or faster than animation).  Look for anything like looks like skating or moon walking.

![change blend space speed to 20 by turning off snap to grid](images/ChangeBlendTo10.png)

![](../images/line2.png)

##### `Step 20.`\|`ITA`| :large_blue_diamond: :large_blue_diamond:

Select the **File | Save All** then press the <kbd>Revision Control</kbd> button and select **Submit Content**.  If you are prompted, select **Check Out** for all items that are not checked out of source control. Update the **Changelist Description** message and with the latest changes. Make sure all the files are correct and press the <kbd>Submit</kbd> button. A confirmation will pop up on the bottom right with a message about a changelist was submitted with a commit number. Quit Unreal and make sure your **Pending** tab in **P4V** is empty. **Submit** any work that is still in the editor.

![save all and submit to perforce in P4V](images/submitP4.png)

![](../images/line2.png)

##### `Step 21.`\|`ITA`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond:

Sometimes not all files get submitted to Unreal especially for files that don't show up in the editor.  It is good practice one you submit in **Unreal** and quit the game to right click on the top most project folder and select **Reconcile Offline Work...**.

This will either give a message saying ther is nothing to reconcile or bring up a tab.  Make sure that these are **NOT** files in the **Intermediate** and **Saved** folders as these should be ignored from the `.p4ignore`.

If the files are in **Content** or **Configuration** then press the <kbd>Reconcile</kbd> button.  Then submit the changes with a message and press the <kbd>Submit</kbd> button.

![reconcile offline work](images/reconcile.png)

![](../images/line1.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Double Jump"> -->
![next up next tile](images/banner.png)

![](../images/line1.png)

| [previous](../jumping-ii/README.md#user-content-jumping-animation-ii)| [home](../README.md#user-content-ue4-animations) | [next](../double-jump/README.md#user-content-double-jump)|
|---|---|---|
