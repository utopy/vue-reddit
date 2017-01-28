<template>
  <div class="card">
    <div class="title">{{post.data.title}}</div>
    <span class="author">{{this.post.data.author}}</span>
  </div>
</template>
<script>
  export default {
    props: ['post']
    // here you define the attributes/props of the component, will be available via this.note
    // when using component you can use the prop externally via '<note :note"{title: 'hi', content: 'lorem'}" ></note>'
  }

</script>
<style>
  .card {
    margin-bottom: 5px;
    background-color: white;
    padding: 50px;
    border: 1px solid rgba(33, 33, 33, 0.19);
    border-bottom: 3px solid rgba(33, 33, 33, 0.19);
  }
  
  .card>.title {
    text-align: justify;
  }
  
  .card>.author {
    text-align: left;
    font-size: 12px;
    color: white;
    padding: 5px;
    width: auto;
    background: black;
    float: left
  }

</style>
