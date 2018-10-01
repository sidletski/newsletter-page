<template>
  <div class="article">
    <div class="article-nav">
      <a href="#" class="nav-bttn prev">
        See Previous
      </a>
      <a href="#" class="nav-bttn next">
        See Next
      </a>
    </div>
    <div class="article-content">
      <div class="article-picture" :style="{backgroundImage: `url(${ news_picture })`}"/>

      <h3 class="article-title">
        {{ news.title }}
      </h3>

      <div class="article-date">
        {{ news.date }}
      </div>

      <div class="article-text" v-html="news.text"/>

      <div class="article-social">
        <div>
          <a href="#" class="like-bttn">
            {{ format_number(news.likes) }}
          </a>
          <div class="views-amount">
            {{ format_number(news.views) }}
          </div>
        </div>
        <div>
          <a href="#" class="social-bttn share"/>
          <a href="#" class="social-bttn facebook"/>
          <a href="#" class="social-bttn twitter"/>
        </div>
      </div>
    </div>

    <div class="article-comments">
      <div class="comments-header">
        <div class="comments-title">
          Comments: <span class="amount"> {{ comments.length }} </span>
        </div>
        <div class="comments-filters">
          <a href="#" class="comments-filter" @click.prevent="change_filter('popular')" :class="{selected: filter == 'popular'}">
            Popular
          </a>
          <a href="#" class="comments-filter" @click.prevent="change_filter('recent')" :class="{selected: filter == 'recent'}">
            Recent
          </a>
        </div>
      </div>
      <form class="comments-form">
        <label class="inline-label">
          <input class="text-input" v-model="comment" placeholder="Type comment here..">
          <button class="form-submit" type="submit"/>
        </label>
      </form>
      <div class="comments-list">
        <div class="comment" v-for="comment in comments">
          <div class="avatar-container">
            <div class="avatar">
              <img :src="require(`@/assets/images/photos/avatars/${ comment.author.avatar }.png`)">
            </div>
          </div>
          <div class="comment-details">
            <span class="username">
              {{ comment.author.username }}
            </span>
            <span class="date">
              {{ comment.date }}
            </span>
            <div class="text">
              {{ comment.text }}
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Article',
  data () {
    return {
      news: {
        title: 'The International 2018 Collector’',
        picture: 'collector',
        date: 'July 24, 2018',
        text: '<p>Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry\'s standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages</p><p>Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry\'s standard dummy text ever since the 1500s. </p>',
        likes: 345,
        views: 7649,
      },
      comments: [
        {
          author: {
            avatar: 'user',
            username: 'Svetlakov',
          },
          date: '22 May',
          text: 'Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry\'s standard dummy text ever since the 1500.',
        },
        {
          author: {
            avatar: 'user',
            username: 'Svetlakov',
          },
          date: '22 May',
          text: 'Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry\'s standard dummy text ever since the 1500.',
        },
        {
          author: {
            avatar: 'user',
            username: 'Svetlakov',
          },
          date: '22 May',
          text: 'Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry\'s standard dummy text ever since the 1500.',
        },
      ],
      comment: '',
      filter: 'popular',
    }
  },
  computed: {
    news_picture() {
      return require(`@/assets/images/articles/${ this.news.picture }.jpg`)
    }
  },
  methods: {
    format_number(num) {
      return num.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ".");
    },
    change_filter(filter) {
      this.filter = filter
    },
  }
}
</script>

<style lang="scss" scoped>
  .article {
    .article-nav {
      border-radius: 15px;
      background-color: rgba(36,35,51,.8);
      box-shadow: 0 22px 40px rgba(36,35,51,.45);
      padding: 27px;
      display: flex;
      flex-direction: row;
      justify-content: space-between;
      margin-bottom: 20px;

      .nav-bttn {
        color: #9d9acc;
        text-decoration: none;
        font-size: 14px;
        font-weight: 500;
        transition: 150ms color ease;

        &:hover {
          color: #b7b5d8;
        }

        &:before {
          content: '';
          width: 8px;
          height: 12px;
          display: inline-block;
          margin-top: 3px;
          background: url('../assets/images/icons/article_nav.png') no-repeat;
        }

        &.prev {
          &:before {
            margin-right: 20px;
            float: left;
          }
        }

        &.next {
          &:before {
            margin-left: 20px;
            float: right;
            background-position: right top;
          }
        }
      }
    }

    .article-content {
      border-radius: 15px;
      padding: 23px 23px 0;
      background-color: #242333;
      box-shadow: 0 22px 40px rgba(36,35,51,.45);

      .article-picture {
        border-radius: 15px;
        min-height: 308px;
        background-position: center center;
        background-repeat: no-repeat;
      }

      .article-title {
        font-size: 22px;
        color: #fff;
        font-weight: 600;
        margin: 21px 0 11px;
        padding: 0;
      }

      .article-date {
        color: #9d9acc;
        font-weight: 500;
        font-size: 16px;
        opacity: .5;
      }

      .article-text {
        color: #9d9acc;
        font-size: 16px;
        font-weight: 500;
        line-height: 24px;
      }

      .article-social {
        border-top: 2px solid #302f43;
        margin: 60px -23px 0;
        padding: 25px 36px;
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;
        justify-content: space-between;
        align-items: center;

        .like-bttn {
          color: #fff;
          text-decoration: none;
          float: left;
          margin-right: 46px;

          &:before {
            content: '';
            display: inline-block;
            margin-right: 14px;
            margin-bottom: -4px;
            width: 20px;
            height: 19px;
            background: url('../assets/images/icons/like.png') no-repeat;
          }
        }

        .views-amount {
          color: #9d9acc;
          float: left;

          &:before {
            content: '';
            display: inline-block;
            margin-right: 14px;
            margin-bottom: -4px;
            width: 30px;
            height: 18px;
            background: url('../assets/images/icons/view.png') no-repeat;
          }
        }

        .social-bttn {
          display: inline-block;
          margin-right: 21px;
          width: 24px;
          height: 23px;
          background: url('../assets/images/icons/social.png') no-repeat;

          &:last-child {
            margin-right: 0;
          }

          &.share {
            background-position-x: 1px;
          }

          &.facebook {
            background-position-x: -23px;
          }

          &.twitter {
            background-position-x: -48px;
          }
        }
      }
    }

    .article-comments {
      border-radius: 15px;
      padding: 0 25px 20px;
      background-color: #242333;
      box-shadow: 0 22px 40px rgba(36,35,51,.45);
      margin-top: 20px;

      .comments-header {
        padding: 27px 30px;
        border-bottom: 2px solid #302f43;
        margin: 0 -25px;
        display: flex;
        flex-direction: row;
        justify-content: space-between;

        .comments-title {
          color: #9d9acc;
          font-size: 18px;
          font-weight: 500;

          &:before {
            content: '';
            display: inline-block;
            float: left;
            width: 21px;
            height: 21px;
            margin: 3px 20px 0 0;
            background: url('../assets/images/icons/comments.png') center center no-repeat;
          }

          .amount {
            color: #fff;
          }
        }

        .comments-filters {
          margin: -27px 0 -33px;

          .comments-filter {
            text-align: center;
            letter-spacing: .7px;
            text-shadow: 0 5px 10px rgba(0,0,0,.1);
            color: #ffffff;
            text-decoration: none;
            font-size: 14px;
            display: inline-block;
            line-height: 80px;
            height: 80px;
            padding: 0 10px;
            position: relative;
            font-weight: 500;

            &.selected {
              &:after {
                visibility: visible;
              }
            }

            &:after {
              content: '';
              display: block;
              position: absolute;
              left: 0;
              bottom: 0;
              height: 2px;
              width: 100%;
              visibility: hidden;
              transition: transform 150ms ease-in-out;
              background: -moz-linear-gradient(left, rgba(217,79,199,1) 0%, rgba(255,144,90,1) 100%);
              background: -webkit-linear-gradient(left, rgba(217,79,199,1) 0%,rgba(255,144,90,1) 100%);
              background: linear-gradient(to right, rgba(217,79,199,1) 0%,rgba(255,144,90,1) 100%);
              box-shadow: 0 0 16px rgba(233,107,152,.5);
            }
          }
        }
      }

      .comments-form {
        padding: 29px 0;
        margin-bottom: 5px;

        .inline-label {
          border-radius: 5px;
          height: 62px;
          background-color: #2a293b;
          display: block;
          width: 100%;
          position: relative;

          .text-input {
            border: none;
            background: transparent;
            color: #716dab;
            font-size: 16px;
            font-weight: 500;
            height: 62px;
            padding: 0 45px 0 27px;
            width: 100%;
            box-sizing: border-box;
          }

          .form-submit {
            position: absolute;
            right: 0;
            top: 0;
            border: none;
            width: 55px;
            height: 62px;
            cursor: pointer;
            background: url('../assets/images/ui/submit.png') center center no-repeat;
          }
        }
      }

      .comments-list {
        .comment {
          border-bottom: 2px solid #302f43;
          padding-bottom: 25px;
          margin-bottom: 18px;

          &:last-child {
            margin-bottom: 0;
            border: none;
            padding-bottom: 0;
          }

          .avatar-container {
            float: left;
            padding-left: 2px;
            box-sizing: border-box;
            width: 79px;

            .avatar {
              width: 60px;
              height: 60px;
              border-radius: 100%;
            }
          }

          .comment-details {
            margin-left: 79px;
            padding-top: 6px;

            .username {
              font-size: 18px;
              font-weight: 500;
              color: #9d9acc;
              letter-spacing: 1px;
            }

            .date {
              color: #9d9acc;
              opacity: .5;
              font-size: 16px;
              font-weight: 500;
              margin-left: 7px;
            }

            .text {
              font-weight: 500;
              font-size: 14px;
              color: #fff;
              margin: 13px 1px 0 0;
              line-height: 22px;
            }
          }
        }
      }
    }
  }
</style>
