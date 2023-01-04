<template lang="">
    <li>
        <div 
            style="display: inline-block"
            :class="{'fav':post.fav}"
        >{{ post.title }}</div> | 
        <button @click="handleClick(post)">Delete Post</button>
        <button @click="$emit('fav',post)">Fav Post</button>
    </li>
</template>
<script>
export default {
    name: "SinglePost",
    props: ["post"],
    methods: {
        handleClick(post){
            // console.log(post)
            this.$emit('delete',post)
        }
    }
    // props: {
    //     post: {
    //         type:Object,
    //         required:true
    //     }
    // }
}
</script>
<style scoped>
    .fav{
        color: green;
    }
</style>