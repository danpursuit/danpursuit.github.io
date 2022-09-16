# Full Stack MERN Application
Website: [https://blog-tutorial-888.herokuapp.com/](https://blog-tutorial-888.herokuapp.com/)

Github: xxx

## Summary
On my journey to becoming a great fullstack engineer, my time is split between learning new tools/concepts, and building projects to solidify these concepts.
However, I have issues with scaling. I haven't learned what a good project structure looks like--one that allows for new components to be added, old components
to be modified, and what "proper" integrations of databases/authentications looks like.

This time, my project is based on following [this 7.5 hour tutorial](https://www.youtube.com/watch?v=VsUzmlZfYNg) where an experienced developer walks
through the entire process, from creating a client/server, adding MongoDB, google authentication, and regular authentication, all the way to deploying
the app to Heroku. Having done all of these parts myself in the past, seeing how a professional would assemble the pieces together opened my eyes to
the power of React and a proper workflow!

## Project Specs
- Backend server that stores posts and users in a database
- Frontend client that fetches and displays posts
- Authentication to allow users to sign in via Google or email/password
- Signed in users can create posts, modify/delete their own posts, and like other posts
- Users can search through posts by title or by tags
- Posts have their own page that allows users to comment and view related posts

## Skills Learned
### Redux
Redux for JS is a lifesaver. In my last project, after repeatedly merging smaller variables created with React's useState, I "discovered" the concept of 
maintaining a global state that is passed into every react component, and how useful that could be. Like a caveman who was airdropped schematics to a spaceship
right after discovering fire, I was airdropped Redux! In this tutorial, I learned how to separate my state management tools into different files, which
makes adding new states or referencing states from new objects very clean. This is the process:
- initial state and state updating is handled in Reducers folder
- state initialized as a Store in the client index.js
- any component can access state through useSelector to capture part or all of the state
- any component can update state through useDispatch to issue a well-defined action that is implemented in Reducers

### Proper API structure
Similar to Redux, I learned a good workflow for sending API calls from client to server. To implement a new API call, simply walk through this process:
- Find the client component and the place a function should be called
- Implement this function in an Actions folder, where the function will make an API call and potentially dispatch redux actions to manage local state
- Implement the API call separately in an API folder, where JS objects are assembled into parameters for axios
- Receive the API call on the server end through a Routes folder that is only responsible for translating endpoints into function calls, or chains of function calls
- Implement the function calls in a dedicated Controllers folder
This workflow is great because it keeps the project organized and easy to understand. Also, throughout the tutorial we often had to make changes to past
objects to support future features--a problem that I often encounter. This formal structure helps make the process very clean; it is easy to visualize all
dependencies.

### Proper Server Security
With the proper API structure, it also becomes clear how to isolate unwanted bugs and how to protect them. The possible unknowns from client API calls are all
handled in the Controllers, so it is enough to protect these with a try//catch. Authentication is easy as well! API calls that require the user to have
certain levels of access can have the Route first forward the parameters (which include Auth headers) into a Middleware object, which will let further 
callbacks in Controllers know what level of access the user has.

### Models in MongoDB
At this point I've used several database solutions (MySQL, Bubble.io, local JSON file), and this tutorial adds MongoDB to my repertoire. I especially like
how table types can be defined in Model files on the fly. In the tutorial, we change objects in the DB several times--for example, tracking likes through
an integer at first, but later through a list of user IDs--and MongoDB makees this process seamless.

Overall, I'm very impressed with MongoDB--especially the performance of its free tier--and will be looking to use it often in my future projects.

### Material UI and Proper Component Structure
I've used vanilla React for long enough that different packages built on top of React are starting to make sense to me. Here, we use Material UI to build
components and apply styles in a way that is different (better?) than raw CSS. With Material UI, there are several advantages:
- Creating new complex front-end components is sped up, with many components already prebuilt and found in Material UI's extensive documentation
- As a bonus, being able to import tons of stock icons included with Material UI
- Applying styles is more functional than CSS, allowing for easier integration with React and JS
- Styles have better organization using themes with keywords such as "primary/secondary color", making it easier to create a consistent UI experience.

This tutorial also taught me a significantly better folder structure for React components. Instead of putting all components into the same folder, each
component goes into its own folder, with folders nested the way the components themselves are nested. Styling and
other component-specific utilities can also be included in the component's own folder for clarity.

### Routing within the client UI
Something that has confused me up to this point is routing that allows users to toggle between different views. Notably, when it comes time to convert a
single-page app to a multiple page app, I'm at a loss as to where to start. This tutorial goes through how to add the BrowserRouter component to a
single-page application, which made the process very clear to me. By keeping some components like the NavBar outside of the Switch, I can
control what is shared between pages and what is not. Adding new pages such as a login page, or even "auto generated" pages such as a detail
page for any post, is no longer a mystical concept but simply comes down to adding more react components.

### Making elements more responsive
Another issue I don't deal with too often is applying a lot of polish to the end product. Here, I learned some tricks to make the application nicer for the 
user:
- the like button can update its state before the API request is successful, so that the user can immediately see their like go through instead of waiting
the 100 ms (more like 500 ms on Heroku+MongoDB's free plan) for the request to come back
- scrolling to the user's comment when it is posted using useRef
- using Material UI's xs/sm/md/lg/xl tags to easily change how components are displayed across different screen sizes

### Build and Deployment
At this point, I'm becoming quite comfortable with the build+deployment process to Heroku. This tutorial showed me how to launch the server and client as two
separate applications, which is useful to better understand how the two components interact. At the end of the day, however, I opted for serving the client
out of the server as a single Heroku application, since that free application space is limited out here!

Time spent on project: 30 hours over 7 days.




