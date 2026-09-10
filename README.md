# Remote-Android-Access
Android Remote Access is a hands-on cybersecurity project that demonstrates authorized remote access to a personal Android device using Wireless ADB and scrcpy over a local Wi-Fi network. The project explores device pairing, authentication, client-server communication remote screen control, and the security risks associated with exposed remote-access services.

# Tech-Stack: 
Android Wireless ADB
• ADB
• scrcpy
• Windows PowerShell
• Local Wi-Fi

# Step 1 — Enable Developer Options on your Android phone

On your phone:
Open Settings.
1. Go to About phone.
2. Find Software information if your phone has that submenu.
3. Find Build number.
4. Tap Build number 7 times.
5. Enter your phone's PIN/password if asked.
6. You should see something like:
 "Developer mode has been turned on."

Now go back to the main Settings screen.

# Step 2 — Open Developer Options

Go to:

*Settings → Developer options*
The exact location can vary by Android/Samsung version. On Samsung phones, it's usually:

Settings → Developer options
Turn on:
✅ USB debugging or Wireless Debugging

You'll see a warning. Accept it.

This allows your computer to communicate with the Android device through ADB (Android Debug Bridge).

# Step 3 — Enable Wireless Debugging

Inside Developer options, find:
1. Wireless debugging
Turn it ON.
Your phone and laptop need to be connected to the same Wi-Fi network for the simple local-network setup we're doing.
2. Tap Wireless debugging to open its settings.

You should see options such as:

*Pair device with pairing code*
*IP address & Port*
*Paired devices*

# Step 4 — Check ADB on Windows
Run : 
*adb version*
(If ADB is installed correctly, you'll see something similar to : 
Android Debug Bridge version ...)

If PowerShell says:
*adb : The term 'adb' is not recognized*
(then ADB isn't available in your PATH yet. Tell me what you get and we'll fix that before continuing.)

# Step 5 — Start the ADB server
Run:
*adb start-server*

You may see:
* daemon started successfully *
  
Now run:
*adb devices*
(At this point, don't worry if your phone isn't listed yet because we're setting up wireless ADB)

# Step 6 — Pair the phone with PowerShell

On your phone:
*Developer options → Wireless debugging → Pair device with pairing code*

You'll see something like:

*Wi-Fi pairing code: 123456*
*IP address & Port: 192.168.xx.xx:xxxxx*

Keep this screen open.

*In PowerShell, run:*

*adb pair IP_ADDRESS:PAIRING_PORT*

For example:

adb pair 192.168.xx.xx:xxxxx

PowerShell will ask:

Enter pairing code:
Enter the 6-digit pairing code shown on your phone.
If successful, you'll get something like:

*Successfully paired to ...*

*Important*
The pairing port and the later ADB connection port may be different.
Don't assume they are the same.

# Step 8 — Verify the connection

Run:
*adb devices*

You should see something similar to:

*List of devices attached*
192.168.xx.xx:xxxxx    device

The important word is:
device
That means ADB recognizes the phone as an authorized device.

# Step 9 — Install scrcpy

Now we use scrcpy.
scrcpy allows you to display and interact with your Android device from your computer.
After installing scrcpy and making sure it's available 
In PowerShell, run:

*scrcpy*

If only one ADB device is connected, scrcpy should automatically select it.

Or explicitly specify the connected device:

*scrcpy -s IP_ADDRESS:PORT*

For example:

scrcpy -s 192.168.xx.xx:xxxxx

Your Android screen should now appear in a window on your laptop.

🎉 That's the core of your Remote Android Access project.


