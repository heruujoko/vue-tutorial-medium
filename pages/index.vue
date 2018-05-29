<template>
    <div>
        <h1>Halaman List</h1>
        <table>
            <thead>
                <tr>
                    <td>Judul</td>
                    <td>Aksi</td>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(l,key) in list" :key="key">
                    <td>{{ l.title }}</td>
                    <td>
                        <button @click="gotoDetail(l.id)">Detail</button>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
    import axios from 'axios';

    function getData() {
        axios.get('https://jsonplaceholder.typicode.com/posts').then(res => {
            this.list = res.data;
        });
    }

    function gotoDetail(id) {
        this.$router.push('detail/'+id);
    }

    export default {
        name: 'list',
        data() {
            return {
                list: []
            }
        },
        methods: {
            getData,
            gotoDetail
        },
        mounted() {
            this.getData()
        }
    }
</script>