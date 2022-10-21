![](../images/line3.png)

### Jumping Animation II

<sub>[previous](../jumping/README.md#user-content-jumping-animation) • [home](../README.md#user-content-ue4-animations) • [next](../walk-sprint/README.md#user-content-slow-walk--sprint)</sub>

![](../images/line3.png)

Continue implementing jump animation...


<br>

---


##### `Step 1.`\|`ITA`|:small_blue_diamond:

*Open* the **AnimmBP_AJ | Event Graph**. We need to access the character's **IsJumping** variable. We are not in the right class with the Pawn Owner. *Drag* a **Get Character** node from the **Variables** section.  Then *pull* off of it's output pin and select a **Cast To BP AJ** node.

![cast pawn owner to aj_character](images/CastToCharacterBP.png)

![](../images/line2.png)

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

*Connect* the **Sequence | Then 1** pin to the **Cast to BP_AJ** execution pin. 

We need a variable in the animation blueprint to run our transitions with. Add a new **Boolean** Variable named `PressedJump` and make it **Private** and set the tooltip to `Jump button was pressed`. *Put* it in **Catogory** `Player Physics`.

![add new boolean bPressedJump](images/AddPressedJump.png)


![](../images/line2.png)

##### `Step 3.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Pull off the As **BP_AJ_Character** pin on the **Cast** node and select **Get IsJumping**.

![ad get isjumping node](images/GetIsJumpingAJCharacter.png)


![](../images/line2.png)

##### `Step 4.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Drag and drop* the Set **PressedJump** node and connect its execution pin to the **Cast** node. Connect the **IsJumping** pin to the **PressedJump?** pin. *Connect* the execution pins from **Cast** to **BP_AJCharacter** to Set **bPressedJump**.

![connect pins](images/SetIsJumpingNode.png)


![](../images/line2.png)

##### `Step 5.`\|`ITA`| :small_orange_diamond:


![](../images/line2.png)

##### `Step 6.`\|`ITA`| :small_orange_diamond: :small_blue_diamond:


![](../images/line2.png)

##### `Step 7.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:


![](../images/line2.png)

##### `Step 8.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

To keep things need add a **Sequence** node between the **Is Valid** node and the **Set Are We in Air?** node. *Reconnect* **Is Valid** to the **Sequence** input node then the **Then 0** to S**et Are We in Air** node. *Send* the **Then 1** pin to the **Cast** to **BP_AI_Character** node.

![add sequence node connet pins](images/AddSequenceNode.jpg)

![](../images/line2.png)

##### `Step 9.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Go back to the **Anim Graph | Core Locomotion** section of the animatin blueprint and *click on* the transition button from **IdleWalkRun** to **Jump** transition.

![go to idlewalkrun to jump transition in core locomotion](images/TransitionWalkToJump.jpg)

![](../images/line2.png)

##### `Step 10.`\|`ITA`| :large_blue_diamond:

Add a **Get bPressedJump** node and *connect* the pin to the **Result | Can Enter Transition** pin.

![add a bPressedJump node and connect it to can enter transition](images/PressedJumpToResult.jpg)

![](../images/line2.png)

##### `Step 11.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: 

Go back to the **Anim Graph | Core Locomotion** page. *Double click* the **Jump** state to assign the **Jump_Start** animation.

![open jump state](images/DoubleClickJump.jpg)

![](../images/line2.png)


##### `Step 12.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

Drag and drop the **Jump_Start** animation to the graph. *Connect* the animation nodes with the **Final Animation Pose**.

![add jump_start animation to jump state](images/HookUpJumpStartAnim.jpg)

![](../images/line2.png)

##### `Step 13.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Go back to the **Anim Graph | Core Locomotion** screen. *Double click* on the transition in the **Anim Graph | Core Locomotion** page from **IdleWalkRun** to **Falling**.

![go idelwalkrun to falling transition](images/WalkToFallTransition.jpg)

![](../images/line2.png)

##### `Step 14.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

This is for falling off the edge of an object without jumping. We need to find out if we are in the air but not pressing the jump button. *Drag* a **Get Are We in Air** and **Get Pressed Jump** nodes onto the graph.

![add get are we in air and get pressed jump nodes](images/CheckIfInAirJumpNotPressed.jpg)

![](../images/line2.png)

##### `Step 15.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: 

*Drag* off of the **Are We in Air?** pin and *add* a **Boolean AND** node.

![add boolean AND node](images/BooleanAnd.jpg)

![](../images/line2.png)

##### `Step 16.`\|`ITA`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

*Drag off* of the **Pressed Jump** pin and select **NOT Boolean**. *Connect* it to the input of the **AND** pin. *Connect* the output of the **AND** node to **Result** node.

![connect pressed jump to NOT Boolean to AND to Result](images/ConnectOuputOfAndToResult.jpg)

![](../images/line2.png)

##### `Step 17.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

*Double click* on the **Jump** to **Falling** transition button on the **Anim Graph | Core Locomotion** screen.

![enter the jump to falling transition](images/DoubleClickJumpFallingTransition.jpg)

![](../images/line2.png)

##### `Step 18.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Right click* on the graph and select a **Time Remaining (ratio) (Jump_Start)** node.

![add a Time Remaining (ratio) node](images/TimeRemainingJumpToFall.jpg)

![](../images/line2.png)

##### `Step 19.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Pull off* of the **Return Value** pin and select a **float <= float** node. *Set* the bottom to `0.5`. *Connect* the output to the **Result** pin. *Press* <kbd>Compile</kbd> on all open blueprints and the warning will disapear.

![add a float <= with bottom value set to .5](images/LessThanPointSevenFive2.png)

![](../images/line2.png)

##### `Step 20.`\|`ITA`| :large_blue_diamond: :large_blue_diamond:

Press *play* and run around and fall off edge and jump. Make sure both transitions of running off edge and jumping are working correctly? I run up to the cube and the character penetrates it too much for my liking. The head when jumping up the wall gets buried inside the wall geometry. Lets fix this.

https://user-images.githubusercontent.com/5504953/133070942-118cb874-f74f-48c3-8a71-a2a381dc69c0.mp4

![](../images/line2.png)

##### `Step 21.`\|`ITA`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond:

Go to the **BP_AJ_Character** blueprint and *select* the **Mesh** component. I adjust the mesh back on the **Y** Location a bit.

![adjust y location of ajcharacter bp](images/MovingCharacterFurtherBack.jpg)

![](../images/line2.png)

##### `Step 22.`\|`ITA`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:

I then go to the **Capsule** component and increase the **Capsule Radius**. For my character `70.0` seems to work fine. I also adjusted the height as it was a bit short to a **Capsule Half Height** of `95.0`.

![increase radius of capsule to 60](images/CapsuleRadiusGreater.png)

![](../images/line2.png)

##### `Step 23.`\|`ITA`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now I like the collision much better. The player small amount of penetration does not bother me and the collisions feel better.  

Select the **File | Save All** then press the <kbd>Source Control</kbd> button and select **Submit to Source Control...**.  Enter a **Changelist Description** and then press <kbd>Submit</kbd>.  Open up **GitHub Desktop** and select **Push origin** to update the server with the latest changes.

https://user-images.githubusercontent.com/5504953/135758442-fcf8a098-5c4b-4bf4-847c-a7ae513f6e55.mp4

![save, commit and push to github](images/GitHub.png)

___


![](../images/line1.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Slow Walk & Sprint"> -->
![next up next tile](images/banner.png)

![](../images/line1.png)

| [previous](../jumping/README.md#user-content-jumping-animation)| [home](../README.md#user-content-ue4-animations) | [next](../walk-sprint/README.md#user-content-slow-walk--sprint)|
|---|---|---|
