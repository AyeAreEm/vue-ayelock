<template>
  <div>
    <img src="./assets/AyeLock.png" alt="AyeLock" title="AyeLock">
    <div class="password-box">
      <h3>Weak:</h3>
      <h3>{{ weak }}</h3>
    </div>
    <div class="password-box">
      <h3>Recommended:</h3>
      <h3>{{ rec }}</h3>
    </div>
    <div class="password-box">
      <h3>Strong:</h3>
      <h3>{{ strong }}</h3>
    </div>
    <div class="password-box">
      <h3>Easy to read:</h3>
      <h3>{{ easy }}</h3>
    </div>
    <button v-on:click="refresh">Refresh</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      weak: this.gen(true, true, true, true, 12),
      rec: this.gen(true, true, true, true, 15),
      strong: this.gen(true, true, true, true, 18),
      easy: this.gen(true, true, true, true, 15)
    }
  },
  methods: {
    gen(isLetters, isUpperCase, isNumbers, isSpecial, len) {
      const lowercase = "abcdefghijklmnopqrstuvwxyz";
      const uppercase = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
      const numbers = "0123456789";
      const special = "!@#%^&*()_-+={}[]:'/?\$|;.,";

      let allowedChars = "";

      allowedChars += (isLetters ? lowercase : '');
      allowedChars += (isUpperCase ? uppercase : '');
      allowedChars += (isNumbers ? numbers : '');
      allowedChars += (isSpecial ? special : '');

      let result = "";

      for (let i = 0, n = allowedChars.length; i < len; i++) {
        result += allowedChars.charAt(Math.floor(Math.random() * n));
      }

      return result;
    },
    refresh() {
      this.weak = this.gen(true, true, true, true, 12)
      this.rec = this.gen(true, true, true, true, 15)
      this.strong = this.gen(true, true, true, true, 18)
      this.easy = this.gen(true, true, false, false, 15)
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto&display=swap');

body {
  background: #B20940;
  font-family: 'Roboto', sans-serif;
  text-align: center;
}

h1 {
  color: white;
}

button {
  margin-top: 40px;
  background: black;
  color: white;
  height: 50px;
  width: 100px;
  border-radius: 5px;
  border: none;
}

button:focus {
  outline: none;
}

button:hover {
  cursor: pointer;
}

img {
  width: 340px;
  height: 110px;
}

.password-box {
  background: white;
  width: 35%;
  height: 100px;
  margin: auto;
  border-radius: 10px;
  box-shadow: 10px 10px 10px black;
  font-size: 24px;
}
</style>
