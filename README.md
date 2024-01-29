# Rotating Gallery with HTML, CSS, and JavaScript

In this project, I created a rotating gallery using a combination of HTML, CSS, and JavaScript. The gallery allows images to cycle through in a visually appealing way.

## HTML Structure

I started by setting up the HTML structure. The gallery container is a `<div>` with a unique ID, and each image is placed inside an `<img>` tag with a common class.

```html
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Rotating Gallery</title>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <div class="image-container">
      <span style="--i: 1">
        <img
          src="https://images.unsplash.com/photo-1477884213360-7e9d7dcc1e48?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxzZWFyY2h8MTN8fGRvZ3xlbnwwfHwwfHw%3D&auto=format&fit=crop&w=600&q=60"
        />
      </span>
      <span style="--i: 2">
        <img
          src="https://images.unsplash.com/photo-1484399172022-72a90b12e3c1?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxzZWFyY2h8MTN8fGdpcmx8ZW58MHx8MHx8&auto=format&fit=crop&w=600&q=60"
        />
      </span>
      <span style="--i: 3">
        <img
          src="https://images.unsplash.com/photo-1581704906775-891dd5207444?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxzZWFyY2h8MTR8fGJveXxlbnwwfHwwfHw%3D&auto=format&fit=crop&w=600&q=60"
        />
      </span>
      <span style="--i: 4">
        <img
          src="https://images.unsplash.com/photo-1441974231531-c6227db76b6e?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxzZWFyY2h8N3x8bmF0dXJlfGVufDB8fDB8fA%3D%3D&auto=format&fit=crop&w=600&q=60"
        />
      </span>
      <span style="--i: 5">
        <img
          src="https://images.unsplash.com/photo-1426604966848-d7adac402bff?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxzZWFyY2h8OXx8bmF0dXJlfGVufDB8fDB8fA%3D%3D&auto=format&fit=crop&w=600&q=60"
        />
      </span>
      <span style="--i: 6">
        <img
          src="https://images.unsplash.com/photo-1548036328-c9fa89d128fa?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxzZWFyY2h8N3x8YmFnfGVufDB8fDB8fA%3D%3D&auto=format&fit=crop&w=600&q=60"
        />
      </span>
      <span style="--i: 7">
        <img
          src="https://images.unsplash.com/photo-1544716278-ca5e3f4abd8c?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxzZWFyY2h8MTB8fGJvb2t8ZW58MHx8MHx8&auto=format&fit=crop&w=600&q=60"
        />
      </span>
      <span style="--i: 8">
        <img
          src="https://images.unsplash.com/photo-1582142407894-ec85a1260a46?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxzZWFyY2h8MTJ8fGdsYXNzZXN8ZW58MHx8MHx8&auto=format&fit=crop&w=600&q=60"
        />
      </span>
    </div>

    <div class="btn-container">
      <button class="btn" id="prev">Prev</button>
      <button class="btn" id="next">Next</button>
    </div>

    <script src="app.js"></script>
  </body>
</html>
```

# CSS Styling
I applied some basic styling to the gallery container to ensure proper positioning and visual appeal. Feel free to customize the styles according to your design preferences.

```css
body {
  margin: 0;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
  height: 100vh;
  background: black;
  overflow: hidden;
}

.image-container {
  position: relative;
  width: 200px;
  height: 200px;
  transform-style: preserve-3d;
  transform: perspective(1000px) rotateY(0deg);
  transition: transform 0.7s;
}

.image-container span {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  transform: rotateY(calc(var(--i) * 45deg)) translateZ(400px);
}

.image-container span img {
  position: absolute;
  left: 0;
  top: 0;
  width: 100%;
}

.btn-container {
  position: relative;
  width: 80%;
}

.btn {
  position: absolute;
  bottom: -80px;
  background: crimson;
  color: #fff;
  border: none;
  padding: 10px 20px;
  border-radius: 5px;
  cursor: pointer;
}

#prev {
  left: 20%;
}

#next {
  right: 20%;
}

.btn:hover {
  filter: brightness(1.5);
}
```

# JavaScript for Rotation
To make the gallery rotate, I utilized JavaScript to handle the logic. The script fetches all the gallery items, then iterates through them, displaying each image for a certain duration before moving to the next.

```js
const imageContainer = document.querySelector(".image-container");
const prevBtn = document.getElementById("prev");
const nextBtn = document.getElementById("next");

let x = 0;

prevBtn.addEventListener("click", () => {
  x = x + 45;
  rotate();
});

nextBtn.addEventListener("click", () => {
  x = x - 45;
  rotate();
});

function rotate() {
  imageContainer.style.transform = `perspective(1000px) rotateY(${x}deg)`;
}
```
