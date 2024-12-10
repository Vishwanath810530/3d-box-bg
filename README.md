# 3d-box-bg
//index.html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link
      rel="stylesheet"
      href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.14.0/css/all.min.css"
      integrity="sha512-1PKOgIY59xJ8Co8+NE6FZ+LOAZKjy+KY8iq0G4B3CyeY6wYHN3yt9PW0XpSriVlkMXe40PTKnXrLnZ9+fkDaog=="
      crossorigin="anonymous"
    />
    <link rel="stylesheet" href="style.css" />
    <title>3D Boxes Background</title>
  </head>
  <body>
    <button id="btn" class="magic">Magic 🎩</button>
    <div id="boxes" class="boxes big"></div>
    <script src="script.js"></script>
  </body>
</html>

//script.js
const boxesContainer = document.getElementById('boxes')
const btn = document.getElementById('btn')

btn.addEventListener('click', () => boxesContainer.classList.toggle('big'))

function createBoxes() {
  for (let i = 0; i < 4; i++) {
    for (let j = 0; j < 4; j++) {
      const box = document.createElement('div')
      box.classList.add('box')
      box.style.backgroundPosition = `${-j * 125}px ${-i * 125}px`
      boxesContainer.appendChild(box)
    }
  }
}

createBoxes()

//style.css
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Poppins&display=swap');

* {
  box-sizing: border-box;
}

body {
  background-color: #fafafa;
  font-family: 'Roboto', sans-serif;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  overflow: hidden;
}

.magic {
  background-color: #f9ca24;
  color: #fff;
  font-family: 'Poppins', sans-serif;
  border: 0;
  border-radius: 3px;
  font-size: 16px;
  padding: 12px 20px;
  cursor: pointer;
  position: fixed;
  top: 20px;
  letter-spacing: 1px;
  box-shadow: 0 3px rgba(249, 202, 36, 0.5);
  z-index: 100;
}

.magic:focus {
  outline: none;
}

.magic:active {
  box-shadow: none;
  transform: translateY(2px);
}

.boxes {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
  height: 500px;
  width: 500px;
  position: relative;
  transition: 0.4s ease;
}

.boxes.big {
  width: 600px;
  height: 600px;
}

.boxes.big .box {
  transform: rotateZ(360deg);
}

.box {
  background-image: url('https://media.giphy.com/media/EZqwsBSPlvSda/giphy.gif');
  background-repeat: no-repeat;
  background-size: 500px 500px;
  position: relative;
  height: 125px;
  width: 125px;
  transition: 0.4s ease;
}

.box::after {
  content: '';
  background-color: #f6e58d;
  position: absolute;
  top: 8px;
  right: -15px;
  height: 100%;
  width: 15px;
  transform: skewY(45deg);
}

.box::before {
  content: '';
  background-color: #f9ca24;
  position: absolute;
  bottom: -15px;
  left: 8px;
  height: 15px;
  width: 100%;
  transform: skewX(45deg);
}
