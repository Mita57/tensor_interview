<template>
    <div id="sidebar">
        <button id="addNote" @click="showOverlay"> + Заметка</button>
        <input type="text" id="search" placeholder="Поиск" @input="searchChanged()">
        <div id="sort">
            Сортировка:
            <select name="sortBy" @change="sortChanged()" id="sortPicker">
                <option value="asc">По возрастанию даты</option>
                <option value="desc">По убыванию даты</option>
                <option value="name">По возрастанию заголовка</option>
                <option value="nameDesc">По убыванию заголовка</option>
            </select>
            <ul id="notes">
                <li v-for="(note, index) in notes" :id='"entry"+index' @mouseover="showDeleteButton(index)"
                    @mouseleave="hideDeleteButton(index)" @click="openInEditor(note.id, index)">
                    <h3>{{note.header}}</h3>
                    <img src="../assets/remove.png" :id='"deleteIcon"+index'
                         @click="removeNote(note.id, note.header, index)">
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
        props: {
            notes: Array,
        },
        data() {
            return {
                deleteCancelOpen: false,
                prevEdited: 0,
                prevStyle: '',
            }
        },
        methods: {
            showOverlay() {
                document.getElementById('addNoteDim').style.display = 'block';
            },

            showDeleteButton(id: number): void {
                let elementId: string = 'deleteIcon' + id;
                document.getElementById(elementId).style.display = 'block';
            },

            hideDeleteButton(id: number): void {
                let elementId: string = 'deleteIcon' + id;
                document.getElementById(elementId).style.display = 'none';
            },

            removeNote(id: number, text: string, index: number): void {
                let flag: boolean = confirm('Вы хотите удалить запись ' + text + '?');
                if (flag) {
                    this.$parent.removeNote(id);
                    this.deleteCancelOpen = true;
                    if (index == this.prevEdited) {
                        document.getElementById('entry' + index).style.backgroundColor = this.prevStyle;
                    }
                } else {
                }
            },

            openInEditor(id: number, index: number): void {

                if (!this.deleteCancelOpen) {
                    this.$parent.noteSelected(id, index);
                    if (this.prevStyle == '') {
                        document.getElementById('entry' + index).style.backgroundColor
                    }
                    document.getElementById('entry' + this.prevEdited).style.backgroundColor = this.prevStyle;
                    document.getElementById('entry' + index).style.backgroundColor = '#fff6cc';
                    this.prevEdited = index;

                } else {
                    this.deleteCancelOpen = false;
                }
            },

            searchChanged() {
                let searchQuery: RegExp = new RegExp((document.getElementById('search') as HTMLInputElement).value, 'i');
                this.$parent.searchChanged(searchQuery);
            },

            sortChanged() {
                this.$parent.sortChanged((document.getElementById('sortPicker') as HTMLSelectElement).value);
            }

        }
    })
</script>

<style scoped>

    #sidebar {
        height: 100%;
        width: 100%;
        font-family: 'Roboto', 'Avenir', Helvetica, Arial, sans-serif;
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
        font-family: 'Roboto', 'Avenir', Helvetica, Arial, sans-serif;
    }

    #search {
        width: 87%;
        height: 25px;
        border: dodgerblue 2px solid;
        padding: 4px;
        box-shadow: 0px 0px 6px 2px grey;
        font-family: 'Roboto', 'Avenir', Helvetica, Arial, sans-serif;
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

    li {
        transition: 0.1s;
    }

    li:hover {
        background-color: #d7efff;
        cursor: pointer;
    }

    li img {
        height: 30px;
        width: 30px;
        float: right;
        margin-top: -20px;
        margin-right: 5px;
        display: none;
    }


</style>
