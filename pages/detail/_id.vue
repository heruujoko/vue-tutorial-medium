<template>
    <div>
        <h1>Halaman Detail</h1>
        <p><b>{{ title }}</b></p>
        <p>{{ body }}</p>

        <br />
        <button @click="goBack">Kembali</button>
    </div>
</template>

<script>
    import axios from 'axios';

    function getData() {
        axios.get('https://jsonplaceholder.typicode.com/posts/'+this.$route.params.id).then(res => {
            this.body = res.data.body;
            this.title = res.data.title;
        });
    }

    function goBack() {
        this.$router.go(-1);
    }

    export default {
        name: 'list',
        data() {
            return {
                title: "",
                body: ""
            }
        },
        methods: {
            getData,
            goBack
        },
        mounted() {
            this.getData();
        }
    }
</script>