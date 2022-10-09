<template>
  <v-list
    subheader
    flat
    class="pa-6"
  >
    <v-text-field
      v-model="newItemTitle"
      label="add element"
      append-icon="mdi-cart-plus"
      clearable
      @click:append="addNewItem()"
      @keyup.enter="addNewItem()"
    ></v-text-field>
    <div v-for="item in productsList"
         :key="item.id">
      <v-list-item
        @click="doneBought(item.id)"
        :class="{ 'blue lighten-5' : item.bought }"
      >
        <template>
          <v-list-item-action>
            <v-checkbox
              :input-value="item.bought"
              color="primary"
            ></v-checkbox>
          </v-list-item-action>

          <v-list-item-content>
            <v-list-item-title
              :class="{ 'text-decoration-line-through' : item.bought }"
            >{{ item.title }}</v-list-item-title>
          </v-list-item-content>
          <v-list-item-action>
            <v-btn icon @click.stop="deleteItem(item.id)">
              <v-icon color="grey lighten-1">mdi-delete</v-icon>
            </v-btn>
          </v-list-item-action>
        </template>

      </v-list-item>
    <v-divider></v-divider>
    </div>
  </v-list>
</template>

<script>

export default {
  name: 'List-View',

  data: () => ({
    productsList: [
      { id: 1, title: 'Potato', bought: false },
      { id: 2, title: 'Grape', bought: false }
    ],
    newItemTitle: ''
  }),

  components: {

  },
  methods: {
    doneBought: function (id) {
      const item = this.productsList.filter(item => item.id === id)[0]
      item.bought = !item.bought
    },
    deleteItem: function (id) {
      this.productsList = this.productsList.filter(item => item.id !== id)
    },
    addNewItem: function () {
      const newItem = {
        id: Date.now(),
        title: this.newItemTitle,
        bought: false
      }
      this.productsList.push(newItem)
      this.newItemTitle = ''
    }
  }
}
</script>
