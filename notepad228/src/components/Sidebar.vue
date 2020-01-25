<template>
    <div id="sidebar">
        <button id="addNote" @click="showOverlay"> + Заметка</button>
        <input type="text" id="search" placeholder="Поиск">
        <div id="sort">
            Сортировать по:
            <select name="sortBy">
                <option value="asc">По возрастанию даты</option>
                <option value="desv">По убыванию даты</option>
            </select>
            <ul id="notes">
                <li v-for="note in notes">
                    <h3>{{note.header}}</h3>
                    <p>{{note.text}}</p>
                </li>
            </ul>
        </div>
    </div>
</template>

<script lang="ts">
    import Vue from 'vue'

    export default Vue.extend({
        name: 'Sidebar' as string,
        data() {
            return {

            }
        },
        props: {
            notes: Array
        }
        ,
        methods: {
            showOverlay() {
                document.getElementById('addNoteDim').style.display = 'block';
            }
        }
    })
</script>

<style scoped>

    #sidebar {
        height: 100%;
        width: 100%;
        font-family: 'Roboto' ,'Avenir', Helvetica, Arial, sans-serif;
    }

    #addNote {
        width: 90%;
        margin: 10px;
        height: 40px;
        font-size: 16pt;
        background-color: dodgerblue;
        color: white;
        border: 0;
        box-shadow: 0px 0px 6px 2px grey;
        transition: 0.3s;
        font-family: 'Roboto' ,'Avenir', Helvetica, Arial, sans-serif;
    }

    #search {
        width: 87%;
        height: 25px;
        border: dodgerblue 2px solid;
        padding: 4px;
        box-shadow: 0px 0px 6px 2px grey;
        font-family: 'Roboto' ,'Avenir', Helvetica, Arial, sans-serif;
    }

    #addNote:hover {
        background-color: #3da4ff;
        cursor: pointer;
    }

    #sort {
        margin-top: 10px;
        width: 100%;
    }

    #notes {
        text-align: left;
        list-style-type: none;
        padding: 0;
    }

    #notes li {
        padding: 0px;
        margin: 0px;
        border: 1px grey solid;
    }

    #notes li h3, p {
        padding: 0px;
        margin: 7px;
        overflow: hidden;
        white-space: nowrap;
        text-overflow: ellipsis;
    }


</style>
