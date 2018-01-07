## How To Install

Step 1: Create ".themes" and ".icons" directories  in your user directory if they don't already exist.
(Note: You may have to enable "view hidden folders" in the file manager to see the ".themes" ".icons" directories after creating them.)

    mkdir -p ~/.themes/ ~/.icons/

Step 2: Copy the "Chicago95-custom" directory into the ".themes" directory.

    cp -r Chicago95-Custom-XUbuntu-16.04-/theme/Chicago95-custom/ ~/.themes/

Step 3: Copy the "Chicago95-icons-tux" directory into the ".icons" directory.

    cp -r Chicago95-Custom-XUbuntu-16.04-/icons/Chicago95-icons-tux/ ~/.icons/

Step 4: Copy the "gtk.css" file from the "misc" directory into "/home/$USER/.config/gtk-3.0/" or append the file if a gtk.css file already exists.
(Note: You may have to create the "gtk-3.0" directory.)

    mkdir -p ~/.config/gtk-3.0 && cat Chicago95-Custom-XUbuntu-16.04-/misc/gtk.css >> ~/.config/gtk-3.0/gtk.css

## Configuration

Enable the notification balloon theme.

• To set the notification theme, open the system notification settings manager (xfce4-notifyd-config) and in the "Theme" option select Chicago95-custom in the pull down menu.

Enable the XFCE shell and icon themes.

• In XFCE select Settings -> Appearance. Click on 'Style' and select Chicago95-custom.

• In the Appearance manager click on the "Icons" tab and select Chicago95.

Enable the XFCE window manager theme.

• In XFCE select Settings -> Window Manager. Under 'Style' select Chicago95-custom.

#### • Font Settings:

In the XFCE Appearance Manager, select the "Fonts" tab and apply the following information.

    Default Font: Sans 10

    Enable Antialiasing: Yes

    Hinting: Full

    Sub-pixel order: None

In the XFCE Window Manager

    Title bar font: Sans Bold 8pt

#### • Compositor Settings:

In the XFCE "Window Manager Tweaks" manager, select the "Compositor" tab. Uncheck "Show shadows under dock windows." This will prevent applications from casting a shadow onto the task bar.

#### • Panel Setup:

Create a new panel if necessary. Horizontal, 32px high ONLY (this is for the persistent START button), and 100% Length. (Only horizontal taskbar. No vertical taskbar, sorry.) In the “Appearance” tab set the background style to "None" so that it inherits the theme style and adjust the Alpha to 100.

In the “Items” tab, add the following in this order:

    1. Application Menu OR Whisker Menu; 

    2. Separator (Handle Style); 

    3. Custom Launcher, Custom Launcher, Custom Launcher, etc.

    4. “Show Desktop” plugin; 

    5. Separator (Handle Style); 

    6. Window Buttons (Sorting Order: Time-stamp and Window Grouping is Always. Uncheck “Show Handle” if it’s enabled. Uncheck "Show flat buttons" if it's enabled.); 

    7. Separator (Transparent with Expanding); 

    8. Separator (Handle Style); 

    9. Notification Area (19px max icon size); 

    10. PulseAudio Plugin (Uncheck mark in the plugin settings, "Show Notifications when volume changes." it will conflict with XFCE notifiyd by making duplicate volume notifications); 

    11. Separator (Transparent); 

    12. Orage Panel Clock. ( In the plugin settings, enable check box “Show frame” and replace the text in “Line 1” with %I:%M %p.) Note: If you want to display the date in the clock, append “%D” in “Line 1.” If you want a better looking date, you could replace that by appending “%b %m %Y” instead.

#### • GTK3 (GNOME) applications missing titlebar colour & border - workaround:
Disabling Client Side Decorations with [gtk3-nocsd](https://github.com/PCMan/gtk3-nocsd) will allow for the XFCE window manager to correctly display borders and titlebars over GTK3 applications that are utilizing Client Side Decorations. Check the README.md for this reason.

Note: If you run this theme without gtk3-nocsd, you will notice some GTK3 applications (Software centre, Cat Fish file search, or the Gnome Disk utility) missing visible borders and lack of a distinct header bar. They are still usable, but just unsightly.

• If you want to **INSTALL** gtk3-nocsd:

Download the repo and extract it:

    wget https://github.com/PCMan/gtk3-nocsd/archive/master.zip
    unzip master.zip

Install the dependencies:

    sudo apt install pkg-config libgtk-3-dev libgirepository1.0-dev

Move to gtk3-nocsd directory and build the application:

    cd gtk3-nocsd-master/
    make

Move the newly compiled executable file and library.

    sudo cp libgtk3-nocsd.so.0 /usr/lib/x86_64-linux-gnu/
    sudo cp gtk3-nocsd /usr/bin/

Set the system variable for gtk3-nocsd.

    echo "GTK_CSD=0" | sudo tee --append /etc/environment
    echo "LD_PRELOAD=/usr/lib/x86_64-linux-gnu/libgtk3-nocsd.so.0" | sudo tee --append /etc/environment

Log out then log back in.

• If you want to **UNINSTALL** gtk3-nocsd:

Remove the following system variables from your `/etc/environment` file with a file editor such as nano or VI.

    GTK_CSD=0
    LD_PRELOAD=/usr/lib/x86_64-linux-gnu/libgtk3-nocsd.so.0

Log out then log back in before continuing!

Remove the gtk3-nocsd executable and library from your system.

    rm /usr/bin/gtk3-nocsd
    rm /usr/lib/x86_64-linux-gnu/libgtk3-nocsd.so.0

Remove the dependencies unless they are required by any other appplication.

    sudo apt remove libgtk-3-dev libgirepository1.0-dev

#### • Whisker Menu / Application Menu start button:

Open the properties menu of either Whisker Menu or Application Menu by right clicking on their panel icons and selecting “properties.” Click the icon button in the properties window. 

The custom Start Button icons are located in the following directory (depending on where you installed the overall theme): /home/$USER/.themes/Chicago95-custom/misc/GTK2 Start Buttons/. Select a button that you would like.

If the icon appears crunched or blurry, then log out and log back in. The icon should appear a regular size. If it still appears out of resolution, make sure that the task panel is set to 32px high.

## Extra Stuff:

If you want to install the mouse cursor theme, lightdm theme, Plymouth theme, these are available at [https://github.com/grassmunk/Chicago95](https://github.com/grassmunk/Chicago95). Follow the guides there if you want these.
