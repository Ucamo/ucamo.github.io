# Unity Object Pooling

One of the simplest and flashiest way of getting a game to stand out it’s presenting something amazing at the screen, this can be in a form of many objects interacting with each other’s at the same time, in this article we are going to learn how to keep control of the objects we are showing to the player while also being cautious about the memory we are using to do so.

<img src="https://raw.githubusercontent.com/Ucamo/ucamo.github.io/main/assets/images/object_pooling/img_1.gif" width="80%" height="50%" alt="Unity object pooling implementation">

_Object Pooling in action_

[**You can get this project with the actual implementation here.**](https://github.com/Ucamo/Unity-Object-Pooling)

Let’s think on a simple scenario, you are spawning game objects in unity and you start seeing that the more time the game runs, the slower it gets, or maybe you are spawning explosions or bullets, or confetti at the screen and you are seeing that sometimes the game have a hard time processing all those objects in the screen at the same time and it’s slowing down or starts to lag.

<img src="https://raw.githubusercontent.com/Ucamo/ucamo.github.io/main/assets/images/object_pooling/img_2.gif" width="80%" height="50%" alt="Unity object pooling falling infinetly">

_GameObjects intantiated will be moving downwards infinetly. (Look how the list of GameObjects increase on the Hierarchy window on the left side)_

If you want to follow along, create a 3D object (it can be an empty object too, but I wanted to show it on the images so it would be clearer) and create a SpawnerController c# file and assign it to it.

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class SpawnController : MonoBehaviour
{
    public GameObject objectToSpawn;
    public float spawnFrequency;
    void Start()
    {
        InvokeRepeating ("SpawnObject", spawnFrequency, spawnFrequency);
    }

    void SpawnObject(){
        Vector3 position;
        position = new Vector3 (gameObject.transform.position.x, gameObject.transform.position.y, gameObject.transform.position.z);
        GameObject newGameObject = Instantiate (objectToSpawn);
    }
}
```

It will receive a objectToSpawn parameter (that you will have to drag and drop in order to make it work, it can be anything, but a generic 3D GameObject with Rigidbody, will work as in this example) and the spawnFrequency parameter will instantiate a GameObject based on that parameter.

### What’s happening?
The CPU of the device that your game is running on it’s trying to keep track of all the game objects that are on the scene, and while you may have created a new object and then destroy it, this kind of approaches are not recommended in all the scenarios.

### How do we solve it?
Having a game slowing down may be the cause of different reasons, but Object pooling is in general a good practice to implement in your game if you have multiple GameObjects showing up at random or by a trigger of the player that can cause the game to slow down, so you might want to consider it implementing if this is starting to happen on your Unity project.

### How does it work?
Object pooling will create a specific set of objects, or pool, ready to be used, and when they are no longer needed, they will be back on the pool, ready to be used again.

Imagine that you have a player shooting marbles, and you decide that each marble should be a game object with it’s own set or properties, features, texture, physics, etc. Now imagine that the player can shoot an unlimited number of marbles and that it’s possible that the player want to shoot marbles all the time, so the longer the game it’s running, Unity will try to process all of those indivual marbles and keep track of all their propierties at all time, if the player keeps shooting marbles that will start to add up on the procesator and the game will lag.

Now, something that we can do in that case for those marbles is:

* Setting physical boundries for the GameObjects, in this case, the marbles, and if they go out of bounds, the GameObject will dissapear.
* Setting up a span of life for those objects to be active, if they exceed the time, they will dissapear for the player.
* Setting a specific number of marbles that the player can shoot, or a specific number of marbles that the player can see at the scene for each time, if the number exceeds those values, we can make dissapear the marble that has been on the game by the most time.
* If a marble touches an specific GameObject, make them dissapear.

<img src="https://raw.githubusercontent.com/Ucamo/ucamo.github.io/main/assets/images/object_pooling/img_3.gif" width="80%" height="50%" alt="Unity object pooling destroying objects">

_If a marble touches the bottom rectangle, it will Destroy it._

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class ObjectDestroyer : MonoBehaviour
{
    public void OnCollisionEnter(Collision obj) {
		Destroy (obj.gameObject);
	}
}
```

_The Rectangle is using this code snippet to destroy each object it collisions with (make sure the rectangle and the collisioned object both have Rigidbodies assigned to them)_

Now that’s some of the rules we can have for our game, normally we could think that making a game object appear on the screen will be through the Instantiate method, and make it dissapear with Destroy() or SetAvailable(false), but we can do better and translate what does “dissapear” would mean in our game.

### How to do it?
* Create a list of objects to make a pool of it
* Instantiate some of them at the start of the scene or in the lading scene as Inactive
* If one object of the pool is needed, activate it
* Use the game object whoerever you want
* When you want them to make it “dissapear”, don’t destroy it, de-activate it and return it to the pool.
* Repeat

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class SpawnController : MonoBehaviour
{
    public GameObject objectToSpawn;
    public int poolSize;
    public float spawnFrequency;
    List<GameObject> objectPool;
    Vector3 position;
    void Start()
    {
        //Initialize your properties
        position = new Vector3 (gameObject.transform.position.x, gameObject.transform.position.y, gameObject.transform.position.z);
        objectPool = new List<GameObject>();
        //Create a pool and fill it with inactive GameObjects.
        for (int i = 0; i < poolSize; i++) {
            GameObject newGameObject = Instantiate (objectToSpawn);
            newGameObject.SetActive(false);
            objectPool.Add(newGameObject);
        }

        //start spawning objects.
        InvokeRepeating ("SpawnObject", spawnFrequency, spawnFrequency);
    }

    void SpawnObject(){             
        GameObject spawnObject = GetObjectFromPool();
        if(spawnObject!=null){
            spawnObject.transform.position=position;
            spawnObject.SetActive(true);
        }
        
    }

    GameObject GetObjectFromPool(){
         //Get object from the pool
        foreach(GameObject objInPool in objectPool){
            //check if the object is inactive
            if(!objInPool.activeInHierarchy){
                return objInPool;
            }
        }
        return null;
    }
}
```

_This is the base Object Pooling implementation_

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class ObjectDestroyer : MonoBehaviour
{
    public void OnCollisionEnter(Collision obj) {
		obj.gameObject.SetActive(false);
	}
}
```

_Now instead of destroying object, it will set them as inactive_

<img src="https://raw.githubusercontent.com/Ucamo/ucamo.github.io/main/assets/images/object_pooling/img_4.gif" width="80%" height="50%" alt="Unity object pooling activating and deactivating objects">

_In this case, a set of GameObjects are created at the Start of the Scene (inactives) and when needed they would be turned on._

### What if there is a need of more object that’s what’s currently in the pool?
If that’s the case, we can instantiate a new one, use it, and when we no longer need it, de-activate it and put in on the pool with the others. Instantiate games is not a bad thing so we can use it all the time, but if we already have some pool of objects ready to be used, we can use those objects first, and if needed, create a new one, but having the same behavior for re-using those too in our pool.

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class SpawnController : MonoBehaviour
{
    public GameObject objectToSpawn;
    public int poolSize;
    public float spawnFrequency;
    List<GameObject> objectPool;
    Vector3 position;
    void Start()
    {
        //Initialize your properties
        position = new Vector3 (gameObject.transform.position.x, gameObject.transform.position.y, gameObject.transform.position.z);
        objectPool = new List<GameObject>();
        //Create a pool and fill it with inactive GameObjects.
        for (int i = 0; i < poolSize; i++) {
            GameObject newGameObject = Instantiate (objectToSpawn);
            newGameObject.SetActive(false);
            objectPool.Add(newGameObject);
        }

        //start spawning objects.
        InvokeRepeating ("SpawnObject", spawnFrequency, spawnFrequency);
    }

    void SpawnObject(){             
        GameObject spawnObject = GetObjectFromPool();
        if(spawnObject!=null){
            spawnObject.transform.position=position;
            spawnObject.SetActive(true);
        }
        
    }

    GameObject GetObjectFromPool(){
         //Get object from the pool
        foreach(GameObject objInPool in objectPool){
            //check if the object is inactive
            if(!objInPool.activeInHierarchy){
                return objInPool;
            }
        }
        //No inactive objects found, instantiate a new one and add it to the pool.
        GameObject newGameObject = Instantiate (objectToSpawn);
        newGameObject.SetActive(false);
        objectPool.Add(newGameObject);
        return GetObjectFromPool();
    }
}
```

_An expandible version of Object Pooling_

That’s where the magic of object pooling comes from, you have a pool that can increase on size and will be available to you when you need it with just the right amount of objects that you might need!

<img src="https://raw.githubusercontent.com/Ucamo/ucamo.github.io/main/assets/images/object_pooling/img_5.png" width="80%" height="50%" alt="Unity object pooling setting on Editor">

_In this case the initial pool size will be 1, and the spawn frequency every 0.2 seconds_

<img src="https://raw.githubusercontent.com/Ucamo/ucamo.github.io/main/assets/images/object_pooling/img_6.gif" width="80%" height="50%" alt="Unity object pooling configurable">

_When needed, the script will create a new object for the pool, if they are other GameObjects available, it will use those._

And let’s not forget that since our Object Pool is made of GameObjects, we can use it in a lot of different ways.

<img src="https://raw.githubusercontent.com/Ucamo/ucamo.github.io/main/assets/images/object_pooling/img_7.gif" width="80%" height="50%" alt="Unity object pooling multiple pools of gameObjects">

_Multiple spawners all using the same Object pool, will initialize just the ones needed, and re-use the ones available first._

So there you have it, a very usefull approach to a very basic problem that will solve some of your problems and can make your game stand out while also respecting the hardware it’s running on.

[Don’t forget to check out the actual implementation of this here.](https://github.com/Ucamo/Unity-Object-Pooling)

Happy gamedev!
