<template>
    <div id="addNoteGUI">
        <div id="titleAndArea">
            <input type="text" placeholder="Название"  id="addNoteTitle" @input="checkInputs()">
            <textarea name="addNoteTextArea"  id="addNoteTextArea" placeholder="Содержание"
                      @input="checkInputs()"></textarea>
        </div>
        <div id="addNoteButtons">
            <button id="addNoteCancel" @click="hideAddOverlay()">Отмена</button>
            <button id="addNoteAdd" @click="addNote()" disabled>Добавить</button>
        </div>
    </div>
</template>

<script lang="ts">
    import Vue from 'vue'

    export default Vue.extend({
        name: 'Add' as string,
        data() {
            return {}
        },
        methods: {
            hideAddOverlay() {
                document.getElementById('addNoteDim').style.display = 'None';
                (document.getElementById('addNoteTitle') as HTMLInputElement).value = '';
                (document.getElementById('addNoteTextArea') as HTMLInputElement).value = '';
            },

            addNote() {
            },

            checkInputs() {
                let titleFlag: boolean = false;
                let textFlag: boolean = false;
                if ((document.getElementById('addNoteTitle') as HTMLInputElement).value) {
                    titleFlag = true;
                } else {
                    titleFlag = false;
                }
                if ((document.getElementById('addNoteTextArea') as HTMLInputElement).value) {
                    textFlag = true;
                } else {
                    textFlag = false;
                }
                if (titleFlag && textFlag) {
                    (document.getElementById('addNoteAdd') as HTMLButtonElement).disabled = false;
                } else {
                    (document.getElementById('addNoteAdd') as HTMLButtonElement).disabled = true;
                }
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
    }

    #addNoteAdd:enabled {
        background-color: dodgerblue;
        cursor: pointer;
    }

    #addNoteAdd:disabled {
        background-color: #adc2e2;
        color: gray;
        cursor: default;
    }

    #addNoteAdd:disabled:hover {
        background-color: #adc2e2;
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
    }

    #addNoteCancel:hover {
        background-color: lightgray;
        cursor: pointer;
    }


</style>
