<template>
  <div id="app">
    <contactsList :contacts="contacts" />
    <addContact @addContact="addContact"/>
  </div>
</template>

<script>
import addContact from "./components/addContact";
import contactsList from "./components/contactsList";

export default {
  data() {
    return {
      contacts: [
        { name: "Антон", 
        tel: "11111111", 
        position: "Стажер во Frontend-разработке", 
        content: "Хороший парень",
        createDate: new Date(2021, 5, 17) 
        },
        {
          name: "Чендлер",
          tel: "2212412411",
          position: "До сих пор непонятно, кем он работает",
          content: "Зато смешно шутит",
          createDate: new Date(2021, 6, 15)
        },
         {
          name: "Тест",
          tel: "232423423423",
          position: "Тестировщик",
          content: "Тестирует",
          createDate: new Date(2021, 6, 11)
        },
      ],
    };
  },

  methods: {
    addContact(newContact) {
      this.contacts.push(newContact);
    },
  },

  name: "App",
  components: {
    addContact,
    contactsList,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
