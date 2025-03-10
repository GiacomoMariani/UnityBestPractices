# PILLARS
* **FOCUS**: Complete the task with the essentials. Do not assume that further features are required.
* **EFFECTIVE**: It’s better to work 2 weeks, instead of working 1 week and then spend 2 weeks solving bugs.
* **SIMPLE**
* **AWARE**: Bug randomly fixed by an update are not solved. Aim at understanding and solving their source cause.
* **UNBROKEN**: Compile it. Run it. Use it. Please test the feature before sending it to review.
* **COHESIVE**: Everything we write should look like one person writes it all.

# VERSION CONTROL
* Create a new *branch* for each *card* or each *bug*.
  * This branch should be based on the main/master branch and remain independent from any unconfirmed features.
* Add a specific folder for a new feature and gather all files there. After approval assign everything to its folder.
* `merge master` inside your branch before asking a review
* Create proper commits:
```
git commit -m “-[Tag] - [Main/Secondary] [Commit_Title]” -m “-SCENE: main changes in scene 
-CODE: list of changes in code etc.”
```
### COMMIT TAGS

!G | !B | !A | !N | !U | !T | !R
------------ | ------------- | ------------- | ------------- | ------------- | ------------- | -------------
Gameplay | Bug fix | Art | Network/Multiplayer | Assets Update | Tools | Assets removal

# CODING
* **Decouple**
  * `class` max 300 lines and max 2 references to other classes (Except for composition)
  * `method` max 50 lines, does one thing (*cohesion*), and requires 5 parameters at most.
  * `inheritance` max 2 levels of inheritance in our Domain. 3 in exceptional cases
* *Command-query separation (CQS)*: Implement either **Command** (change/noreturn) or **Query** (nochange/return)
* *Logic **or** view*: logic script contains no view script and viceversa (IE health logic is separate from health UI)
  * **Views**: each view (such as UI) have a single [actor](https://gamedevacademy.org/lessons-learned-in-unity-after-5-years/) and multiple actor elements, no master components

-----------------

* Use **Assertions** instead of exceptions for error checking.
* Use **Assertions** instead of flags such as `if (anything != null)`
* Each **scene** runs independently
* *Seal*: **seal** the end class to [help the compiler with virtual members](http://codebetter.com/patricksmacchia/2008/01/05/rambling-on-the-sealed-keyword/)
* *Inline*: Avoid method calls inside performance loops and understand [inlining optimization](https://www.codeproject.com/Tips/1072041/NET-Methods-Inlining-and-Loops)
* *Scriptable Object(SO)* Use **SO** [wisely](https://www.youtube.com/watch?v=raQ3iHhE_Kk) (also [here](https://stackoverflow.com/questions/56054864/what-is-the-best-practice-to-load-scriptableobjects-to-single-prefab-multiple-pr/56063333#56063333)), for shared values and library content. The best SO is stateless.
* *Strings*: use only **const strings**. Group them inside files used only for these constants.
* *Log*: isolate logging (IE [JLog](https://github.com/GiacomoMariani/JReact/blob/master/JLog.cs)) and avoid Debug.Logs or Print
* Use weak parameter types and strong return types. `HighLevelClass Method (iLowLevelInterface interface);`
* *GC Optimization*: Avoid large objects, make small objects either permanent ([pooling](https://learn.unity.com/tutorial/object-pooling)) or disposed almost instantly
* *Structs*: structs [may be useful](https://jacksondunstan.com/articles/3453), but override `Equals` and `GetHashCode` to implement [`IEquatable`](https://docs.microsoft.com/en-us/dotnet/api/system.iequatable-1?view=netframework-4.8)
* Never overwrite source codes from third party libraries. Override or extend it.
* Isolation layers prevent vendor lock-ins on 3rd party libraries: *IE: YourAPI.GetInput() => ThirdParty.GetInput();*
* Use `[RuntimeInitializeOnLoadMethod(RuntimeInitializeLoadType.AfterAssembliesLoaded)]` to run before Awake
* Make at most 2 calls on method chains. `objectA.DoSomething().ThenSomething()`.
  * *Exception*: do any amount of calls when using a **very stable library**.
* Free the resource in the same process that is using it.

### CODING CONVENTIONS
* Prioritize readability above performance, we can change code later
* *Comments* are few and very relevant
* Method Signature Order: `public MyType MethodName(ref MyType myTypeRef, in MyType myTypeIn, MyType myType, out MyType myTypeOut, MyType* myTypeRead, MyType* myTypeWrite)`
* Follow [C# Coding Standards and Naming Conventions](https://github.com/ktaranov/naming-convention/blob/master/C%23%20Coding%20Standards%20and%20Naming%20Conventions.md)
* Follow [Clean Code](https://gist.github.com/wojteklu/73c6914cc446146b8b533c0988cf8d29)

#### BASIC PERFORMANCE
* No public fields. When required use public properties with private setter.
* Cache Components on Awake. Do not use GetComponent() anywhere else
* Use readonly or readonly ref when the member does not change the state, valid also for property getters
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
* Unit Test our `domain`, from entrance (that might be `Raycast` from Unity domain) to exit (such as final `HitPoints`)
* User errors should 'inform and continue'. Programmers errors should be made obvious
* Make the code reusable, even if you won't re use it. For a better architecture.

#### SCENE
* Each scene is separated in: Managers, Environment, UserInterface, Actors
* Each scene has an entry point, used also as exit point

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
* **Coding Patterns**: [Unity Patterns Ebook](https://unity.com/resources/level-up-your-code-with-game-programming-patterns)

