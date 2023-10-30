<script>
export default {
  name: "PostForm",
  props: {
    changeShow: {
      type: Function,
      required: false,
      default: () => {},
    },
  },
  data: () => {
    return {
      title: "",
      body: "",
    };
  },
  methods: {
    sendPostEntity() {
      this.$emit("create-post", { title: this.title, body: this.body });
      this.title = "";
      this.body = "";
      this.changeShow();
    },
    changeTitle(value) {
      this.title = value;
    },
    changeBody(value) {
      this.body = value;
    },
  },
};
</script>

<template>
  <form>
    <!-- <input type="text" class="input" placeholder="название" v-model="title" />
    <input type="text" class="input" placeholder="описание" v-model="body" /> -->
    <MyInput
      :placeholder="'Название'"
      :value="title"
      @change-value="changeTitle"
    />
    <MyInput
      :placeholder="'Описание'"
      :value="body"
      @change-value="changeBody"
    />
    <MyButton @click.prevent="sendPostEntity"> Создать </MyButton>
  </form>
</template>

<style scoped>
.close-button {
  background-color: red;
}
</style>
