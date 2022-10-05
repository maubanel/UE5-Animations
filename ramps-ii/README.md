![](../images/line3.png)

### Speed Up & Down Ramps II

<sub>[previous](../ramps/README.md#user-content-speed-up--down-ramps) • [home](../README.md#user-content-ue4-animations) • [next](../ramps-iii/README.md#user-content-speed-up--down-ramps-iii)</sub>

![](../images/line3.png)

Running up & down ramps continued...

<br>

---


##### `Step 1.`\|`ITA`|:small_blue_diamond:

Now we need to cast a line down the player based on his world angle. So we will drag and drop the **Capsule Component** from the **Component** menu and then pull the pin and add a **Get Up Vector** node. This gets a vector pointing upwards from his head.

![add a get up vector node](images/GetUpVectorOfCapsuleComponent.jpg)

![](../images/line2.png)

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

Now *add* a **Vector * Float** node. We need to scale this normalized vector 300 units in the opposite direction. Set the multiplication amount to `-300.0` (multiplying a vector by -1 reverses the direction of the vector, since Unreal is Z-Up this will make it 300 cm downwards). 

![multiply by -300](images/Down300Units.jpg)

![](../images/line2.png)

##### `Step 3.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

To see this line trace we will turn the **Draw Debug Type** to `For One Frame`. This will allow us to see the line being cast and wether it collides with a surface.

![change draw debug type to for one frame](images/DrawDebugLine.jpg)

![](../images/line2.png)

##### `Step 4.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now this value is in local space and we need to translate it to world space. We do this by adding the actual world location. *Pull off* the **Multiplication** pin and select a **vector + vector** node. *Add* the **Return Value** to the **Get Actor Location**. *Send* the output to the **End** pin of the **Line Trace By Channel** node.

![add9t90jm node summing Return value to Get Actgor Location going to the Line Trace node](images/SetEndForFirstLineCast.jpg)

![](../images/line2.png)

##### `Step 5.`\|`ITA`| :small_orange_diamond:

I add a comment explaining my actions.

![add code comments](images/LocalToGlobalComment.jpg)

![](../images/line2.png)

##### `Step 6.`\|`ITA`| :small_orange_diamond: :small_blue_diamond:

*Run* the game. You should see a red line casting downwards with a hit target on the ground beneath the player when the player is moving and no line cast when they stop.

https://user-images.githubusercontent.com/5504953/134693811-e7d62071-15c4-4623-830c-1ee9b8658ed3.mp4

![](../images/line2.png)

##### `Step 7.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Now I need to cast a second line then be the angle of the slope. This will tell me if I am going up or down the slope as well. I am going to cast a line 10 units ahead based on the direction of their **Velocity**. *Add* a second **Line Trace By Channel** node to the graph beneath the previous one. To the left add a **Get Actor Location** node. Set **Draw Debug Type** to `For One Frame`.

![Add second line trace by channel and get actor location nodes](images/SecondLineTraceGetActorLocation.jpg)

![](../images/line2.png)

##### `Step 8.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

We need to get forward by 10 velocity units from the current location. *Add* a **vector + vector** node and connect the input to the **Return Value** of the **Get Actor Location** pin. Send the output to the **Start** pin of the **Line Trace By Channel** node.

![add return value and get actor location vectors together and send to line trace by channel](images/VectorPlusVectorStartSecondLineTrace.jpg)

![](../images/line2.png)

##### `Step 9.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Drag* a **Character Movement** node from the **Component** menu. *Drag off* of its pin and select a **Get Velocity** node.

![add a get velocity node](images/GetTheVelocity.jpg)

![](../images/line2.png)

##### `Step 10.`\|`ITA`| :large_blue_diamond:

Grab the output of the **Velocity** pin and select a **Normalize** node. Now add a **vector * float** node to multiply the vector by `10.0` to scale it up. Remember a normalized vector is 1 unit in length. Multiplying it by 10 sends it forward by 10 units. Send this output to the second side of the vector **Addition** node.

![multiply veocity by 10](images/FinishGettingStartPoint10UnitsInFrontOfPlayer.jpg)

![](../images/line2.png)

##### `Step 11.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: 

The end unit will be 300 units underneath the player. *Add* a **vector + vector** node.

![add vector + vector nodez](images/CheckDownwardsBy300ForSecondLineTrace.jpg)

![](../images/line2.png)


##### `Step 12.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

*Connect* the output of the **Multiplication** pin where you go down 300 units from the center downwards to the topside of the addition node. Take the output of the **Addition** pin to the input of the other end of the addition node. *Send* the output of to the **End** pin in the **Line Trace by Channel** node. Set the **Draw Debug Type** to `For One Frame` to test out.

![connect multiply to addition pin then go to end of line trace by channel](images/ConnectEndOfSecondLineByChannel.jpg)

![](../images/line2.png)

##### `Step 13.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

*Connect* the execution pin between the two **Line Trace by Channel** nodes. *Play* the game and see if you can see the second vector. It renders two vectors very close to each other (which is what we want) which might still looks like one single vector. What we need to do is termporarilly make them further apart. Change the distance of the **Multiplication** pin from `10.0` to `50.0` and make sure the second vector is in front of the player.

![change length to 50](images/ChangeTo50.jpg)

![](../images/line2.png)

##### `Step 14.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

*Play* the game and you should now see the second vector. Set the **Multiplication** pin back to `10.0`.

https://user-images.githubusercontent.com/5504953/134770183-e9882c0c-d9f6-4af9-90b8-1b00ef7783a6.mp4

![](../images/line2.png)

##### `Step 15.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: 

To get the angle we need to results of the two line traces of where they hit on the ground. *Pull* from the **Out Hit** output pin of BOTH **Line Trace By Channel** nodes and select **Break Hit Result** to *split* the struct pins for the separate return value pins.

![break it result pins in both line grace by channels node](images/BreakHitResultsForBoth.jpg)

![](../images/line2.png)

##### `Step 16.`\|`ITA`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

*Add* a **Find Look at Rotation** node and break the output pins to their individual outputs by clicking on the pin and select **Split Struct Pin**.

![find look at rotation node](images/FindLookAtRotation.jpg)

![](../images/line2.png)

##### `Step 17.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

*Connect* the **Location** the top **Break Hit Results** node to the **Start** pin of the **Find Look at Rotation** node. *Send* the second **Location** pin to the **Target** pin on the **Find Look at Rotation** node. So we are looking from the collision point just beneath us to the one 10 units ahead.

![connect pins to collide with ground](images/ConnectStartTargetGetAngle.jpg)

![](../images/line2.png)

##### `Step 18.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Lets print this on the screen to make sure we have this right. Add an **Append String** node and in the **A** box put in `Pitch`:.

![add append string and add Pitch to A](images/PrintOnScreenPitch.jpg)

![](../images/line2.png)

##### `Step 19.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Connect* the **Return Value Y (Pitch)** to the **B** pin of the **Append String** node:

![connect Pitch pin to the B side of the append node](images/AppendPitchOutput.jpg)

![](../images/line2.png)

##### `Step 20.`\|`ITA`| :large_blue_diamond: :large_blue_diamond:

*Pull off* of the output of the **Append** node and select the ***Print String*** node. *Change* the **Duration** to `0.0`.

![add print string node and send output of append node](images/AddPrintString.jpg)

![](../images/line2.png)

##### `Step 21.`\|`ITA`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond:

*Connect* the **Execution** pins from the first **Line Trace by Channel** to the second **Line Trace by Channel** to the **Print String** nodes.

![connect execution pins](images/ConnectExecutionPinsToPrint.jpg)

___


![](../images/line1.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Speed Up / Down Ramps III"> -->
![next up next tile](images/banner.png)

![](../images/line1.png)

| [previous](../ramps/README.md#user-content-speed-up--down-ramps)| [home](../README.md#user-content-ue4-animations) | [next](../ramps-iii/README.md#user-content-speed-up--down-ramps-iii)|
|---|---|---|
