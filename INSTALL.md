## How To Install

Step 1: Create ".themes" and ".icons" directories  in your user directory if they don't already exist.
(Note: You may have to enable "view hidden folders" in the file manager to see the ".themes" ".icons" directories after creating them.)

    mkdir -p ~/.themes/ ~/.icons/

Step 2: Copy the "Chicago95-custom" directory into the ".themes" directory.

    cp -r Chicago95-Custom-XUbuntu-16.04--master/theme/Chicago95-custom/ ~/.themes/

Step 3: Copy the "Chicago95-icons-tux" directory into the ".icons" directory.

    cp -r Chicago95-Custom-XUbuntu-16.04--master/icons/Chicago95-icons-tux/ ~/.icons/

Step 4: Copy the "gtk.css" file from the "misc" directory into "/home/$USER/.config/gtk-3.0/" or append the file if a gtk.css file already exists.
(Note: You may have to create the "gtk-3.0" directory.)

    mkdir -p ~/.config/gtk-3.0 && cat Chicago95-Custom-XUbuntu-16.04--master/misc/gtk.css >> ~/.config/gtk-3.0/gtk.css

## Configuration

#### Enabling the GTK theme
Open the XFCE settings manager > Appearance.

- Choose Chicago95 as the theme style.

#### Enabling the Window Manager theme
Open the XFCE settings manager > Window Manager.

- Choose Chicago95.
- Set Title font to Sans Bold, 8 points.

#### Enabling the theme for QT5 applications (optional)
Open your terminal and install the qt5 style plugins package.

- sudo apt install qt5-style-plugins

Relogin for changes to take place.

#### Enabling the notification theme
Open the XFCE settings manager > Notifications.

- Choose Chicago95 for the theme.
- Adjust Opacity to 100%.

#### Setting up the XFCE panel
Open the XFCE settings manager > Panel

- Measurments: Even numbers are preffered for the Row Size slider. The smallest optimal panel row size for this theme is 26 pixels. If your panel is below that size, you will encounter icon scaling issues.
- Under the Appearance tab set the background style to "None (use system style.)"

Here's a list for the panel Items plugin layout as seen from the screen-shots. This is optional, the item configuration is up to you after all.

1. Application Menu or Whisker Menu;
2. Separator (Handle Style);
3. Custom Launcher, Custom Launcher, Custom Launcher, etc;
4. “Show Desktop” plugin;
5. Separator (Handle Style);
6. Window Buttons (Uncheck "Show flat buttons" and "Show Handle.;" Sorting Order: None; Window grouping: Never);
7. Separator (Transparent with Expanding);
8. Separator (Handle Style);
9. Indicator Plugin OR Notification Area (19px max icon size preferred);
10. Separator (Transparent);
11. Orage Panel Clock. (Enable check box “Show frame” and replace the text in “Line 1” with %I:%M %p.)

#### • Libre Office 5 (GTK3 theme Inconsistencies) - workaround:
Libre Office with the GTK3 theme doesn't look very good. I'm not sure why, but I'm trying to fix it. In the mean time you can remove the `libreoffice-gtk3` package which will cause Libre Office to fallback onto GTK2 which is far more consistent and looks better.

    sudo apt remove libreoffice-gtk3


#### • Disable GNOME client side decorations and scroll bars:
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
    echo "GTK_OVERLAY_SCROLLING=0" | sudo tee --append /etc/environment

Log out then log back in.

• If you want to **UNINSTALL** gtk3-nocsd:

Remove the following system variables from your `/etc/environment` file with a file editor such as nano or VI.

    GTK_CSD=0
    LD_PRELOAD=/usr/lib/x86_64-linux-gnu/libgtk3-nocsd.so.0
    GTK_OVERLAY_SCROLLING=0

Log out then log back in before continuing!

Remove the gtk3-nocsd executable and library from your system.

    rm /usr/bin/gtk3-nocsd
    rm /usr/lib/x86_64-linux-gnu/libgtk3-nocsd.so.0

Remove the dependencies unless they are required by any other appplication.

    sudo apt remove libgtk-3-dev libgirepository1.0-dev

## Optional configurations
The following configurations are optional and not required but can be used to enhance the theme.

#### Whisker Menu and XFCE Application Menu Start Buttons

#### • Whisker Menu
Open the XFCE settings manager > Panel > Items tab > Double click the Whisker menu item in the item list.

- In the whisker properties menu click the icon option.
- In the icon select window navigate to `/home/$USER/.themes/Chicago95/misc` (with $USER being your username.)

`misc/` contains simple small icons if you want a basic icon. These might be ideal for vertical deskbar panels.

`GTK2 start buttons/` contains start button icons.

`GTK3 start buttons/` contains start button icons if you are using the GTK3 version of the plugin.

Since the Whisker Menu plugin is GTK2 by default, you'll have to choose an icon associated with your panel size. For example, tux_32px.png would be ideal on a panel with a row size of 32 pixels.

Note: The smallest optimal panel row size for this theme is 26 pixels. If your panel is below that size, you will encounter icon scaling issues.

#### • Application Menu
Open the XFCE settings manager > Panel > Items tab > Double click the Applications Menu item in the item list.

- In the Applications properties menu click the icon option.
- In the icon select window navigate to `/home/$USER/.themes/Chicago95/misc` (with $USER being your username.)

`misc/` contains simple small icons if you want a basic icon. These might be ideal for vertical deskbar panels.

`GTK2 start buttons/` contains start button icons.

Since the Application Menu plugin is GTK2 by default, you'll have to choose an icon associated with your panel size. For example, tux_32px.png would be ideal on a panel with a row size of 32 pixels.

Note: The smallest optimal panel row size for this theme is 26 pixels. If your panel is below that size, you will encounter icon scaling issues.

#### Launcher Button scaling (advanced)
If you want to force 16x16px icons in the launcher buttons, you can do this by making your own custom icons or through the theme by editing the panel.rc file.

- Open a text editor and navigate to `/home/$USER/.themes/Chicago95/gtk-2.0/panel.rc` (with $USER being your username.)
- Move to line 268 of the file where you will see a section specified for Launcher buttons.

Example steps: You will first need to determine the panel bar row size since the launcher button icon padding is determined by the size of the panel bar.

- Open the XFCE settings manager > Panel
- Verify the "Row Size (pixels)". (Lets say that it's 38 pixels for this example.)
- Return back to the text editor and locate the line comment that is specifying your panel bar row size. (38px height panel for this example is on line 302.)
- Delete the "#" pound character in front of the xthickness and the ythickness values for the specified panel bar size.
- Now Insert a "#" pound character in front of the xthickness and the ythickness values of the previous default selection, which is for a 26px height panel.
- Save the file and reload the xfce panel bar. You can run `xfce4-panel -r` in a terminal to reload the panel.

Note: If you use a vertical deskbar, you could add a second row from the panel properties menu to organize the launcher buttons into rows.

#### Shadows
Disable shadows in compositing for an authentic appearance, or at the very least disable “show shadows under dock windows” to prevent dark shading from the panel bar overlapping onto maximized applications.

- Open the XFCE settings manager > Window Manager Tweaks > Compositor tab
- Uncheck "Show shadows under pupup windows."
- Uncheck "Show shadows under dock windows."
- Uncheck "Show shadows under regular windows."

## Extra Stuff:

If you want to install the mouse cursor theme, lightdm theme, Plymouth theme, these are available at [https://github.com/grassmunk/Chicago95](https://github.com/grassmunk/Chicago95). Follow the guides there if you want these.
