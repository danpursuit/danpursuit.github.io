# Spellbook: Demo
Website: [https://spellbookdemo.herokuapp.com/](https://spellbookdemo.herokuapp.com/)

## Summary
<img src="img/kazuya_MainMenu.png" alt="MainMenu" title="MainMenu" width="600" height="463" /> 
This project puts my MERN stack knowledge and Stable Diffusion creative abilities to the test! My vision is to create a multiplayer online game that
involves real time strategy and coherent, fantasy graphics. I also wanted to give the UI a Pokemon Showdown style feel, where the player can join a lobby
to chat with other players, send friendly challenges, and spectate games. This is my capstone project for my Javascript learning--tying everything I've learned together in one beautiful
application

## Project Specs
- Create a site with a Navbar, a Character Select page, and a Welcome page
- Allow Battles and Chat Rooms to be opened up as extra tabs, and create a tab UI to allow for switching and closing tabs
- Allow users to create a Username to find battles/chat/record scores, and allow users to later attach a password to their account
- Create the actual gameplay!
  - Gameplay revolves around searching through a variety of spells and casting them to beat your opponent. Create a search bar with intelligent autocomplete and
intuitive navigation through typing, arrow keys, numbers, tab, and enter.
  - Display character sprites, stat bars, and equipment. Add animations to spice up the actions
  - Use proper state management across clients and server
- Create CPUs with prebuilt strategies for single player games
- Using my own creative tools (Stable Diffusion AI and GIMP for editing), generate *all* graphics for the game! Including characters, equipment, logos, and
backgrounds.


## Process
This is the largest project I've undertaken by myself. In total I built about 40 React components, synthesized 50 game sprites, 
and created 10 pieces of equipment and 13 spells!

### Step 1, UI design
My first step was to create the front end website. After mocking out the interface in Figma, I built the primary components in React with the Material UI package that I'm now quite familiar with. Once the elements were built, I added some flair by using Stable Diffusion to create graphics such as the character portraits, logo, and background. Creating finished graphics this early also served to give me some thematic guidelines for how I'll design the movesets for characters later on. I'm also learning Stable Diffusion on the fly as prompt engineering is a very new field, and using tutorials and experimenting to discover new techniques.

### Step 2, Server authentication, Socket creation
Similar to the blog that I created in the past, Spellbook allows users to authenticate via username/password to receive a token to add in requests. Unlike the blog, however, users can also submit only a username. This is easily managed on the server by simply saving usernames to MongoDB without a password. One other important difference is the inclusion of a websocket! Users in the chat room and playing the game need to communicate using a socket instead of rest. Passing the authentication token to verify users via websocket works seamlessly, and allows me to explore the workflow to add new websocket actions in the future.

### Step 3, Chat room
Before building the actual game, I built a chat room on the website for users to talk. This will be an important function of the app, and also lets me practice working with the websocket futher. Using knowledge from past tutorials, I designed a chat room state to maintain on the server side, and methods to pass either the whole state or just deltas to the client, depending on whether they are just connecting, or already connected and listening for updates. Clients also have the ability to pass in updates to the state, which simply consists of joining/leaving the room or sending messages. When I build the game later, I'll essentially be building a glorified chat room that also manages a state on the server, communicates state with the client, and displays state via graphics and text.

### Step 4, Notifications
At this point it's worth noting for new readers that I'm using React Redux to manage state on the client side.

Time spent on project: 200 hours over 40 days. Whew!



