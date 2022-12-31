<template>
  <div class="page"></div>
  <div class="top-navigation">
    <router-link to="/"
      ><img class="logo" src="../public/logo.png"
    /></router-link>
  </div>
  <div class="side-nav">
    <div class="">
      <ul class="">
        <li><router-link to="/">Home</router-link></li>
        <li><router-link to="/guess-my-number">About</router-link></li>
      </ul>
    </div>
  </div>
  <div class="container"><router-view /></div>
</template>
