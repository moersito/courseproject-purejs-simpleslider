# courseproject-purejs-simpleslider
Sample project using pure or vanilla Javascript for simple slider

### 1. Buatlah file index.html kemudian tulis dengan kode berikut,
```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Slider</title>

    <!-- styles -->
    <link rel="stylesheet" href="styles.css" />
  </head>
  <body>
    <div class="slider-container">
      <div class="slide">
        <img src="./img-1.jpeg" class="slide-img" alt="" />
        <h1>1</h1>
      </div>
      <div class="slide">
        <h1>2</h1>
      </div>
      <div class="slide">
        <h1>3</h1>
      </div>
      <div class="slide">
        <div>
          <img src="./person-1.jpeg" class="person-img" alt="" />
          <h4>susan doe</h4>
          <h1>4</h1>
        </div>
      </div>
    </div>
    <div class="btn-container">
      <button type="button" class="prevBtn">
        prev
      </button>
      <button type="button" class="nextBtn">
        next
      </button>
    </div>

    <!-- javascript -->
    <script src="app.js"></script>
  </body>
</html>
```

### 2. Buatlah file app.js kemudian tulis dengan kode berikut,
```
const slides = document.querySelectorAll(".slide");
const nextBtn = document.querySelector(".nextBtn");
const prevBtn = document.querySelector(".prevBtn");
slides.forEach(function (slide, index) {
  slide.style.left = `${index * 100}%`;
});
let counter = 0;
nextBtn.addEventListener("click", function () {
  counter++;
  carousel();
});

prevBtn.addEventListener("click", function () {
  counter--;
  carousel();
});

function carousel() {
  // working with slides
  // if (counter === slides.length) {
  //   counter = 0;
  // }
  // if (counter < 0) {
  //   counter = slides.length - 1;
  // }
  // working with buttons

  if (counter < slides.length - 1) {
    nextBtn.style.display = "block";
  } else {
    nextBtn.style.display = "none";
  }
  if (counter > 0) {
    prevBtn.style.display = "block";
  } else {
    prevBtn.style.display = "none";
  }
  slides.forEach(function (slide) {
    slide.style.transform = `translateX(-${counter * 100}%)`;
  });
}

prevBtn.style.display = "none";
```

### 3. Buatlah file style.css kemudian tulis dengan kode berikut,
```
/*
=============== 
Fonts
===============
*/
@import url("https://fonts.googleapis.com/css?family=Open+Sans|Roboto:400,700&display=swap");

/*
=============== 
Variables
===============
*/

:root {
  /* dark shades of primary color*/
  --clr-primary-1: hsl(205, 86%, 17%);
  --clr-primary-2: hsl(205, 77%, 27%);
  --clr-primary-3: hsl(205, 72%, 37%);
  --clr-primary-4: hsl(205, 63%, 48%);
  /* primary/main color */
  --clr-primary-5: #49a6e9;
  /* lighter shades of primary color */
  --clr-primary-6: hsl(205, 89%, 70%);
  --clr-primary-7: hsl(205, 90%, 76%);
  --clr-primary-8: hsl(205, 86%, 81%);
  --clr-primary-9: hsl(205, 90%, 88%);
  --clr-primary-10: hsl(205, 100%, 96%);
  /* darkest grey - used for headings */
  --clr-grey-1: hsl(209, 61%, 16%);
  --clr-grey-2: hsl(211, 39%, 23%);
  --clr-grey-3: hsl(209, 34%, 30%);
  --clr-grey-4: hsl(209, 28%, 39%);
  /* grey used for paragraphs */
  --clr-grey-5: hsl(210, 22%, 49%);
  --clr-grey-6: hsl(209, 23%, 60%);
  --clr-grey-7: hsl(211, 27%, 70%);
  --clr-grey-8: hsl(210, 31%, 80%);
  --clr-grey-9: hsl(212, 33%, 89%);
  --clr-grey-10: hsl(210, 36%, 96%);
  --clr-white: #fff;
  --clr-red-dark: hsl(360, 67%, 44%);
  --clr-red-light: hsl(360, 71%, 66%);
  --clr-green-dark: hsl(125, 67%, 44%);
  --clr-green-light: hsl(125, 71%, 66%);
  --clr-black: #222;
  --ff-primary: "Roboto", sans-serif;
  --ff-secondary: "Open Sans", sans-serif;
  --transition: all 0.3s linear;
  --spacing: 0.25rem;
  --radius: 0.5rem;
  --light-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
  --dark-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
  --max-width: 1170px;
  --fixed-width: 620px;
}
/*
=============== 
Global Styles
===============
*/

*,
::after,
::before {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  font-family: var(--ff-secondary);
  background: var(--clr-grey-10);
  color: var(--clr-grey-1);
  line-height: 1.5;
  font-size: 0.875rem;
}
ul {
  list-style-type: none;
}
a {
  text-decoration: none;
}
img:not(.person-img) {
  width: 100%;
}
img {
  display: block;
}

h1,
h2,
h3,
h4 {
  letter-spacing: var(--spacing);
  text-transform: capitalize;
  line-height: 1.25;
  margin-bottom: 0.75rem;
  font-family: var(--ff-primary);
}
h1 {
  font-size: 3rem;
}
h2 {
  font-size: 2rem;
}
h3 {
  font-size: 1.25rem;
}
h4 {
  font-size: 0.875rem;
}
p {
  margin-bottom: 1.25rem;
  color: var(--clr-grey-5);
}
@media screen and (min-width: 800px) {
  h1 {
    font-size: 4rem;
  }
  h2 {
    font-size: 2.5rem;
  }
  h3 {
    font-size: 1.75rem;
  }
  h4 {
    font-size: 1rem;
  }
  body {
    font-size: 1rem;
  }
  h1,
  h2,
  h3,
  h4 {
    line-height: 1;
  }
}
/*  global classes */

.btn {
  text-transform: uppercase;
  background: transparent;
  color: var(--clr-black);
  padding: 0.375rem 0.75rem;
  letter-spacing: var(--spacing);
  display: inline-block;
  transition: var(--transition);
  font-size: 0.875rem;
  border: 2px solid var(--clr-black);
  cursor: pointer;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.2);
  border-radius: var(--radius);
}
.btn:hover {
  color: var(--clr-white);
  background: var(--clr-black);
}
/* section */
.section {
  padding: 5rem 0;
}

.section-center {
  width: 90vw;
  margin: 0 auto;
  max-width: 1170px;
}
@media screen and (min-width: 992px) {
  .section-center {
    width: 95vw;
  }
}
main {
  min-height: 100vh;
  display: grid;
  place-items: center;
}
/*
=============== 
Slider
===============
*/

.slider-container {
  border: 5px solid var(--clr-primary-5);
  width: 80vw;
  margin: 0 auto;
  height: 40vh;
  max-width: 80rem;
  position: relative;
  border-radius: 0.5rem;
  overflow: hidden;
  margin-top: 4rem;
}
.slide {
  position: absolute;
  width: 100%;
  height: 100%;
  background: var(--clr-primary-9);
  color: var(--clr-white);
  display: grid;
  place-items: center;
  transition: all 0.25s ease-in-out;
  text-align: center;
}
.slide-img {
  height: 100%;
  object-fit: cover;
}
.slide h1 {
  font-size: 5rem;
}
.person-img {
  border-radius: 50%;
  width: 6rem;
  height: 6rem;
  margin: 0 auto;
  margin-bottom: 1rem;
}
.slide:nth-child(1) h1 {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
.slide:nth-child(3) {
  background: linear-gradient(rgba(0, 0, 0, 0.4), rgba(0, 0, 0, 0.4)),
    url("./img-2.jpeg") center/cover no-repeat;
}
.btn-container {
  display: flex;
  justify-content: center;
  margin-top: 0.75rem;
}
.prevBtn,
.nextBtn {
  background: transparent;
  border-color: transparent;
  font-size: 1.75rem;
  cursor: pointer;
  margin: 0 0.25rem;
  text-transform: capitalize;
  letter-spacing: 2px;
  color: var(--clr-grey-5);
  transition: var(--transition);
}
.prevBtn:hover,
.nextBtn:hover {
  color: var(--clr-grey-3);
}

@media screen and (min-width: 576px) {
  .slider-container {
    height: 45vh;
  }
}
@media screen and (min-width: 768px) {
  .slider-container {
    height: 55vh;
  }
}
@media screen and (min-width: 992px) {
  .slider-container {
    height: 65vh;
  }
}
```

### 4. Lakukan "git merge" antara branch "main" dengan branch "requiredimages" dengan perintah berikut,
```
git merge requiredimages
```

