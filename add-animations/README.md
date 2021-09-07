<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

### Add Animations

<sub>[previous](../fixing-model/README.md#user-content-fixing-mixamo-models) • [home](../README.md#user-content-ue4-animations) • [next](../character-bp/README.md#user-content-setting-up-character-blueprint)</sub>

<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

Lets add the animations we downloaded to the game and map them to the skeleton so that they drive the skeletal mesh.

<br>

---


##### `Step 1.`\|`ITA`|:small_blue_diamond:

Add to the Content Browser's Character | AJ folder, a new sub-folder called `Animations`.

![add folder called Character | AJ | Animations](images/AJAnimationsFolder.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

Press the <kbd>Import</kbd> button and select the six animations we downloaded from Mixamo:

![drag and drop animations downloaded from mixamo](images/ImportAnimations.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 3.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now the **FBX Import Options** appear. *Select* the **Skeleton** tab and select the skeleton asset we just downloaded. There should only be one option.

![select skeleton from player dowloaded](images/ImportSkeleton.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 4.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Once you select the skeleton press the <kbd>Import All</kbd> button.

![import all button](images/ImportAllMotionAnimation.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 5.`\|`ITA`| :small_orange_diamond:

Now this will take a while as it is solving the animation to this skeleton.

![UE4 progress bar importing animations](images/ImportingAnimationsTakeTime.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 6.`\|`ITA`| :small_orange_diamond: :small_blue_diamond:

Double click each animation then watch them. Rename the animation appropriately.

![slow walk animation frame](images/PlayAnim.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 7.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

I have named mine `Creep_Walk`, `Fast_Run`, `Idle`, `Idle_Fidget` and `Run and Walk`. This gives me two run cycles, an idle and walk animations to use in our animation graph.

![animation name](images/NameEachAnim.jpg)

___


<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

<img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Setting Up Character Blueprint">

<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

| [previous](../fixing-model/README.md#user-content-fixing-mixamo-models)| [home](../README.md#user-content-ue4-animations) | [next](../character-bp/README.md#user-content-setting-up-character-blueprint)|
|---|---|---|
