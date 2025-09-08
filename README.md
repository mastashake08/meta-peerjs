# Quest/Mobile AR Game
## Project Overview
This is a two-player, cross-platform Augmented Reality (AR) game designed to be played between a Meta Quest headset and a standard mobile device. The game creates a shared experience where one player navigates the real world while the other participates in a virtual shooting gallery overlaid on the first player's live video feed.

The core concept involves:

The Mobile Player (Runner): This player is out in the real world. Their goal is to physically navigate to a randomly generated GPS target location. They see an AR view of their surroundings with virtual cubes overlaid.

The Quest Player (Shooter): This player is stationary, wearing a Meta Quest headset. They see a live video stream from the mobile player's camera. Their goal is to shoot and destroy virtual cubes that appear in the video feed.

The game state, including GPS locations, cube positions, and projectile launches, is synchronized in real-time between the two devices using PeerJS (WebRTC).

## Features
Mobile Player (Caller)
Live Video Streaming: Streams the device's rear-facing camera to the Quest player.

GPS Tracking: Continuously sends real-time GPS data (latitude, longitude) to the Quest.

AR Overlay: Renders a 3D view of the virtual cubes and incoming projectiles on top of the camera feed.

Game Objective UI: Displays the distance to the final target location.

PWA Ready: Can be installed on the home screen for a native app-like experience.

Quest Player (Shooter)
Immersive Video Feed: Receives the video stream from the mobile player and displays it as the background for the AR experience.

WebXR Session: Utilizes the Meta Quest's VR capabilities for an immersive, head-tracked view.

Shooting Mechanic: Allows the player to aim with a crosshair and shoot projectiles using the VR controller.

Real-time UI: Displays critical game information, including the mobile player's GPS coordinates, the distance to the target, and the number of cubes remaining.

Dynamic Gameplay: New waves of cubes with randomized positions and depths are spawned after the previous wave is cleared.

## How to Play
Deployment: First, you must host the three project files (index.html, manifest.json, sw.js) on a web server that uses HTTPS. A free and easy way to do this is with Netlify Drop or by creating a GitHub Pages site.

Open the App: Open the deployed HTTPS URL on both the mobile device and in the Meta Quest browser.

Select Roles:

On the mobile phone, tap "Mobile Device (Player)".

On the Meta Quest, click "Meta Quest (Shooter)".

Connect the Devices:

The Quest will display a unique 6-character Peer ID.

On the mobile device, enter this ID into the input field and tap "Call Meta Quest".

Grant Permissions: Both devices will request permissions.

Mobile: Allow access to Camera, Microphone, and Location.

Quest: Allow access to Microphone.

Start the Game:

On the Quest, once the video stream appears, click the "Start AR" button to enter the immersive session.

The game will automatically begin. The mobile player must physically move towards the target, and the Quest player must shoot all the cubes. New waves will spawn until the target is reached.

Deployment on GitHub Pages
Create a Repository: Create a new public repository on GitHub.

Upload Files: Upload the index.html, manifest.json, and sw.js files to the repository.

Enable Pages: In the repository's "Settings" tab, go to the "Pages" section. Under "Source," select "Deploy from a branch," choose the main branch, and save.

Launch: After a minute or two, your site will be live at https://your-username.github.io/your-repo-name/.

Technical Stack
Vue 3: For the application's reactive UI and state management.

Three.js: For all 3D rendering, including the AR scenes, objects, and video textures on both devices.

PeerJS (WebRTC): For establishing the direct peer-to-peer connection between the mobile device and the Quest to transfer video, audio, and game state data with low latency.

WebXR API: Used on the Meta Quest to create an immersive AR/VR session.

Tailwind CSS: For styling the user interface.

PWA Technologies: Service Worker and Web App Manifest for installation and caching.
