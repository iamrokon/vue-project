<template>
    <!-- <h1>{{ message }}</h1> -->
    <button @click="addPost">Add Post</button>
    <!-- fav_count: {{favCount}}
    unfav_count: {{unFavCount}} -->
    <h1>All</h1>
    <ul>
        <!-- <abc></abc> -->
        <!-- <Number></Number>
        <Number/>
        <number></number> -->
        <!-- <number/>
        <school-name/>
        <SchoolName></SchoolName>
        <SlotComponent></SlotComponent> -->
        <single-post 
            style="margin-bottom: 10px"
            v-for="(post, index) in posts" 
            :key="index"
            :post="post"
            @delete="handleDelete"
            @fav="handleFav"
        />

    </ul>
    <br>
    <h1>Favs</h1>
    <ul>
        <single-post 
            style="margin-bottom: 10px"
            v-for="(post, index) in favs" 
            :key="index"
            :post="post"
            @delete="handleDelete"
            @fav="handleFav"
        /> 
    </ul>
    <br>
    <h1>unFavs</h1>
    <ul>
        <single-post 
            style="margin-bottom: 10px"
            v-for="(post, index) in unFavs" 
            :key="index"
            :post="post"
            @delete="handleDelete"
            @fav="handleFav"
        /> 
    </ul>
</template>
<script>
import Number from '../components/Number.vue'
import SchoolName from '../components/SchoolName.vue'
import SlotComponent from '../components/SlotComponent.vue'
import SinglePost from '../components/SinglePost.vue'
export default{
    name: "HomePage",
    components:{SinglePost, SchoolName, Number, SlotComponent},
    // components:{abc: Number},
    data() {
        return {
            message: 'Hello Bangladesh',
            posts: [
                {
                    id:1,
                    title:"Post 1",
                    fav: true
                },
                {
                    id:2,
                    title:"Post 2",
                    fav: false
                },
                {
                    id:3,
                    title:"Post 3",
                    fav: true
                },
            ]
        
        }
    },
    computed: {
        favs(){
            return this.posts.filter(post => post.fav)
        },
        unFavs(){
            return this.posts.filter(post => !post.fav)
        }
    },
    methods: {
        handleDelete(post){
            this.posts = this.posts.filter(p => p.id !=post.id)
            // console.log(this.posts)
        },
        addPost(){
            this.posts.push({
                id: this.posts.length+1,
                title: `Post ${this.posts.length+1}`
            })
        },
        handleFav(post){
            // console.log(post)
            this.posts = this.posts.map(p => {
                if(p.id == post.id){
                    p.fav = !p.fav
                }
                return p
            })
        }
    }










    // beforeCreate() {
    //     console.log('HomePage beforeCreate')
    // },
    // created() {
    //     console.log('HomePage created')
    // },
    // beforeMount() {
    //     console.log('HomePage beforeMount')
    // },
    // mounted() {
    //     console.log('HomePage mounted')
    // },
    // beforeUnmount() {
    //     console.log('HomePage beforeUnmount')
    // },
    // unmounted() {
    //     console.log('HomePage unmounted')
    // },
}
</script>

<style scoped>
h1{
    color: green;
}
</style>