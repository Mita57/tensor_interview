<template>
    <div id="addNoteGUI">
        <div id="titleAndArea">
            <input type="text" placeholder="Название" id="addNoteTitle">
            <textarea name="addNoteTextArea" id="addNoteTextArea" placeholder="Содержание"></textarea>
        </div>
        <div id="addNoteButtons">
            <button id="addNoteCancel" @click="hideAddOverlay()">Отмена</button>
            <button id="addNoteAdd">Добавить</button>
        </div>
    </div>
</template>

<script lang="ts">
    import Vue from 'vue'

    export default Vue.extend({
        name: 'Add' as string,
        data() {
            return {

            }
        },
        methods: {
            hideAddOverlay() {
                document.getElementById('addNoteDim').style.display = 'None';
            }
        }
    })
</script>

<style scoped>
    #addNoteGUI {
        width: 100%;
        height: 100%;
    }

    #titleAndArea {
        width: 100%;
        height: 90%;
        display: grid;
        grid-template-columns: 2% 96% 4%;
        grid-template-rows: 2% 5% 2% 90%;
    }

    #addNoteButtons {
        width: 100%;
        height: 10%;
        display: grid;
        grid-template-columns: 50% 23% 2% 23% 2%;
        grid-template-rows: 5% 80% 10%;
    }

    #addNoteTitle {
        grid-row: 2;
        grid-column: 2;
        box-shadow: 0px 0px 8px 2px darkgrey;
        padding: 10px;
        font-size: 16pt;
        font-family: 'Roboto', 'Avenir', Helvetica, Arial, sans-serif;
        border: 0;
    }

    #addNoteTextArea {
        grid-row: 4;
        grid-column: 2;
        box-shadow: 0px 0px 8px 2px darkgrey;
        padding: 10px;
        font-size: 16pt;
        font-family: 'Roboto', 'Avenir', Helvetica, Arial, sans-serif;
        border: 0;
    }

    #addNoteCancel {
        grid-column: 2;
        grid-row: 2;
        background-color: #eeeeee;
        color: dodgerblue;
        border: 1px solid grey;
    }

    #addNoteAdd {
        grid-column: 4;
        grid-row: 2;
        background-color: dodgerblue;
    }

    button {
        font-size: 16pt;
        color: white;
        border: 0;
        transition: 0.3s;
        font-family: 'Roboto', 'Avenir', Helvetica, Arial, sans-serif;
        border-radius: 3px;
    }

    #addNoteAdd:hover {
        background-color: #3da4ff;
        cursor: pointer;
    }

    #addNoteCancel:hover {
        background-color: lightgray;
        cursor: pointer;
    }

</style>
