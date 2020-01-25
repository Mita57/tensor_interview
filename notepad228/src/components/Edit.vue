<template>
    <div id="edit">
        <div id="buttons">
            <button id="editBtn">Редактировать</button>
            <button id="deleteBtn">Удалить</button>
        </div>
        <div id="content">
            <input id="headerInput" type="text">
            <textarea id="textArea"> </textarea>
        </div>
    </div>
</template>

<script lang="ts">
    import Vue from 'vue'

    export default Vue.extend({
        name: 'Edit' as string,
        data() {
            return {}
        },
        props: {
            noteId: Number
        },
        methods: {

        }
    })
</script>

<style scoped>

    #edit {
        height: 100%;
        width: 100%;
    }

    #buttons {
        height: 8%;
        width: 100%;
        background-color: dodgerblue;
        display: grid;
        grid-template-columns: 25% 20% 10% 20% 25%;
    }

    #content {
        height: 92%;
        width: 100%;
        background-color: #eeeeee;
        box-shadow: inset 13px 13px 9px -7px grey;
        display: grid;
        grid-template-columns: 2% 96% 2%;
        grid-template-rows: 3% 5% 2% 87% 3%;
    }

    button {
        font-size: 16pt;
        background-color: dodgerblue;
        color: white;
        border: 0;
        transition: 0.3s;
        font-family: 'Roboto' ,'Avenir', Helvetica, Arial, sans-serif;
    }

    button:hover {
        background-color: #3da4ff;
        cursor: pointer;
    }

    #editBtn {
        grid-column: 2;
        grid-row: 1;
    }

    #deleteBtn {
        grid-column: 4;
        grid-row: 1;
    }

    #headerInput {
        grid-column: 2;
        grid-row: 2;
        border: 0;
        box-shadow: 0px 0px 8px 2px darkgrey;
        font-size: 16pt;
        padding: 10px;
        font-family: 'Roboto' ,'Avenir', Helvetica, Arial, sans-serif;
        font-weight: bold;
    }

    #textArea {
        grid-column: 2;
        grid-row: 4;
        border: 0;
        box-shadow: 0px 0px 8px 2px darkgrey;
        font-size: 16pt;
        padding: 10px;
        font-family: 'Roboto' ,'Avenir', Helvetica, Arial, sans-serif;
    }


</style>
