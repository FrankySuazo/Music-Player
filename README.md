Sometimes when you're coding a web application, you'll need to be able to accept input from a user. Learn how to validate user input, perform calculations based on that input, and dynamically update your interface to display the results.

In this practice project, I learn basic regular expressions, template literals, the addEventListener() method, and more.

	• Javacript:

In this project you will learn basic string and array methods by building a music player app. You will be able to play, pause, skip, and shuffle songs.

Start by accessing the #playlist-songs, #play, and #pause elements with the getElementById() method. Assign them to variables playlistSongs, playButton and pauseButton respectively.

Access the #next, #previous and #shuffle elements from the HTML file.

Assign them to variables named nextButton, previousButton, and shuffleButton, respectively.

Next, create an array to store all the songs.

Create an empty allSongs array.

Inside the allSongs array, create an object with the following properties and values:

id: 0,
title: "Scratching The Surface",
artist: "Quincy Larson",
duration: "4:25",
src: "https://s3.amazonaws.com/org.
freecodecamp.mp3-player-project/scratching-the-surface.mp3",

Add a second object with the following keys and values:

id: 1,
title: "Can't Stay Down",
artist: "Quincy Larson",
duration: "4:15",
src: "https://s3.amazonaws.com/org.freecodecamp.mp3-player-project/cant-stay-down.mp3",

Add a third object with the following properties and values:

id: 2,
title: "Still Learning",
artist: "Quincy Larson",
duration: "3:51",
src: "https://s3.amazonaws.com/org..freecodecamp.mp3-player-project/still-learning.mp3",

Next, you'll learn about the Web Audio API and how to use it to play songs. All modern browsers support the Web Audio API, which lets you generate and process audio in web applications.

Use const to create a variable named audio and set it equal to new Audio(). This will create a new HTML5 audio element.

Create a userData object that will contain the songs, the current song playing, and the time of the current song.

Declare an empty userData object using the let keyword.

Since users will be able to shuffle and delete songs from the playlist, you will need to create a copy of the allSongs array without mutating the original. This is where the spread operator comes in handy.

The spread operator (...) allows you to copy all elements from one array into another. It can also be used to concatenate multiple arrays into one. In the example below, both arr1 and arr2 have been spread into combinedArr:4

Inside the userData object create a songs property. For the value, spread allSongs into an array.

To handle the current song's information and track its playback time, create a currentSong and songCurrentTime properties. Set the values to null and 0 respectively.

Now you need a way to display the songs in the UI. To do this, you'll create a renderSongs function using the arrow function syntax.

Use the arrow function syntax to create a renderSongs function that takes in array as its parameter.

Later when you call the renderSongs function, you'll pass in the songs array inside the userData object. When you do, the function will loop through the array and build HTML for all the songs.

For now, use const to declare a variable named songsHTML and assign it array.map().

Pass in a callback function to the map() method. The callback function should take song as a parameter, use the arrow function syntax, and have an empty body.

Inside the map(), add a return statement with backticks

Inside the backticks, create an li tag with the id song-${song.id} as the first attribute. Also, add the class playlist-song as the second attribute.

Create a button element with class playlist-song-info. Inside the button, add a span element with the class playlist-song-title, then interpolate song.title as the text.

Inside the button, create two more span elements. The first span element should have class playlist-song-artist and interpolate song.artist. The second span element should have class playlist-song-duration and interpolate song.duration.

Create another button element with the class playlist-song-delete and the aria-label attribute set to Delete interpolated with song.title. For the content of the delete icon, paste in the following SVG:

Chain the join() method to your map() method and pass in an empty string for the separator.

Next, you will need to update the playlist in your HTML document to display the songs.

Assign songsHTML to the innerHTML property of the playlistSongs element. This will insert the li element you just created into the ul element in the already provided HTML file.

Now you need to call the renderSongs function and pass in userData?.songs in order to finally display the songs in the UI.

Call the renderSongs function with the songs property of userData. This will render the songs in the playlist.

Add the sort() method to userData?.songs.

For now, add an empty callback function to your sort() method and use a and b for the parameter names.

Inside your callback function, add another if statement to check if a.title is greater than b.title. If so, return the number -1.

Inside your callback function, add an if statement to check if a.title is less than b.title. If so, return 1.

Below your if statements, return the number 0 to leave the order of the two elements unchanged.

Now you should see the songs in alphabetical order in the playlist.

It's time to begin implementing the functionality for playing the displayed songs.

Define a playSong function using const. The function should take an id parameter which will represent the unique identifier of the song you want to play.

Use const to create a variable named song and assign it result of the find() method call on the userData?.songs array. Use song as the parameter of the find() callback and check if song.id is strictly equal to id.

This will iterate through the userData?.songs array, searching for a song that corresponds to the id passed into the playSong function.

Inside the playSong function, set the audio.src property equal to song.src. This tells the audio element where to find the audio data for the selected song.

Also, set the audio.title property equal to song.title. This tells the audio element what to display as the title of the song.

Before playing the song, you need to make sure it starts from the beginning. This can be achieved by the use of the currentTime property of the audio object.

Add an if statement to check whether the userData?.currentSong is null or if userData?.currentSong.id is strictly not equal song.id. Inside if block, set the currentTime property of the audio object to 0.

Add an else block to handle the current song's position in the playlist.

Within the else block, set the currentTime property of the audio object to the value stored in userData?.songCurrentTime.

You need to update the current song being played as well as the appearance of the playButton element.

Start by accessing the userData object and its currentSong property. Set its value equal to the song variable.

Note: You should not use the optional chaining operator ?. in this step because userData.currentSong will not be null or undefined at this point.

Next, use the classList property and the add() method to add the playing class to the playButton element. This will look for the class playing in the CSS file and add it to the playButton element.

To finally play the song, use the play() method on the audio variable. play() is a method from the web audio API for playing an mp3 file.

You need to hook up the playSong function to a click event listener so the songs will start playing when the play button is clicked.

Add a click event listener to the playButton element, then use arrow syntax to pass in a callback with an empty pair of curly braces.

Within the arrow function of the event listener, add an if to check if userData?.currentSong is null.

Inside the if block, call the playSong() function with the id of the first song in the userData?.songs array. This will ensure the first song in the playlist is played first.

Add an else block. Inside the else block, call the playSong function with the id of the currently playing song as an argument.

This ensures that the currently playing song will continue to play when the play button is clicked.

To play the song anytime the user clicks on it, add an onclick attribute to the first button element. Inside the onclick, call the playSong function with song.id.

Define a pauseSong function using the const keyword and arrow function syntax. The function should take no parameters.

To store the current time of the song when it is paused, set the songCurrentTime of the userData object to the currentTime of the audio variable.

Note: You should not use optional chaining for this step because userData.songCurrentTime will not be null or undefined at this point.

Use classList and remove() method to remove the .playing class from the playButton, since the song will be paused at this point.

To finally pause the song, use the pause() method on the audio variable. pause() is a method of the Web Audio API for pausing music files.

You need to hook up the pauseSong function to an event listener to make it work.

Add a click event listener to the pauseButton element, then pass in pauseSong as the second argument of the event listener. This is the function the event listener will run.

Before you start working on playing the next and previous song, you need to get the index of each song in the songs property of userData.

Start by creating an arrow function called getCurrentSongIndex.

Inside your getCurrentSongIndex function, return userData?.songs.indexOf(). For the indexOf() argument, set it to userData?.currentSong.

You need to work on playing the next song and the previous song. For this, you will need a playNextSong and playPreviousSong function.

Use const and arrow syntax to create an empty playNextSong function.

Inside the playNextSong function, create an if statement to check if the currentSong of userData is strictly equal to null. This will check if there's no current song playing in the userData object.

If the condition is true, call the playSong function with the id of the first song in the userData?.songs array as an argument.

Add an else block to the if statement. Inside the else block, call the getCurrentSongIndex() function and assign it to a constant named currentSongIndex.
 
Create a constant called nextSong and assign userData?.songs[currentSongIndex + 1] to it.

Lastly, call the playSong function and pass in nextSong.id as the argument.

Add a click event listener to the nextButton element, then pass in playNextSong as the second argument of your event listener. This is the function the event listener will run.

Use const and arrow syntax to create an empty playPreviousSong function.

Within the playPreviousSong function, add an if statement with a condition of userData?.currentSong === null. This will check if there is currently no song playing. If there isn't any, exit the function using a return.

Inside the else block, create a constant named currentSongIndex and assign it getCurrentSongIndex().

To get the previous song, subtract 1 from the currentSongIndex of userData?.songs and assign it to the constant previousSong. After that, call the playSong function and pass previousSong.id as an argument.

Add a click event listener to the previousButton element, then pass in playPreviousSong as the second argument.

If you check closely, you'd see the currently playing song is not highlighted in the playlist, so you don't really know which song is playing. You can fix this by creating a function to highlight any song that is being played.

Using an arrow syntax, create a highlightCurrentSong function. Inside the function, use querySelectorAll to get the .playlist-song element and assign to a playlistSongElements constant.

You need to get the id of the currently playing song. For this, you can use userData?.currentSong?.id.

Use getElementById() to get the id of the currently playing song, then use template literals to prefix it with song-. Assign it to the constant songToHighlight.

Use the forEach method on playlistSongElements. Pass in songEl as the parameter and use arrow syntax to add in an empty callback.

Within the callback function, use the removeAttribute() method to remove the "aria-current" attribute. This will remove the attribute for each of the songs.

Create an if statement with the condition songToHighlight. For the statement, use setAttribute on songToHighlight to pass in "aria-current" and "true" as the first and second arguments.

Inside the playSong function, call the highlightCurrentSong function.

Next, you need to display the current song title and artist in the player display. Use const and arrow syntax to create an empty setPlayerDisplay function.

Inside the function, obtain references to the HTML elements responsible for displaying the song title and artist.

Access the #player-song-title and #player-song-artist elements with the getElementById() method. Assign them to variables playingSong and songArtist respectively.

Access the userData?.currentSong?.title and userData?.currentSong?.artist properties and assign them to a currentTitle and currentArtist variables respectively.

Use a ternary operator to check if currentTitle is truthy. If so, implicitly return currentTitle otherwise implicitly return an empty string. Assign this result to playingSong.textContent.

Then, use a ternary operator to check if currentArtist is truthy. If so, implicitly return currentArtist otherwise implicitly return an empty string. Assign this result to songArtist.textContent.

To ensure the player's display updates whenever a new song begins playing, call the setPlayerDisplay() function within the playSong() function.

Now you should see the song title and the artist show up in the display.

Use const and arrow syntax to define a function called setPlayButtonAccessibleText.

This function will set the aria-label attribute to the current song, or to the first song in the playlist. And if the playlist is empty, it sets the aria-label to "Play".

You need to get the currently playing song or the first song in the playlist. To do that, create a song constant and use the OR operator (||) to set it to the current song of userData, or the first song in the userData?.songs array.

Don't forget to use optional chaining

Now, call the setPlayButtonAccessibleText function inside the playSong function

Using const and arrow syntax to create an empty function called shuffle.

This function is responsible for shuffling the songs in the playlist and performing necessary state management updates after the shuffling.

Use the sort() method on the userData?.songs array. Pass a callback to the method, and return the result of Math.random() - 0.5.

When the shuffle button is pressed, you want to set the currentSong to nothing and the songCurrentTime to 0.

Set userData.currentSong to null and userData.songCurrentTime to 0.

Call the renderSongs function and pass in userData?.songs as an argument. Also, call the pauseSong, setPlayerDisplay, and setPlayButtonAccessibleText functions

Add a click event listener to the shuffleButton element. For the function to run, pass in the shuffle function.

Note: You don't need a callback inside this particular event listener. You also don't need to call the shuffle function, just pass in its identifier.

It's time to implement a delete functionality for the playlist. This would manage the removal of a song from the playlist, handle other related actions when a song is deleted, and create a Reset Playlist button.

Use const and arrow syntax to create an empty deleteSong function and pass in id as a parameter.

Use the filter() method on userData?.songs. Pass in song as the parameter of the arrow function callback and use implicit return to check if song.id is strictly not equal to id. Assign all of that to the userData.songs.

Note: You should not use optional chaining when you assign the result of userData?.songs.filter to userData.songs because the allSongs array will not be undefined or null at that point.

Need to re-render the songs, highlight it and set the play button's accessible text since the song list will change.

Call the renderSongs function and pass in the userData?.songs array as an argument, this displays the modified playlist.

After that, call the highlightCurrentSong function to highlight the current song if there is any also and the setPlayButtonAccessibleText function to update the play button's accessible text.

Before deleting a song, you need to check if the song is currently playing. If it is, you need to pause the song and play the next song in the playlist.

Use an if statement to check if the userData?.currentSong?.id is equal to the id of the song you want to delete.

If there is a match then set userData?.currentSong to null and userData?.songCurrentTime to 0.

After that, call the pauseSong() function to stop the playback and the setPlayerDisplay() function to update the player display.

Within the button element in the renderSongs function, add an onclick attribute as the first attribute. For the value, call the deleteSong function and interpolate song.id.

Need to check if the playlist is empty. If it is, you should reset the userData object to its original state.

Use an if statement to check if the userData?.songs has a length of 0.

Inside your if statement, declare a resetButton constant, then use createElement() to create a button.

Use the createTextNode() method to create a Reset Playlist text, then assign it to a resetText constant.

Set the id attribute of resetButton to reset and its aria-label attribute to Reset playlist.

Use appendChild() to attach resetText to resetButton element, and resetButton to the playlistSongs element.

Now, it's time to add the reset functionality to the resetButton. This will bring back the songs in the playlist when clicked.

Add a click event listener to the resetButton variable. Pass in a callback using arrow syntax and leave it empty for now.

To reset the playlist to its original state, spread allSongs into an array and assign it to userData.songs.

Finally, should render the songs again, update the play button's accessible text, and remove the reset button from the playlist. You also need to remove the resetButton from the DOM.

Call the renderSongs() function with userData?.songs as an argument to render the songs again.

Call the setPlayButtonAccessibleText() function to update the play button's accessible text.

Remove the reset button from the playlist by calling the remove() method on the resetButton variable.

Add an event listener to the audio element which listens for the ended event. Pass in a callback using arrow syntax with empty curly braces.

Next, you need to check if there is a next song to play. Retrieve the current song index by calling the getCurrentSongIndex() function, and save it in a currentSongIndex constant.

After that, create a nextSongExists constant that checks if a next song exists.

Use an if statement to check if nextSongExists exists, then call the playNextSong() function in the if block. This will automatically play the next song when the current song ends.

If there is no next song in the playlist, use the else block to reset the currentSong key of userData to null, and its songCurrentTime property to 0.

With everything set in place, call the pauseSong(), setPlayerDisplay(), highlightCurrentSong(), and setPlayButtonAccessibleText() functions to correctly update the player.

![image](https://github.com/FrankySuazo/Music-Player/assets/114836913/15283edf-3c2c-4acc-b5ff-184cee1e863d)
