![](../images/line3.png)

### Animation Blend Space

<sub>[previous](../adding-controls/README.md#user-content-adding-controls) • [home](../README.md#user-content-ue4-animations) • [next](../anim-bp/README.md#user-content-our-first-animation-blueprint)</sub>

![](../images/line3.png)

To go between stand, creep walk, walk, run and fast run that can adopt to any speed will blend between our animations. We need to create an animation blend space to achieve this.

---

##### `Step 1.`\|`ITA`|:small_blue_diamond:

The first thing we will implement is our player movement. The player will go from idle to creep walk to walk to run to speed run. We will be blending between these 5 animations. Go to the **Animations** folder and *press* the <kbd>+ Add</kbd> button. *Select* **Animation | Legacy | Blend Space 1D**. This will be a 1 dimensional blend.

![add blend space](images/AddBlendSpace1D.png)

![](../images/line2.png)

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

This brings up a **Pick Skeleton** overlay. Pick the skeleton you imported.

![pick skeleton](images/BringsUpPickSkeleton.png)

![](../images/line2.png)

##### `Step 3.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Call it `BS_IdleWalkRun`.

![idle walk run](images/IdleWalkRunName.png)

![](../images/line2.png)

##### `Step 4.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Double click* the blend space you just created. Open up the **Axis Settings** tab on the **Asset Details** and *change* the **Number of Grid Divisions** to `8`. *Change* the name of this **Horizontal Axis | Name** to `Speed` and **Maximum Axis Value** to `300`.

![set maximum axis value to 350 and grid division to 8](images/SetAxisValueAndGridDivisions.png)

![](../images/line2.png)

##### `Step 5.`\|`ITA`| :small_orange_diamond:

Make sure on the right hand side you are on the **Asset Browser** tab and *drag and drop* the **Idle** animation (the breathing idle that loops and not the fancier one) to the far left side of the blend space. It should be at location `0`.

![drag idle to blend space](images/AddIdleAnimToBlendSpace.png)

![](../images/line2.png)

##### `Step 6.`\|`ITA`| :small_orange_diamond: :small_blue_diamond:

Drag and drop the **CreepWalk** animation and put it close to `40.0` on the **1D blend space**.

![creep walk to 40](images/SlowWalkTo50.png)

![](../images/line2.png)

##### `Step 7.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

*Drag and drop* the **Walk** animation to around `80` on the **blend space**.

![drag walk animation to 80 on blend space](images/WalkTo87BlendSpace.png)

![](../images/line2.png)

##### `Step 8.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Drag and drop* **Run** around `250.0` on **blend space**.

![drag run animation to 250 on blend space](images/DragRunTo250.png)

![](../images/line2.png)

##### `Step 9.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Finally *place* the **Sprint** animation at the end of the *timeline* at `350`.

![add fast run to very end](images/FastRunToEnd.png)

![](../images/line2.png)

##### `Step 10.`\|`ITA`| :large_blue_diamond:

Scrub along the timeline and watch animation states blend. In this case I am happy with the results and can leave the blend defaults as they stand. The animation will be selected based on the speed of the character.

https://user-images.githubusercontent.com/5504953/196059260-aa3292ba-848e-41b7-bf9f-5d991eac75f6.mp4

![](../images/line2.png)

##### `Step 11.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: 

Select the **File | Save All** then quit UE5.   Go to **P4V** and go the top project folder (the one that holds the `.uproject` file and **Content** folder) and press the <kbd>+Add</kbd> then <kbd>OK</kbd> button.  This makes sure any files that Unreal didn't add get added to source control. Press the <kbd>Submit</kbd> button and enter a message explaining the work done.  Press <kbd>Submit</kbd>.

![save all and submit to perforce in P4V](images/submitP4.png)


___


![](../images/line1.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Our First Animation Blueprint"> -->
![next up next tile](images/banner.png)

![](../images/line1.png)

| [previous](../adding-controls/README.md#user-content-adding-controls)| [home](../README.md#user-content-ue4-animations) | [next](../anim-bp/README.md#user-content-our-first-animation-blueprint)|
|---|---|---|
