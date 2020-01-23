<template>
    <div id="app">
        <div id="left">
            <Sidebar>
            </Sidebar>
        </div>
        <div id="right">
            <Edit>
            </Edit>
        </div>
    </div>
</template>

<script lang="ts">
    import {Component, Vue} from 'vue-property-decorator';
    import Sidebar from './components/Sidebar.vue';
    import Edit from "@/components/Edit.vue";

    @Component({
        components: {
            Sidebar,
            Edit
        },
    })
    export default class App extends Vue {

    }
</script>

<style>
    html, body {
        height: 100%;
        margin: 0;
    }

    #app {
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        height: 100%;
    }

    #left {
        float: left;
        height: 100%;
        width: 20%;
        background-color: white;
        overflow-y: scroll;
    }

    #right {
        float: right;
        height: 100%;
        width: 80%;
        background-color: #eeeeee;
        box-shadow: inset 13px 0 9px -7px grey;
    }
</style>
