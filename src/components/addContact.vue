<template>
  <form @submit.prevent="addContact">
    <button class="add-button" type="button" @click="show=true">+</button>
    <div v-show="show">
    <h2>Добавить контакт</h2>
    <fieldset>
    <label for="name">Имя
    <input type="text" name="name" id="name" v-model="name" />
    </label>
    <label for="tel">Телефон
    <input type="tel" name="tel" id="tel" v-model="tel" />
    </label>
    <label for="content">Должность
    <input type="text" name="position" id="position" v-model="position" />
    </label>
    <label for="content">Описание
    <input type="text" name="content" id="content" v-model="content" />
    </label>
    </fieldset>
    <button class="submit-button" type="submit" @click="show=false">Добавить</button>
    </div>
  </form>
</template>

<script>
export default {
  data() {
    return {
      show: false,
      name: "",
      tel: "",
      content: "",
      position: "",
      editDate: ""
    };
  },

  props: ["contacts"],

  methods: {
    // Создаем метод добавления новой записи, и передаем с помощью эмит в родительский компонент.
    addContact() {
      const newItem = {
        name: this.name,
        tel: this.tel,
        content: this.content,
        position: this.position,
        createDate: new Date()
      };
      this.$emit("addContact", newItem);
      this.name = "";
      this.tel = "";
      this.content = "";
      this.position = "";
    },
  },
};
</script>

<style>

button {
  width: 322px;
  padding: 10px;
  border: 1px solid blueviolet;
  background-color: blueviolet;
  color: white;
  font-size: 15px;
  font-weight: 400;
  transition: box-shadow 0.5s ease;
}

button:hover {
  box-shadow: 0 0 1px 3px darkmagenta;
}

button:active {
  box-shadow: none;
}

.submit-button {
  margin: 0 auto;
  width: 400px;
}

fieldset {
 display: grid;
 grid-template-columns: repeat(2,1fr);
 text-align: left;
 grid-gap: 20px;
 padding: 20px 10px 20px 10px;
 margin-bottom: 20px;
}

input {
  width: 200px;
}

label {
  display: flex;
  justify-content: space-between;
}
</style>