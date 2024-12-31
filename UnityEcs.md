# CODE

* Use [ISharedComponentData](https://docs.unity3d.com/Packages/com.unity.entities@0.1/manual/shared_component_data.html)
  to organize your chunks
* Create BlobAssets
  with [BlobBuilder](https://docs.unity3d.com/Packages/com.unity.entities@0.3/api/Unity.Entities.BlobBuilder.html) to
  share values
* Manipulate chunks with batched operations (to add and remove
  components) `AddComponent(EntityQuery entityQuery, ComponentType componentType)`. [List of operations](https://gametorrahod.com/batched-operation-on-entitymanager/)
* IComponentData fields optimal size is 128 and 256 (4 or 8 int, or also xmm and ymm in assembly). See
  also [this article](https://gametorrahod.com/analyzing-burst-generated-assemblies/).
* Use `EntityQuery.CopyFromComponentDataArray` to add a new data, with a setup, to a given query
* Try running systems and queries when changed `chunk.DidChange(reqVersion)`.
  Also [this article](https://gametorrahod.com/designing-an-efficient-system-with-version-numbers/)
* Generics and Interfaces can be [supported by Burst](https://jacksondunstan.com/articles/5516), also
  with [fluent syntax](https://jacksondunstan.com/articles/5380)
* Virtual Functions can be [created in Burst](https://jacksondunstan.com/articles/5494)
* Use [JobsUtility.JobWorkerCount](https://docs.unity3d.com/2019.3/Documentation/ScriptReference/Unity.Jobs.LowLevel.Unsafe.JobsUtility.JobWorkerCount.html) to get the amount of worker in the running platform
* Use `EntityTypeHandle cth = entityManager.GetEntityTypeHandle();` to catch `NativeArray<Entity> entities = chunk.GetNativeArray(cth);`
* `[NativeSetThreadIndex] private int _threadIndex` attribute [gets the thread id](https://docs.unity3d.com/ScriptReference/Unity.Collections.LowLevel.Unsafe.NativeSetThreadIndexAttribute.html)
* Use `RequireForUpdate(_requiredQuery);` to avoid running a `System` when the query has not changed
* Use **Tags** (empty `IComponentData`) to partition data and you don't need to move tags each frame, otherwise use a
  conditional IComponentData (more [here](https://gametorrahod.com/tag-component/amp/))
* Understand [how structs are packed](https://docs.microsoft.com/en-us/dotnet/api/system.runtime.interopservices.structlayoutattribute.pack?view=net-5.0) when using them

## IJobFor Structure

```
//---------------------------------------
// 1 Choose the best compilation
//---------------------------------------
[BurstCompile(CompileSynchronously = true, OptimizeFor = OptimizeFor.Performance)]
public struct JobForName : IJobFor
{
    //---------------------------------------
    // 2 All fields are private
    //---------------------------------------
    [ReadOnly] private MyStruct item1;
    [WriteOnly] private MyStructOtherStruct item2;

    public void Execute(int index)
    {
        //logic here
    }

    //---------------------------------------
    // 3 Run and Schedule are responsible to create the job
    //---------------------------------------
    public static void Run(MyStruct one, MyStructOtherStruct two, JobHandle inputDeps = default)
    {
        Schedule(one, ref two, inputDeps).Complete();
    }

    public static JobHandle Schedule(MyStruct one, MyStructOtherStruct two, JobHandle inputDeps = default)
    {
        var job = new JobForName()
        {
            item1 = one,
            item2 = two,
        };

        var jobHandle = job.ScheduleParallel(allNodes.Length, 8~~~~, inputDeps);
        return jobHandle;
    }    
}
```

### BurstCompile Parameters

1. **CompileSynchronously**
    - **Type:** `bool`
    - **Default:** `false`
    - **Description:** Blocks until compilation is complete.

2. **DisableSafetyChecks**
    - **Type:** `bool`
    - **Default:** `false`
    - **Description:** Disables safety checks for improved performance.

3. **FloatMode**
    - **Type:** `FloatMode`
    - **Default:** `FloatMode.Default`
    - **Description:** Can be `Default`, `Deterministic`, or `Fast`.

4. **FloatPrecision**
    - **Type:** `FloatPrecision`
    - **Default:** `FloatPrecision.Standard`
    - **Description:** Can be `Standard` or `High`.

5. **OptimizeFor**
    - **Type:** `OptimizeFor`
    - **Default:** `OptimizeFor.Default`
    - **Description:** Can be `Default`, `Size`, or `Speed`.

6. **Debug**
    - **Type:** `bool`
    - **Default:** `false`
    - **Description:** Enables generation of debug information.

### LINKS

* [Conversion (Authoring) Workflow](https://gametorrahod.com/world-system-groups-update-order-and-the-player-loop/)
* [SystemBase document](https://docs.unity3d.com/Packages/com.unity.entities@0.9/api/Unity.Entities.SystemBase.html)
* [Entities.Foreach document](https://docs.unity3d.com/Packages/com.unity.entities@0.9/manual/ecs_entities_foreach.html)
* [Ecs Extensions](https://github.com/Unity-Technologies/UnityCsReference/blob/2018.1/Runtime/Export/NativeArray/NativeArray.cs)
  from [this article](https://jacksondunstan.com/articles/4713). Also
  with [events](https://jacksondunstan.com/articles/4713)
