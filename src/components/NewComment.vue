<template>
  <form
    class="new-comment-form"
    @submit.prevent="addComment"
    @keyup.ctrl.enter.prevent="addComment"
  >
    <textarea
      name="comment"
      v-model="comment"
      cols="30"
      rows="10"
      class="new-comment-form__field"
    ></textarea>
    <button class="new-comment-form__button" type="submit">
      Написать консультанту
    </button>
  </form>
</template>

<script>
import { v4 as uuid } from "uuid";

export default {
  name: "NewComment",
  data: () => {
    return {
      comment: ""
    };
  },

  methods: {
    addComment() {
      if (this.comment === "") {
        return;
      }

      const newComment = {
        id: uuid(),
        text: this.comment,
        author: "Вы",
        date: new Date().toLocaleString("ru", {
          year: "numeric",
          month: "long",
          day: "numeric"
        })
      };
      this.$emit("add-comment", newComment);

      this.comment = "";
    }
  }
};
</script>

<style lang="scss" scoped>
.new-comment-form {
  display: flex;
  flex-direction: column;
  align-items: center;

  &__field {
    resize: none;
    width: 100%;
    height: 63px;
    margin-bottom: 23px;

    &:focus {
      outline: 0;
      border-color: #fdd539;
    }
  }

  &__button {
    padding: 11px 45px;
    background-color: #fdd539;
    border: 1px solid #fdd539;
    border-radius: 23px;
    font-weight: 700;
    cursor: pointer;
    font-family: "PT Sans", sans-serif;
    transition: background-color 0.2s;

    &:hover {
      background-color: #fff;
    }
  }
}
</style>
