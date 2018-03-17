<template>
  <div id="main-menu">
      <nav>
          <h2 class="sr-only">Main Menu</h2>
          <ul>
              <li><a href="/#">Home</a></li>
              <li><a href="/#employment">Employment</a></li>
              <li><a href="/#skills">Skills</a></li>
              <li><a href="/#contact">Contact</a></li>
          </ul>
      </nav>
  </div>
</template>

<script>
    export default {
        name: 'MainMenu'
    }
</script>

<style lang="scss" scoped>
    ul {
        list-style-type: none;
        padding: 0;
        li {
            display: inline-block;
            text-decoration: none;
        }
    }
</style>
