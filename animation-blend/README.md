![](../images/line3.png)

### Animation Blend Space

<sub>[previous](../adding-controls/README.md#user-content-adding-controls) • [home](../README.md#user-content-ue4-animations) • [next](../anim-bp/README.md#user-content-our-first-animation-blueprint)</sub>

![](../images/line3.png)

To go between stand, creep walk, walk, run and fast run that can adopt to any speed will blend between our animations. We need to create an animation blend space to achieve this.

<br>

---


##### `Step 1.`\|`ITA`|:small_blue_diamond:

The first thing we will implement is our player movement. The player will go from idle to creep walk to walk to run to speed run. We will be blending between these 5 animations. Go to the **Animations** folder and *press* the <kbd>Add/Import</kbd> button. *Select* **Animation | Blend Space 1D**. This will be a 1 dimensional blend.

![add blend space](images/AddBlendSpace1D.jpg)

![](../images/line2.png)

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

This brings up a **Pick Skeleton** overlay. Pick the skeleton you imported.

![pick skeleton](images/BringsUpPickSkeleton.jpg)

![](../images/line2.png)

##### `Step 3.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Call it `IdleWalkRun_BlendSpace`.

![idle walk run](images/IdleWalkRunName.jpg)

![](../images/line2.png)

##### `Step 4.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Double click* the blend space you just created. Open up the **Axis Settings** tab on the **Asset Details** and *change* the **Maximum Axis Value** to `350.0` and the **Number of Grid Divisions** to `8`. *Change* the name of this **Horizontal Axis | Name** to `Speed`.

![set maximum axis value to 350 and grid division to 8](images/SetAxisValueAndGridDivisions.jpg)

![](../images/line2.png)

##### `Step 5.`\|`ITA`| :small_orange_diamond:

Make sure on the right hand side you are on the **Asset Browser** tab and *drag and drop* the **Idle** animation (the breathing idle that loops and not the fancier one) to the far left side of the blend space.

![drag idle to blend space](images/AddIdleAnimToBlendSpace.jpg)

![](../images/line2.png)

##### `Step 6.`\|`ITA`| :small_orange_diamond: :small_blue_diamond:

Drag and drop the **CreepWalk** animation and put it close to `40.0` on the **1D blend space**.

![creep walk to 40](images/SlowWalkTo50.jpg)

![](../images/line2.png)

##### `Step 7.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

*Drag and drop* the **Walk** animation to around `80` on the **blend space**.

![drag walk animation to 80 on blend space](images/WalkTo87BlendSpace.jpg)

![](../images/line2.png)

##### `Step 8.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Drag and drop* **Run** around `250.0` on **blend space**.

![drag run animation to 250 on blend space](images/DragRunTo250.jpg)

![](../images/line2.png)

##### `Step 9.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Finally *place* the **Fast_Run** animation at the end of the *timeline*.

![add fast run to very end](images/FastRunToEnd.jpg)

![](../images/line2.png)

##### `Step 10.`\|`ITA`| :large_blue_diamond:

Scrub along the timeline and watch animation states blend. In this case I am happy with the results and can leave the blend defaults as they stand. The animation will be selected based on the speed of the character.

https://user-images.githubusercontent.com/5504953/132963289-7ecbd5a7-5735-4144-a4da-0a0320bd893f.mp4

![](../images/line2.png)

##### `Step 11.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: 

Select the **File | Save All** then press the <kbd>Source Control</kbd> button and select **Submit to Source Control...**.  Enter a **Changelist Description** and then press <kbd>Submit</kbd>.  Open up **GitHub Desktop** and select **Push origin** to update the server with the latest changes.

![save, commit and push to github](images/GitHub.png)

___


![](../images/line1.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Our First Animation Blueprint"> -->
![next up next tile](images/banner.png)

![](../images/line1.png)

| [previous](../adding-controls/README.md#user-content-adding-controls)| [home](../README.md#user-content-ue4-animations) | [next](../anim-bp/README.md#user-content-our-first-animation-blueprint)|
|---|---|---|
