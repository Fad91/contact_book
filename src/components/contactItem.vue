<template>
  <li>
    <p
      @mouseover="show = true"
      @mouseleave="show = false"
      @click="editShow = true"
    >
      ИМЯ: {{ item.name }}
    </p>
    <transition name="show">
      <p v-show="editShow" class="edit">
        <input
          type="text"
          v-model="editedName"
          placeholder="Редактируйте имя"
        />
        <input
          type="text"
          v-model="editedContent"
          placeholder="Редактируйте описание"
        />
        <button type="button" @click="editContent">
          Изменить
        </button>
        <button type="button" @click="closeEdit">
          Закрыть
        </button>
      </p>
    </transition>
    <transition name="show">
      <p class="content" v-show="show">
        {{ item.content }}
      </p>
    </transition>
    <p>Должность: {{ item.position }}</p>
    <p>ТЕЛЕФОН: {{ item.tel }}</p>
    <p>ДАТА СОЗДАНИЯ: {{ item.createDate }}</p>
    <p>ДАТА РЕДАКТИРОВАНИЯ: {{ this.editDate }}</p>
  </li>
</template>

<script>
export default {
  data() {
    return {
      show: false,
      editShow: false,
      editedName: "",
      editedContent: "",
      editDate: "",
    };
  },
  props: {
    item: {
      required: true,
    },
  },
  name: "ContactItem",
  components: {},
  methods: {
    editContent() {
      if (this.editedName !== "" && this.editedContent !== "") {
        this.item.name = this.editedName;
        this.item.content = this.editedContent;
        this.editedName = "";
        this.editedContent = "";
        (this.editDate = new Date()), (this.editShow = false);
      } else {
        alert("Заполни все ячейки, приятель!");
      }
    },

    closeEdit() {
      this.editShow = false;
    },
  },
};
</script>

<style scoped>
li {
  justify-content: center;
  align-items: center;
  border: 1px solid blueviolet;
}

p {
  margin: 20px 50px;
  text-align: left;
  cursor: pointer;
}

.content {
  padding: 20px;
  border: 1px solid blueviolet;
}

.show-enter-active,
.show-leave-active {
  transition: opacity 1s ease;
}

.show-enter,
.show-leave-to {
  opacity: 0;
}

.edit {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-gap: 20px;
}

input {
  max-width: 300px;
  padding: 10px;
  border-radius: 6px;
  border: 1px solid blueviolet;
  transition: box-shadow 0.5s ease;
}

input:hover {
  box-shadow: 0 0 3px 1px darkmagenta;
}

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

@media (max-width:768px) {
  .edit {
    grid-template-columns: 1fr;
    width: 300px;
    margin: 0 auto;
  }

  input {
    max-width: 250px;
  }

  button {
    max-width: 272px;
  }
}
</style>
