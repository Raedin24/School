# Background
This is, once again, a test to measure Obsidian's performance
The *difference* here is that this time, I'm not using the sync option via google drive
The objective is to see whether the slow response in the other vault is due to Obsidian having to wait for a response from the drive for each action performed, and if so, how to speed up the process or switch to a different solution.

So far, all the tests I've performed have led me to the conclusion that although **Obsidian** is better in terms of customization, **Joplin** takes the cake when it comes to response time, sync speed, and basic note-taking functionality. 

However, I came to the realisation that this might be due to the sync I had set up. As I'm working on a Linux OS, I do not have a Google Drive client available. As such, I had to implement a roundabout method of syncing, in which I use **RClone** as my desktop client to sync files between Obsidian and Drive. After that I use **Autosync** on my phone to get the files from Drive onto my local storage, which Obsidian is then given access to.

In this vault, I plan to test the Git community theme, to see if I can use this as a means of backup and sync, all while maintaining a reasonable speed

Here goes

# Tests
## 1
- Right off the bat, I can see that it makes a huge difference in startup time. When opening Obsidian with this vault, the response time is even faster than my previous experience with Joplin. This might be either because of the sync challenges in the other vault, or the lack of community themes in this.
- It is good to note, however, that the Obsidian mobile does not face such startup challenges. Even with the same sync and themes, the start-up time is as fast as can possibly be

Tests shall end here for now, as I require rest. I have installed the git plugin and will proceed to set it up and test it in the coming hours