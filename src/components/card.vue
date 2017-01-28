<template>
  <div class="card">
    <div class="card-content">
      <div class="title">{{post.data.title}}</div>
      <span class="author">{{post.data.author}}</span>
      <span class="score">{{post.data.score}}</span>
    </div>
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
  
  .card .card-content >.title {
    text-align: left
  }
  
  .card .card-content >.author {
    text-align: left;
    font-size: 12px;
    color: white;
    padding: 5px;
    width: auto;
    background: black;
    float: left
  }

  .card .card-content >.score{
    text-align: left;
    font-size: 12px;
    color: #4A354E;
    float: left;
    margin-left: 20px;
    padding-top: 6px;
  }

</style>
