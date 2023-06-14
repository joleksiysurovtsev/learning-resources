<style>
body {
    width: auto;
    max-width: 100%;
    margin: 0 auto;
    padding: 20px;
    font-family: "Verdana";
    font-size: 13px;
    background: rgba(92,129,202,1);
    background:
        -moz-linear-gradient(
            left, rgba(92,129,202,1) 0%,rgba(249,140,112,1) 100%);
    background:
        -webkit-linear-gradient(
            left,rgba(92,129,202,1) 0%,rgba(249,140,112,1) 100%);
}

.skill_ico {
    float: left;
    display: block;
    margin-right: 10px;
    vertical-align: middle;
}

.block {
    background: linear-gradient(#111, #333);
    color: #fff;
    padding-top: 5px;
    box-shadow: 0 1px 2px #ccc;

}

.block input[type='radio']:checked ~ .info {
    height: 130px;
    transition: .3s ease-in;

    background:
        -moz-linear-gradient(
            left, rgba(92,129,202,1) 0%,rgba(249,140,112,1) 100%);
    background:
        -webkit-linear-gradient(
            left,rgba(92,129,202,1) 0%,rgba(249,140,112,1) 100%);
}

input[type='radio'] {
    width: 100%;
    display: none;
}

label {
    width: 450px;
    max-width: 100%;
    cursor: pointer;
}

span {
    font-family: 'Arial';
    font-weight: bold;
    display: block;
    padding: 10px 12px 12px 15px;
    margin: 0;
    cursor: pointer;
}

.info {
    background: #fff;
    color: #222;
    width: 100%;
    height: 0;
    line-height: 2;
    padding-left: 15px;
    display: block;
    overflow: hidden;
    box-sizing: border-box;
    transition: .3s ease-out;
}

h4 {
    color: #111;
    text-align: right;
    text-shadow: 2px 2px 3px #fff;
    position: absolute;
    bottom: 20px;
    right: 15px;
}

h4 a {
    color: #111;
    text-decoration: none;
}

::selection {
    background: #222;
    color: #fff;
}

</style>

# My Library

---
<details>
   <summary>
      <h1>Todo list:</h1>
   </summary>
   <p>Study</p>
   <p>Grocery Shop</p>
   <p>Clean The House</p>
</details>





<div class="block">
  <input type="radio" name="skill" id="skillA" checked />
  <label for="skillA"><img class="skill_ico" src="https://skillicons.dev/icons?i=gradle" alt="Gradle"><span>Gradle</span></label>
  <div class="info">
    <p>
      <a href="gradle/Videos.md">Video tutorials</a>
    </p>
    <p>
      <a href="gradle/Articles.md">Articles</a>
    </p>
    <p>
      <a href="gradle/Literature.md">Literature</a>
    </p>
  </div>
</div>

---

<div class="block">
  <input type="radio" name="skill" id="skillB"/>
  <label for="skillB"><img class="skill_ico" src="https://skillicons.dev/icons?i=kotlin" alt="Kotlin"><span>Kotlin</span></label>
  <div class="info">
    <p>
      <a href="kotlin/Videos.md">Video tutorials</a>
    </p>
    <p>
      <a href="kotlin/Articles.md">Articles</a>
    </p>
    <p>
      <a href="kotlin/Literature.md">Literature</a>
    </p>
  </div>
</div>

---

<div class="block">
  <input type="radio" name="skill" id="skillC" />
  <label for="skillC"><img class="skill_ico" src="https://skillicons.dev/icons?i=postgres" alt="Postgres"><span>Postgres</span></label>
  <div class="info">
    <p>
      <a href="postgres/Videos.md">Video tutorials</a>
    </p>
    <p>
      <a href="postgres/Articles.md">Articles</a>
    </p>
    <p>
      <a href="postgres/Literature.md">Literature</a>
    </p>
</div>
</div>
