<template>
  <main class="main-content">
    <!--
    <a href="https://github.com/nostalgic-css/NES.css" target="_blank" rel="noopener" class="github-link"
       v-bind:class="{active: isActive}">
      <p class="nes-balloon from-right">Go, Play Game!~</p>
      <i class="nes-octocat animate"></i>
    </a>
    -->
    <router-view></router-view>
  </main>
</template>
<script>
  export default {
    name: 'PixelContent',
    props: [
      'isActive'
    ]
  }
</script>
