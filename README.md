# How to setup desktop icon and other necessary stuff in Ubuntu if it doesn't appear properly

## Features
* Name changing
* Icon changing

## How to use
I'll walk you through a demonstration by installing and setting up `helium` browser.
### Step 0: Software installation
Go to the official site of helium (https://helium.computer/) and then install
```bash
https://github.com/imputnet/helium-linux/releases/download/0.13.4.1/helium-0.13.4.1-x86_64.AppImage
```
After installation, give it permission to execute by running-
```bash
chmod +x helium-0.13.4.1-x86_64.AppImage
```
And now execture by-
```bash
./helium-0.13.4.1-x86_64.AppImage
```
Now you can see only a gear icon is visible and that's why we need to setup manually to resolve the issue.
### Step 1: Directory Setup
I expect that your `.AppImage` software appeared in `/home/username/Downloads` directory. If so, then create new directory labeling as `Software` and then create a directory again named `helium`. Now move the `.AppImage` file into `helium` directory. Now download helium browser icon-
```bash
wget https://github.com/imputnet/helium/blob/main/resources/branding/app_icon/raw.png
```
name the image from `raw.png` to `helium.png`. Ensure to keep the image and `AppImage` inside the `helium` directory. The ultimate directory path and structure would be something like this way
```bash
/home/username/Downloads/Software/helium

Downloads/
├── Software/
│   └── helium/
│       └── helium-0.13.4.1-x86_64.AppImage
        └── helium.png
```

### Step 2: Configuration
Open your terminal and create a new desktop entry file using a text editor (like `nano` or `vim` or you might use `gnome-text-editor`, I use `nano` for this demonstration)-
```bash
nano ~/.local/share/applications/helium.desktop
```
Paste the following text into the editor. Make sure to replace `/home/yourusername/...` with the actual absolute paths to your AppImage and icon file.
```bash
[Desktop Entry]
Type=Application
Name=Helium
Exec=/home/username/Downloads/Software/helium/helium-0.13.4.1-x86_64.AppImage
Icon=/home/username/Downloads/Software/helium/helium.png
Terminal=false
Categories=Utility;
```
Save and exit the text editor (in `nano`, press `Ctrl+O`,`Enter`, then `Ctrl+X`. For `vim`, `esc` and then `:wq`. For `gnome-text-editor`, `Ctrl+S` and then `Ctrl+Q`).
Give the desktop file proper execution permissions by running:
```bash
chmod +x ~/.local/share/applications/helium.desktop
```
