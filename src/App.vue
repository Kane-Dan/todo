<template>
  <div class="main_container">
    <router-view />
  </div>
</template>

<style>
body,
html {
  margin: 0;
  padding: 0;
}

.main_container {
  height: 100vh;
  width: 100vw;
  background-color: black;
  color: white;
  /* background: rgb(131,58,180); */
  /* background: linear-gradient(310deg, rgba(131,58,180,1) 30%, rgba(30,42,248,1) 38%, rgba(29,253,145,1) 70%, rgba(253,49,80,1) 86%, rgba(252,176,69,1) 98%); */
  overflow: hidden;
}

.pt-1 {
  padding-top: 5px;

}

.pb-1 {
  padding-bottom: 5px;
}

hr {
  display: block;
  height: 1px;
  border: 0;
  border-top: 2px solid rgb(29, 5, 5);
  margin: 1em 0;
  padding: 0;
}

.mt-1 {
  margin-top: 5px;

}

.mb-1 {
  margin-bottom: 5px;
}

.text-center {
  text-align: center;
}
</style>
