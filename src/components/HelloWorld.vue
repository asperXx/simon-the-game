<template>
  <div class="hello">
   <div id="app">
  
</div>
  </div>
</template>

<script>
export default {
 
}
</script>

<style lang="scss">
$color-black: #000;
$color-dark-gray: #2e2e2e;
$color-med-gray: #666;
$color-light-gray: #ccc;
$color-green: darken(green, 5%);
$color-red: darken(red, 10%);
$color-yellow: darken(#ffd700, 10%);
$color-blue: darken(#0000cd, 5%);
$color-white: #fff;
$color-light-green: lighten(green, 5%);
$color-light-red: lighten(red, 5%);
$color-light-blue: lighten(#0000cd, 5%);
$color-light-yellow: lighten(#ffd700, 5%);
$color-bisque: #ffe4c4;

// Main Styles
body {
  font-family: 'Open Sans', sans-serif;
  user-select: none;
  background-color: $color-bisque;
}
h1 {
  font-family: 'Russo One', sans-serif;
  font-size: 3rem;
  cursor: default;
  margin: 1rem 0;
}
#simon {
  margin: 2rem auto 0 auto;
  max-width: 680px;
  min-width: 680px;
  max-height: 680px;
  min-height: 680px;
  background-color: $color-dark-gray;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  box-shadow: 0px 0px 18px rgba(0,0,0,.6)
}
#buttons {
  display: flex;
  flex-wrap: wrap;
  max-width: 620px;
  min-width: 620px;
  justify-content: space-between;
}
.button {
  cursor: pointer;
  min-width: 300px;
  min-height: 300px;
  max-width: 300px;
  max-height: 300px;
}
#green { 
  background-color: $color-green; 
  border-top-left-radius: 300px;
  margin-bottom: 20px;
  box-shadow: inset 3px 3px 10px rgba(255,255,255,.3);
}
#blue { 
  background-color: $color-blue; 
  border-bottom-right-radius: 300px;
  box-shadow: inset -3px -3px 10px rgba(255,255,255,.3);
}
#yellow { 
  background-color: $color-yellow; 
  border-bottom-left-radius: 300px;
  box-shadow: inset 3px -3px 10px rgba(255,255,255,.3);
}
#red { 
  background-color: $color-red; 
  border-top-right-radius: 300px;
  margin-bottom: 20px;
  box-shadow: inset -3px 3px 10px rgba(255,255,255,.3);
}
#green.highlight { background-color: $color-light-green; }
#red.highlight { background-color: $color-light-red; }
#blue.highlight { background-color: $color-light-blue; }
#yellow.highlight { background-color: $color-light-yellow; }

// Center Controls
#center {
  border: 20px solid $color-dark-gray;
  box-sizing: border-box;
  position: absolute;
  min-width: 300px;
  max-width: 300px;
  min-height: 300px;
  max-height: 300px;
  border-radius: 50%;
  background-color: $color-light-gray;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
  color: $color-dark-gray;
}
#title {
  margin-top: 20px;
  text-align: center;
  background-color: $color-light-gray;
  width: 200px;
  border-top-left-radius: 50%;
  border-top-right-radius: 50%;
}
#controls {
  display: flex;
  justify-content: space-between;
  align-items: center;
  min-width: 180px;
  margin-top: .5rem;
}
#counter {
  display: inline-block;
  width: 60px;
  height: 40px;
  color: $color-med-gray;
  background-color: $color-black;
  border: 4px solid $color-dark-gray;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 8px;
  font-size: 1.6rem;
}
.lit { color: $color-red; }
#power {
  margin-top: 1rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 110px;
  font-size: .875rem;
  text-transform: uppercase;
  font-weight: bold;
}
#switch { 
  cursor: pointer;
  display: inline-block; 
  width: 50px;
  height: 25px;
  background-color: $color-dark-gray;
  position: relative;
}
#switch:after {
  content: '';
  position: absolute;
  top: 0;
  height: 19px;
  width: 19px;
  border: 3px solid $color-dark-gray; 
  background-color: $color-red;
}
#switch.off:after { left: 0 }
#switch.on:after { right: 0 }
.btn {
  cursor: pointer;
  position: relative;
  display: inline-block;
  width: 24px;
  height: 24px;
  background-color: $color-yellow;
  border-radius: 50%;
  border: 4px solid $color-dark-gray;
  margin-top: 1rem;
  box-shadow: 2px 2px 3px rgba(0,0,0,.4);
}
.btn::after {
  position: absolute;
  top: -20px;
  left: -25%;
  font-size: 12px;
  text-transform: uppercase;
  font-weight: bold;
}
.btn:hover { background-color: $color-light-yellow; }
#start.btn { background-color: $color-red; }
#start.btn:hover { background-color: $color-light-red; }
#strict.btn::before {
  position: absolute;
  content: '';
  top: -34px;
  left: 7px;
  display: inline-block;
  width: 6px;
  height: 6px;
  border: 2px solid $color-dark-gray;
  border-radius: 50%;
  background-color: $color-black;
}
#strict.strict.btn::before { background-color: $color-yellow; }
#start::after { content: 'Start'; }
#strict::after { content: 'Strict'; }

footer {
  padding: 3rem 0;
  text-align: center;
  font-size: .875rem;
}
</style>
