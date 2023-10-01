![](../images/line3.png)

### Download Character & Animations

<sub>[previous](../setting-up/README.md#user-content-setting-up) • [home](../README.md#user-content-ue4-animations) • [next](../fixing-model/README.md#user-content-fixing-mixamo-models)</sub>

![](../images/line3.png)

There are many options available to us, but lets use a non UE4 solution to see just how easy it is to import an FBX file with animations. We will start by selecting a character then downloading some animations.

<br>

---

##### `Step 1.`\|`ITA`|:small_blue_diamond:

Navigate in a web browser to [mixamo.com](https://www.mixamo.com/#/) and you can sign in with your **Adobe** credentials (they are run by Adobe) or create a new account (it is free to use).

![mixamo website](images/LoginSignUpToMixamo.png)

![](../images/line2.png)

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

*Press* the **Characters** tab and *scroll* through their selection of character models. I will select **AJ** but you can pick the one of your choice. Once you have chosen press the <kbd>Download</kbd> button.

![select AJ character](images/SelectAJ.jpg)

![](../images/line2.png)

##### `Step 3.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

You will now get a **Download Settings** menu. We will leave the **Format** as `FBX` and the **Pose** as `T-pose`. Press the <kbd>Download</kbd> button to get the model.

![mixamo download menu](images/PressDownloadAgainDefaultSettings.jpg)

![](../images/line2.png)

##### `Step 4.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Press* on the **Animations** tab. Lets find some animations. Lets start with the regular run speed. *Type* `Run` in the **Search** menu and *click* through various runs. Pick a moderate speed run that you like. Now adjust the various settings to make it as you would like. Make sure the arms don't swing into the body polygons.

![run animation](images/FindRunAnimationAndPreview.png)

![](../images/line2.png)

##### `Step 5.`\|`ITA`| :small_orange_diamond:

Now the unreal engine will be propelling the player forward and backward. So we do not want the animation to translate through space. When you find an animation you like make sure you press the **In Place** toggle so that the player runs on the spot. *Make sure you do this for ALL your animations that are controlled by player or AI*. Make all adjustments then press the <kbd>Download</kbd> button.

![make sure inplace is checked](images/inPlace.png)

https://user-images.githubusercontent.com/5504953/132144425-3b043aff-a8a6-4de0-a65c-7435a532e222.mp4

![](../images/line2.png)

##### `Step 6.`\|`ITA`| :small_orange_diamond: :small_blue_diamond:

In the Download Settings you will need to make a change. We do not need the model every time, and now only need animation data that is solved to this model. Select the **Skin** drop down menu and change it to `Without Skin`. Press the <kbd>Download</kbd> button.

![download run animation with no skin](images/ExportRunWithoutSkin.jpg)

![](../images/line2.png)

##### `Step 7.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Repeat this process for a fast run. Make sure you select **In Place** and download this new animation as you did previously.

![download fast run animation](images/DownloadFastRunAnim.jpg)

![](../images/line2.png)

##### `Step 8.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Repeat for a slow walk animation. I found one that looks like he is sneaking up on someone.

![download slow walk animation](images/DownloadSlowWalk.jpg)

![](../images/line2.png)

##### `Step 9.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Download a normal speed walk.

![download normal walk speed animation](images/NormalSpeedWalk.jpg)

![](../images/line2.png)

##### `Step 10.`\|`ITA`| :large_blue_diamond:

Pick two idle animations. One that is just breathing and another one that we can cut to after a timer to give the animation some personality. My second animation is **Happy Idle**. Make sure you pick an idle that starts and stops in the same position and doesn't move around too much (so they don't collide with objects accidentally when they are triggered).

![select two idle animations](images/TwoIdlesDownload.png)

![](../images/line2.png)

##### `Step 11.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: 

Double click the **IntroToAnimation.uproject** from **P4V** to open up the game editor. Create two new folders called `Characters | AJ`. You can call the name of the second folder by the character you picked for the game (I picked AJ). Go to your **Downloads** folder and drag the file that has the characters name on it into the **AJ** character folder. As a hint, it will be the largest file (model is bigger than the animations, but they are all .fbx format).

Now in a production game we want to share the same base skeleton where we can. To learn more about this go to this [Skeletal Assets Unreal Training Video](https://www.youtube.com/watch?v=JkcJ5bjGPsg) to find out more. For us we will use the skeleton that is provided with this geometry. So make sure you leave **Skeleton** blank and you can leave all the other settings as default. It should set **Skeletal Mesh** and **Import Mesh** to `true` as it should detect the skeleton automatically.  If it doesn't set these to `true`.

![add Characters/AJ folder to game](images/ImportAJFbx.png)

![](../images/line2.png)


##### `Step 12.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

With the AJ model I got a few errors.  It looks like it had an issue with the facial textures. Now this imports a lot of files into the project. You should see a **Skeletal Mesh**, a **Physics Asset**, a **Skeleton**, a group of **Materials** and finally a group of **Textures**. If you picked a different character then your folder will have different files.

![folder full of skeletal mesh assets](images/LargeGroupOfFiles.png)

![](../images/line2.png)

##### `Step 13.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

In importing the mesh an error popped up telling me it had to duplicate textures.  It created three copies of `Boy01_FacialAnimMap`.  Right click the two copies and select the <kbd>Delete</kbd> button and then select the original file press the <kbd>Replace References</kbd> button to replace the refences with the one original file.  In my case I did not get this menu. If you can't replace the textures then we will manually fix them.

![duplicate textures](images/ImportError.png)

![](../images/line2.png)

##### `Step 14.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Now open up **Boy01_Eyes_MAT2**, **Boy01_Brow_MAT2** and **Boy01_Mouth_MAT2**.  Make sure all textures are pointing to the texture sheet with all the small images. There should be no compile errors in any of these three materials.

![leave settings default](images/SharingMesh.png)

![](../images/line2.png)

##### `Step 15.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: 

Create a new folder under **AJ** called `Materials`. *Drag and drop* to *move* the materials into this folder. The materials have the green line in their icon.

![move aj materials to materials folder](images/MoveAJMaterialsToFolder.png)

Create a new folder under **AJ** called `Textures`. *Drag and drop* to move the textures into this folder.

![move textures to AJ | Textures folder](images/MoveAJTexturesToFolder.png)

![](../images/line2.png)

##### `Step 16.`\|`ITA`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

Right click on the **Characters** folder and select **Fix Up Redirectors in Folder**. This will fix all the links to the files we moved around.  

*Double click* the **Physics** asset and look at it. You can see that this has the collision volumes that move with the mesh. The default settings should be fine. Notice that is has a simplified collision shape around each bone (a bone is a line between two joints in a skeleton).

![aj physics asset](images/PhysicsAsset.png)
![](../images/line2.png)

##### `Step 17.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:



![](../images/line2.png)

##### `Step 18.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:


![](../images/line2.png)

##### `Step 19.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:



![](../images/line2.png)

##### `Step 20.`\|`ITA`| :large_blue_diamond: :large_blue_diamond:

Open the **skeletal mesh**. Look at the left-hand side and you will see a list of bones that are on the skeleton.

![bones of skeletal mesh](images/PlayerBones.png)

![](../images/line2.png)

##### `Step 21.`\|`ITA`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond:

Double click the **Skeletal Mesh** and lets look at the model. Now when going from Mixamo to UE4 there are some errors in how the Materials are put together. In some cases it is quite prominent. With **AJ**, something is wrong with the face. We will fix this on the next page.

![look at skeletal mesh to see if materials are correct](images/SkeletalMesh.png)
___

![](../images/line2.png)

##### `Step 22.`\|`ITA`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Select the **File | Save All** then quit UE5.   Go to **P4V** and go the top project folder (the one that holds the `.uproject` file and **Content** folder) and press the <kbd>+Add</kbd> then <kbd>OK</kbd> button.  This makes sure any files that Unreal didn't add get added to source control. Press the <kbd>Submit</kbd> button and enter a message explaining the work done.  Press <kbd>Submit</kbd>.

![save all and submit to perforce in P4V](images/submitP4.png)

___


![](../images/line1.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Fixing Mixamo Models"> -->
![next up next tile](images/banner.png)

![](../images/line1.png)

| [previous](../setting-up/README.md#user-content-setting-up)| [home](../README.md#user-content-ue4-animations) | [next](../fixing-model/README.md#user-content-fixing-mixamo-models)|
|---|---|---|
