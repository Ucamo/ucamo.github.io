# **Postmortem: Dots of War**

<img src="https://raw.githubusercontent.com/Ucamo/ucamo.github.io/main/assets/images/postmortem_Dots_of_War/img_1.png" width="80%" height="50%" alt="Dots of War Postmortem">


[Originally published in spanish on Oct 17,2020](https://medium.com/@carrillouriel/postmortem-dots-of-war-1193fb9c1767)

[Dots of War](http://lunarcrown.com/dotsofwar/) is a fast online strategy game for mobile devices, it is based on the game [Dots and Boxes](https://en.wikipedia.org/wiki/Dots_and_Boxes) and the objective is to conquer the majority of the map by connecting four lines to score points. Once you capture a part of the map, your player’s energy rises and with it you can make special abilities that will allow you to affect your opponent’s turn.

Dots of War was the first game that was made by the [LunarCrown](http://lunarcrown.com/) studio, an independent video game studio based in Hermosillo Sonora, Mexico founded by other local studios in an effort to professionalize our work and reach a wider audience.

<iframe width="560" height="315" src="https://www.youtube.com/embed/dkBLGVO7Sc4" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

_Dots of War Trailer_


### **How do we choose the theme?**

<img src="https://raw.githubusercontent.com/Ucamo/ucamo.github.io/main/assets/images/postmortem_Dots_of_War/img_2.jpeg" width="80%" height="50%" alt="Dots of war early game design sketches">

_Early game design sketches_

Like most of the decisions that were made in the project, we relied on votes. At the beginning of the project, we asked ourselves to pitch 1 or 2 proposals that we would like to develop as the first game, then we explained them to the team and at the end we would vote for the one that seemed easier to implement, interesting to work on and that we would like to work on.

From all these pitches the winner was to recreate the game of Dots and Boxes and give it a twist by gaining power-ups to affect the rival.

<img src="https://raw.githubusercontent.com/Ucamo/ucamo.github.io/main/assets/images/postmortem_Dots_of_War/img_3.jpeg" width="80%" height="50%" alt="Dots and boxes witches game">

<img src="https://raw.githubusercontent.com/Ucamo/ucamo.github.io/main/assets/images/postmortem_Dots_of_War/img_4.jpeg" width="80%" height="50%" alt="Dots of war prototype characters a king, a warrior and a witch">

<img src="https://raw.githubusercontent.com/Ucamo/ucamo.github.io/main/assets/images/postmortem_Dots_of_War/img_5.png" width="80%" height="50%" alt="Dots and boxes concept art with robots">

_Early game design sketches_

After that a “mood board” (a board to inspire us) was made about the type of artistic decisions that would be made, something to point out about how we would like the game to look like, where several photographs were placed to inspire us, [you can see the mood board here](https://www.pinterest.com.mx/jose3892/puntos/), the Professor Layton saga and Advance Wars were a great inspiration for the look and feel we gave to Dots of War.

### **How long do we though the project would last?**

Initially we thought that the project would last around 3 months, however, once we had the art of the game we decided to extend the development time “a little bit longer” to deliver a better quality product, that would become a process of around 9 months.

### **How do we divide the work/time/tasks/talent on the project?**

Initially the project began with 8 members, 3 programmers, 2 3D artists, 1 2D artist (who also had the task of art director), a person in charge of user experience and quality, and a person in Game Design and 2D art.

But like other decisions, each time the team made a proposal for change we took into account what was agreed by the majority, within each sub-team the final decision was left within them, taking into account the opinions that were gave, we did not want to influence decisions that we were not very sure of the opinion we were giving.

At the beginning, these positions did not exist but we let it be known what type of role we felt most comfortable to work during the project, taking into account the abilities of each person and the area in which we would like to collaborate.

<img src="https://raw.githubusercontent.com/Ucamo/ucamo.github.io/main/assets/images/postmortem_Dots_of_War/img_6.png" width="80%" height="50%" alt="Dots of war stone character">

From the beginning, we decided that this would be a project that we would have to complete in our spare time, when we were not attending our main responsibilities with our work and family.

Therefore, each week during a small call of 15–30 minutes, we would update our progress during the project and we would end up clarifying how many hours we were going to be able to dedicate to the project that week, normally, it would be 6 to 10 hours per week.

We respect each member’s time a lot and we didn’t want them to feel that a lot of time was being demanded from them, so we let each member take responsibility for their time.

To divide the tasks, we used [Trello](https://trello.com/), where each member could select the task they wanted to work on based on their talents and what needed to be done at that time.

### **How do we calculate how much it costs to make a game?**

At the beginning of the project, we asked everyone involved to calculate how much they would charge for an hour of their work, that amount would be multiplied by the hours worked in a week, we would take 4 weeks as a month, and that would be the cost of “a month of development”.

Given that Dots of War was a hobby project, that money would not come from any investor and would be “absorbed” by us, at the end of the day we wanted to know how much it would cost us to make a game of these features between the team. This excersie gave us an idea of the real cost of production for a game like this.

<img src="https://raw.githubusercontent.com/Ucamo/ucamo.github.io/main/assets/images/postmortem_Dots_of_War/img_7.png" width="80%" height="50%" alt="Dots of war human character">

$ 27,650 Mexican pesos (about 1,370 USD) was the average cost per month to maintain the team, this without counting any other operating expenses, licenses or computer equipment, those 27 thousand virtual pesos would be exclusively to pay salaries.

If the project lasted 3 months, the calculation would be: 3 x $ 1,370 = $ 4,110 USD That would be the amount that the game should earn as profit to come out in black numbers if we had invested in real money wages.

Every month that we go overboard with the game’s release, $ 1,370 USD should be added to pay for that month’s wages.

Properly, in a real project, you should have a monetization strategy to try to earn 5 times the development cost, giving a total of: $ 20,550 USD which would keep LunarCrown with enough money to pay the salaries, licenses and the development of the following game.

As we will see throughout this article, we will find out how we failed to reach those goals.

### **Create an MVP**

Once we had defined the idea of ​​the game we wanted to do and the tasks that had to be completed to launch the game, we decided to make a Minimum viable product (MVP) or Proof of concept (POC) that is simply to implement the basic mechanics of the game to test it internally and see if it was actually fun.

<img src="https://raw.githubusercontent.com/Ucamo/ucamo.github.io/main/assets/images/postmortem_Dots_of_War/img_8.gif" width="80%" height="50%" alt="Dots of war first prototype MVP">

_First version of Dots of War_

- The player can connect two dots with a line
- The player can make a square by connecting four points with lines
- The game identifies that it is a “square” and gives a score to the player who closed it.
- The game identifies when it is the turn of each of the two players.
- The game ends when there are no more possible moves to make and determines which of the two players is the winner.
- The player can choose to play again.

All this was done with very rudimentary placeholder art, a user interface that would not be the final but that would help us to know what was happening “behind the scenes” of our game.

<img src="https://raw.githubusercontent.com/Ucamo/ucamo.github.io/main/assets/images/postmortem_Dots_of_War/img_9.gif" width="80%" height="50%" alt="Dots of war first prototype MVP two player local">

Once we had the basic mechanics of the game, we knew that we could finish such a game and the next thing would be to polish the game to make it more fun and add the art.

### **Scope creep first signs and how to deal with them**

Scope creep is a term used in projects when the scope of the project begins to extend from a small project to a larger and larger project.

It is very easy to get carried away by the hype of wanting to add more features to a game, but it is also part of the responsibility and professionalism of the members to know how to recognize when the project should be adjusted to what has been agreed to and respect the time of everyone in the team.

<img src="https://raw.githubusercontent.com/Ucamo/ucamo.github.io/main/assets/images/postmortem_Dots_of_War/img_10.png" width="80%" height="50%" alt="Dots of war wizard character">

At LunarCrown, we care a lot about the team’s time, so we highly respect the time they put into the project and we like to know that we are making the most of it.

Once we had the MVP and had a Dots and boxes game that worked and was for two players, making it stand out was part of the next task.

This can be achieved thanks to amazing art, interesting visuals, or unique mechanics that would set it apart from the rest of the games of this genre.

But in each of those aspects, it’s easy to get carried away and want to add “just one more thing.”

For example, in Dots of War you can choose 3 different heroe classes to play, each class has at least 1 2D skin to represent it (with the option to buy additional skins) and 3 3D models to represent when they have captured an area in the game map.

<img src="https://raw.githubusercontent.com/Ucamo/ucamo.github.io/main/assets/images/postmortem_Dots_of_War/img_11.gif" width="80%" height="50%" alt="Dots of war 3d prototype Pre alpha build">

_Pre-Alpha build of Dots of War_

It was very tempting for the team to say “Let’s add another class”, but that represents:

- Create more 2D assets.
- Balance the character selection user interface (or code a workaround for the selection menu that accommodates each new character, which would also take unbudgeted time)
- Create 3 extra 3D models.
- Make a complete regression test with the new combinations between classes.

<img src="https://raw.githubusercontent.com/Ucamo/ucamo.github.io/main/assets/images/postmortem_Dots_of_War/img_12.png" width="80%" height="50%" alt="Dots of war stone character color">

At times like that we can ask ourselves as a team: Is it really necessary to add a new character? Will it add more value to our game? Is it worth the reward that we will receive in exchange for the effort that has to be made? Are there other pending goals that we could be achieving instead?

Game development is full of decisions that are not fun, but that have to be made in order for the project to be completed in the end.

At the start of the project, each class also had a “special ability”, this ability could be used when the player gained 3 energy points and those energy points were obtained by capturing adjacent squares, the amount varied depending on the class.

Aside from their special ability, all classes have a common ability called “block” that when used, the opponent cannot continue their turn after capturing a square.

- Humans could spend their 3 energies to steal a square from the opponent.
- Stonemen could lock their squares to be un-stealables.
- Wizards could block a line so that only they could use it.

Having a special ability for each player was very attractive to the team and to the game, but that functionality had to be programmed individually by each class and tested several times against different combinations of players to balance them.

<img src="https://raw.githubusercontent.com/Ucamo/ucamo.github.io/main/assets/images/postmortem_Dots_of_War/img_13.gif" width="80%" height="50%" alt="Dots of war wizard using his special ability">

_Wizard using his special ability_

Special abilities became a very big problem, the game had to keep moving forward, the programming team had to finish implementing that functionality and test it to see if the mechanics were balanced and if the game became more or less fun with it.

Something that happens in game development is that we focus so much on the project that sometimes we can no longer trust if what we are trying over and over again is still fun, so we must constantly be testing with people outside the team to listen fresh feedback and opinions.

Explaining the mechanics of class abilities was so difficult for outside players that the best decision we had was to cut that aspect of the game.

We had invested a lot of time on this feature, and we still didn’t know if this other great piece of game design was going to fit in with the core mechanic or if it was going to have some detrimental effect when players realized that a certain class had an advantage over others.

There was an internal vote to talk about this feature, and an agreement was reached to remove it from the game and only leave the general blocking ability for all classes, at this point all classes are the same.

### **Make an online game**

Some would think that the most difficult part of the project was the online mode, but thanks to plugins like [Photon](https://medium.com/@carrillouriel/unity-multiplayer-tutorial-using-photon-pun-fa6f86e44c44) this part was relatively simple.

In the original scope of the project we wanted to make a game that was multiplayer online, no team member had done a project like this before and it was really challenging for us.

Very early in the design of the game (and several times it was recommended by acquaintances outside of game development) the option of creating our own client-server logic was contemplated to have a more complete control of the game. It was agreeded not to use our own solution since we didn’t have the estimated time for doing so, and at the end it wouldn’t add value of our end goal.

We built the online interaction to be scalable in case in future versions we decided to create our own API for it, but for now, no one was going to commit to leaving the development of the game to create those pieces, so we voted not to do it.

<img src="https://raw.githubusercontent.com/Ucamo/ucamo.github.io/main/assets/images/postmortem_Dots_of_War/img_14.png" width="80%" height="50%" alt="Dots of war human character color art">

Photon is a tool that manages the logic of receiving and transmitting information from clients to servers.

It has a free plan that allows you 20 concurrent connections, if there are more than 20 players playing the game at the same time, it begins to deny the service to those who are arriving, but as an account administrator, you can decide at what time to upgrade your account and allow more concurrent connections.

We concluded that, for an MVP and as an initial version, the free version of Photon would serve us quite well, and that if we had the “problem” that more than 20 players were playing at the same time, it would be worth upgrading, but for now we would monitor the number of concurrent players and we would evaluate the situation according to the data we have.

The way we implement the logic for the online game is quite simple.

- First we finished the whole game so that it could be played with only one person.
- Then we did the logic for the game to be played with 2 people using the same device and thus see how the turns behaved.
- Once we polish that part, we create the online mode, where a room is created and we wait for another player to connect, once inside the room the game begins and determines who is player 1 and who is player 2 .
- The actions of each player are transmitted to the network, and the game is designed to receive the actions and show the same interaction regardless of the devices.

### **The devil is in the details**

So what happens when you already have a game, the art is in place, and you already have the online game mechanics in place?

**You have to finish the game.**

That last 10% to finish a project of this type where you have to correct the bugs, finish doing the complete regression tests, create the images for the stores where the game will be published, prepare the optimized text with ASO (App Store Optimization) So that it has a good ranking in each store, do your best to translate your images and text into other languages, prepare a trailer, and a list of tasks that are not technical but have to be done.

It is hard to finish a game and when you have invested so much time in a project you can focus a lot on one aspect and start neglecting others, so it is important that team members have a clear goal of what they want to achieve.

The development of Dots of War began in July 2019 and by October we already had an MVP and from then on it would be a matter of polishing it.

<img src="https://raw.githubusercontent.com/Ucamo/ucamo.github.io/main/assets/images/postmortem_Dots_of_War/img_15.png" width="80%" height="50%" alt="Dots of war wizard character color art">

We started the project with 3 programmers, but before the first three months the programming team was reduced to 1 since one programmer had to move to another city for a better job, and another was cut from his job and we understood that making games as a hobby it wasn’t going to be their priority for the next few months.

At LunarCrown we always think of people first before work, and at the end of the day, it was a joint time that we were giving for the project, so there were no misunderstandings, they remained part of the team and gave their feedback but they were not assigned tasks each week.

### **Do you know what happened in late 2019 and early 2020 too?**

The **COVID-19** pandemic affected all industries and all jobs included where 2 team members worked, they had to reduce staff, so one was fired, and the one who remained had to take the work from several positions.

So once again certain tasks were going to be put on hold while everything settled down and they had more free time to dedicate to the project.

<img src="https://raw.githubusercontent.com/Ucamo/ucamo.github.io/main/assets/images/postmortem_Dots_of_War/img_16.gif" width="80%" height="50%" alt="Dots of war stone vs human match">

I believe that at this point, more than one person would have put this project on hold and rethink the scope, or perhaps release a simpler game, or some other solution.

In our case, the art team had finished their assignments, and had done such a good job that it seemed like a waste not to finish Dots of War.

So we decided to go a little slower but still keep going. After all, the game was almost done, only that last 10% was missing.

### **The worst mistake we made**

<img src="https://raw.githubusercontent.com/Ucamo/ucamo.github.io/main/assets/images/postmortem_Dots_of_War/img_17.png" width="80%" height="50%" alt="Dots of war human samurai skin">

_Optional Samurai Skin for Humans_

We are a team that likes to share updates, bugs and other details during the development process of a game, Dots of War was no exception, we did not have a pre-established Marketing campaign apart from the diffusion that we gave to the game with acquaintances, relatives and on social networks.

We liked to participate in posts where progress was shared or in #screenshotsaturday.

Given the great progress we had, we made what I consider to be the biggest mistake during the entire project development process.

### **Commit to a game release date.**

At the end of March 2020 we calculated what had to be done (include the purchases of skins in the game and do the whole submit process for iTunes) and we guess the date when we would have everything ready, so we implemented it and started the submission process to iTunes.

In this part I was going to comment on a long list of things that displeased me about the process that Apple has to submit its applications but I prefer to summarize it with:

_I have nothing good to say about the app development process for Apple or its platform._

For people interested in publishing their game with [Unity](https://unity.com/) on iOs, here are some tips we learned the hard way.

- Have a Mac on hand with the version of Unity you are developing on, there are options such as Unity Cloud build but if there is a slight possibility that you have to alter a configuration file for iOs, get a mac with someone you know or member of your team.
- The change on status of your application take time, nobody knows how long they can take and you have no control over how long it may take.
- Keep in mind that iOs is very selective with the plugins that you can use in your project, sometimes certain plugins can alter some permissions of your application that will give you a headache once they start rejecting your application and tracking the error code that apple sends you.

### **Why do I say that giving a release date was the worst mistake we made?**

Because we really didn’t have the need to give a launch date, we could have launched in the same way on some other date and there would have been no problem or angry reviews, coming up with a launch date puts extra weight on the team and on this case it was a Hobby project, no one was asking or expecting one except us.

### **Burnout**

During this project I had to take two breaks due to the burnout (or exhaustion / fatigue syndrome) that I felt, one in December to have the opportunity to spend more time with my family, and another in May, when the pandemic was on the rise and the stress I had from working manifested itself as a rash on the skin of my hands that so far has not completely gone away (constantly washing my hands and putting alcohol on them to prevent COVID doesn’t help either)

Right before launch we did the media outreach by sending personalized emails to about 200 websites to cover the launch, we fixed the latest bugs, and we were able to launch the game.

### **When you realize that the last 10% is actually the last 30%**

<img src="https://raw.githubusercontent.com/Ucamo/ucamo.github.io/main/assets/images/postmortem_Dots_of_War/img_19.png" width="80%" height="50%" alt="Dots of war stone robot skin">

Once we launched the game and had the external impressions, we noticed some minor bugs, and a major one (the skins could not be bought), we had a group of alpha users who helped us a lot during development, but we never tested directly that part with them, only internally.

At that time, since we saw that the effort to contact the press did not give the results we expected (we ended up being covered by some portals, but in general many websites ask you for money to cover your game, money that we did not have budgeted for, so we had to miss that opportunity) and having the whole team really tired, we decided to take a few days to rest, and return to the project with fresher eyes.

In the end the errors were corrected and the project was complete in its first version, we had made a game together with a 100% remote team and we finished Dots of War.

### **What to do in case of fire?**

We had an entire marketing strategy planned before launch that included:

- Attend local events
- Attend national video game development events
- Make public presentations where attendees could test the game, give us their comments, win prizes.

But any face-to-face activity was totally ruled out as of March 2020 here in Mexico when the quarantine plans officially began.

<img src="https://raw.githubusercontent.com/Ucamo/ucamo.github.io/main/assets/images/postmortem_Dots_of_War/img_19.png" width="80%" height="50%" alt="Dots of war wizard cowboy skin art">

Being a team that already worked remotely, it did not affect us at the time of work but we were quite affected in other areas, both in our formal work and in our interpersonal relationships, there were months of a lot of personal stress so we didn’t asked anyone to do more work than they were comfortable with and we relaxed the notion of due dates quite a bit.

Even so, working your full shift from home, taking care of your family and working on a project like this, even if it is a hobby, takes a price on one, many team members experience burnout to a greater or lesser extent.

The best thing to do in these cases is to take a step back, take a deep breath and evaluate what your priorities are, take time to rest and when we are in a better state of mind, continue.

We are very grateful to be part of a team that understands and is responsible for its members, who knows how to demand results but who also really cares about the person who is delivering them, after all, we started as a group of friends. with a common goal, and our relationship is more important than any project.

### **What did we learn? How can we end this on a happy note?**

The development of Dots of War is not a commercial or media success story, but it is a success story for game development on remote teams.

**Any game that is completed is a success.**

There are many opportunity areas in Dots of War, but we are also very happy with what we achieved, a precedent was made for this type of development, no funds, no third-party money injections, no loans or government aid, all valid ways to start making games, but not the only ones.

There will always be a way to move a project forward, and not even a pandemic or the end of the world can stop it.

### **What could have gone much worse?**

Good and bad decisions were made during the development of Dots of War, some based on time and some based on money.

Long before starting this project, we talked to team members about creating a game for PC and consoles with a development model very similar to what we had (but including an office provided by a group of investors), in the middle of the development of Dots of War we realized that if we had committed ourselves to making that game with that much larger scope, it would have placed us in a much more difficult situation and not at all redeemable as this project was.

We are very happy with the results we had and with the decisions we made, but we are also very happy with the other decisions that we did not make.

<img src="https://raw.githubusercontent.com/Ucamo/ucamo.github.io/main/assets/images/postmortem_Dots_of_War/img_20.png" width="80%" height="50%" alt="LunarCrown logo">

### **What’s next?**

As a final note, we want to thank everyone involved during the development of Dots of War, all beta and alpha testers, the [Unity user group HMO](https://www.facebook.com/UnityHmo/) community that supported us from the beginning, the people who found out about the project and they gave their words of encouragement to us and to all Dots of War players.

Thank you very much, we did the best we could at the time that we could.

Now as we recover from burnout, it becomes clear to us that there will always be more games to do, a next project to do and when you develop as a hobby and to learn, you do not have to be accountable to anyone.

It‘s OK to learn from our experiences and not think that they were a failure, it’s OK to take a step back or stay for a while to catch your breath, everyone advances at their own pace and we are very happy to know that we keep trying.

For [LunarCrown](http://lunarcrown.com/) there are surely more projects, but given the current situation, we do not know what form they may take in the immediate future, but we are sure that we will count on each other to continue supporting each other.

<img src="https://raw.githubusercontent.com/Ucamo/ucamo.github.io/main/assets/images/postmortem_Dots_of_War/img_21.png" width="80%" height="50%" alt="Dots of War logo">

## Credits

**Game Design, 2D art**

Arvin Valenzuela

**UX-UI, Quality Assurance**

Jose Miguel Angulo

**Art Director, 2D art**

[Roberto Carlos Nuñez](https://www.instagram.com/carlosnlart/)

**3D art**

[Mariel Rojas Pérez](https://www.instagram.com/rojasmariel/)

[Sergio Mireles](https://smirelesz.artstation.com/)

**Programming**

[Antonio Martinez](https://gatomocho.com/)

[Uriel Carrillo](https://ucamo.github.io/)
