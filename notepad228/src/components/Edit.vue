<template>
    <div id="edit">
        <div id="buttons">
            <button id="saveBtn" v-if="editMode" @click="saveChanges()">Сохранить</button>
            <button id="editBtn" v-else @click="enableChagnes()">Редактировать</button>
            <button id="deleteBtn">Удалить</button>
            <button id="cancelBtn" v-if="editMode" @click="cancelChanges()">Отмена</button>
        </div>
        <div id="content">
            <input id="headerInput" type="text" readonly :value=header>
            <textarea id="textArea" readonly> {{text}} </textarea>
        </div>
    </div>
</template>

<script lang="ts">
    import Vue from 'vue'

    export default Vue.extend({
        name: 'Edit' as string,
        data() {
            return {
                editMode: false,
                initHeader:'',
                initText:'',
            }
        },
        props: {
            noteId: Number,
            header: String,
            text: String,
            id: Number
        },
        methods: {
            enableChagnes() {
                (document.getElementById('headerInput') as HTMLInputElement).readOnly = false;
                (document.getElementById('textArea') as HTMLInputElement).readOnly = false;
                this.editMode = true;
                this.initHeader = (document.getElementById('headerInput') as HTMLInputElement).value;
                this.initText = (document.getElementById('textArea') as HTMLInputElement).value;
            },

            saveChanges() {
                alert('cock');
            },

            cancelChanges() {
                let result: boolean = window.confirm("Вы хотите отменить измененеия?");
                if(result) {
                    (document.getElementById('headerInput') as HTMLInputElement).readOnly = true;
                    (document.getElementById('textArea') as HTMLInputElement).readOnly = true;
                    (document.getElementById('headerInput') as HTMLInputElement).value = this.initHeader ;
                    (document.getElementById('textArea') as HTMLInputElement).value = this.initText;
                    this.editMode = false;
                }

            }
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
        grid-template-columns: 25% 20% 10% 20% 20% 5%;
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

    #saveBtn {
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

    #cancelBtn {
        grid-column: 5;
        grid-row: 1;
    }


</style>
