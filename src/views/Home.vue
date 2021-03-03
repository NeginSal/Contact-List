<template>
  <div class="list">
  <h1 class="purple--text mx-5 my-5">Contact List</h1>
  <v-btn to="../Newpage" v-bind="attrs" v-on="on" class=" my-5 mx-5" absolute centered right  top dark color="purple">
   Me
  </v-btn>
  <v-container class="mx-5 my-5">
  <v-data-table :headers="headers" :items="nums">
    <template v-slot:top>
      <v-toolbar flat>
        <v-toolbar-title class="blue--text">My Contact</v-toolbar-title>
<!--Newcontact-->
        <v-spacer></v-spacer>
        <v-dialog v-model="dialog" max-width="500px">
          <template v-slot:activator="{ on, attrs }">
            <v-btn color="primary" dark class="mb-2" v-bind="attrs" v-on="on">
              New Contact
            </v-btn>
          </template>
          <v-card>
            <v-card-title>
              <span class="headline blue--text">Add New Contact!</span>
            </v-card-title>

            <v-card-text>
              <v-container>
                <v-row>
                  <v-col cols="12" sm="6" md="4">
                    <v-text-field v-model="editedItem.name" label="Name"></v-text-field>
                  </v-col>
                  <v-col cols="12" sm="6" md="4">
                    <v-text-field v-model="editedItem.phones" label="number"></v-text-field>
                  </v-col>
                </v-row>
              </v-container>
            </v-card-text>

            <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn color="blue darken-1" text @click="close">Cancel</v-btn>
              <v-btn color="blue darken-1" text @click="save">Save</v-btn>
            </v-card-actions>
          </v-card>
        </v-dialog>
<!--newcontact-->
<!--Delete icon modal-->
        <v-dialog v-model="dialogDelete" max-width="550px">
          <v-card>
            <v-card-title class=" headline">Are you sure you want to delete this contact?</v-card-title>
            <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn color="red" text @click="closeDelete">Cancel</v-btn>
              <v-btn color="red" text @click="deleteItemConfirm">OK</v-btn>
              <v-spacer></v-spacer>
            </v-card-actions>
          </v-card>
        </v-dialog>
<!--Delete icon modal-->
      </v-toolbar>
    </template>
<!--Delete & Edit icon-->   
    <template v-slot:[`item.actions`]="{ item }">
      <v-icon small class="mr-2" @click="editItem(item)" color="green">
        mdi-account-edit
      </v-icon>
      <v-icon small @click="deleteItem(item)" color="red">
        mdi-delete
      </v-icon>
    </template>

  </v-data-table>
  </v-container>
  </div>
</template>


<script>
  export default {
    data: () => ({
      dialog: false,
      dialogDelete: false,
      headers: [
        {
          text: 'Name',
          align: 'start',
          sortable: false,
          value: 'name',
        },
        { text: 'PhoneNumber', value: 'phones' },
        { text: 'Edit/Delete', value: 'actions', sortable: false },
      ],
      nums: [],
      editedIndex: -1,
      editedItem: {
        name: '',
        phones: 0,
      },
      defaultItem: {
        name: '',
        phones: 0,  
      },
    }),

    computed: {
      formTitle () {
        return this.editedIndex === -1 ? 'New Item' : 'Edit Item'
      },
    },

    watch: {
      dialog (val) {
        val || this.close()
      },
      dialogDelete (val) {
        val || this.closeDelete()
      },
    },

    created () {
      this.initialize()
    },

    methods: {
      initialize () {
        this.nums = [
          {
            name: 'Fatemeh',
            phones: 9354536,
          },
          {
            name: 'Amir',
            phones:776885949 ,

          },
          {
            name: 'Reza',
            phones: 857748262,

          },
          {
            name: 'Ali',
            phones: 75847305,

          },
          {
            name: 'Zahra',
            phones: 74837356,

          },

        ]
      },

      editItem (item) {
        this.editedIndex = this.nums.indexOf(item)
        this.editedItem = Object.assign({}, item)
        this.dialog = true
      },

      deleteItem (item) {
        this.editedIndex = this.nums.indexOf(item)
        this.editedItem = Object.assign({}, item)
        this.dialogDelete = true
      },

      deleteItemConfirm () {
        this.nums.splice(this.editedIndex, 1)
        this.closeDelete()
      },

      close () {
        this.dialog = false
        this.$nextTick(() => {
          this.editedItem = Object.assign({}, this.defaultItem)
          this.editedIndex = -1
        })
      },

      closeDelete () {
        this.dialogDelete = false
        this.$nextTick(() => {
          this.editedItem = Object.assign({}, this.defaultItem)
          this.editedIndex = -1
        })
      },

      save () {
        if (this.editedIndex > -1) {
          Object.assign(this.nums[this.editedIndex], this.editedItem)
        } else {
          this.nums.push(this.editedItem)
        }
        this.close()
      },
    },
  }
</script>
<style>
  .list{
   
    border: 5px solid purple;
  }
</style>






