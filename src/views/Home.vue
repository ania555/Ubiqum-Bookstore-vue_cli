<template>
  <div class="home">
    <Modal v-if="isModalVisible" v-on:close="popClose" :myFruit="fruit" :modalBook="currentBook"/>
    <div class="myHeader" id="headerBackground">
      <div class="grid1">
        <img id="item2" alt="Vue logo" src="../assets/logo111-books.png">
        <h1 id="item1">UBIQUM BOOKSTORE</h1>
        <div id="itemSearch">
          <nav>
            <form class="form-inline">
              <input id="searchInput" class="form-control mr-sm-2" type="search" placeholder="Search" aria-label="Search" v-model="message" />
            </form>
          </nav>
        </div>
      </div>
    </div>
    <div class="myMain">
      <div class="grid1" id="myMain">
        <br><br>
        <div id="itemBooksContainer">                
                <div id="putBooks">
                  <div v-for="(book, index) in filteredBooks" :key="index">  
                    <div class="flip-card" >
                      <div class="flip-card-inner" >
                        <div class="flip-card-front">
                          <img :src="book.portada" alt="book cover">
                        </div>
                        <div class="flip-card-back">
                          <h5>{{ book.titulo }}</h5>
                          <p>{{ book.descripcion }}</p>
                          <input  value="More Info" id="myBtn" v-on:click="popUp(book.detalle)">                         
                        </div>
                      </div>
                    </div>
                    </div>
                  </div>             
            <br><br><br>
        </div>
      </div>
    </div>
    <!-- <div v-for="item in allBooks" :key="item.id" ></div>  -->
    <div class="myFooter">
      <div class="grid1">
        <footer id="itemFooter">2018 Bookstore All Rights Reserved</footer>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import Modal from '@/components/Modal.vue'

export default {
  name: 'home',
  // props: ["allBooks"],
  components: { 
    Modal,
  },
  data () {
    return {
      isModalVisible: false,
      currentBook: null,
      message: "",
      fruit: "Orange",
      allBooks: [],
    }
  },
  mounted(){
    console.log(this.$route.params.booksForHome)
    if(!this.$route.params.booksForHome){
      this.allBooks = this.$parent.myBooks
    } else {
      this.allBooks = this.$route.params.booksForHome
    }
  },
  computed: {
    filteredBooks() {
      // console.log(this.message);
        if (this.message == "") {
          return this.allBooks;
        }
        else if (this.message != "") {
          var selected = [];
          for (let i = 0; i < this.allBooks.length; i++) {
            if (this.allBooks[i].titulo.toLowerCase().indexOf(this.message.toLowerCase()) > -1 || this.allBooks[i].descripcion.toLowerCase().indexOf(this.message.toLowerCase()) > -1) {
              selected.push(this.allBooks[i]);
            } 
          }
          console.log(selected);
          return selected;     
        }
    }
  },
  methods: {
    popUp(item) {
      console.log("open");
      this.currentBook = item
      console.log(this.currentBook)
      console.log(this.isModalVisible)
      this.isModalVisible = true;
    },
    popClose() {
      console.log("close");
      this.isModalVisible = false;
    }
  }
}
</script>


<style scoped>
.grid1 {
    display: grid;
    grid-template-columns: 44px 120px auto 180px 120px 44px;
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
#mySearch:hover {
    background-color: cadetblue;
    color:white;  
}
#headerBackground {
    background-image: url(../assets/books.jpg);
    filter: saturate(0.9);
}
#myMain {
    background-color: rgb(115, 178, 180);
    filter: saturate(0.95);
}
#itemBooksContainer {
    grid-column: 3/span 2;
    grid-row: 2;
}
#putBooks {
    display: flex;
    flex-wrap: wrap;
    justify-items: center;
    background-color: rgb(17, 49, 49);
    padding-top: 0px;
    padding-bottom: 0px;
}
h5 {
    margin: 15px 15px 0px 15px;
    text-align: left;
   font-size: 18px;
}
p {
    margin: 0px 15px 0px 15px;
    font-size: 13px;
    text-align: left;
    font-stretch: ultra-condensed;
}
#myBtn {
    margin: 0px 0px 20px 0px;
    width: 70px;
    text-align: center;
    align-self: flex-end;
    background-color: white;
    color: rgb(35, 98, 100);
    font-size: 12px;
    font-weight: 600;
    padding: 3px;
    border-radius: 5px;
}
#myBtn:hover {
    text-decoration: none;
    background-color: darkorange;
    color: rgb(55, 118, 120);
    cursor: pointer;
}
img {
    height: 300px;
    width: 204px;
    border-style: solid;
    border-color: rgb(17, 49, 49);
    border-width: 3px;
}
.flip-card {
    background-color: transparent;
    width: 204px;
    height: 300px;
    perspective: 1000px;
}
.flip-card-inner {
    width: 204px;
    height: 300px;
    transition: transform 0.6s;
    transform-style: preserve-3d;
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
}
.flip-card:hover .flip-card-inner {
    transform: rotateY(180deg);
}
.flip-card-front,
.flip-card-back {
    position: absolute;
    width: 204px;
    height: 300px;
    backface-visibility: hidden;  
}
.flip-card-front {
    background-color: #bbb;
    color: black;
    z-index: 2;
}
.flip-card-back {
    background-color: rgb(55, 118, 120);
    color: white;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    transform: rotateY(180deg);
    z-index: 1;
    border-style: solid;
    border-color: rgb(17, 49, 49);
    border-width: 3px;
}
#itemFooter {
    grid-column: 1/span 6;
    grid-row: 3;
    background-color: rgb(55, 118, 120);
    padding: 30px;
    text-align: center;
    font-weight: bolder;
    color: black;
}
</style>
