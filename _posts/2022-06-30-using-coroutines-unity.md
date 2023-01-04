# **Using coroutines in Unity**

<img src="https://raw.githubusercontent.com/Ucamo/ucamo.github.io/main/assets/images/using_coroutines_unity/using-coroutines-unity-copy.avif" width="80%" height="50%" alt="Using coroutines in Unity">

[Originally posted on LogRocket on June 30,2022](https://blog.logrocket.com/using-coroutines-unity/)

As your Unity project grows, there will be a need to create more complex logic. You might need to load different resources or prepare time-sensitive scenes. Ultimately, we want players to have the most seamless experience without breaking their immersion.

With coroutines, you can use various approaches to achieve this. In this tutorial, we will go over different uses of coroutines and when to use them.

### **What are coroutines?**

Unity uses frames as a way to represent time. Normal methods will execute in one frame and move into the next instruction.

[Coroutines can be used to execute a piece of code across multiple frames](https://docs.unity3d.com/Manual/Coroutines.html). They can also be used to keep executing a section of code until you tell it to stop. A coroutine contains a yield instruction that will wait a certain amount of time you tell it to.

### **When to use coroutines**

Let’s say you want to use a normal call method with a for loop to fill a health bar from 1–100 HP. The player will see a full health bar at the end of your method. That’s because the time it takes the method to count to 100 is faster than a frame on Unity, and is also faster than your players’ eyes.

This is a good example of when to use coroutines. You’d tell the coroutine to fill 1 HP, wait a fraction of a second, and do it again until we reach the full 100 HP.

This way, your players will watch the health bar fill up smoothly over time.

```cs
​​using System.Collections;
using UnityEngine;

public class HealthBar : MonoBehaviour
{
   int maxHP=100;
   int currentHP=0;


   void Start()
   {
       Debug.Log("Start Increasing Health");
       StartCoroutine(HealthIncrease());
       Debug.Log("Finish start event");
   }

   IEnumerator HealthIncrease(){
       Debug.Log("Start Coroutine");
       for(int x=1; x<=maxHP;x++){
           currentHP=x;
           //Increase or decrease the parameter of WaitForSeconds
           //to test different speeds.
           yield return new WaitForSeconds(0.2f);
           Debug.Log("HP: "+currentHP+" / "+maxHP);
       }
       Debug.Log("Current health is "+maxHP);
       Debug.Log("End Coroutine");
   }
}
```

Another potential use case could be if a player is being hit by an object and you want to add a few seconds when nothing else can hit them. This will create temporary invincibility to avoid an unjust game experience.

In pseudocode, we would end up with something like this: when an object hits the player, deactivate the player hitbox for two seconds and then activate it again.

### **An example of a coroutine**

coroutine is a method from MonoBehavior that has an IEnumerator return type. To

invoke and start using it, you should use the StartCoroutine method and pass your coroutine method and parameters if needed.

On a coroutine, the yield return is when your code pauses for the next frame and continues afterward. If you don’t need your coroutine to wait, you can use WaitForSeconds (or any other yield instruction), as well as null.

```cs
using System.Collections;
using UnityEngine;

public class Coroutines : MonoBehaviour
{
   void Start(){
       Debug.Log("Begin Start event");
       StartCoroutine(WaitCoroutine(2f));
       Debug.Log("End Start event");
   }

   private IEnumerator WaitCoroutine(float time){
       Debug.Log("Inside coroutine");
       yield return new WaitForSeconds(time);
       Debug.Log("Finish coroutine after "+time+" seconds");
   }
}
```

The example above will print:

```cs
Begin Start event
Inside coroutine
End Start event
```

It will wait for two seconds, and will print:

```cs
Finish coroutine after 2 seconds
```

### **Implementing a coroutine that never stops**

You can also declare an IEnumerator variable and reference it with your coroutine to invoke it.

In the example below, since the while loop will always be true, the coroutine will continue executing after waiting for two seconds.

```cs
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class InfiniteLoopCoroutine : MonoBehaviour
{
   IEnumerator myCouroutine;

   void Start(){
       myCouroutine= InfiniteLoop(2f);
       StartCoroutine(myCouroutine);
   }

   IEnumerator InfiniteLoop(float seconds){
       while(true){
           yield return new WaitForSeconds(seconds);
           Debug.Log("Inside infiniteLoop");
       }
   }
}
```

Please note that WaitForSeconds uses a float parameter divided by Time.timeScale. We do this so we can mimic a real second on the game’s device.

### **How to stop a coroutine**

Now we have a coroutine that has an infinite loop. But how do we make it stop?

You can stop a running coroutine with the StopCoroutine method, which will accept either of the following as a parameter:

- A string with the name of the coroutine
- An IEnumerator reference of your coroutine

So, in the previous example, we could do:

```cs
StopCoroutine("InfiniteLoop");
```

or…

```cs
StopCoroutine(myCoroutine);
```

A coroutine will also stop if the object that it’s attached to is disabled by SetActive(false) or by destroying the object with Destroy().

The following example will stop the coroutine when the player presses the Space key.

```cs
using System.Collections;
using UnityEngine;

public class InfiniteLoopCoroutine : MonoBehaviour
{
   IEnumerator myCouroutine;

   void Start(){
       myCouroutine= InfiniteLoop(2f);
       StartCoroutine(myCouroutine);
   }

   IEnumerator InfiniteLoop(float seconds){
       while(true){
           yield return new WaitForSeconds(seconds);
           Debug.Log("Inside infiniteLoop");
       }
   }

   void Update(){
       if (Input.GetKeyDown(KeyCode.Space))
       {
           StopCoroutine("InfiniteLoop");
           Debug.Log("Coroutine stopped");
       }
   }
}
```

### **Pausing games with coroutines**

A popular way of pausing a game in Unity is by setting Time.timeScale equal to 0. This sets the property that Unity uses to measure time based on the device running the game.

Keep in mind that this is all in a game/unity project environment, so it’s not equivalent to the time in the real world.

When Time.timeScale is set to 0, the game pauses and the Update method is no longer being executed in each frame. Every animation being executed is stopped and every moving object that was using timescale stops in place.

For coroutines, this is a little different.

If you are executing a coroutine in a loop and it’s still going when Time.timeScale is set to 0, the coroutine will keep going but WaitForSeconds will not.

WaitForSeconds uses Time.timeScale to know what a real second is. In this case, it will behave properly, but the rest of the code in the coroutine will continue executing.

```cs
using System.Collections;
using UnityEngine;

public class TimeStop : MonoBehaviour
{
   // Start is called before the first frame update
   void Start()
   {
       StartCoroutine(PrintEverySecond());
   }

   // Update is called once per frame
   void Update()
   {
       if(Input.GetKeyDown(KeyCode.Space)){
           if(Time.timeScale==1.0){
               Debug.Log("Time Stop");
               Time.timeScale=0.0f;
               StartCoroutine(PrintOnStop()); //We start a new coroutine after stopping time.
           }else{
               Debug.Log("Time Continue");
               Time.timeScale=1.0f;
           }
       }
   }

   IEnumerator PrintEverySecond(){
       while(true){
           yield return new WaitForSeconds(1.0f);
           Debug.Log("Inside Coroutine");
       }
   }

   IEnumerator PrintOnStop(){
       for(int x=0;x<=10;x++){
           Debug.Log("Time is stopped but I'm still running "+x);
       }
       yield return null;
   }
}
```

Please keep in mind that you can stop a coroutine with StopCoroutine before pausing the game to prevent unexpected behavior.

You can also stop all coroutines at the same time! We’ll go over this in the next section.

### **Using multiple coroutines and stopping them all at once**

As you know, you can execute multiple coroutines that behave differently at the same time. They can be stopped all at once by the StopAllCoroutines() method.

```cs
using System.Collections;
using UnityEngine;

public class MultipleCoroutines : MonoBehaviour
{
   void Start()
   {
       //You can use multiple coroutines at the same time,
       //even on the same definition.
       //Each one will behave individually.
       StartCoroutine(MyCoroutine(1f));
       StartCoroutine(MyCoroutine(3f));
       StartCoroutine(MyCoroutine(5f));
   }

   void Update(){
       //If you hit space at runtime, all the coroutines will stop
       if(Input.GetKeyDown(KeyCode.Space)){
           StopAllCoroutines();
           Debug.Log("All coroutines stopped");
       }
   }

   IEnumerator MyCoroutine(float sec){
       while(true){
           yield return new WaitForSeconds(sec);
           Debug.Log("I'm on a loop that prints every "+sec+" seconds");
       }
   }
}
```

StopAllCoroutines() doesn’t take a parameter for stopping all the coroutines in the game at the same time.

### **Coroutines vs. threads**

Keep in mind that coroutines are not threads. Any synchronous code executed in a coroutine will be on the main thread.

If you want to use threads for consuming an HTTP request, for example, you can use async methods.

Here’s an example of consuming an HTTP request using coroutines:

```cs
using System.Collections;
using UnityEngine.Networking;
using UnityEngine;

public class HTTP_Request_Example : MonoBehaviour
{
   void Start()
   {
       //Consume an HTTP request with a coroutine
       //It happens on the main thread, which might cause the UI
       //to be unresponsive for a bit
       StartCoroutine(MyRequest("www.google.com"));
   }

   IEnumerator MyRequest(string url){
       using (UnityWebRequest request = UnityWebRequest.Get(url))
       {
           //Fetches a page and displays the number of characters of the response.
           yield return request.SendWebRequest();
           Debug.Log("Page length: "+request.downloadHandler.text.Length);
       }
   }
}
```

Although there are a lot of examples of this approach, it’s not ideal for this kind of situation when you don’t have full control of the time responses of these external APIs.

Here’s the same example using an asynchronous method instead:

```cs
using System.Collections;
using UnityEngine.Networking;
using UnityEngine;
using System.Threading.Tasks;
using System.Runtime.CompilerServices;

//By default, UnityWebRequest is not async, so you will need this extension
//Credit goes to: https://gist.github.com/mattyellen/d63f1f557d08f7254345bff77bfdc8b3
public static class ExtensionMethods
{
   public static TaskAwaiter GetAwaiter(this AsyncOperation asyncOp)
   {
       var tcs = new TaskCompletionSource<object>();
       asyncOp.completed += obj => { tcs.SetResult(null); };
       return ((Task)tcs.Task).GetAwaiter();
   }
}

public class HTTP_Request_Async_Example : MonoBehaviour
{
   void Start()
   {
       //Invoke a new thread when the web request will happen without blocking the UI
       ConsumeWebRequest();
   }

   async void ConsumeWebRequest(){
       Debug.Log(await MyRequest("www.google.com"));
   }

   async Task<string> MyRequest(string url){
       using (UnityWebRequest request = UnityWebRequest.Get(url))
       {
           //Fetches a page and displays the number of characters of the response.
           await request.SendWebRequest();
           string response = "Page length: "+request.downloadHandler.text.Length;
           return response;
       }
   }
}
```

Out of the box, Unity uses its own networking package called UnityEngine.Networking.

By default, this package is not asynchronous. If you use it inside of a coroutine, it could potentially lock the main thread of your app, resulting in some unexpected behavior.

The second example will use its own thread and leave the main thread free for the player. The game will feel like it’s running as smoothly as ever!

### **Additional thoughts**

Coroutines are very resource-efficient, so don’t be afraid of trying them out. If you end up in a situation where you have too many coroutines at the same time, you might need to double-check your design for solutions. Two or three coroutines in the same objects that really need them could be enough.

There are a lot of examples of using coroutines with WebRequest out there, but, in general, if you have to consume external resources that your project can’t control (like the time it takes a server to answer your request), it’s a good idea to use asynchronous methods instead of coroutines. This is because coroutines execute synchronous code and might use the main thread, resulting in a bad experience for your players.

I’m not saying that async/ await are better than coroutines in Unity, they both are great tools. It really depends on your design and choices about when and where to use them. A general rule of thumb could be that for internal processes, use coroutine and for external processes, use asynchronous methods.

### **Conclusion**

Coroutines are a great tool to have on your belt. They can help you set up the level for your players in front of their eyes, make smooth transitions between events, or create new functionality for you to impress your players.

I hope you found this article useful and liked reading it as much as I enjoyed writing it!

Happy gamedev!