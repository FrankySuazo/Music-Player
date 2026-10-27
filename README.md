# 🎵 JavaScript Music Player

An interactive **MP3 music player built with HTML, CSS, and vanilla JavaScript**.

The application provides a playlist-based music experience with playback controls, song navigation, shuffle functionality, playlist management, and a dynamically updated user interface.

This project helped me practice working with the **JavaScript Audio API, arrays, objects, DOM manipulation, event handling, application state, and array methods** while building an interactive browser application.

## 🎧 Features

The music player includes:

- ▶️ Play music
- ⏸️ Pause music
- ⏭️ Play the next song
- ⏮️ Return to the previous song
- 🔀 Shuffle the playlist
- 🗑️ Remove songs from the playlist
- 🔄 Restore the playlist after all songs are removed
- 🎵 Select individual songs directly from the playlist
- 🖥️ Dynamically display the current song and artist
- ✨ Highlight the currently playing song
- ⏱️ Preserve the current playback position when pausing
- ♿ Dynamically update accessibility information

## 🧠 How It Works

The application separates the interface, styling, and player logic into:

```text
Music-Player/
├── index.html
├── styles.css
├── script.js
└── README.md
```

### HTML

HTML provides the structure of the music player, including:

- Playback controls
- Current song information
- Playlist container
- Player buttons
- SVG icons

### CSS

CSS controls the visual appearance and layout of the music player and playlist.

### JavaScript

JavaScript handles the application's behavior, including:

- Audio playback
- Playlist state
- Song selection
- Navigation
- Shuffling
- Song deletion
- Playlist restoration
- Dynamic HTML generation
- UI updates

## 🎼 Song Data

The playlist is represented as an array of JavaScript objects.

Each song contains information such as:

```javascript
{
    id: 0,
    title: "Scratching The Surface",
    artist: "Quincy Larson",
    duration: "4:25",
    src: "..."
}
```

Using objects makes it possible to keep the information for each song organized while the array allows the application to manage the playlist as a collection.

## 🔊 Audio Playback

The player uses JavaScript's `Audio` object:

```javascript
const audio = new Audio();
```

When the player selects a song, JavaScript assigns its source to the audio player and begins playback.

The application also keeps track of the current playback position when a song is paused so playback can resume from the same location.

## 🗂️ Managing Application State

The application stores its current state inside an object containing:

- The current playlist
- The currently selected song
- The current playback position

This allowed me to practice thinking about an application as **state that changes in response to user actions**.

For example, selecting a song changes the current song, deleting a song changes the playlist, and shuffling changes the order of the playlist.

## ▶️ Play and Pause

The `playSong()` function:

1. Finds the selected song.
2. Updates the audio source.
3. Determines the playback position.
4. Updates the current song.
5. Updates the interface.
6. Highlights the selected track.
7. Starts audio playback.

The `pauseSong()` function stores the current playback position before pausing the audio.

This helped me understand how multiple pieces of application state need to remain synchronized with the user interface.

## ⏭️ Previous and Next Song Navigation

The player determines the position of the currently playing song within the playlist.

That index is then used to find the previous or next song.

This gave me additional practice working with:

```javascript
array[index]
array[index + 1]
array[index - 1]
```

and understanding how indexes can be used to navigate through collections.

## 🔀 Shuffle

The playlist can be randomized using `Math.random()` and `.sort()`.

After shuffling:

- The song order changes.
- The current song is reset.
- Playback is paused.
- The playlist is rendered again.
- The player display is updated.

This showed me that changing data alone is not enough in an interactive application—the UI also needs to be updated to represent the new state.

## 🗑️ Playlist Management

Individual songs can be removed from the playlist.

The project uses `.filter()` to create an updated playlist without the selected song.

If every song is deleted, JavaScript dynamically creates a **Reset Playlist** button.

Selecting it restores the original playlist.

This gave me practice with:

- `.filter()`
- Spread syntax `...`
- Dynamic element creation
- Event listeners
- Conditional UI behavior

## 🖥️ Dynamic Playlist Rendering

Rather than manually writing every playlist item in HTML, JavaScript generates the playlist dynamically.

The project uses methods such as:

```javascript
.map()
.join()
```

to transform the song data into HTML.

This helped me understand the relationship:

```text
JavaScript data
      ↓
Transform data
      ↓
Generate HTML
      ↓
Render UI
```

That pattern is important in larger front-end applications and frameworks as well.

## 🔍 Finding Songs

The project uses `.find()` to locate a song based on its unique ID.

For example, when a user selects a song, the program searches the playlist for the object containing that ID.

This helped reinforce how unique identifiers can connect user-interface actions to specific data.

## ♿ Accessibility

The player also dynamically manages accessibility information.

For example, the currently playing song receives an `aria-current` attribute, and controls receive descriptive ARIA labels.

This introduced me to the idea that JavaScript can update not only visible content but also accessibility information as application state changes.

## 💡 What I Learned

This project helped reinforce several JavaScript and front-end development concepts:

- JavaScript arrays
- JavaScript objects
- Application state
- Functions
- Arrow functions
- Event listeners
- DOM manipulation
- Dynamic HTML generation
- Template literals
- Array indexing
- Optional chaining `?.`
- Spread syntax `...`
- `Math.random()`
- `.find()`
- `.filter()`
- `.forEach()`
- `.map()`
- `.join()`
- `.sort()`
- Audio playback
- Dynamic UI updates
- Accessibility attributes

One of the biggest lessons from this project was understanding how **data, application logic, and the user interface interact**.

For example, playing a song is not simply calling:

```javascript
audio.play();
```

The application also needs to determine which song was selected, update the audio source, remember the current song, update the song information displayed to the user, highlight the correct playlist item, update accessibility information, and maintain the playback state.

Breaking those responsibilities into separate functions made the application easier to manage.

## 🚀 Running the Project

Clone the repository:

```bash
git clone https://github.com/FrankySuazo/Music-Player.git
```

Open the project directory and launch:

```text
index.html
```

in a modern web browser.

## 🛠️ Technologies

**HTML5** · **CSS3** · **JavaScript**

## 📚 Project Purpose

This project was created as a hands-on JavaScript learning project focused on building an interactive application with **audio playback, state management, array manipulation, event-driven programming, and dynamic DOM updates**.

It represents part of my progression from learning individual JavaScript concepts toward understanding how those concepts work together inside a complete front-end application.
