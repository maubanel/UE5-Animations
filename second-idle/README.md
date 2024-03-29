![](../images/line3.png)

### Time Out for Second Idle

<sub>[previous](../anim-bp/README.md#user-content-our-first-animation-blueprint) • [home](../README.md#user-content-ue4-animations) • [next](../second-idle-ii/README.md#user-content-time-out-for-second-idle-ii)</sub>

![](../images/line3.png)

Now we are going to add a state change when the idle animation times out. How will we do this? We will keep track of when the Velocity Length is 0 and add a timer. After 5 seconds we will switch to the alternate idle animation. Lets begin.

---

##### `Step 1.`\|`ITA`|:small_blue_diamond:

Open the **ABP_AJ** and go to the **Event Graph**. *Add* a new **Variable** called `bDoesIdleTimeOut` and make it **Variable Type** `Boolean`. *Set* **Private** to `true` and **Description** to `timeout boolean for alternate idle` and add a **Cateogry** of `Player Physics`.

![add boolean bDoesIdleTimeOut to anim blueprint](images/AddDoesIdleTimeOutBooleanVar.png)

![](../images/line2.png)

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

*Add* a new **Variable** called `IdleTimer` and make it **Variable Type** `Float`. Set **Private** to `true` and add a **Tooltip** of `Calculates time in seconds when velocity length is 0`.

![add idletimer float variable](images/AddIdleTimerVariable.png)

![](../images/line2.png)

##### `Step 3.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now we are going to see if this vector is close enough to zero. *Pull* from the **Return Value** pin on the **Set Speed** node and look for **Nearly Equal (float)** node. Now we need to check if the Vector Length is 0. Add a **Branch** node to the right of the **Set Speed** node.

![add branch node](images/AddBranchNodeToAnimBP.png)

![](../images/line2.png)

##### `Step 4.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

We will leave the default values alone. We want it to be close to `0.0` and the error tolerance seems fine. *Connect* the execution pin from the **Set Speed** node to the **Branch** node. *Connect* the **Return Value** pin from the **Nearly Equal** node to the **Branch** node.  *Drag* a **Get Idle Timer** variable to the graph.

![connect set speed to branch and return value to nearly equal](images/ExecutionPinsAndBranchCondition.png)

![](../images/line2.png)

##### `Step 5.`\|`ITA`| :small_orange_diamond:

*Add* a **Get Delta Seconds** node.

![add get idle time node and world delta seconds node](images/GetIdleTimerDeltaSeconds.png)

![](../images/line2.png)

##### `Step 6.`\|`ITA`| :small_orange_diamond: :small_blue_diamond:

Add two **Set Idle Timer** nodes.

![add two set idel timer nodes and attach both to branch](images/AddTwoSetIdleTimerNodes.png)

![](../images/line2.png)

##### `Step 7.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

*Add* a **float + float** node and put it between the **Idle Timer** and **Set Idle Timer** nodes. *Connect* the outut of **Idle Timer** and **Get Delta Seconds** nodes to the input pins of the **Addition** node. *Send* the output to the **Set Idle** Timer pin.  Connected to the **Branch | True** execution pin. Connect the **False** execution pin to the second **Set Timer** leaving the **Idle Timer** value set to the default of `0`.  Essentially if the player is moving then reset the timer to zero.  If true add the time since last frame.

![Add a float plus float node](images/AddFloatPlusFloatNode.png)

![](../images/line2.png)

##### `Step 8.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now we want to check to see if we have been idling for more than 5 seconds. Add a **Branch** node and a **float >= float** node and set the bottom pin value to `5.0`.

![check to see if idle is longer than 5 seconds](images/LongerThan5SecondsInIdle.png)

![](../images/line2.png)

##### `Step 9.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Connect* the execution pin from **Set Idle Timer** node to the new **Branch** node. *Connect* the output pin of the **Set Idle Timer** to the **>=** node. *Send* the output of the **>=** node to the **Condition** pin of the **Branch** node.

![connect set idle timer to branch](images/ConnectIdletimerToBranch.png)

![](../images/line2.png)

##### `Step 10.`\|`ITA`| :large_blue_diamond:

*Pull off* of the execution pin of the **Branch** node and select a **Set Does Idle Time Out** node. Set this **boolean** to `true`.

![add set does idle time out node](images/PullOffExecutionPin.png)

![](../images/line2.png)

##### `Step 11.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: 

*Add* a **comment** around these new nodes and call it `Idle Timer`.

![add set idle timer node set to 0](images/SetIdleTimeToZeroAddComment.png)

![](../images/line2.png)


##### `Step 12.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

Go back to the **ABP_AJ | Anim Graph** tab and *double click* on the **BasicLocomotion** node.

![go to core locomotion in animblueprint anim graph](images/DoubleClickCoreLocoStateMach.png)

![](../images/line2.png)

##### `Step 13.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Now you should see our only **IdleWalkRun** state. *Right click* above this on the open graph and select **Add State**. Now we will be switching to the alternate animation state based on the player not controlling the game character for at least 5 seconds.  If the player hits any valid button or key we will switch back to the regular motion tree. *Call* this new state `AlternateIdle`. 

![add state](images/CallItAlternateIdle.png)

![](../images/line2.png)

##### `Step 14.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

*Connect* the state from **IdleWalkRun** to **AlternateIdle** states **and** back again. There should be two arrows coming to and from **both** states. Look at the two icons next to the arrows. This handles the logic of when we switch to and from these animations! This dicates when the animation moves from **IdleWalkRun** to **Alternate Idle** and back.

![add state](images/twoArrows.png)

![](../images/line2.png)

##### `Step 15.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: 

Double click on the left hand button next to the arrow going from **IdleWalkRun** to **AlternateIdle** to adjust the logic for this transition. The logic is simple. It will transition when the idle time out boolean switches to true. So add a **Get Does Idle Time Out** node and attach it to the **Result** node so it can enter the transition.

![add get does idle time out node](images/AddDoesIdleTimeOutTrue.png)

![](../images/line2.png)

##### `Step 16.`\|`ITA`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

Go back to the **Core Locomotion** state screen. Now *double click* on the right hand transition from **Alternate Idle** back to **IdleWalkRun**. Drag a **Get Does Idle Time Out?** variable onto the graph. Now we are looking for the opposite so we want the **Does Idle Time Out?** to be false. So we pull off the pin and select a **NOT** (Math | NOT Boolean) node which looks to see if it is the opposite of **True** (false).

![add NOT node](images/BooleanNotNode.png)

![](../images/line2.png)

##### `Step 17.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

*Connect* the output of the **NOT** node to the **Can Enter Transition** pin in the **Result** node.

![conect not to can enter transition node](images/OutputOfNotToTransition.png)

![](../images/line2.png)

##### `Step 18.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Go back to the **Basic Locomotion** state tab. Now we have dealt with the transitions but not the actual animation in this new state. *Double click* the **Alternate Idle** node. Drag a reference to **SpecialIdle** to the open graph.

![add idle_fidget to graph](images/PlayIdleFidget.png)

![](../images/line2.png)

##### `Step 19.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

**Connect** the animation pins and then *press* the <kbd>Compile</kbd> button. That should do it for the animation blueprint. Press the <kbd>Compile</kbd> button.

![connect animation pins and compile](images/ConnectAnimationPinsAlternateIdle.png)


![](../images/line2.png)

##### `Step 20.`\|`ITA`| :large_blue_diamond: :large_blue_diamond:

Now go into the game. After 5 seconds the player should go to the alternate idle. But he/she never leaves this state. We now want to reset the Does Idle Time Out? variable back to false. 

https://github.com/maubanel/UE5-Animations/assets/5504953/e1f128db-1ffd-42bf-9257-144349f97410

![](../images/line1.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Time Out for Second Idle II"> -->
![next up next tile](images/banner.png)

![](../images/line1.png)

| [previous](../anim-bp/README.md#user-content-our-first-animation-blueprint)| [home](../README.md#user-content-ue4-animations) | [next](../second-idle-ii/README.md#user-content-time-out-for-second-idle-ii)|
|---|---|---|
