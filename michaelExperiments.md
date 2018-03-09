### Experiment Time!
I have always thought it was a bit silly that the field of computer science was called "computer science". As far as I had ever experienced, there was nothing really sciencey about it. You take technologies that have already been proven to be useful, and use them to make something. That was pretty much the extent of my experience. Recently, however, I finally got the opporunity to learn more about where the word "science" really comes from. This quarter I got the opportunity to play around with and run experiemnts on capsule networks.

#### Setting Up My Environment:
This part was a pain in the butt. I had to simultenously learn how to do several things in order to get started. First, there was relearning how python works. To be hoenst, I haven't used this language much since I first started learning how to program. Second, I had to learn how to interface with Tensorflow. Thankfully, Keras helped abstract a lot of the ugly math away from me, so this part wasn't as difficult. Next, I had to somehow figure out how to incorperate Horovod into all of this so that I could distribute my network. Again, thankfully this was surprisingly easy. I had to copy a few lines of code that they recommended here and there throughout my python script and then I was good to go on that end. Finally, after hours of playing around with different versions of libraries and setting different environment variabels, I was running experiments. I saw something similar to this in my console.

![alt text](FreeMemory.png)

When we first started trying to run experiments, we realized that they were running a lot slower than we initially expected. 
