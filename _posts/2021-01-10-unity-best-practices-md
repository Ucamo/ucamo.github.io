# Unity Best Practices

<img src="https://raw.githubusercontent.com/Ucamo/ucamo.github.io/main/assets/images/unity_best_practices/img_1.png" width="80%" height="50%" alt="Unity Best Practices">

In this post, we are going to list a series of Best practices to use while working on a Unity Project, please keep in mind that not all of these practices are the necesary to include in each project, and as you get more experience working on Unity, you will get a better judgment about when or which ones to use for your own projects.

### **Project Organization**

**Project Folders**
Try to keep your scripts in an organized way, something that can be easy for you to navigate to when looking for a specific script, having multiple folders inside your script folder is also a good way to keep your logic organized.

<img src="https://raw.githubusercontent.com/Ucamo/ucamo.github.io/main/assets/images/unity_best_practices/img_2.png" width="80%" height="50%" alt="Unity Project folder structure best practices">

Some assets or pluggins from the Unity Asset Store, will include a Folder called “Scripts” whith their own scripts from another author, to prevent confusion, name the script folder for your project something that makes sense to you plus it’s easily described for your project (I go with “MyScripts” because those are scripts made by me)

### **Grouping Objects in the Hierarchy**

<img src="https://raw.githubusercontent.com/Ucamo/ucamo.github.io/main/assets/images/unity_best_practices/img_3.png" width="80%" height="50%" alt="Unity Hierarchy best practices">

<img src="https://raw.githubusercontent.com/Ucamo/ucamo.github.io/main/assets/images/unity_best_practices/img_4.png" width="80%" height="50%" alt="Unity child game objects">

To avoid clutter in your Hierarchy window, you can drag and drop Game Objects inside each other to group them, doing so let you expand the “parent” Game Object and still have control for the childs.

If you don’t want to have the parent-child relationship, you can add an Empty Object as a Holder for all the childs, just to have a cleaner look in your Hierarchy window.

### **General Tips**

**Use source control**

Unity projects can get mesy really fast, and having the ability to “make everything as it was before” it’s a huge time saver.

[I personally recomend Git and wrote another article about how to use it with Unity.](https://ucamo.github.io/2020/12/01/how-to-use-git-with-unity.html)

**While working on a Team project, make some ground rules**

Out of the box, Unity doesn’t really like that 2 or more persons are updating the same Scene or Prefab at the same time. Make sure that everyone that it’s going to interact with the scene has the latest version and will only change something specific and push their changes to the repository.

Have somebody in charge of putting all together in case that a merge conflict it’s in place. After the merge conflict is resolved, talk with your team about it in order to prevent those, everyone should be on the same page regarding what’s need to be changed.

A general rule of thumb is, if you update something, and other stuff got updated but you didn’t intend to update it, leave it out of your commit, and reverse it.

**Keep the same version of Unity for your project across your team**

If somebody has a newer or lower version of the team that the rest, this might cause unnecesary and unexpected behavior while other member tries to open the project, Unity will try to update the version of the project and this might cause something to broke, it’s relative easy to fix, but this is totally unnecesary.

Using the latest long-term support release of Unity (LTS) it’ recommended for most projects, unless you are planing to use some super-specific feature that is in an unstable version, or not fully integrated to the Edior yet, thats totally not a bad thing!, but just keep in mind that everyone is aware of the version that your project is using.

While in mid-project, updating to a newer version should be done if that’s absolutely necesary. Unity Hub let’s you handle multiple versions of the Editor, so you can have for example, One project that started with Unity 2019, and it will stay with that version until completion, and having newer projects with Unity 2020. It’s up to the team to decide.

### **Working with Prefabs**

**Prefabs are your friends**

Prefabs make it easier to make changes without changing the scene, try to work with prefabs as much as posible.

**Prefabs reference**

While reference an instance of Game Object, this should be made from a Prefab to Prefab and not between instances on the scene.

That’s it for today, Happy gamedev!