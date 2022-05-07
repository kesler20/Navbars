HTML 
```HTML
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link rel="stylesheet" href="style.css" />
    <link rel="stylesheet" href="presentation.css" />
    <link rel="stylesheet" href="navbar.css" />
    <link rel="stylesheet" href="sidebar.css" />
    <link rel="stylesheet" href="food.css" />
    <link rel="stylesheet" href="meal.css" />
    <title>Sofia Diet</title>
  </head>
  <body>
    <div id="root">
      <nav class="navbar">
        <div class="hamburger-menu">
          <div class="hamburger"></div>
          <div class="hamburger"></div>
          <div class="hamburger"></div>
        </div>
        <div class="site-title">
          <a href="./"><img src="Logo.png" alt="" srcset="" /></a>
          <p>sofiaDiet</p>
        </div>
        <!--change the text content of the version dynamically using the version class on javascript-->
        <div class="version">
          <p>version: v.0.1</p>
        </div>
      </nav>
      <hr />
      <nav class="side-bar hide">
        <a href="./diet" class="nav-link hide">Diet Plan v</a>
        <a href="./meal" class="nav-link hide">Meals v</a>
        <a href="./food" class="nav-link hide">Foods v</a>
      </nav>
```
CSS

```CSS
navbar.css

* {
  --nav-margins: 100px;
}

.navbar {
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  align-items: center;
  width: 100%;
  height: 80px;
  border: 10px black;
}

.hamburger-menu {
  border: 0.1px solid rgb(186, 202, 183);
  width: 57px;
  height: 42px;
  margin-right: 50px;
  border-radius: 5px;
  display: flex;
  justify-content: space-evenly;
  flex-direction: column;
  align-items: center;
}

.hamburger {
  border-bottom: solid 3px grey;
  width: 28px;
}

.hamburger-menu:hover {
  box-shadow: 1px 1px 1px 10px rgb(245, 255, 229);
}

.site-title {
  font-size: 40px;
  font-weight: 700;
  width: 280px;
  display: flex;
  justify-content: space-evenly;
  margin-left: var(--nav-margins);
}

.site-title p {
  /* global 94%+ browsers support */
  background: linear-gradient(
    90deg,
    rgba(0, 255, 235, 1) 0%,
    rgba(7, 58, 187, 1) 100%
  );
  -webkit-text-fill-color: transparent;
  -webkit-background-clip: text;
  background-clip: text;
}

.site-title img {
  width: 59px;
  height: 53px;
  border-radius: 20px;
}

.version {
  font-size: 28px;
  font-weight: 400;
  display: flex;
  color: #555555;
  justify-content: space-evenly;
  width: 180px;
  align-items: center;
  margin-left: var(--nav-margins);
}

styles.CSS

@import url("https://fonts.googleapis.com/css2?family=Inter&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Roboto+Mono:ital,wght@1,300&display=swap");
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  font-family: "Inter", sans-serif;
  --presentation-font-family: "Roboto Mono", monospace;
}

body {
  display: flex;
  justify-content: center;
  align-items: center;
  background-image: url(Logo.png);
  background-position-x: left;
  background-position-y: bottom;
  background-repeat: no-repeat;
  background-size: 10%;
}

#root {
  max-width: 1065px;
  height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0px;
  height: 100vh;
}

a {
  text-decoration: none;
  list-style: none;
  outline: none;
}

hr {
  border: 1px #e3eafc solid;
  width: 100%;
  height: 0;
}

.hide {
  display: none;
}

.info-btn {
  margin: 20px;
}

sidebar.css 

.side-bar {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    width: 100%;
}

.nav-link {
    text-decoration: none;
    outline: none;
    margin-right: 20px;
    color: rgb(104, 104, 104);
}

.nav-link:hover {
    border-bottom: 1px solid rgb(104, 104, 104);
}

```

javascript

```javascript

const hamburger = document.querySelector(".hamburger-menu");
const sideBar = document.querySelector(".side-bar");
const mealTable = document.querySelector(".meal-table");
const addButton = document.querySelector(".add-btn");
const deleteButton = document.querySelector(".delete-btn");

let hamburgerClicked = true;
hamburger.addEventListener("click", (e) => {
  sideBar.classList.toggle("hide", hamburgerClicked);
  for (const element of sideBar.children) {
    element.classList.toggle("hide", !hamburgerClicked);
  }
  hamburgerClicked = !hamburgerClicked;
});

addButton.addEventListener("click", (e) => {
  const tableRow = document.createElement("tr");
  const tableFoodData = document.createElement("td");
  const tableAmountData = document.createElement("td");

  // when this is for the meal you should pu mealname, for food, foodname
  const foodInputField = document.createElement("input");
  foodInputField.name = mealTable.children[0].children[1].children[0].children[0].name;
  foodInputField.type = "text";

  const amountInputField = document.createElement("input");
  amountInputField.name = mealTable.children[0].children[1].children[1].children[0].name;
  amountInputField.type = "number";

  tableAmountData.appendChild(amountInputField);
  tableFoodData.appendChild(foodInputField);

  tableRow.appendChild(tableFoodData);
  tableRow.appendChild(tableAmountData);
  mealTable.children[0].appendChild(tableRow);
});

deleteButton.addEventListener("click", (e) => {
  let lastTableRow = mealTable.children[0].children;
  const lastTableIndex = mealTable.children[0].children.length
  lastTableRow = mealTable.children[0].children[lastTableIndex - 1]
  mealTable.children[0].removeChild(lastTableRow)
});
// const foodButton = document.querySelector('.create-food-btn')
// foodButton.addEventListener('submit', e => {
//     let form = document.querySelector('.create-food-form')
//     alert('hey')
//     console.log(form)
// })

```