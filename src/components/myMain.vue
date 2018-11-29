<template>
  <div class="myMain">
    <div class="grid1" id="myMain">
       <br><br>
       <p>{{ myBooks }} pp</p>
        <div id="itemBooksContainer" class="container">
            <div class="row">
                <div class="col"></div>
                <div class="col-11" id="putBooks">
                    <myBook :myBooks="myBooks"/>
                </div>
                <div class="col"></div>
            </div>
            <br><br><br>
        </div>
    </div>
  </div>
</template>



<script>


export default {
  name: 'myMain',
  data() {
      return {
        
      }
  },
  components: {
     
  },
  props: {
      filteredBooks: Array,
      myBooks: Array,
      num: Number,
      fruit: String,
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
#myMain {
    background-color: rgb(115, 178, 180);
    filter: saturate(0.95);
}
#itemBooksContainer {
    grid-column: 2/span 3;
    grid-row: 2;
}
#putBooks {
    display: flex;
    flex-wrap: wrap;
    background-color: rgb(17, 49, 49);
    padding-top: 20px;
    padding-bottom: 20px;
}
</style>