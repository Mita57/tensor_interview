<template>
    <div id="app">
        <div id="left">
            <Sidebar :notes="notes" />
        </div>
        <div id="right">
            <Edit :header=editorHead :text=editorText :id="editorId"/>
        </div>
        <div id="addNoteDim">
            <div id="addNoteDiv">
                <Add/>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
    import {Vue} from 'vue-property-decorator';
    import Sidebar from './components/Sidebar.vue';
    import Edit from "@/components/Edit.vue";
    import Add from "@/components/Add.vue"

    export default Vue.extend({
        name: 'App' as string,
        components: {
            Sidebar,
            Edit,
            Add
        },
        methods: {
            noteSelected(id:number) {
                let note:object = this.notes[id];
                this.editorText = note.text;
                this.editorHead = note.header;
                this.editorId = note.id;
            }
        },
        mounted() {
            this.notes = JSON.parse(localStorage.items);
        },
        data() {
            return {
                notes: [],
                editorHead: '',
                editorText: '',
                editorId: 0
            }
        },
    })
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
        height: 100%;
        font-family: 'Roboto', 'Avenir', Helvetica, Arial, sans-serif;
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
    }

    ::-webkit-scrollbar {
        width: 6px;
        background-color: #F5F5F5;
    }

    ::-webkit-scrollbar-thumb {
        box-shadow: inset 0 0 5px grey;
        background: dodgerblue;
    }

    #addNoteDim {
        position: absolute;
        background-color: rgba(0, 0, 0, 0.8);
        width: 100%;
        height: 100%;
        display: none;
    }

    #addNoteDiv {
        width: 80%;
        height: 90%;
        margin-left: 10%;
        margin-top: 2.5%;
        background-color: #eeeeee;
        opacity: 1;
    }

</style>
