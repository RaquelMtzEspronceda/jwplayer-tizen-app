# JW Player Tizen App

[JW Player Tizen Docs: Embed a Player in a Tizen App](https://developer.jwplayer.com/jwplayer/docs/jw8-embed-a-player-in-a-tizen-app)

This is JW Player’s demo application for Samsung Tizen Smart TVs showcasing how the player can be used for such applications. It is a Tizen Web Application built with HTML, CSS, and JS and targeting Tizen 4.0+ and 2018 Smart TVs and later.

There are three screens to the demo app. The main playlist landing page, the video detail page, and the player page.

    
## Build System

The Tizen Demo App has a unique build setup to make it easier to integrate webpack and es6. The build system is a simple webpack/babel setup used for compiling with eslint used for linting. The source code in `src` is compiled and output to `app/dis`. The app itself is created in this `app` directory and imports the compiled source code directly.

## Getting Started

Download Tizen SDK: https://developer.tizen.org/development/tizen-studio/download

1. Clone or download this repository.
    
2. Launch Tizen Studio and select `File -> Import -> Tizen -> Tizen Project`
    
3. Import the `app` folder from the `tizen-demo-app` directory into your workspace.

4. Open a terminal from the `tizen-demo-app` directory and run `npm install` to initialize the project dependencies.
    
5. Run `yarn build`. This will generate or update `jw-tizen.css` and `jw-tizen.js` do not exist in the `app/dist` folder, both of which are needed to run the project.
    
6. In `app/index.html`, you will need to add a link to your player that will be used in the app. It is the same process as [Adding a JW Player Library to a Page](https://developer.jwplayer.com/jwplayer/docs/jw8-add-a-player-library)

	In the `<head>`, add either of the following:
    
	- `<script src="https://www.yourdomain.com/{player_folder}/jwplayer.js"></script>`
  `<script>jwplayer.key='{player_key}'</script>`
    
	- `<script src="{CLOUD-HOSTED_PLAYER_LIBRARY_URL}"></script>`
    

## Application Certificates

In order to run the application, you need to create an author and a distributor certificate: [Samsung Creating Certificates Docs](https://developer.samsung.com/SmartTV/develop/getting-started/setting-up-sdk/creating-certificates.html).

If you are running the application on a TV, you need to know the TVs Unique Device ID (DUID), which can be found here:

-  On your TV, go to `Menu > Support > Contact Samsung > Unique Device ID`.
    

## Running the Application

You can run the application in 3 different environments - a Web Simulator, an Emulator, or a TV. The simulator is great for development and quick run throughs, whereas the tv is better for the actual experience.

#### Web Simulator
[Samsung Web Simulator Docs](https://developer.samsung.com/smarttv/develop/getting-started/using-sdk/tv-simulator.html)

1. Right click the project and select `Run As > Tizen TV Web Simulator Application (Samsung TV)`

**Right click on the simulator to open a settings menu so you can access things like the web inspector.*

#### Emulator
[Samsung Emulator Docs](https://developer.samsung.com/smarttv/develop/getting-started/using-sdk/tv-emulator.html)

1. Right-click on the project and select `Run As > Tizen Web Application`

If that doesn’t work try:
    
1. Go to `Tools > Emulator Manager`
    
2. Select the Emulator you want and click `Launch`
    
3. Wait for a colorful ATV Screen
    
4. Right-click on the application's folder and choose `Run As > Tizen Web Application`

**The emulator can lag, so it is recommended to use a real device if possible.*

#### Tizen TV
[Samsung TV Docs](https://developer.samsung.com/SmartTV/develop/getting-started/using-sdk/tv-device.html)

Directions to setup the TV and configure it as a device are outlined in the linked doc.

- Make sure the TV is connected to the same wifi as your computer.
    
- To find the TVs IP Address:
    
	1. Open the TV Settings Menu by selecting **SETTINGS** on your remote or navigating to **SETTINGS** from the Smart Hub
    
	2. Select `General -> Network -> Network Status -> IP Settings`
    
- When configuring the device in Tizen Studio, if there is no port, keep the default `26101` port
 
Once you finish setting up and configuring in Tizen Studio

1. Right click the project and select `Run As > Tizen Web Application`
    

## Updating the App

#### Adding/Updating Application Screens

- Any changes made to the application’s source code belong in the `src` folder.
    
- Run `yarn build` after any changes to update the compiled dist files.

- You will need to restart the app to show any changes.

#### Adding/Updating Application Media

To change the media used within the application, you will need to update the playlist feeds supplied to it.
    
- In `src/js/index.js` in the `init` function, you will see an object passed into the Gallery component like below:

		gallery = new Gallery({  
			feeds: [PLAYLIST_ID_1, PLAYLIST_ID_2, ...],  
			parent: {view: mainDiv},  
			init  
		});

	The values in this object’s `feeds` array are Playlist IDs from your account dashboard.
    
- To update a playlist used within the app, you will just need to update the playlist for the desired playlist id in your dashboard.
    
- To add a new playlist to the app, create a new playlist in your dashboard and add the created playlist’s id to this array.
    
- You will need to restart the app to see your changes reflected.
    

## Debugging

If you are using the Web Simulator, you can debug similarly to how you would debug in a browser. To pull up the web inspector, right click on the simulator and select `Web Inspector`.

If you are using the Emulator or TV, you can right click on the project and select `Debug As -> Tizen Web Application` and a web inspector will appear.

## Possible Issues

Check out [JW Player Tizen Troubleshooting](https://developer.jwplayer.com/jwplayer/docs/troubleshoot-tizen-app-issues).

Still need help? Please [open an issue](https://github.com/jwplayer/jwplayer-tizen-app/issues) in this repo or reach out to our [Support Team](https://support.jwplayer.com/submit-support-case).
  

Helpful Resources
------------

- [Tizen App Development Guide](https://medium.com/norigintech/the-ultimate-guide-to-samsung-tizen-tv-web-development-f4613f672368)

- [Building a React App for Tizen](https://stackoverflow.com/a/59603438)

- [Official Samsung Tizen Demo Apps](https://github.com/Samsung/TizenTVApps)

- [Tizen Remote Controls Reference](https://developer.samsung.com/SmartTV/develop/guides/user-interaction/remote-control.html#)

- Full list of Tizen Platforms and the devices that support them [here](https://developer.samsung.com/smarttv/develop/specifications/tv-model-groups.html).
	- Tizen 4.0 and below is supported on 2018 TVs
	- Tizen 5.0 and below is supported on 2019 TVs