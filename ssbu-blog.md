# Super Smash Bros. Blog
Website: [https://kazuyasmash.herokuapp.com/](https://kazuyasmash.herokuapp.com/)

Github: xxx

## Summary
After my [last project](https://danpursuit.github.io/fullstack-mern-app) where I followed a 7.5 hour tutorial to create a fullstack MERN application, it's
time to make this project truly my own! This means iterating over the code to add new features and styling, while also using the actual application to
see how to enhance the user experience. At the end, I have a blog in the theme of my favorite Smash character Kazuya, and it's filled with Kazuya content.

My goal here is to internalize my learning by implementing a bit more of everything I learned. This includes:
- adding a new state to React Redux
- adding a new model to MongoDB
- playing with the Material UI docs and adding new components
- completely restyling the site with my own CSS and Material UI knowledge

Check out my site using the link above! Compared to my end product from the last project, the results are here are beautiful.

## Project Specs
- Restyle the whole site, including Navigation Bar, Post Thumbnails, Search/Create Post, and Post Details
- Allow users to tag posts with my custom smash tags using an autocomplete feature.
- Allow users to use a slider to label posts with a winrate (0-100), and have the server generate more tags off of this number.
- Add a view counter to the site, and use localStorage to prevent the number from skyrocketing on every refresh
- Add a welcome screen that is displayed the first time the user visits the page, and can be disabled/reenabled later

Although I didn't initially expect this, it turns out the tutorial I was following used a very outdated version of Material UI. As a result, the first project
spec is one that wasn't originally planned:
- Install the new Material UI and update all components to be compatible with the new API

## Skills Practiced
Updating the entire site to the new Material UI was great practice for learning this amazing JS package. The docs were well written, and through solving
challenges I came across (why is there random padding being inserted? oh, I should use this component?), I learned a lot about Javascript practices
in general, CSS tricks, and really solidified MUI as a tool in my front-end toolbelt.

Building off of the project structure established in the past project taught me more about building scalable projects. I implemented several actions, such
as the View Counter and the Welcome panel, that allowed me to make a full passes through the client<->server pipeline. By following the process several times,
I've become quite confident in visualizing and implementing future actions:
- adding the redux state
- dispatching redux actions
- linking redux actions to an API
- implementing routes in the server to receive the API
- building server controllers and middleware to respond to client

Needless to say, I'm starting to fall in love with the beauty of Javascript, and it's becoming a close competitor to my real comfort language (watch out Python!)


Time spent on project: 16 hours over 5 days. (In addition to the previous project where the base site was built)



