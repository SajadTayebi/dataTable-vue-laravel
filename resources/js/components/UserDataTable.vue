<template>
    <v-card>
        <v-card-title>
            Users
            <v-spacer></v-spacer>
            <v-text-field
                v-model="search"
                append-icon="mdi-magnify"
                label="Search"
                single-line
                hide-details
            ></v-text-field>
        </v-card-title>
        <v-data-table
            :headers="headers"
            :items="users"
            :search="search"
        ></v-data-table>
    </v-card>
</template>

<script>
export default {
    name: "UserDataTable"
}

</script>
<script>
export default {
    data () {
        return {
            search: '',
            headers: [
                {
                    text: 'ID',
                    align: 'start',
                    value: 'id',
                },
                { text: 'Name', value: 'name' },
                { text: 'Email', value: 'email' },
                { text: 'Joined At', value: 'created_at' },
            ],
            users: []
        }
    },
    methods: {
        fatchData()
        {
            axios.get('api/users').then(res => {
                this.users = res.data
            }).catch(err => {
                console.log(err)
            })
        }
    },
    created(){
        this.fatchData()
    }
}
</script>
<style scoped>

</style>
