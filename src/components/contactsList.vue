<template>
  <div>
    <h1>Контактная книга</h1>
    <ul>
      <ContactItem
        v-for="(item, index) in contacts"
        :key="index"
        :item="item"
      />
    </ul>
  </div>
</template>

<script>
import ContactItem from "./contactItem";

export default {
  props: ["contacts"],

  components: {
    ContactItem,
  },

  methods: {
  },
};
</script>

<style scoped>

div {
  margin: 30px 0;
}

ul {
  max-width: 1200px;
  padding: 0;
  margin: 0 auto;
  list-style: none;
  display: flex;
  flex-direction: column;
  row-gap: 20px;
}
</style>
