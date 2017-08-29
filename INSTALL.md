## How To Install

Step 1: Create ".themes" and ".icons" directories  in your user directory if they don't already exist.
(Note: You may have to enable "view hidden folders" in the file manager to see the ".themes" ".icons" directories after creating them.)

Step 2: Copy the "Chicago95-custom" directory into the ".themes" directory. 

Step 3: Copy the "Chicago95-icons-tux" directory into the ".icons" directory.

Step 4: Copy the "gtk.css" file from the "misc" directory into "/home/$USER/.config/gtk-3.0/" or append the file if a gtk.css file already exists.
(Note: You may have to create the "gtk-3.0" directory.)

## Configuration

Enable the notification balloon theme.

Enable the XFCE shell and icon themes.

Enable the XFCE window manager theme.

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

Create a new panel if necessary. Horizontal, 32px high ONLY, and 100% Length. In the “Appearance” tab set the background style to "None" so that it inherits the theme style. (Only horizontal taskbar. No vertical taskbar, sorry.)

In the “Items” tab, add the following in this order:

    1. Application Menu OR Whisker Menu; 

    2. Separator (Handle Style); 

    3. Custom Launcher, Custom Launcher, Custom Launcher, etc.

    4. “Show Desktop” plugin; 

    5. Separator (Handle Style); 

    6. Window Buttons (Sorting Order: Time-stamp and Window Grouping is Always. Uncheck “Show Handle” if it’s enabled.); 

    7. Separator (Transparent with Expanding); 

    8. Separator (Handle Style); 

    9. Notification Area (19px max icon size); 

    10. PulseAudio Plugin (Uncheck mark in the plugin settings, "Show Notifications when volume changes." it will conflict with XFCE notifiyd by making duplicate volume notifications); 

    11. Separator (Transparent); 

    12. Orage Panel Clock. ( In the plugin settings, enable check box “Show frame” and replace the text in “Line 1” with %I:%M %p.) Note: If you want to display the date in the clock, append “%D” in “Line 1.” If you want a better looking date, you could replace that by appending “%b %m %Y” instead.

#### • GTK3 (GNOME) applications missing titlebar & border - workaround:
Disabling Client Side Decorations with [gtk3-nocsd](https://github.com/PCMan/gtk3-nocsd) will allow for the theme to correctly display borders and titlebars in GTK3 applications utilizing the CSD "feature."

Client Side Decorations is a design decision from GNOME developers that runs contrary to established practice in the X11 windowing system. Client Side Decorations are unacceptable for non GNOME desktop enviroments, so I recommend disabling it as shown in the following steps.

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


#### • Whisker Menu / Application Menu start button:

Open the properties menu of either Whisker Menu or Application Menu by right clicking on their panel icons and selecting “properties.” Click the icon button in the properties window. 

The custom Start Button icons are located in the following directory (depending on where you installed the overall theme): /home/$USER/.themes/Chicago95-custom/misc/GTK2 Start Buttons/. Select a button that you would like.

If the icon appears crunched or blurry, then log out and log back in. The icon should appear a regular size.

## Extra Stuff:

If you want to install the mouse cursor theme, lightdm theme, Plymouth theme, these are available at [https://github.com/grassmunk/Chicago95](https://github.com/grassmunk/Chicago95). Follow the guides there if you want these.
