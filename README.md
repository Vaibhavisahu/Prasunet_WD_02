Prasunet_Code_TaskNo 0TASK-02.HTML

<!DOCTYPE html>
 <html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Gold Stopwatch</title>
    <link rel="stylesheet" href="style.css" />
    <link
      href="https://fonts.googleapis.com/css2?family=Montserrat:wght@200;900&display=swap"
      rel="stylesheet"
    />
    <link
      href="https://fonts.googleapis.com/css2?family=Roboto+Mono:ital,wght@0,300;1,300&display=swap"
      rel="stylesheet"
    />
  </head>

  <body>
    <div class="stopwatch">
      <h1><span class="gold">GOLD</span> STOPWATCH</h1>
      <div class="circle">
        <span class="time" id="display">00:00:00</span>
      </div>

      <div class="controls">
        <button class="buttonPlay">
          <img id="playButton" src="https://res.cloudinary.com/https-tinloof-com/image/upload/v1593360448/blog/time-in-js/play-button_opkxmt.svg" />

          <img id="pauseButton" src="https://res.cloudinary.com/https-tinloof-com/image/upload/v1593360448/blog/time-in-js/pause-button_pinhpy.svg" />
        </button>

        <button class="buttonReset">
          <img id="resetButton" src="https://res.cloudinary.com/https-tinloof-com/image/upload/v1593360448/blog/time-in-js/reset-button_mdv6wf.svg" />
        </button>
      </div>
    </div>
    <script src="script.js"></script>
  </body>
  </html>

  Prasunet_Code_TaskNo 0TASK-02.CSS

  body {
  background-color: #2c3347;
  color: #ffffff;
}

h1 {
  font-size: 48px;
  font-family: "Montserrat", sans-serif;
  font-weight: 200;

  text-align: center;
  line-height: 59px;

  padding: 0 64px;
  margin: 0;
}

.stopwatch {
  display: grid;
  justify-items: center;
  grid-row-gap: 23px;
  width: 100%;
  padding-top: 25px;
}

.circle {
  display: flex;
  justify-content: center;
  align-items: center;

  height: 270px;
  width: 270px;

  border: 2px solid;
  border-radius: 50%;
}

.time {
  font-family: "Roboto Mono", monospace;
  font-weight: 300;
  font-size: 48px;
}

.gold {
  font-weight: 900;

  color: #f2c94c;
  text-shadow: 0 0 0px #fff, 0 0 50px #f2c94c;
}

.controls {
  display: flex;
  justify-content: space-between;

  width: 187px;
}

button {
  cursor: pointer;
  background: transparent;
  padding: 0;
  border: none;
  margin: 0;
  outline: none;
}

#playButton {
  display: block;
}

#pauseButton {
  display: none;
}

Prasunet_Code_TaskNo 0TASK-02.JAVA

/ Convert time to a format of hours, minutes, seconds, and milliseconds

function timeToString(time) {
  let diffInHrs = time / 3600000;
  let hh = Math.floor(diffInHrs);
  let diffInMin = (diffInHrs - hh) * 60;
  let mm = Math.floor(diffInMin);

  let diffInSec = (diffInMin - mm) * 60;
  let ss = Math.floor(diffInSec);

  let diffInMs = (diffInSec - ss) * 100;
  let ms = Math.floor(diffInMs);

  let formattedMM = mm.toString().padStart(2, "0");
  let formattedSS = ss.toString().padStart(2, "0");
  let formattedMS = ms.toString().padStart(2, "0");

  return ${formattedMM}:${formattedSS}:${formattedMS};
}

// Declare variables to use in our functions below

let startTime;
let elapsedTime = 0;
let timerInterval;

// Create function to modify innerHTML

function print(txt) {
  document.getElementById("display").innerHTML = txt;
}

// Create "start", "pause" and "reset" functions

function start() {
  startTime = Date.now() - elapsedTime;
  timerInterval = setInterval(function printTime() {
    elapsedTime = Date.now() - startTime;
    print(timeToString(elapsedTime));
  }, 10);
  showButton("PAUSE");
}

function pause() {
  clearInterval(timerInterval);
  showButton("PLAY");
}

function reset() {
  clearInterval(timerInterval);
  print("00:00:00");
  elapsedTime = 0;
  showButton("PLAY");
}

// Create function to display buttons

function showButton(buttonKey) {
  const buttonToShow = buttonKey === "PLAY" ? playButton : pauseButton;
  const buttonToHide = buttonKey === "PLAY" ? pauseButton : playButton;
  buttonToShow.style.display = "block";
  buttonToHide.style.display = "none";
}
// Create event listeners

let playButton = document.getElementById("playButton");
let pauseButton = document.getElementById("pauseButton");
let resetButton = document.getElementById("resetButton");

playButton.addEventListener("click", start);
pauseButton.addEventListener("click", pause);
resetButton.addEventListener("click", reset);


