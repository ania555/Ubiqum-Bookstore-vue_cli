<template>
  <div class="myHeader" id="headerBackground">
    <div class="grid1">
      <img id="item2" alt="Vue logo" src="../assets/logo111-books.png">
      <h1 id="item1">BOOKSTORE</h1>
      <div id="itemSearch">
        <nav>
          <form class="form-inline">
            <input id="searchInput" class="form-control mr-sm-2" type="search" placeholder="Search" aria-label="Search"  />
            <input type="button" class="btn my-2 my-sm-0" value="Search" id="mySearch" @click="filterBooks"/>
          </form>
        </nav>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'myHeader',
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
#item1 {
    grid-column: 3;
    grid-row: 1;
    margin: 0;
    padding: 45px;
    color: white;
    font-size: 50px;
    font-weight: 1000;
}
#item2 {
    grid-column: 2;
    grid-row: 1;
    height: 100px;
    width: 115px;
    margin-top: 25px;
    border-color: transparent;
    border-radius: 10px;
    filter: opacity(0.8)
}
#itemSearch {
    grid-column: 4;
    grid-row: 1;
    margin-top: 55px; 
}
#mySearch {
    background-color: white;
    color: cadetblue;
    font-weight: 600;
    border-style: solid;
    border-color: cadetblue;
}
#mySearch:hover {
    background-color: cadetblue;
    color:white;  
}
#headerBackground {
    background-image: url(../assets/books.jpg);
    filter: saturate(0.9);
}
</style>
