# PILLARS
* **FOCUS**: Complete the task with the essentials. Do not ﻿assume that further features are required. 
* **EFFECTIVE**: It’s better to work 2 weeks instead of working one week and then spend 2 weeks solving bugs.
* **SIMPLE**
* **AWARE**: Bug randomly fixed by an update are not solved. Aim at understanding and solving their source cause.
* **UNBROKEN**: Compile it. Run it. Use it. Please test the feature before sending it to review.
* **COHESIVE**: Everything we write should look like one person writes it all.


# VERSION CONTROL
* Add a new *branch* for each *card* or each *bug*.
* Add a specific folder for a new feature and gather all files there. After approval assign everything to its folder.
* `merge master` inside your branch before asking a review
* Create proper commits: 
```
git commit -m “-[Tag] - [Main/Secondary] [Commit_Title]” -m “-SCENE: main changes in scene 
-CODE: list of changes in code etc.”
```
### COMMIT TAGS

!G | !B | !A | !N | !U | !R
------------ | ------------- | ------------- | ------------- | ------------- | -------------
Gameplay change | Bug fix | A change on art | Network Improvement | Update of assets | Assets removal

# CODING
* **Decouple** 
  * A `class` has 250 lines max and references 2 other classes at most (Except for composition)
  * A `method` has 50 lines max, does one thing (*cohesion*), and requires 5 parameters at most.
* *Logic **or** view*: logic script contains no view script (such as UI)
* Use **Assertions** instead of exceptions for error checking.
* Use **Assertions** instead of flags such as `if (anything != null)`
* Each scene can run independently
* UI: each ui element will have an [actor](https://gamedevacademy.org/lessons-learned-in-unity-after-5-years/) and multiple actor elements, no master components
* *Seal*: always **seal** the end class to [help the compiler with virtual members](http://codebetter.com/patricksmacchia/2008/01/05/rambling-on-the-sealed-keyword/)
* Use Scriptable Objects [wisely](https://www.youtube.com/watch?v=raQ3iHhE_Kk) (also [here](https://stackoverflow.com/questions/56054864/what-is-the-best-practice-to-load-scriptableobjects-to-single-prefab-multiple-pr/56063333#56063333)), for shared values, systems and as event listeners.
* *Strings*: use only **const strings**. Group them inside files used only for these constants.
* Follow *CQS* => Command (change/noreturn) vs Query (nochange/return)
* Cache Components on Awake. Do not use GetComponent() anywhere else
* Use the JLog and avoid Debug.Logs and or Print
* Use weak parameter types and strong return types. `HighLevelClass Method (iLowLevelInterface interface);`
* Assume that large objects are long lived, and small objects are short lived
* Never overwrite source codes from the Plugin folder. Override or extend it.

### CODING CONVENTIONS 
* Prioritize readability above performance, we can change code later
* COMMENTS are very few and very relevant
* Follow [C# Coding Standards and Naming Conventions](https://github.com/ktaranov/naming-convention/blob/master/C%23%20Coding%20Standards%20and%20Naming%20Conventions.md)
