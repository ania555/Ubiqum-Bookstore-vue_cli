<template>
  <div class="BookList">
    <h1 >This is a book list</h1>
    <div v-for="book in listBooks">
      <ul>
        <li>{{ book.titulo }}</li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'BookList',
  data(){
    return{
      listBooks: this.$route.params.booksForList
    }
  }
}

</script>
