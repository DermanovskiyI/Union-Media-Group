<template>
 <div class="wrapper">
   <router-view/>
 </div>

</template>

<style lang="scss">
body, html {
  height: 100%;
}
.wrapper {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
