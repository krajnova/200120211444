<template>
  <div class="comments">
    <div
      v-for="comment in comments"
      :key="'comment' + comment.id"
      class="comments__item comment"
    >
      <h3 class="comment__title">
        {{ comment.author }}
        <span class="comment__date">{{ comment.date }}</span>
      </h3>
      <div class="comment__text">{{ comment.text }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ConsultantComments",

  props: {
    comments: Array
  }
};
</script>

<style lang="scss" scoped>
.comments {
  &__item {
    margin-bottom: 16px;
  }
}

.comment {
  &__title {
    margin-bottom: 10px;
    font-size: 14px;
    line-height: 19px;
  }

  &__date {
    margin-left: 10px;
    font-size: 11px;
    font-weight: normal;
    color: #808080;
  }

  &__text {
    position: relative;
    padding-right: 15px;
    padding-left: 20px;
    padding-top: 14px;
    padding-bottom: 14px;
    background-color: #f2fbff;
    border: 1px solid #c4cbcf;
    box-shadow: 0px 4px 10px rgba(128, 128, 128, 0.1);

    &:before {
      content: "";
      position: absolute;
      width: 0;
      height: 0;
      left: 30px;
      top: -10px;
      border: 5px solid;
      border-color: transparent transparent #c4cbcf #c4cbcf;
    }

    &:after {
      content: "";
      position: absolute;
      width: 0;
      height: 0;
      left: 31px;
      top: -8px;
      border: 4px solid;
      border-color: transparent transparent #f2fbff #f2fbff;
    }
  }
}
</style>
