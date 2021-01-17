# PILLARS
* **FOCUS**: Complete the task with the essentials. Do not ﻿assume that further features are required. 
* **EFFECTIVE**: It’s better to work 2 weeks, instead of working 1 week and then spend 2 weeks solving bugs.
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
    * `class` max 250 lines and max 2 references to other classes (Except for composition)
    * `method` max 50 lines, does one thing (*cohesion*), and requires 5 parameters at most.
* *Logic **or** view*: logic script contains no view script (such as UI) and viceversa
* Use **Assertions** instead of exceptions for error checking.
* Use **Assertions** instead of flags such as `if (anything != null)`
* Each **scene** runs independently
* *UI*: each ui element have an [actor](https://gamedevacademy.org/lessons-learned-in-unity-after-5-years/) and multiple actor elements, no master components
* *Seal*: always **seal** the end class to [help the compiler with virtual members](http://codebetter.com/patricksmacchia/2008/01/05/rambling-on-the-sealed-keyword/)
* *Inline*: Avoid method calls inside loops and understand [inlining optimization](https://www.codeproject.com/Tips/1072041/NET-Methods-Inlining-and-Loops)
* *Scriptable Object(SO)* Use **SO** [wisely](https://www.youtube.com/watch?v=raQ3iHhE_Kk) (also [here](https://stackoverflow.com/questions/56054864/what-is-the-best-practice-to-load-scriptableobjects-to-single-prefab-multiple-pr/56063333#56063333)), for shared values, systems and as event listeners.
* *Strings*: use only **const strings**. Group them inside files used only for these constants.
* *Command-query separation (CQS)*: Implement either **Command** (change/noreturn) or **Query** (nochange/return)
* *Log*: contain all logs inside in a loggers such as [JLog](https://github.com/GiacomoMariani/JReact/blob/master/JLog.cs) and avoid Debug.Logs or Print
* Use weak parameter types and strong return types. `HighLevelClass Method (iLowLevelInterface interface);`
* *GC Optimization*: Avoid large objects, make small objects either permanent ([pooling](https://learn.unity.com/tutorial/object-pooling)) or disposed almost instantly
* *Structs*: structs [may be useful](https://jacksondunstan.com/articles/3453), but override `Equals` and `GetHashCode` to implement [`IEquatable`](https://docs.microsoft.com/en-us/dotnet/api/system.iequatable-1?view=netframework-4.8)
* Never overwrite source codes from the Plugin folder. Override or extend it.
* Isolation layers prevent vendor lock-ins on 3rd party libraries: *IE: YourAPI.GetInput() => ThirdParty.GetInput();*

### CODING CONVENTIONS
* Prioritize readability above performance, we can change code later
* *Comments* are few and very relevant
* Follow [C# Coding Standards and Naming Conventions](https://github.com/ktaranov/naming-convention/blob/master/C%23%20Coding%20Standards%20and%20Naming%20Conventions.md)

#### BASIC PERFORMANCE
* Cache Components on Awake. Do not use GetComponent() anywhere else
* Declare expected sizes for all collections. IE `new List<int>(50);`
* Use `GetHashCode()` instead of `GetInstanceID()` to avoid security checks in the main thread
* Avoid casting

### CODE QUALITY
* **UNIT TEST PILLARS**:
    1. RESISTANCE TO REFACTORING (MANDATORY): refactoring does not produce false positives
    2. PROTECTION AGAINST REGRESSION: test will find the bugs correctly
    3. FAST FEEDBACK: the test must be fast to execute
    4. MAINTAINABILITY: the test is easy to understand and to run
* Separate `//ARRANGE`, `//ACT` and `//ASSERT` with comments
* *ARRANGE* may use a Factory method if we need the same code (avoid `[SetUp]`)
* *ACT* must be one line
* Use readable names with underscore `Player_Dies_If_Gets_More_Damage_Than_Hit_Points`
* Avoid `if` statements (and also `switch`) inside the test
* Unit Test our `domain behaviour`, from entrance to exit. Entrance may be a `Raycast`, exit may be the final `HitPoints` 

#### PROFILING AND BENCHMARKING
* Implement [Performance Testing](https://docs.unity3d.com/Packages/com.unity.test-framework.performance@1.0/manual/index.html) following [this guide](https://blogs.unity3d.com/2018/09/25/performance-benchmarking-in-unity-how-to-get-started/)
* Use [Memory Profiler](https://docs.unity3d.com/Packages/com.unity.memoryprofiler@0.2/manual/index.html) or [dotMemory](https://www.jetbrains.com/dotmemory/?gclid=Cj0KCQiAhojzBRC3ARIsAGtNtHXqI3Y3ldb3Ri0Qlgw5HuvtelE7xVpG4S_LRz-J9HmoDrqHeWJzQrcaAmuGEALw_wcB) to check for memory usage
* Use [Profile Analyzer](https://docs.unity3d.com/Packages/com.unity.performance.profile-analyzer@0.6/manual/index.html) to check CPU performance
* Use [Render Doc](https://renderdoc.org/) to analyze draw calls and overdraw (switching the **overlay mode** to *Quad Overdraw (Draw)*)
* [Asset Hunter Pro](https://assetstore.unity.com/packages/tools/utilities/asset-hunter-pro-135296) might find the most large files in the build
* Run `gci -r| sort -descending -property length | select -first [AMOUNT] name, length` to catch the larger files

# ASSETS
* **Art**: Follow [Art Asset Best Practices](https://docs.unity3d.com/Manual/HOWTO-ArtAssetBestPracticeGuide.html) and [ARM Guide for Developers](https://developer.arm.com/solutions/graphics-and-gaming/gaming-engine/unity/arm-guide-for-unity-developers)
* **Audio**: Follow [Audio Optimization Tps](https://gamedevbeginner.com/unity-audio-optimisation-tips/) and [Audio Import Optimization](https://www.gamasutra.com/blogs/ZanderHulme/20190107/333794/Unity_Audio_Import_Optimisation__getting_more_BAM_for_your_RAM)
