<template>
    <div class="movies-page">
        <Navbar />
        <div class="page-content">
            <div class="container">
                <input 
                    type="text" 
                    placeholder="Search for a movie" 
                    class="form-control my-5 bg-dark text-light" 
                    v-model="movieToSearch"
                    @keydown="handleKeyDown"
                />

                <div class="items-found-container">
                    <span>{{this.totalItems}} items founded:</span>
                    <div class="row">
                        
                            <div class="card bg-dark col-lg-3 col-md-6" v-for="item in items" :key="item.id">
                                <div class="card-body">
                                    <h5 class="card-title">{{item.title}}</h5>
                                    <p class="card-text">Category: {{item.type}}</p>
                                    <div class="item-ranking my-2">{{item.score}}</div>
                                    <a href="#" class="btn btn-primary">More info</a>
                                </div>
                            </div>
                        
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    
    import axios from 'axios';
    import Navbar from '~/components/Navbar.vue';

    export default{
        name:"Movies",
        components:{
            Navbar,
            Navbar
        },
        data(){
            return{
                movieToSearch:'',
                totalItems: 0,
                items:[]
            }
        },
        methods:{
            async findMovie(movie){
                const options = {
                    method: 'GET',
                    url: 'https://mdblist.p.rapidapi.com/',
                    params: {s: movie},
                    headers: {
                        'X-RapidAPI-Key': '4bf4e1d639mshb07e87486579702p17a898jsnf75a5eb31167',
                        'X-RapidAPI-Host': 'mdblist.p.rapidapi.com'
                    }
                };

                const response = await axios.request(options);
                this.items = response.data.search;
                console.log(this.items);
                this.totalItems = response.data.total;
            },
            handleKeyDown(event){
                if(event.key == "Enter"){
                    this.findMovie(this.movieToSearch);
                }
            }
        }
    }
</script>

<style>
    body{
        background-color: #293462;
        color: white;
     }

     .item-ranking{
        display: block;
        width: 10%;
        text-align: center;
        border-radius: 3px;
     }
</style>
