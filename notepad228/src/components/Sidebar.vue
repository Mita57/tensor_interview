<template>
    <div class="sidebar">
        <button id="addNote"> + Заметка</button>
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
                    }

                ],
            }
        },
    })
</script>

<style scoped>
    #addNote {
        width: 90%;
        margin: 10px;
        height: 40px;
        font-size: 16pt;
        background-color: dodgerblue;
        color: white;
        border: 0;
        box-shadow: 0px 0px 6px 2px grey;
    }

    #search {
        width: 89%;
        height: 30px;
        border: dodgerblue 2px solid;
        padding: 4px;
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
    #notes li h3,p{
      padding: 0px;
      margin: 7px;
    }

</style>
