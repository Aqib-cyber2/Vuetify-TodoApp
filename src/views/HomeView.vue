<template>


  <v-row class="mt-7">

    <v-col cols="9 mx-auto" class="mb-0">
      <v-toolbar elevation="0" flat>

        <v-toolbar-title> User List </v-toolbar-title>

        <v-spacer></v-spacer>

        <todo-from @submittedData="submittedData"></todo-from>

      </v-toolbar>

      <v-divider></v-divider>

      <v-simple-table fixed-header color="purple lighten-5" class="pa-3">

        <thead>
          <tr>
            <th>#</th>
            <th>Avator</th>
            <th>Full Name</th>
            <th>
              Username
            </th>
            <th>
              Action
            </th>
          </tr>
        </thead>

        <tbody>
          <tr v-for="item in fetchData" :key="item.id">

            <td>{{ item.id }}</td>

            <td>
              <v-avatar size="30">
                <img v-bind:src="item.avator" alt="user avator">
              </v-avatar>
            </td>

            <td>{{ item.name }}</td>

            <td>{{ item.username }}</td>

            <td>
              <v-btn fab dark x-small outlined color="blue darken-1">
                <v-icon dark small>
                  mdi-account-edit
                </v-icon>
              </v-btn>
              <v-btn @click="deleteUser(item.id)" class="ml-2" fab dark x-small color="red darken-4">
                <v-icon dark small>
                  mdi-delete
                </v-icon>
              </v-btn>
            </td>

          </tr>

        </tbody>

      </v-simple-table>
    </v-col>

  </v-row>

</template>

<script>
  import TodoFrom from '../components/TodoFrom.vue'
  export default {
    name: 'Home',

    components: {
      TodoFrom
    },

    data: () => {
      return {
        desserts: [{
            id: '1',
            avator: 'https://cdn.vuetifyjs.com/images/john.jpg',
            name: 'Frozen Yogurt',
            username: 'user1@gmail.com',
          },
          {
            id: '2',
            avator: 'https://cdn.vuetifyjs.com/images/john.jpg',
            name: 'Frozen Yogurt',
            username: 'user1@gmail.com',
          },
          {
            id: '3',
            avator: 'https://cdn.vuetifyjs.com/images/john.jpg',
            name: 'Frozen Yogurt',
            username: 'user1@gmail.com',
          }
        ]

      }
    },

    methods:{
      submittedData(user){
        this.desserts.push(user)
        console.log(this.desserts)
      },

      deleteUser(id){
        let item = this.desserts.filter(user=> user.id !== id)
        this.desserts = item;
      }
    },

    computed: {
      fetchData(){
        return this.desserts;
      }
    }

  }
</script>