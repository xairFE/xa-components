<template>
  <div class="xa-copyright">Copyright &copy; {{ thisYear }}</div>
</template>

<script>
  export default {
    name: 'copyright',
    data () {
      return {
        thisYear: new Date().getFullYear()
      }
    }
  }
</script>

<style scoped>
  .xa-copyright{text-align:center;line-height:30px;color:#999;font-size:13px;}
</style>
