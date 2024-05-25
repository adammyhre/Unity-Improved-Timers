# Improved Unity Timers
![PlayerLoop2](https://github.com/adammyhre/Unity-Improved-Timers/assets/38876398/faefe51b-3fef-42ea-8440-1a92cd5c5abc)

An extensible Timer solution for Unity Game Development.  Timers are self managing 
by injecting a Timer Manager class into Unity's Update loop.

Create your own Timers by extending the Timer abstract class!

## Example Usage

```csharp
CountdownTimer timer = new CountdownTimer(5f);

void Start() {
    timer.OnTimerStart += () => Debug.Log("Timer started");
    timer.OnTimerStop += () => Debug.Log("Timer stopped");
    timer.Start();
    
    timer.Pause();
    timer.Resume();
    
    timer.Reset();
    timer.Reset(10f);
    
    Debug.Log(timer.IsRunning ? "Timer is running" : "Timer is not running");
    Debug.Log(timer.IsFinished ? "Timer is finished" : "Timer is not finished");
    
    timer.Stop();
}

void Update() {
    Debug.Log(timer.CurrentTime);
    Debug.Log(timer.Progress);
}

void OnDestroy() {
    timer.Dispose();
}
```

## Notes

Several Timers are already included, but you can create any kind of Timer you need that can be 
adjusted every frame.  The included Timers are:

- CountdownTimer: Counts down from a specified time to zero.
- FrequencyTimer: Ticks N times per second.
- StopwatchTimer: Counts up from zero to infinity.

Classes extending the Timer class must implement the `Tick` method to increment or decrement the Timer,
and the `IsFinished` property which is a convenience for consumers.

Call `Dispose` when you don't need a Timer anymore to ensure proper garbage collection.

## How to Install

Simply download the library into your Unity project and access the utilities across your scripts or import it in Unity with 
the Unity Package Manager using this URL:

`https://github.com/adammyhre/Unity-Improved-Timers.git`

### Add to Manifest

Alternatively, you can add the following line to your project's `manifest.json` file.

```
"com.gitamend.improvedtimers": "https://github.com/adammyhre/Unity-Improved-Timers.git"
```

## YouTube

- [Improved Timers in Unity](https://youtu.be/ilvmOQtl57c)

You can also check out my [YouTube channel](https://www.youtube.com/@git-amend?sub_confirmation=1) for more Unity content.
