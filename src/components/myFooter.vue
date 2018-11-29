<template>
  <div class="myFooter">
    <div class="grid1">
        <footer id="itemFooter">2018 Bookstore All Rights Reserved {{ num  }}</footer>
    </div>
  </div>
</template>

<script>
export default {
  name: 'myFooter',
  props: {
    
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.grid1 {
    display: grid;
    grid-template-columns: 30px 120px auto 300px 30px;
    grid-template-rows: auto auto auto;
}
#itemFooter {
    grid-column: 1/span 5;
    grid-row: 3;
    background-color: rgb(55, 118, 120);
    padding: 30px;
    text-align: center;
    font-weight: bolder;
    color: black;
}
</style>