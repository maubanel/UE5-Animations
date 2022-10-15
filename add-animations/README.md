![](../images/line3.png)

### Add Animations

<sub>[previous](../fixing-model/README.md#user-content-fixing-mixamo-models) • [home](../README.md#user-content-ue4-animations) • [next](../character-bp/README.md#user-content-setting-up-character-blueprint)</sub>

![](../images/line3.png)

Lets add the animations we downloaded to the game and map them to the skeleton so that they drive the skeletal mesh.

<br>

---


##### `Step 1.`\|`ITA`|:small_blue_diamond:

Add to the Content Browser's Character | AJ folder, a new sub-folder called `Animations`. *Drag and drop* the 6 animations you downloaded to the new **Animations** folder.

![add folder called Character | AJ | Animations](images/AJAnimationsFolder.png)

![](../images/line2.png)

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

Now the **FBX Import Options** appear. *Select* the **Skeleton** tab and select the skeleton asset we just downloaded. There should only be one option.

![select skeleton from player dowloaded](images/ImportSkeleton.png)

![](../images/line2.png)

##### `Step 3.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Once you select the skeleton press the <kbd>Import All</kbd> button leaving all the other options at their default setting.

![import all button](images/ImportAllMotionAnimation.png)


![](../images/line2.png)

##### `Step 4.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now this will take a while as it is solving the animation to this skeleton.

![UE4 progress bar importing animations](images/ImportingAnimationsTakeTime.jpg)

![](../images/line2.png)

##### `Step 5.`\|`ITA`| :small_orange_diamond:
Double click each animation then watch them. Rename the animation appropriately.

![slow walk animation frame](images/PlayAnim.jpg)



![](../images/line2.png)

##### `Step 6.`\|`ITA`| :small_orange_diamond: :small_blue_diamond:

I have named mine `Creep_Walk`, `Fast_Run`, `Idle`, `Idle_Fidget` and `Run and Walk`. This gives me two run cycles, an idle and walk animations to use in our animation graph.

![animation name](images/NameEachAnim.jpg)

![](../images/line2.png)

##### `Step 7.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Select the **File | Save All** then press the <kbd>Source Control</kbd> button and select **Submit to Source Control...**.  Enter a **Changelist Description** and then press <kbd>Submit</kbd>.  Open up **GitHub Desktop** and select **Push origin** to update the server with the latest changes.


![check model for errors](images/GitHub.png)

![](../images/line2.png)

##### `Step 8.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:



___

![](../images/line1.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Setting Up Character Blueprint"> -->
![next up next tile](images/banner.png)

![](../images/line1.png)

| [previous](../fixing-model/README.md#user-content-fixing-mixamo-models)| [home](../README.md#user-content-ue4-animations) | [next](../character-bp/README.md#user-content-setting-up-character-blueprint)|
|---|---|---|
