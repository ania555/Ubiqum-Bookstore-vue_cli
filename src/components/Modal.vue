<template>
  <!-- <div class="modal-wrapper"> -->
  <div id="myModal" class="myBookModal">
    <!-- <div > -->
      <!-- Modal content -->
      <div class="myModal-content">
        <span class="close" v-on:click="$emit('close')">&times;</span>
        <img :src="modalBook" alt="magnified book cover">
        
      </div>
    <!-- </div> -->
  </div>
</template>

<script>
    // @ is an alias to /src
    
export default {
  name: 'Modal',
  props:["myFruit", "modalBook"],
  data () {
    return {
    }
  },   
}

</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
 img {
 height: 550px;
 width: 530px;
 
}
/* .modal-wrapper{
  height: 100vh;
  width: 100vh;

} */
.myBookModal {
    position: fixed;  /*Stay in place */
    z-index: 1;  /*Sit on top */
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;
    width: 100%; /* Full width */
    height: 100%; /* Full height */
    overflow: auto;                 
    /*  background-color: red; Fallback color */
    background-color: rgba(0, 0, 0, 0.8); /* Black w/ opacity */
}
/* Modal Content/Box */
.myModal-content {
    display: flex;
    flex-direction: column;
    align-items: center;
    
    background-color :rgb(20, 20, 20);
    margin: 1% auto; /* 15% from the top and centered */
    padding: 0px;
    box-shadow: 2px 2px 20px 1px;
    height: 93%;
    width: 50%; /* Could be more or less, depending on screen size */
}
/* The Close Button */
.close {
    color: #aaa;
    align-self: flex-end;
    font-size: 28px;
    font-weight: bold;
}
.close:hover,
.close:focus {
    color: black;
    text-decoration: none;
    cursor: pointer;
}
</style>