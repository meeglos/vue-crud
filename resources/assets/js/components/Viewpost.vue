<template id="post">
    <div>
        <h2>{{ post.name }}</h2>
        <b>Description: </b>
        <div>{{ post.description }}</div>
        <br/>
        <span class="glyphicon glyphicon-arrow-left" aria-hidden="true"></span>
        <router-link v-bind:to="'/'">Back to Post list</router-link>
    </div>
</template>

<script>
export default {
    data: function () {
        return {post: {name: '', description: ''}}
    },
    created: function(){
        let uri = 'http://vue-crud.local/api/'+this.$route.params.id;
        Axios.get(uri).then((response) => {
            this.post = response.data;
        });
    }
}
</script>
