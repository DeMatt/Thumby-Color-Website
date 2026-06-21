# Connect and First Save
First things first, make sure your **Thumby Color** or **Thumby Color Dev Board** is connected to your computer using a USB-C cable. Once physically connected, press the **red stop sign** symbol in the top left of Thonny. The **Shell** window will output the **>>>** prompt once connected.

Inside **Thonny**, left-click the **< untitled >** pane and then press **ctrl-s** and choose **Raspberry Pi Pico**:

![](images/1_save.png)

Next, navigate into the **Games** folder by double left-clicking it, and then right-click anywhere and choose **New Directory...**
![](images/2_create_game_folder.png)

Choose any name for your game folder and then navigate into it. Name the file you're saving as **main.py** and press **OK**.
![](images/3_finish_saving.png)

Now anytime you press **ctrl-s**, the file will be saved to the device.


# First Game
To create a very basic scene we need to:

* Import `engine_main` to set the engine up
* Import `engine` for starting or ticking
* Import the nodes we want and a camera
* Create the nodes
* Start the engine

```py
import engine_main
import engine
from engine_nodes import Rectangle2DNode, CameraNode

rectangle = Rectangle2DNode()
camera = CameraNode()

engine.start()
```

![](images/4_first_game.png)

A white square on a black background!  Pushing any of the buttons does nothing, and you'll have to restart the Thumby Color by flipping the power switch (or hit Thonny's "Stop/Restart backend" button if we've got the Thumby Color connected).  Well, that's boring.

## Start() and Tick()
Now, there are two main ways to run the game engine:  `engine.start()` and `engine.tick()`.

* `engine.start()` is a more object-oriented way of running the game engine:  you set up all your Nodes with `.tick()` attributes to update them, and then call `engine.start()` and let it rotate through all your Nodes, calling their respective `.tick()` attributes during each frame.
* `engine.tick()` is more procedural.  You call `engine.tick()` to check whether the engine has started the next frame; True = yes, False = no.  Note that when it is time, the call to `engine.tick()` will also call all your Nodes' `.tick()` attributes.
