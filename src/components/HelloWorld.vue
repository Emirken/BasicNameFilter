<template>
  <v-container>
      <v-row >
          <v-text-field class="mt-5"
              outlined
              v-model="searchValue"
              label="Write Name">
          </v-text-field>
      </v-row>

      <v-row>
          <v-col  >
              <v-card
                      class="mx-auto"
                      max-width="400"
                      tile
              >
                  <v-list-item v-for="(item, index) in filteredItems" :key="index" >
                      <v-list-item-content>
                          <v-list-item-title><strong>{{index+1}}.</strong> {{item.name}}</v-list-item-title>
                      </v-list-item-content>
                  </v-list-item>
              </v-card>
          </v-col>
      </v-row>

  </v-container>
</template>

<script lang="ts">
  import Vue from 'vue'

  export default Vue.extend({


    data: () => ({
        listItems:[{name:'Emircan'},{name:'Çetin'},{name:'Berke'},{name:'Sebo'},{name:'Emre'},{name:'Caner'}],
        searchValue:''
    }),
      computed: {
          filteredItems() {
              if (this.searchValue.trim() === '') {
                  return this.listItems; // Return the original list if searchValue is empty
              } else {
                  const searchTerm = this.searchValue.toLowerCase().trim();
                  return this.listItems.filter(item => item.name.toLowerCase().includes(searchTerm));
              }
          }
      }

  })
</script>
