---
layout: default
title: Step by step tutorial
menu: Getting Started
num: 3
permalink: /getting-started/step-by-step
type: fullpage
---

So you have discovered SAMMI... I can only say: Welcome to the world of endless possibilities!

We will walk you through a step by step tutorial on how to set up SAMMI, and connect it to OBS and your Twitch account. You will also learn how to create your first button, add a command and trigger it via Twitch chat. 

{% include alert.html text="SAMMI is a closed source application made for Windows (other platforms will be fully supported later as well). Our tutorial covers its usage in Windows only." type="warning" %} 

#### 1. Install all dependencies
- Download and install **[OBS Studio](https://obsproject.com/)**. As of now, SAMMI does not support other streaming software.
- Download and install **[OBS Websocket](https://obsproject.com/forum/resources/obs-websocket-remote-control-obs-studio-from-websockets.466/)** This is how SAMMI communicates with OBS Studio. You can download OBS Websocket 5.0 along with the [OBS Websocket 4.9-compat](https://github.com/obsproject/obs-websocket/releases/tag/4.9.1-compat) in order to preserve backwards compatibility. However, this means you will need to set up two instances of OBS in SAMMI, one using 5.0 and one using the 4.9-compat version. For the time being, until you are sure your extensions have been fully updated to use OBS Websocket 5.0, we suggest staying on 4.9.1.

#### 2. Download SAMMI

We recommend selecting **64bits release**.

<a href="https://sammisolutions.itch.io/sammi"><button type="button" class="btn btn-primary mt-1">Download SAMMI</button></a>

Unpack the zip file and place the folder anywhere in your computer, preferably in your non windows drive.

{% include alert.html text="Do not place SAMMI folder in your Program Files or any network drives (Google Drive, OneDrive, Dropbox), as it sometimes can cause issues." type="danger" %} 

#### 3. Launch SAMMI

Navigate to the unpacked folder and launch SAMMI Core.exe.    
Allow the app through the firewall if there's a prompt and you're ready to start!

#### 4. Connect SAMMI to your OBS

1. In your OBS go to Tools-Websocket Server Settings. Uncheck 'Enable authorization' (for easy setup, you can change it later) and press OK. 
	  
	{% include image.html w="100" src="obsws_settings.png" alt="OBS Websocket Settings" type="image" %}

{:start="2"}
2. In your SAMMI, click on **OBS Connections** at the bottom menu. Unless you changed your port in OBS-Tools-Websocket Server Settings or set up a password, you can leave everything at default and press Connect.\
You should see a yellow notification message `OBS [Main] Connected` and the status indicator for `Main OBS` in the left bottom corner should change from red to green. 

  {% include image.html w="75" src="obs-connected.png" alt="OBS is connected" %}

#### 5. Add Bridge to your OBS Dock

In your OBS menu navigate to **View - Docks - Custom Browser Docks**. Your new dock name can be `Bridge` and the URL will be the path to the `bridge.html` file located in your `SAMMI/bridge` folder.

{% include image.html w="100" src="bridge-dock.png" alt="OBS Dock Settings" type="image" %}

Press **apply** and you should see your new dock. If it does not pop up for some reason, you can always go to View - Docks - Bridge.   
Fit your new dock somewhere in your OBS screen as you see fit. 

{% include image.html w="75" src="bridge-dock2.png" alt="Bridge in a dock in OBS" %}

#### 6. Connect Bridge to SAMMI
In your **SAMMI-Settings** menu, check `Allow SAMMI Deck and Bridge` to allow Bridge to connect.\
In your **Bridge-status** tab (in our OBS dock), you can now modify your connection settings.\
Default IP address for SAMMI is always `127.0.0.1` and port is always `9425`. Unless you changed port in your SAMMI-Settings, you can leave it at its default value.\
You must fill out the password if you decided to use one in SAMMI-Settings menu.\
Note that you only need to do this once, as your Bridge will remember the previous settings and will attempt to auto connect next time.

{% include alert.html text="Bridge Port and Password must match what's in the Settings window, not the OBS Connections window." type="danger" %} 

{% include image.html w="75" src="bridge-connection.png" alt="Bridge Connection Settings" %}

In your Bridge you should now see **{% include colored_text.html color="green" text="Connected" %}** or {% include svg_dot.md color="green" %} next to SAMMI. This means it is connected to your SAMMI and listening for messages. 

#### 7. Link your Twitch account

Linking your Twitch account to SAMMI is a necessary step if you want to be able to listen to alerts and control your Twitch via SAMMI.\
*You can link multiple Twitch accounts, however in this tutorial we will focus on connecting your main account.*

{% include video.html w="75" src="link-twitch.mp4" alt="Linking a Twitch account" %}

1. In your SAMMI click on **Twitch Connections** button.
2. Click on **Open URL** which should open a new browser window and redirect you to Twitch to authorize SAMMI.  
3. Press **Authorize** and wait to be redirected again to see `All good, you can go back to SAMMI now` message in your browser.
4. Back in SAMMI you should now see your Twitch account in the list! 
5. You can now optionally check which events to listen for and whether you want to Join Chat Channel for this particular Twitch channel. You want to also check `Auto connect to Twitch Chat`, else you will need to always press the **Connect Twitch Chat** button when you open SAMMI to be able to receive and send chat messages from SAMMI.
6. Press **Connect Twitch Chat** to connect to Twitch chat.

  {% include image.html w="100" src="link-twitch.png" alt="Active Twitch Connection" %}

{:start="7"}
7. Now that your Twitch account is linked in SAMMI, Pubsub status in your Bridge should change to **{% include colored_text.html color="green" text="Connected" %}** or {% include svg_dot.md color="green" %}.\
**Remember you Bridge must be running at all times to be able to listen to Twitch events.**

  {% include image.html w="75" src="pubsub-connected.png" alt="Pubsub connected" %}
  
#### 8. Create your first button

In this part of the tutorial we will learn how to create a button with a simple command and add a Twitch chat trigger to it.     
You can follow the text instructions or click on <i class="far fa-plus-square fa-2x mx-auto"></i> to watch a short video.

{% include alert.html text="Pressing Save <b>twice</b> (once in your edit button screen and once in your edit deck screen) is essential to permanently saving any changes you make to a button." type="warning" %}

<ol>
  <li>{% include video_collapse.html w="80" alt="Creating a new deck" src="create_deck.mp4" %} In your SAMMI click on <strong>Add New Deck</strong> button. You should see a newly created blank deck named Deck 1. Double click on it.</li><br>
  <li>{% include video_collapse.html w="80" name="add_button" alt="Creating a new button" src="create_button.mp4" %} You will see an empty grid. This is your deck where you can create new buttons. Right click anywhere in the empty area and select <strong>Create Button</strong> or simply double click. A new empty button will be created. You can optionally add some text to it as well by right clicking on the button and selecting <b>Edit Appearance</b>.</li><br>
  <li>{% include video_collapse.html w="80" src="add_command.mp4" alt="How to add commands to a button" %} Right click on the empty button - <strong>Add Commands</strong> or double click on it.</li><br>
  <li>{% include video_collapse.html w="80" src="create_command.mp4" alt="Adding a new command to a button" %} Click on the <strong>+</strong> symbol. A dropdown menu will appear. Click on Twitch Commands and select <b>Twitch: Send Message</b> (you can also just start typing <code>message</code> in the search box).</li><br>
  <li>{% include video_collapse.html w="80" src="populate_command.mp4" alt="Edit Twitch: Chat button command" %} Populate the fields:
    <ol>
      <li><code>Message</code> - Put a random text in there. For example <code>Hello World!</code>.</li>
      <li><code>Channel Name</code> - Leave empty</li>
    </ol>Press <b>Save</b> once you're finished.
  </li><br>
  <li>{% include video_collapse.html w="80" src="add_trigger.mp4" alt="Edit Twitch: Chat button command" %} Back at our main deck view, right click on the new button - <b>Edit Triggers</b>. This is where you can assign a Twitch event (such as new subscriber or chat message) to automatically trigger your button.
    <ol>
      <li>Click on the + sign and selected Twitch Chat from the dropdown menu.</li>
      <li>Remove the <code>*</code> in the Message field and populate it with <code>!test</code>.</li>
      <li>Press Save.</li>
    </ol>
  </li><br>
  <li>Once you're back at your main deck view, press <strong>Save</strong>.</li>We have now created a button that will send a chat message <code>Hello World</code> anytime it's triggered. We have also created a Twitch chat trigger which will execute the button any time someone types <code>!test</code> in your Twitch chat.<br><br>
  <h5>Trigger the button manually from SAMMI Deck</h5>
  <ol>
    <li>{% include video_collapse.html w="80" src="open-streamdeck.mp4" alt="Open SAMMI Deck" %} Back in your main SAMMI menu, press <strong>SAMMI Deck</strong> to open it. This is your SAMMI Deck where you can manually press buttons you create in your SAMMI.<br>
      <br>
      {% include alert.html text="sammi only acts as an editor. You can press your buttons in SAMMI Deck." type="warning" %}
      <p>Once launched, you will see connection settings. As we are just keeping everything at default in this tutorial, you can press <b>Connect</b>. Selected deck should be <b>Deck 1</b>. Press <b>Load Deck</b> and you should see your newly created button that we named <code>Send message</code>.</p>
    </li>
    <li>{% include video_collapse.html w="100" src="trigger_button.mp4" name="button_manual" alt="Press your newly created button" %} While looking at your Twitch chat, click on the button in your SAMMI Deck. It should send a <code>Hello World</code> message to your chat!<br>
    <b>Important:</b> Your SAMMI must be running and connected to Twitch Chat (SAMMI-Twitch Connections-Connect Twitch Chat).</li>
  </ol><br>
  <h5>Trigger the button via your Twitch chat</h5>
  <p>Do you still remember the Twitch chat trigger you configured for your button? If you followed the tutorial, it should be <code>!test</code>.</p>
  <ol>
    <li>{% include video_collapse.html w="80" src="trigger_button_chat.mp4" name="button_trigger_twitch" alt="Trigger your button from Twitch chat" %} Try typing <code>!test</code> (or anything else you chose to be your trigger) in your Twitch chat while looking both at your chat and SAMMI Deck.<br>
      Two things should happen:
      <ul>
        <li>You will see the button in your SAMMI Deck blink, just like when you manually pressed it with your mouse.</li>
        <li>SAMMI will respond back with <code>Hello World</code> in your Twitch chat.</li>
      </ul>
    </li><br>
	  </ol>
</ol>

Now you have learned how to create a button, add a command and trigger it via Twitch chat! You can find more information about the individual components, commands and triggers in the next sections of the documentation. 

{% include alert.html text="Didn't work as expected? Cannot connect to OBS, Bridge or Twitch chat? Please refer to our <a href='/troubleshooting/common'>Troubleshooting</a> section!" type="info" %}
