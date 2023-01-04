# **Update vs. FixedUpdate vs. LateUpdate in Unity**

<img src="https://raw.githubusercontent.com/Ucamo/ucamo.github.io/main/assets/images/update_vs_fixed_vs_lateupdate_in_unity/update-vs-fixedupdate-vs-lateupdate-unity.avif" width="80%" height="50%" alt="Update vs FixedUpdate vs lateUpdate in Unity">

[Originally posted on LogRocket on October 12,2022](https://blog.logrocket.com/update-vs-fixedupdate-vs-lateupdate-in-unity/)

In Unity, the way a game is presented to the player is everything. Both the smoothness of the controls and the gameplay they are experiencing are key, and knowing how this information is shown to the player will give you an advantage in the way you approach your Unity projects.

For that reason, we’re going to be discussing update functions, learning their implementations, and deciding when to use each.

### **What is a frame in Unity?**

You can imagine a frame as a picture, and if you have multiple similar pictures showing rapidly, you can create the illusion of movement.

A frame is a term inherited from animation, where some common values are 24, 30, and 60 frames per second (FPS). When it comes to games, we say that “it’s running at 60 FPS” when there are 60 new images in a second presented to the player. This is called frame rate, and frame interval is the time that happens between each frame.

In our example of 60 FPS, 60 would be the frame rate, and frame interval would be 1/60 x 1000 = 16.67 milliseconds.

In Unity, a frame is considered a rendered image presented to the player’s screen. Generally speaking, Unity doesn’t care about time, but it does about frames with its property **Time.DeltaTime** that calculates time between frames.

If for some reason, like having heavy processing during gameplay, time between frames slows down, this drops the frame rate and gives the sensation to the player that the game is running slowly.

### **Explaining the update functions**

During the lifetime of a script, Unity executes its functions in a specific order. You can read more about the [execution order here](https://docs.unity3d.com/Manual/ExecutionOrder.html), but to keep this article simple, we will be focusing on two stages: physics and game logic.

During each frame, Unity executes in order all the event functions of the active scripts.

It will first execute the physics simulation logic, calling **FixedUpdate** first, then the rest of the physics events.

Then it will check for Input events from the user.

Finally, during the game logic, it will execute the **Update** function, all the game logic functions, and finally **LateUpdate**.

It’s important to note that each event is executed in the same order across all the scripts on Unity, so if you have ten scripts that use **FixedUpdate**, those will have higher execution priority than other ten scripts that have code in their **Update** method; same thing with **LateUpdate** with the lower priority in the order for this example.

### **Update functions order**

Here we can see the order of these functions: we would create an empty object in a new Unity scene and attach this script to it.

In this script, we will print out to the console the order of the functions that gets executed. We have set up three flags called **continueUpdate**, **continueFixedUpdate**, and **continueLateUpdate** to prevent our functions from executing the same code multiple times and filling the console with unnecessary results:

```cs
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class UpdateOrder : MonoBehaviour
{
   bool continueUpdate=true;
   bool continueFixedUpdate=true;
   bool continueLateUpdate=true;

   // Start is called before the first frame update
   void Start()
   {
       Debug.Log("Start");
   }
   // Awake is called when the object is enabled
   void Awake()
   {
       Debug.Log("Awake");
   }

   //FixedUpdate is called before Update, at the same rate based on Delta Time
   void FixedUpdate()
   {
       if(continueFixedUpdate)
       {
           Debug.Log("Fixed Update");
           continueFixedUpdate=false;
       }
   }

   // Update is called once per frame
   void Update()
   {
       if(continueUpdate)
       {
           Debug.Log("Update");
           continueUpdate=false;
       }
   }
   //Late Update is called after update
   void LateUpdate()
   {
       if(continueLateUpdate)
       {
           Debug.Log("Late Update");
           continueLateUpdate=false;
       }
   }
}
```

The output will be something like this:

<img src="https://raw.githubusercontent.com/Ucamo/ucamo.github.io/main/assets/images/update_vs_fixed_vs_lateupdate_in_unity/console-list.avif" width="80%" height="50%" alt="Console List">

**Awake** gets called first since the GameObject was active, then **Start**, then **FixedUpdate**, **Update**, and finally **LateUpdate**.

### **FixedUpdate**

**FixedUpdate** is usually used for physics calculations since it has the same frequency as the physics system: by default it executes every 0.02 seconds (50 times per second), but you can double-check it with **Time.fixedDeltaTime**.

You can also change the frequency of **FixedUpdate** in Unity by going to **Edit > Project Settings > Time > Fixed Timestep**.

<img src="https://raw.githubusercontent.com/Ucamo/ucamo.github.io/main/assets/images/update_vs_fixed_vs_lateupdate_in_unity/time-frequency.avif" width="80%" height="50%" alt="Time Frequency">

### **Update**

**Update** is a function that gets called every frame if the **MonoBehaviour** is enabled.

If the frame rate is 60 FPS, it will execute 60 times a second; if it’s 30, it will be 30 times a second.

If the script gets disabled (i.e., **enabled=false**), it will stop.

### **LateUpdate**

Like **Update**, **LateUpdate** executes every frame if the **MonoBehaviour** is enabled, and it will stop if it’s disabled.

It will execute after all the update functions are called, and it’s recommended to use **LateUpdate** on camera scripts instead of **Update** since it can keep track of objects that have already been moved in an **Update** function.

Please keep in mind that the order of execution between **Update** and **LateUpdate** has nothing to do with speed. **Update** is not faster than **LateUpdate**; they are executed in different order to do different stuff. While **Update** might be used to move objects in a time interval, we would use **LateUpdate** to reflect the results after those objects have been moved, and it’s safe to assume that they are in a new state.

## **Where to use each update function**

### **FixedUpdate**

It’s recommended to use **FixedUpdate** when dealing with physics, like Rigidbodies updates.

In the following example, we added three cubes with a **Rigidbody** each.

What the script does in each case is that it takes a reference of the **Rigidbody** of each cube and applies a force upwards in the object they are attached to. The only difference between them is the type of update function they use.

The cube on the left has this script; it will be using **FixedUpdate**:

```cs
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class FixedUpdateRigidBody : MonoBehaviour
{
   public Rigidbody rb;
   // Start is called before the first frame update
   void Start()
   {
       rb = GetComponent<Rigidbody>();
   }

   //Is executed based on the Fixed Timestep (by default 50 times per second)
   void FixedUpdate()
   {
       rb.AddForce(10.0f * Vector3.up);
   }
}
```

The cube in the center will be using this one, using **Update**:

```cs
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class UpdateRigidBody : MonoBehaviour
{
   public Rigidbody rb;
   // Start is called before the first frame update
   void Start()
   {
       rb = GetComponent<Rigidbody>();
   }

   //Is executed every frame
   void Update()
   {
       rb.AddForce(10.0f * Vector3.up);
   }
}
```

And the cube on the right will be using this script, calling **LateUpdate**:

```cs
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class LateUpdateRigidBody : MonoBehaviour
{
   public Rigidbody rb;
   // Start is called before the first frame update
   void Start()
   {
       rb = GetComponent<Rigidbody>();
   }

   //Is executed every frame after Update
   void LateUpdate()
   {
       rb.AddForce(10.0f * Vector3.up);
   }
}
```

<img src="https://raw.githubusercontent.com/Ucamo/ucamo.github.io/main/assets/images/update_vs_fixed_vs_lateupdate_in_unity/fixedupdate-update-lateupdate.gif" width="80%" height="50%" alt="FixedUpdate, Update, LateUpdate">

_From left to right, **FixedUpdate, Update, LateUpdate**_

You can see a clear representation on how each update function works. **FixedUpdate** will be executed once every time step is settled in Unity; that is why the movement is constant and steady.

On the other hand, the cube in the center is using the **Update** function every frame, so each time the function is called to apply force upward, and since each frame is more frequent than the time step of **FixedUpdate**, you can see that it goes up way faster. This is because it’s being called many times more than the cube on the left.

And in the case of the third cube that is using the **LateUpdate** function, it is being executed each frame too, but after the Update function due the order of execution discussed above.

Please note that to the human eye, the difference between executing code in the Update function and **LateUpdate** function is pretty much the same. You couldn’t tell which cube is using the **Update** or **LateUpdate** function.

### **Update**

**Update** is called every frame, so if you need to read the input of the player, this is the perfect function to handle it so you don’t miss any event.

### **LateUpdate**

**LateUpdate** executes after all the Updates functions have been called. This is relevant because the order of execution on Update might be a little chaotic, and you can’t be sure which script will be executed within all your scripts that execute **Update**.

However, with **LateUpdate**, you can be sure that you will call this function after all the states changed with **Update** take place, so you can work with the final results of your objects.

It’s recommended to use **LateUpade** when following objects with the camera and updating the UI for the players.

### **Final thoughts**

There are two main concepts you could take from this article. For one, there is an order of execution that goes: Update is executed each frame; **FixedUpdate** is executed at a specific rate defined in the editor; and **LateUpdate** is executed after all the **Update** functions have been called.

And the second one is that this order is not based on each script; it’s based on your whole project, meaning that all the **Update** events will execute at the same time, and after those are finished, **LateUpdate** will execute. Because of this, one **FixedUpdate** function could be called at the same time the other two are called, so try your best to order your functions and ideas before executing everything at the same time.

You should be aware that the states of your objects and positions could be changed during those events and plan ahead for the best approach to have the most stable experience for your players.

I hope this article has been useful to you. Happy gamedev!