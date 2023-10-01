![](../images/line3.png)

### Fixing Mixamo Models

<sub>[previous](../character-anim/README.md#user-content-download-character--animations) • [home](../README.md#user-content-ue4-animations) • [next](../add-animations/README.md#user-content-add-animations)</sub>

![](../images/line3.png)

There may or may not be issues with the skeletal meshe's material(s). Look carefully for any issues especially around, eyes, mouths and accessories. Compare what it looks like in Unreal versus what it looks like on Mixamo.  It should look the same. If your character has no issues you can move on to the [next section](../add-animations/README.md#user-content-add-animations).

<br>

---

##### `Step 1.`\|`ITA`|:small_blue_diamond:

There are some common issues with the materials. I see problems in the face in my model. I see 3 materials that control the mouth, brow and eyes. I look at one of the materials **Boy01_Eyes_MAT2** and see that it is feeding the **RGB** (Albedo) into the **Opacity** channel.  This really should be the **Alpha** channel of the texture. Change the channel going to the **Opacity** node instead to **Alpha**. Notice now how the graphics for the eyes, brows and mouth all of a sudden are opaque! Press the <kbd>Apply</kbd> button.

![streaks in face material](images/IssueWithAlph2.png)

![](../images/line2.png)

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

Repeat this for the brows material **Boy01_Brows_MAT2** which has the same problem. Connect the **A** channel and press the <kbd>Apply</kbd> button.

![repeat for mouth and brows.](images/browOpacityFix.png)

![](../images/line2.png)

##### `Step 3.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Repeat this for the mouth  material **Boy01_Mouth_MAT2** which have the same problem. Connect the **A** channel and press the <kbd>Apply</kbd> button..

![repeat for mouth and brows.](images/mouthOpacityFix.png)

![](../images/line2.png)

##### `Step 4.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Go back to the skeletal mesh and move the camera around the character. Make sure you have fixed all the material issues that arose. The issues you may have may be different depending on which character you selected. My face is all better now and looks like the version on ***Mixamo***.

![check model for errors](images/ModelFixedMaterials.png)

![](../images/line2.png)

##### `Step 5.`\|`ITA`| :small_orange_diamond:

Select the **File | Save All** then press the #<kbd>Revision Control</kbd> button and select **Submit Content**.  If you are prompted, select **Check Out** for all items that are not checked out of source control. Update the **Changelist Description** message and with the latest changes. Make sure all the files are correct and press the <kbd>Submit</kbd> button. A confirmation will pop up on the bottom right with a message about a changelist was submitted with a commit number. Quit Unreal and make sure your **Pending** tab in **P4V** is empty. **Submit** any work that is still in the editor.

![save all and submit to perforce](images/submitP4.png)

___


![](../images/line1.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Add Animations"> -->
![next up next tile](images/banner.png)

![](../images/line1.png)

| [previous](../character-anim/README.md#user-content-download-character--animations)| [home](../README.md#user-content-ue4-animations) | [next](../add-animations/README.md#user-content-add-animations)|
|---|---|---|
