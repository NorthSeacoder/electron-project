In the last section I give you a soft introduction to electron remember electron is a platform for creating

desktop applications while using familiar web technology tools.

In this section we're going to immediately dive into some of the details electron and get a better sense

of how it works internally.

After that we'll discuss a little bit more about the history of electron and then move towards working

on our first project.

So let's get to it.

So again in this section I want to talk to you a little bit about how the internals of electron works

and we're going to do so by looking at a very familiar piece of software that you might already have

installed on your local machine.

OK.

So here's my claim.

Electron is almost identical in its internal workings to google chrome and I do notice the qualifier

down here mostly mostly though the similar.

So in this section we're going to look at how Google Chrome works internally.

And then we're going to try to move all that understanding of how Google Chrome works over to how electron

works internally.

Now do keep in mind that as we're talking about how electron works internally and how Google Chrome

works internally I really am talking about the internal very internal workings like the inner gears

and the inner code that's working inside of electron.

I'm not necessarily talking about how you and I write code for electrons.

So I want to quantify or clarify that point.

OK.

So to demonstrate a little bit about how Google Chrome works internally give you a better sense of what

it is doing.

I'm going to open up two programs on my local machine.

I'm going to first open Google Chrome of course and then I'm going to open up the activity monitor as

well.

Activity.

There we go.

OK.

So I've got good chrome open.

There it is right there.

And I've got my activity monitor.

If you've never used it before the activity monitor shows me all the different running processes I have

on my local machine.

If you're on Windows right now you can always pull up the Task Manager as well and check out the running

processes that you have on there too.

So in my activity monitor you'll see processes like Adam.

There's my code editor.

Here's balsamic mockups which is what I use to make diagrams for this course.

And if I scroll down a little bit it will come across Google Chrome right here.

So immediately when we look at Google Chrome you see not only Google Chrome but you also see this collection

of Google Chrome helpers.

Hum.

Well that's kind of interesting what in the world are Google Chrome helper's.

Let's investigate what these things are.

Let's get a better sense of what a Google Chrome helper process is.

And do remember as we're walking through this the entire point of looking at Google Chrome is to get

a better sense of how electron is working as well.

So I just want to remind you that's what we're attempting to accomplish here.

I'm going to go back over to my browser and I'm going to open up a couple of different tabs and inside

of each one I'm going to navigate to Google dot com.

It's going to get about six or seven tabs or so that should be good.

Now I'm going to go back over to the Activity Monitor and I'm going to look at the running processes

that I now have.

So after giving it a few seconds to update you're going to notice any second here.

There we go.

A handful of additional Google Chrome helpers were just created.

You can see them all listed here.

Again there's about six or seven one for each tab that I just opened.

So what is Google doing here what is chrome doing here why is it spawning all these different processes.

Well let's look at a diagram.

OK so when you start up Google Chrome and you see inside of your activity monitor a process called Google

Chrome we can refer to that as the browser process.

That is the process that runs the actual window that runs Google Chrome like this actual physical window

like the Holberg outlines the thing that shows the buttons here at the top left.

The thing that shows the menu bar at the top all that different kind of stuff on the other hand we have

these individual tabs which we refer to as child processes or processes that are intended to just run

a single tab inside the browser.

So why might google chrome choose to architect their program in such a fashion why might they choose

to have one process for the overall browser.

And then one process for each of the different tabs that we have opened.

Well Google Chrome decided to architect a program like this to have better encapsulation of each tab.

So if one tab opens up let's say that I open up this tab right here and maybe the rendering engine used

by the browser has some big security issue or some big rendering issue.

The idea is that by isolating each tab into its own separate process we isolate its ability to affect

the overall operating system or overall other tabs that are running inside the browser as well.

So it's really being implemented from a security standpoint and a functionality or essentially bug resilience

standpoint as well.

We referred to those child tabs either as child browser tabs or as render or processes or a render process.

So we have our overall chrome application that spawns all these different render processes each of which

shows some web page.

OK so you're probably sitting here thinking Stephen how again is this all relevant to electron and hey

bear with me here we're getting to the point.

These separate processes that we create or that Google Chrome creates I should say are so separate that

they don't have the ability to directly talk to each other or communicate even with the overall chrome

application.

Instead they communicate through a system called inter-process communication or IPC for short.

We're going to see IPC and this idea of separate render processes come up again and again as we are

working through electron.

So at this point in time you really probably are thinking okay Steve and this is all great.

Thanks for the review of how my browser works.

But what does this have to do with electron.

Ah but that is the point here.

Electron works identically to how your browser browser does surprise under the hood.

Electron makes use of the chromium open source project which is the exact same codebase that the Google

Chrome browser is based upon as well.

So when we work with electron all the same rules and conventions of how chrome works applies directly

to electron as well in an electron up.

We are going to create an object or a process that spawns one main window and that is going to have

some number of child render processes as well.

The purpose of each of these render processes in our electron application is to show a separate window

to use or in a sort of desktop looking environment.

Our electron can have as many running render processes as we wish.

Each would show a separate window to the user communication between each of these windows is going to

be handled by that same IPC or inter-process communication system as well.

So remember at the end of the day whenever we are making use of electron we can really think of it as

working identically or the exact same as our Chrome browser does as well.

And this is really important to understand because behind the scenes you're going to notice some really

weird ways in which we're going to interact with the electron.

The reason I'm showing you all this is to give you a little bit of backstory a little bit of sense of

why we are interfacing with electron and sometimes what might seem like a kind of odd fashion.

OK Selassie I want to say about electrons for now.

So you might be used to developing apps for the web.

So whenever you're making web sites or web applications you can kind of imagine that only the stuff

inside of the body of the browser like this content area right here is fair game for us to mess around

with or to show content or to handle events or stuff like that.

When we start to use electron However I want you to start to imagine that we are now developing for

the same environment.

But the big change is the area that we have to affect with the code that we write with electron are

fair game extends to the entire browser window.

So we are no longer being limited to just the content in here.

We get to have access to absolutely everything that makes the browser the browser.

Now that might seem like kind of a weird comparison to make but again trust me when we start working

through electron having these kind of distinctions or this thought process is going to start to make

life a little bit more easy.

OK.

So now we've got a slightly better sense of what electron is doing behind the scenes.

Let's continue on the next section where we're going to learn a little bit more about the history of

electron.

So I'll see in just a second.
