<template>
    <div id="app">
        <div id="left">
            <Sidebar :notes="notesToRender"/>
        </div>
        <div id="right">
            <Edit :header=editorHead :text="editorText" :index="editorId"/>
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
    import {inBrowser} from "vue-router/src/util/dom";

    class Note {
        id: number;
        header: string;
        text: string;
        dateAdded: Date;

        constructor(id: number, header: string, text: string, dateAdded: Date) {
            this.id = id;
            this.header = header;
            this.text = text;
            this.dateAdded = dateAdded;
        }
    }

    export default Vue.extend({
        name: 'App' as string,
        components: {
            Sidebar,
            Edit,
            Add
        },
        methods: {
            noteSelected(id: number, index: number): void {
                if (id == 0) {
                    this.editorId = 0;
                } else {
                    let note: Note = this.notes.find(o => o.id === id);
                    this.editorText = note.text;
                    this.editorHead = note.header;
                    this.editorId = note.id;
                    this.editorIndex = index;
                }
            },

            saveChanges(): void {
                let index: number = this.notes.findIndex(o => o.id === this.editorId);
                this.notes[index].text = (document.getElementById('textArea') as HTMLInputElement).value;
                this.notes[index].header = (document.getElementById('headerInput') as HTMLInputElement).value;
                this.editorHead = this.notes[index].header;
                localStorage.items = JSON.stringify(this.notes);
            },

            addNote(title: string, text: string): void {
                let id: number = 1;
                try {
                    id = this.notes[this.notes.length - 1].id + 1;
                } catch {
                }
                let newNote: Note = new Note(id, title, text, new Date());
                this.notes.push(newNote);
                localStorage.items = JSON.stringify(this.notes);
                this.searchChanged(new RegExp((document.getElementById('search') as HTMLInputElement).value, 'i'));
                this.noteSelected(id, this.notes.length - 1);
            },

            removeNote(id: Number): void {
                let index: number = this.notes.findIndex(o => o.id === id);
                if (id == this.editorId) {
                    this.editorId = 0;
                }
                this.notes.splice(index, 1);
                localStorage.items = JSON.stringify(this.notes);
                this.searchChanged(new RegExp((document.getElementById('search') as HTMLInputElement).value, 'i'));
            },

            searchChanged(searchQuery: RegExp): void {
                let newNotesToRender = [];
                for (let i = 0; i < this.notes.length; i++) {
                    if (searchQuery.test(this.notes[i].header)) {
                        newNotesToRender.push(this.notes[i]);
                    }
                }
                this.notesToRender = newNotesToRender;
            },

            sortChanged(type: string): void {
                switch (type) {
                    case 'asc': {
                        this.notesToRender.sort(function (a, b) {
                            let keyA = new Date(a.dateAdded),
                                keyB = new Date(b.dateAdded);
                            if (keyA < keyB) return -1;
                            if (keyA > keyB) return 1;
                            return 0;
                        });
                        break;
                    }
                    case 'desc': {
                        this.notesToRender.sort(function (a, b) {
                            let keyA = new Date(a.dateAdded),
                                keyB = new Date(b.dateAdded);
                            if (keyA < keyB) return 1;
                            if (keyA > keyB) return -1;
                            return 0;
                        });
                        break;
                    }
                    case 'name': {
                        this.notesToRender.sort(function (a, b) {
                            let keyA = a.header.toLowerCase(),
                                keyB = b.header.toLowerCase();
                            if (keyA < keyB) return -1;
                            if (keyA > keyB) return 1;
                            return 0;
                        });
                        break;
                    }
                }
            }

        },
        mounted() {
            try {
                this.notes = JSON.parse(localStorage.items);
            } catch (e) {
                localStorage.setItem('items', '');
            }
            this.notesToRender = this.notes;
        },
        data() {
            return {
                notes: [],
                editorHead: '',
                editorText: '',
                editorId: 0,
                editorIndex: -1,
                notesToRender: [],
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
