<template>
  <div style="margin-right: 100px">
    <v-select
      v-model="item.type"
      :items="['title','section','subSection']"
    >
    </v-select>
    <v-text-field v-model="item.name" label="name">

    </v-text-field>
    <v-text-field v-model="title" label="title">

    </v-text-field>
    <v-text-field v-model="section" label="section">

    </v-text-field>
    <v-text-field v-model="subSection" label="subSection">

    </v-text-field>
    <v-text-field v-model="item.content" label="content">

    </v-text-field>
    <v-btn @click="save">הוספת סעיף חדש

    </v-btn>
  </div>
</template>

<script>
import {mapActions} from "vuex";

export default {
  name: "addSection",
  data() {
    return {
      selectOption: null,
      title: null,
      section: null,
      subSection: null,
      item: {
        type: '',
        name: '',
        content: null,
      }
    }
  },
  methods: {
    ...mapActions('contracts', ['insertContract']),
    save() {
      if (this.item.type === 'title') {
        this.item.title = this.title
        this.item.id = this.title
      } else if
      (this.item.type === 'section') {
        this.item.section = this.section
        this.item.title = this.title
        this.item.id = this.title + '.' + this.section

      } else if
      (this.item.type === 'subSection') {
        this.item.subSection = this.subSection
        this.item.section = this.section
        this.item.title = this.title
        this.item.id = this.title + '.' + this.section + '.' + this.subSection
      }
      this.insertContract(this.item)
    }
  }
}
</script>

<style scoped>

</style>
