<template>
  <footer class="footer">
    <div class="container-fluid">
      <nav>
        <ul class="footer-menu">
          <li>
            <router-link :to="{path:'/admin'}">Dashboard</router-link>
          </li>
        </ul>
      </nav>
      <div class="copyright text-center">
        &copy; Coded with
        <i class="fa fa-heart heart"></i> by FireBusters. Template by
        <a href="https://binarcode.com" target="_blank" rel="noopener noreferrer">BinarCode</a>.
        Designed by <a href="https://www.creative-tim.com/?ref=pdf-vuejs" target="_blank" rel="noopener noreferrer">Creative Tim</a>.
      </div>
    </div>
  </footer>
</template>
<script>
  export default {}

</script>
<style>

</style>
