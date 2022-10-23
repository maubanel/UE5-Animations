![](../images/line3.png)

### Speed Up & Down Ramps II

<sub>[previous](../ramps/README.md#user-content-speed-up--down-ramps) • [home](../README.md#user-content-ue4-animations)</sub>

![](../images/line3.png)

Running up & down ramps continued...

<br>

---


##### `Step 1.`\|`ITA`|:small_blue_diamond:



![add a get up vector node](images/autoAllKeys.png)

![](../images/line2.png)

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 



![multiply by -300](images/flattenHumps.png)

![](../images/line2.png)

##### `Step 3.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:


![change draw debug type to for one frame](images/capsuleGetRight.png)

![](../images/line2.png)

##### `Step 4.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:



![add9t90jm node summing Return value to Get Actgor Location going to the Line Trace node](images/upVector.png)

![](../images/line2.png)

##### `Step 5.`\|`ITA`| :small_orange_diamond:

![add9t90jm node summing Return value to Get Actgor Location going to the Line Trace node](images/slopeInAngles.png)


![](../images/line2.png)

##### `Step 6.`\|`ITA`| :small_orange_diamond: :small_blue_diamond:

![add9t90jm node summing Return value to Get Actgor Location going to the Line Trace node](images/gravitySpeedOR.png)

![](../images/line2.png)

##### `Step 7.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:


![Add second line trace by channel and get actor location nodes](images/defaultGravity.png)

![](../images/line2.png)

##### `Step 8.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:



![add return value and get actor location vectors together and send to line trace by channel](images/getValueFromCurve.png)

![](../images/line2.png)

##### `Step 9.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:



![add a get velocity node](images/sprintMultiplier.png)

![](../images/line2.png)

##### `Step 10.`\|`ITA`| :large_blue_diamond:


![multiply veocity by 10](images/sprintMulti.png)

![](../images/line2.png)

##### `Step 11.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: 



![add vector + vector nodez](images/sprintMultimulti.png)

![](../images/line2.png)


##### `Step 12.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 



![connect multiply to addition pin then go to end of line trace by channel](images/switchToMultiplier.png)

![](../images/line2.png)

##### `Step 13.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

![add vector + vector nodez](images/slowWalkMulti.png)


![](../images/line2.png)

##### `Step 14.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

![change length to 50](images/setNewMaxSp.png)

![](../images/line2.png)

##### `Step 15.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: 



![break it result pins in both line grace by channels node](images/connectExecPins.png)

![](../images/line2.png)

##### `Step 16.`\|`ITA`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 



![find look at rotation node](images/setSpeedScalar.png)

![](../images/line2.png)

##### `Step 17.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

*Press* the <kbd>Play</kbd> button.  Run, sprint and slow walk up and down all ramps and see that the speed changes!

https://user-images.githubusercontent.com/5504953/197391355-ead384c6-6f93-4499-9dd3-272f3e96fae2.mp4

![](../images/line2.png)

##### `Step 18.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:


![add append string and add Pitch to A](images/turnOffDebug.png)

![](../images/line2.png)

##### `Step 19.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Press* the <kbd>Play</kbd> button. Now you have a final version of a basic third person player.

https://user-images.githubusercontent.com/5504953/197391363-a29b911d-6e5d-4c35-841d-87761b317051.mp4

![](../images/line2.png)

##### `Step 20.`\|`ITA`| :large_blue_diamond: :large_blue_diamond:

Select the **File | Save All** then quit UE5.   Go to **P4V** and go the top project folder (the one that holds the `.uproject` file and **Content** folder) and press the <kbd>+Add</kbd> then <kbd>OK</kbd> button.  This makes sure any files that Unreal didn't add get added to source control. Press the <kbd>Submit</kbd> button and enter a message explaining the work done.  Press <kbd>Submit</kbd>.

![save all and submit to perforce in P4V](images/submitP4.png)


| `animation.character`\|`THE END`| 
| :--- |
| **That's All Folks!** Thanks for sticking around. That's it for this lesson. |

![](../images/line1.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=The End!"> -->
![next up next tile](images/banner.png)

![](../images/line1.png)

| [previous](../ramps/README.md#user-content-speed-up--down-ramps)| [home](../README.md#user-content-ue4-animations) | 
|---|---|
