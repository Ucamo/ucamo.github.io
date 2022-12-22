# Unity Cloud Build Tutorial.
<img src="https://raw.githubusercontent.com/Ucamo/ucamo.github.io/main/assets/images/unity_cloud_build_Tutorial/img_1.webp" width="80%" height="50%" alt="Unity Cloud build tutorial">

Cloud build is a service included on Unity Teams Advance that let you set up your existing source control repository to automate the compiling, deployment and tests of your games so you can iterate quickly with your team.

Basically you can set up a branch on your repository that Unity Cloud Build will pick up and deploy to the target platform/s of your choosing, you can set up different platforms (like Desktop, iOs, Android, Web) and configure an email alert that will let you know once the build has been completed of if there were some errors with it.

The advantages of using Unity Cloud Build is that all of that workflow is handled by the service, giving you more time to use your local hardware in more usefull stuff (or taking a well deserved rest).

## What do you need?
- A Unity Teams Advance license ($9 USD per month, which include 3 team seats and 25GB of Cloud storage) or a Unity Pro license.
- A Source control repository (like Git)

## How do you set it up?
You can lear how to set up Unity Cloud build in this super easy to follow official tutorial

## Does this mean I can build for iOs without a Mac?
This is a tricky question. The short answer is no (sorry, I would also like this to be a Yes). But let’s elaborate on that.

Yes, you can build for the iOs platform on Unity Cloud Build, but to do that, you will need the certificates that will sign up your iOs build to upload it to the App Store. So at least you will need to get access to a Mac once to get those certificates.

After that, you can continue using Unity Cloud Build to make new versions of that project without the need to use a Mac. But please note that for uploading your project to the App Store, you will need to do so through XCode, so you will also need access to a Mac for that.

<img src="https://raw.githubusercontent.com/Ucamo/ucamo.github.io/main/assets/images/unity_cloud_build_Tutorial/img_2.webp" width="80%" height="50%" alt="a macbook pro in a desk">

Personally, I have been down that rabbit hole before, and comming up from a Microsoft/Windows based background, this transition was hard for me. Some stuff that I learnead along the way:

- You can rent a virtual mac if you don’t want to spend the money on one for you on MacInCloud to get the certificates and you can pay by the hour.
- The process of uploading your game to the App Store can be long (not in time, but on multiple back and fort with the process of getting your game accepted on the App Store), so if you can get a friend or co-worker with a Mac that can help you with this process it’s super recomendable.

## Advantages and Disadvantages of using Unity Cloud Build.

### Advantages:
- It let you focus on the important things, like improving your game.
- It’s a very straightforward way to deliver continuosly, once it’s set up, it’s done and will work until you decide to do some other changes in the way to present the build.
- Building can be very time consuming, and if’s made in another computer it’s a time saver.

### Disadvantages:
- Working with Unity and adding third party assets can mess up your automatic builds. Sometimes it can work on the editor, and in your local build, but on the remote build will fail, luckily Unity Cloud Build count with a very good log system that will let you know where the error is.

This has been a very basic approach to Cloud Build but in general this is a very good way to standarize your project and get to know how continuos integration work with Unity.

Hope you like it and happy gamedev!
