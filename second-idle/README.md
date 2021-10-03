<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

### Time Out for Second Idle

<sub>[previous](../anim-bp/README.md#user-content-our-first-animation-blueprint) • [home](../README.md#user-content-ue4-animations) • [next](../second-idle-ii/README.md#user-content-time-out-for-second-idle-ii)</sub>

<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

Now we are going to add a state change when the idle animation times out. How will we do this? We will keep track of when the Velocity Length is 0 and add a timer. After 5 seconds we will switch to the alternate idle animation. Lets begin.

<br>

---


##### `Step 1.`\|`ITA`|:small_blue_diamond:

Open the **aj_AnimBlueprint** and go to the **Event Graph**. *Add* a new **Variable** called `bDoesIdleTimeOut` and make it **Variable Type** `Boolean`. *Set* **Private** to `true` and add a **Tooltip** of `Switch to alternate idle when main idle times out`.

![add boolean bDoesIdleTimeOut to anim blueprint](images/AddDoesIdleTimeOutBooleanVar.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

*Add* a new **Variable** called `IdleTimer` and make it **Variable Type** `Float`. Set **Private** to `true` and add a **Tooltip** of `Calculates time in seconds when velocity length is 0`.

![add idletimer float variable](images/AddIdleTimerVariable.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 3.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now we need to check if the Vector Length is 0. Add a **Branch** node to the right of the other nodes.

![add branch node](images/AddBranchNodeToAnimBP.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 4.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now we are going to see if this vector is close enough to zero. *Pull* from the **Return Value** pin on the **Vector Length** node and look for **Nearly Equal (float)** node.

![add nearly equal node](images/NearlyEqualVectorLength.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 5.`\|`ITA`| :small_orange_diamond:

We will leave the default values alone. We want it to be close to `0.0` and the error tolerance seems fine. *Connect* the execution pin form the **Set Speed** node to the **Branch** node. *Connect* the **Return Value** pin from the **Nearly Equal** node to the **Branch** node. *Connect* **Nearly Equal | Return Value** to the **Branch | Condition** pin.

![connect set speed to branch and return value to nearly equal](images/ExecutionPinsAndBranchCondition.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 6.`\|`ITA`| :small_orange_diamond: :small_blue_diamond:

*Drag* a **Get Idle Timer** variable to the graph and add a **Get World Delta Seconds** node.

![add get idle time node and world delta seconds node](images/GetIdleTimerDeltaSeconds.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 7.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Add two **Set Idle Timer** nodes. *Connect* each to the **True** and **False** execution pins of the **Branch** node.

![add two set idel timer nodes and attach both to branch](images/AddTwoSetIdleTimerNodes.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 8.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Add* a **float + float** node and put it between the **Idle Timer** and **Set Idle Timer** nodes.

![Add a float plus float node](images/AddFloatPlusFloatNode.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 9.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Connect* the outut of **Idle Timer** and **Get World Delta Seconds** nodes to the input pins of the **Addition** node. *Send* the output to the **Set Idle** Timer pin connected to the **Branch | True** execution pin.

![connect idle timer and get world delat to addition node](images/ConnectAdditionPinsForTimer.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 10.`\|`ITA`| :large_blue_diamond:

Now we want to check to see if we have been idling for more than 5 seconds. Add a **Branch** node and a **float >= float** node and set the bottom pin value to `5.0`.

![check to see if idle is longer than 5 seconds](images/LongerThan5SecondsInIdle.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 11.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: 

*Connect* the execution pin from **Set Idle Timer** node to the new **Branch** node. *Connect* the output pin of the **Set Idle Timer** to the **>=** node. *Send* the output of the **>=** node to the **Condition** pin of the **Branch** node.

![connect set idle timer to branch](images/ConnectIdletimerToBranch.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>


##### `Step 12.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

*Pull off* of the execution pin of the **Branch** node and select a **Set Does Idle Time Out?** node. Set this **boolean** to `true`.

![add set does idle time out node](images/PullOffExecutionPin.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 13.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

*Pull off* of the **Set Does Idle Timer Time Out?** node and select a **Set Idle Timer** node and set it to `0.0` seconds. *Add* a **comment** around these new nodes and call it `Idle Timer`.

![add set idle timer node set to 0](images/SetIdleTimeToZeroAddComment.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 14.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Go back to the **AJ_AnimBlueprint | Anim Graph** tab and *double click* on the **Core Locomotion** node.

![go to core locomotion in animblueprint anim graph](images/DoubleClickCoreLocoStateMach.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 15.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: 

Now you should see our only **IdleWalkRun** state. *Right click* above this on the open graph and select **Add State**.

![add state](images/AddNewAlternateIdleState.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 16.`\|`ITA`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

*Call* this new state `AlternateIdle`. *Connect* the state from **IdleWalkRun** to **AlternateIdle** states. Look at the two icons next to the arrows. This handles the logic of when we switch to and from these animations.

![call new state alternate idle and connect to idle walk run](images/CallItAlternateIdle.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 17.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Double click on the left hand button next to the arrow going from **IdleWalkRun** to **AlternateIdle** to adjust the logic for this transition.

![enter idlewalkrun to alternate idle state by double clicking arrow](images/DoubleClickLeftHandLogic.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 18.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

The logic is simple. It will transition when the idle time out boolean switches to true. So add a **Get Does Idle Time Out?** node and attach it to the **Result** node so it can enter the transition.

![add get does idle time out node](images/AddDoesIdleTimeOutTrue.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 19.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Go back to the **Core Locomotion** state screen. Now *double click* on the right hand transition from **Alternate Idle** back to **IdleWalkRun**.

![go to alternate idle to idlewalk run transition](images/DoubleClickRightHandLogic.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 20.`\|`ITA`| :large_blue_diamond: :large_blue_diamond:

Drag a **Get Does Idle Time Out?** variable onto the graph.

![add a get does idle time out node to graph](images/AddDoesIdleTimeOutVari.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 21.`\|`ITA`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond:

Now we are looking for the opposite so we want the **Does Idle Time Out?** to be false. So we pull off the pin and select a **NOT** node which looks to see if it is the opposite of **True** (false).

![add NOT node](images/BooleanNotNode.jpg)

___


<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

<img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Time Out for Second Idle II">

<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

| [previous](../anim-bp/README.md#user-content-our-first-animation-blueprint)| [home](../README.md#user-content-ue4-animations) | [next](../second-idle-ii/README.md#user-content-time-out-for-second-idle-ii)|
|---|---|---|
