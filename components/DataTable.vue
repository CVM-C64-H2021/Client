<template>
    <div class="DataTable">

        <div>
            filtre: <input v-model="searchQuery">
        </div>

        <div>
            <table>
                <tr>
                    <th>Sensor id</th>
                    <th>Date</th>
                    <th>Type</th>
                    <th>Valeur</th>
                    <th>Alerte</th>
                    <th>Message</th>
                </tr>
                <tr v-for="(item,i) in filteredData" :key="i" @click="onItemSelected(item)">         <!-- Click sur sensor-->
                    <td>{{ item.idApp }}</td>
                    <td>{{ item.date }}</td>
                    <td>{{ item.type }}</td>
                    <td v-if="item.type == 'image'"><img :src="`data:image/png;base64, ${image(item)}`"/></td>
                    <td v-else>{{ item.valeur }}</td>
                    <td>{{ item.alerte }}</td>
                    <td>{{ item.messageAlerte }}</td>
                </tr>
            </table>
        </div>
    </div>
</template>

<script>
    export default {
        name: "DataTable",
        props: ['items'],
        methods: {
            onItemSelected(item) {
                this.$emit('onItemSelected', item)
            },
            image(item){
                return item.valeur.slice(2, -1)
            }
        },
        computed: {
            filteredData: function () {
            // Valeur des caractères recherchés
            const filterKey = this.searchQuery && this.searchQuery.toLowerCase()
            let data = this.items
            if (filterKey) {
                data = data.filter(function (row) {
                    return Object.keys(row).some(function (key) {
                        return String(row[key]).toLowerCase().indexOf(filterKey) > -1
                    })
                })
            }
            return data
            }
        },
        data(){
            return{
                searchQuery : ''
            }
        }
    }
</script>
