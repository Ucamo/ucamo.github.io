## How to use Git with Unity.
<img src="https://raw.githubusercontent.com/Ucamo/ucamo.github.io/main/assets/images/how_to_use_git/1_9qBdoZeHYcaEB64dnwwzgw.png" width="50%" height="25%" alt="Git and Unity">

Let’s picture this, you are working on a document or project, everything is going super, you have everything in place and you are pretty confident with how it’s looking, however, you want to add just a tiny little extra thing to make the whole thing a lot better, you are in the zone today, you finish up adding that extra feature, or that new layout and… now it’s not looking that great, it’s not working the way it was 3 minutes ago, you hit ctrl+Z in hopes to make everything as it was but… nothing… it’s not working as it was before and it’s not working as you wanted with this new changes, has this happen to you?

Git is the tool that would save you from situations like this.

Git is a widely used version control system in the tech industry and has become a standard tool for developers and designers.

### *Basically what Git does is:*
- Save your file or project in a state that you are comfrotable with.
- You can change the project whever you want.
- If you are comfortable with the result, you can save that state again and keep moving forward or you can revert it back to the state it was before.

This “saved state” will be accesible to you through a history even if your computer has been turned off or has happen many years since that last state, also, you can save as frequently as you which.

Unity has it’s own version control system called [Collaborate](https://unity.com/es/products/unity-teams) that is part of [Unity Teams](https://unity.com/es/products/unity-teams), what collaborate does is basically what Git does, but focused heavely on Unity and not a widely used tool as Git, so this tutorial will be based on Git since no mather what you do on IT, Git it’s a very usefull tool to learn.

===========

### If you haven’t used git before, you can download it [here](https://git-scm.com/)

And learn how to use it [here](https://learngitbranching.js.org/) (but if you have any questions feel free to reach out and I will gladly help)

===========

Unity projects contains files that don’t really need to be versioned, those files, between others, are metadata files that are basically environment configuration of your instance of Unity running on your machine, and if another member of the team pick your changes in the repository, between those innecesary files versioned and theirs, there would be a conflict because those 2 machines are not exactly the same.

### *Let’s see an example:*
This is a brand new unity project with all the files that change from one commit to another.
<img src="https://raw.githubusercontent.com/Ucamo/ucamo.github.io/main/assets/images/how_to_use_git/1_lEHrL6cAsMi18zuegIfcUA.gif" width="100%" height="50%" alt="Git and Unity">
*Every green line is one file that it’s has been “updated” according to Unity.*

In this case, if we add those files to the repository we are destined to have a bunch of merge conflicts, that’s where `.gitignore` files come in handy.

A `.gitignore` file it’s a way we have to tell Git to stop tracking files with certain extensions, or that are in specific folders, those files generally don’t add value to the repository and other members of the team don’t need them in order to have their version of the project up and running.

A reccomended `.gitignore` for Unity will [look like this](https://github.com/github/gitignore/blob/main/Unity.gitignore) and in order to include it on your project, you can just create a new file with no name and the extension .gitignore and paste the content of the link above, or download the file and put it on your root folder (the one you initialized with “git init)

Now, after using a `.gitignore` file, we can see that our project will look something like this


every green line is being detected as a change in the repository.

### *Tips and tricks for using Unity and git*

### *What’s something that we should include in the project?*
You can include code files, images, sound files, scenes, just keep in mind that git can handle big files but it’s mostly used for light files sizes, if you feel the need to share really big files (ie: more than 200 mb), maybe use another internal option within your team for those files (maybe Google Drive), since having a repository that’s usually heavy is a bad practice.

### *What to do with merge conflicts?*
If they are code, you can merge it with your external merge tool, but for metadata files, there’s not an easy way of doing this, so pick whatever version makes more sense and then manually include the appropiate changes, I bet there’s a more sophisticated way of doing this but if you don’t have the time, this approach is way easier.

### *What if you get the latest commits of the repository and there’s some weird problems with the plugins or some internal errors in the editor?*
Some of the possible reasons for that are:

- You and your team are using different versions of the Unity Editor, make sure you decide in which version to use. It’s recommended to use the latest stable version at the start of the project and stick with it until the end if you don’t want any problem with this.
- The target platform was different and there were some configuration files that were commited. For example, you made a commit with the target platform as android and your teamate made a pull of your changes with iOs as their target platform.
- Delete the packeges files in `/Packages/manifest.json` , this will cause the unity editor to re-import the assets and the problem might resolve with that, different versions of the tools and plugins can cause this.

### Keeping things organized
Make sure that all the relevant information about how to boilerplate the project is included on the .md file is there some plugins that the team should have installed for this project? are there any files needed for the project to work correctly that are not on the git version control?

While working in a team, don’t make assumptions and lay all the info about how to get the project started in a place where all the members of the team can access it with ease.

— — — — — — — — —

That’s all for now, now you have everything you need to start using version control with Unity, you will get the hang of it eventually so don’t feel overwhelm about all that you learned today, and don’t forget to commit often and have a bunch of fun!

Happy gamedev!
