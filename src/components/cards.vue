<template>
    <div class="card-container">
        <card :post="post" class="card" v-for="post in posts"></card>
    </div>
</template>
<script>
    import Card from "./card"
    export default{
        data(){
            return {
                posts: []
            }
        },
        mounted(){
            console.log("ciao")
            let request = new XMLHttpRequest;
            request.open("GET", "https://www.reddit.com/r/science/new.json", true);
            request.onload = ()=>{
                if(request.status >= 200 && request.status < 400){
                    let data = JSON.parse(request.responseText);
                    data = data.data.children
                    console.log(data.length)
                    for(let i = 0; i < data.length; i++){
                        this.posts.push(data[i])
                    }
                    console.log("---")
                    console.log(this.posts)
                } else {
                    console.log("error")
                }
            }
            request.onerror = ()=>{
                console.log("err")
            }

            request.send()
        }
    }
</script>
<style>

.card-container{
    width: 400px;
    margin: auto;
}
.card{
    margin-bottom: 5px;
    background-color: white;
    padding: 50px;
    border: 1px solid rgba(33, 33, 33, 0.19);
    border-bottom: 3px solid rgba(33, 33, 33, 0.19);
}

.card > .title{
    text-align: justify;

}

.card > .author{
    text-align: left;
    font-size: 12px;
    color: white;
    padding: 5px;
    width: auto;
    background: black;
    float: left
}
</style>