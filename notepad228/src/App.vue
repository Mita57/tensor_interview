<template>
    <div id="app">
        <div id="left">
            <Sidebar :notes="notes"/>
        </div>
        <div id="right">
            <Edit/>
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
            cock()
        }
        ,
        data() {
            return {
                notes: [
                    {
                        id: 1,
                        header: 'Enter sandman',
                        text: 'Prodalis',
                        dateAdded: '23.01.2020',
                    },
                    {
                        id: 2,
                        header: 'Sad but true',
                        text: 'Heeey Im ur life sasok',
                        dateAdded: '21.01.2020',
                    },
                    {
                        id: 3,
                        header: 'Holier than thou',
                        text: 'You are',
                        dateAdded: '22.01.2020',
                    },
                    {
                        id: 4,
                        header: 'The unforgiven',
                        text: 'So I dub thee unforgiven',
                        dateAdded: '20.01.2020',
                    },
                    {
                        id: 5,
                        header: 'Anywhere I may roam',
                        text: 'Nowhere else to fucking roam, nothing else to fucking sing',
                        dateAdded: '23.01.2020',
                    }
                    ,
                    {
                        id: 2,
                        header: 'Sad but true',
                        text: 'Heeey Im ur life sasok',
                        dateAdded: '21.01.2020',
                    },
                    {
                        id: 3,
                        header: 'Holier than thou',
                        text: 'You are',
                        dateAdded: '22.01.2020',
                    },
                    {
                        id: 4,
                        header: 'The unforgiven',
                        text: 'So I dub thee unforgiven',
                        dateAdded: '20.01.2020',
                    },
                    {
                        id: 5,
                        header: 'Anywhere I may roam',
                        text: 'Nowhere else to fucking roam, nothing else to fucking sing',
                        dateAdded: '23.01.2020',
                    },
                    {
                        id: 2,
                        header: 'Sad but true',
                        text: 'Heeey Im ur life sasok',
                        dateAdded: '21.01.2020',
                    },
                    {
                        id: 3,
                        header: 'Holier than thou',
                        text: 'You are',
                        dateAdded: '22.01.2020',
                    },
                    {
                        id: 4,
                        header: 'The unforgiven',
                        text: 'So I dub thee unforgiven',
                        dateAdded: '20.01.2020',
                    },
                    {
                        id: 5,
                        header: 'Anywhere I may roam',
                        text: 'Nowhere else to fucking roam, nothing else to fucking sing',
                        dateAdded: '23.01.2020',
                    }
                    ,
                    {
                        id: 2,
                        header: 'Sad but true',
                        text: 'Heeey Im ur life sasok',
                        dateAdded: '21.01.2020',
                    },
                    {
                        id: 3,
                        header: 'Holier than thou',
                        text: 'You are',
                        dateAdded: '22.01.2020',
                    },
                    {
                        id: 4,
                        header: 'The unforgiven',
                        text: 'So I dub thee unforgiven',
                        dateAdded: '20.01.2020',
                    },
                    {
                        id: 5,
                        header: 'Anywhere I may roam',
                        text: 'Nowhere else to fucking roam, nothing else to fucking sing',
                        dateAdded: '23.01.2020',
                    }

                ],
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
