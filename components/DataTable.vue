<template>
    <div class="DataTable">
        <table>
        <tr>
            <th>Sensor id</th>
            <th>Date</th>
            <th>Type</th>
            <th>Valeur</th>
            <th>Alerte</th>
            <th>Message</th>
        </tr>
        <tr v-for="item in items" :key="item.id" @click="onItemSelected(item)">{{item}}>          <!-- Click sur sensor-->
            <td>{{ item.id }}</td>
            <td>{{ item.date }}</td>
            <td>{{ item.type }}</td>
            <td>{{ item.valeur }}</td>
            <td>{{ item.alerte }}</td>
            <td>{{ item.messageAlerte }}</td>
        </tr>
    </table>
    </div>
</template>

<script>
    export default {
        name: "DataTable",
        props: ['items'],
        data() {
            return {
                
                selectedItem: null
            }
        },
        methods: {
            onItemSelected(item) {
                this.selectedItem = item;
            },
            mounted() {
            this.axios.get('http://localhost:3000/alerts').then(res => {
            this.items = res.data
        })
    }
        }
    }
</script>