<template>
  <main class="consultant-page">
    <div class="consultant-page__consultant consultant">
      <img
        class="consultant__photo"
        src="../assets/consultant-photo.png"
        alt="consultant photo"
      />
      <div class="consultant__info">
        <h1 class="consultant__name">
          {{ name }}
        </h1>
        <p class="consultant__position">
          {{ position }}
        </p>
        <div class="consultant__quotes">
          {{ quotes }}
        </div>
        <div class="consultant__services">
          <ConsultantServices :services="services" />
        </div>
      </div>
    </div>
    <div class="consultant-page__comments">
      <div class="consultant__comments-main-info">
        <h2 class="consultant__comments-title">
          Последние отзывы
          <a href="#" class="consultant__all-comments-link">
            Все отзывы
          </a>
        </h2>
        <div class="consultant__comments-counters-container">
          <div
            class="consultant__comments-counter consultant__comments-counter--likes"
          >
            {{ likes }}
          </div>
          <div
            class="consultant__comments-counter consultant__comments-counter--comments"
          >
            {{ comments }}
          </div>
        </div>
      </div>
      <div class="consultant-page__last-comments">
        <ConsultantComments :comments="lastComments" />
      </div>
    </div>
    <div class="consultant-page__new-comment-wrap">
      <div class="consultant-page__new-comment">
        <NewComment @add-comment="addComment" />
      </div>
    </div>
  </main>
</template>

<script>
import ConsultantServices from "./ConsultantServices";
import ConsultantComments from "./ConsultantComments";
import NewComment from "./NewComment";

export default {
  name: "ConsultantPage",
  components: {
    ConsultantServices,
    ConsultantComments,
    NewComment
  },
  data: () => {
    return {
      name: "Вероника Ростова",
      position: "Менеджер по продажам",
      quotes:
        "Подберу для вас самые лучшие предложения. Мои услуги абсолютно бесплатны.",
      services: [
        {
          id: 0,
          name: "Ручное бронирование",
          amount: 11
        },
        {
          id: 1,
          name: "Пакетные туры",
          amount: 3
        },
        {
          id: 2,
          name: "Отели",
          amount: 1
        }
      ],
      likes: 131,
      comments: 14,
      lastComments: [
        {
          id: 11,
          author: "Самуил",
          date: "13 октября 2011",
          text: "Привет, Верунь! ниче себе ты крутая. фотка класс!!!!"
        },
        {
          id: 12,
          author: "Лилия Семёновна",
          date: "14 октября 2011",
          text:
            "Вероника, здравствуйте! Есть такой вопрос: Особый вид куниц жизненно стабилизирует кинетический момент, это и есть всемирно известный центр огранки алмазов и торговли бриллиантами?"
        },
        {
          id: 13,
          author: "Лилия Семёновна",
          date: "14 октября 2011",
          text:
            "Вероника, здравствуйте! Есть такой вопрос: Особый вид куниц жизненно стабилизирует кинетический момент?"
        }
      ]
    };
  },
  methods: {
    addComment(newComment) {
      this.lastComments = [...this.lastComments, newComment];
    }
  }
};
</script>

<style lang="scss" scoped>
%page-part {
  padding: 20px;
  margin-left: auto;
  margin-right: auto;
  max-width: 720px;
  width: 100%;
}

.consultant-page {
  position: relative;
  display: flex;
  flex-direction: column;
  height: 100%;

  &__consultant {
    @extend %page-part;
    flex: 0 0 auto;
  }

  &__comments {
    @extend %page-part;
    flex: 1 0 auto;
  }

  &__new-comment-wrap {
    position: sticky;
    bottom: 0;
    flex: 0 0 auto;
    background-color: #f2f2f2;
    width: 100%;
  }

  &__new-comment {
    @extend %page-part;

    padding-top: 28px;
  }
}

.consultant {
  position: relative;
  display: flex;

  &__photo {
    margin-right: 10px;
    width: 124px;
    height: 124px;
    border-radius: 50%;
    z-index: 1;
  }

  &__name {
    margin-bottom: 2px;
    font-size: 16px;
    font-weight: 700;
    line-height: 20px;
  }

  &__position {
    margin-bottom: 5px;
    font-size: 12px;
    line-height: 20px;
    color: #808080;
  }

  &__quotes {
    margin-left: -45px;
    margin-bottom: 13px;
    padding-left: 45px;
    padding-right: 10px;
    padding-top: 10px;
    padding-bottom: 10px;
    background-color: #fffbc8;
    border: 1px solid #dadada;
    border-radius: 5px;
    z-index: -1;
  }

  &__services {
    @media (max-width: 425px) {
      margin-left: -45px;
    }
  }

  &__comments-main-info {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
  }

  &__comments-counters-container {
    display: flex;
  }

  &__comments-title {
    font-size: 16px;
    line-height: 16px;
  }

  &__all-comments-link {
    margin-left: 5px;
    font-weight: 400;
    font-size: 14px;
    color: #005da1;
  }

  &__comments-counter {
    display: flex;
    align-items: flex-start;
    font-size: 12px;
    line-height: 100%;

    &:not(:first-child) {
      margin-left: 15px;
    }

    &:before {
      content: "";
      display: inline-block;
      margin-right: 2px;
      width: 13px;
      height: 13px;
      background-size: auto;
      background-repeat: no-repeat;
    }

    &--likes:before {
      background-image: url(../assets/like.svg);
    }

    &--comments:before {
      background-image: url(../assets/comment.svg);
    }
  }
}
</style>
