<template>


  <v-row class="mt-7">

    <v-col cols="9 mx-auto" class="mb-0">
      <v-toolbar elevation="0" flat>
        <v-toolbar-title> User List </v-toolbar-title>
        <v-spacer></v-spacer>

        <v-dialog v-model="dialog" persistent max-width="400px">
          <template v-slot:activator="{ on, attrs }">
            <v-btn color="#005466" dark v-bind="attrs" v-on="on">
              Add new User
            </v-btn>
          </template>
          <v-card>
            <v-card-title>
              <span class="text-h5">User Profile</span>
            </v-card-title>
            <v-card-text>
              <v-container>
                <v-row>
                  <v-col cols="12">
                    <v-text-field hide-details label="Full Name*" required></v-text-field>
                  </v-col>
                  <v-col cols="12">
                    <v-text-field hide-details label="Username"></v-text-field>
                  </v-col>
                </v-row>
              </v-container>
            </v-card-text>
            <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn color="blue darken-1" text @click="dialog = false">
                Close
              </v-btn>
              <v-btn color="blue darken-1" text @click="dialog = false">
                Save
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-dialog>
      </v-toolbar>

      <v-divider></v-divider>

      <v-simple-table fixed-header color="purple lighten-5" class="pa-3">
        <template v-slot:default>
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
            <tr v-for="item in desserts" :key="item.name">

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
                <v-btn class="ml-2" fab dark x-small color="red darken-4">
                  <v-icon dark small>
                    mdi-delete
                  </v-icon>
                </v-btn>
              </td>

            </tr>

          </tbody>
        </template>
      </v-simple-table>
    </v-col>

  </v-row>

</template>

<script>
  export default {
    name: 'Home',

    data: () => {
      return {
        dialog: false,
        desserts: [{
            id: '1',
            avator: 'https://cdn.vuetifyjs.com/images/john.jpg',
            name: 'Frozen Yogurt',
            username: 'user1@gmail.com',
            calories: 159,
          },
          {
            id: '1',
            avator: 'https://cdn.vuetifyjs.com/images/john.jpg',
            name: 'Frozen Yogurt',
            username: 'user1@gmail.com',
            calories: 159,
          },
          {
            id: '1',
            avator: 'https://cdn.vuetifyjs.com/images/john.jpg',
            name: 'Frozen Yogurt',
            username: 'user1@gmail.com',
            calories: 159,
          }
        ]
      }
    }
  }
</script>