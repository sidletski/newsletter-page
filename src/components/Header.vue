<template>
  <div class="header-container">
    <div class="header">
      <div class="header-menu">
        <a href="#" class="header-link" :class="{selected: $route.name == 'Home'}">
          Home
        </a>
        <a href="#" class="header-link" :class="{selected: $route.name == 'Marketplace'}">
          Marketplace
        </a>
        <a href="#" class="header-link" :class="{selected: $route.name == 'BoosterPacks'}">
          Booster Packs
        </a>
        <a href="#" class="play-bttn">
          <div class="bttn-content">
            Play
          </div>
        </a>
      </div>

      <div class="profile-info">
        <a href="#" class="profile-link leaders">
          <div class="icon-status new"/>
        </a>

        <a href="#" class="profile-link notifications">
          <div class="icon-status light"/>
        </a>

        <div class="money-amount">
          <img src="@/assets/images/icons/money.png" class="money-icon">
          <span class="amount">
            {{ amount }}
          </span>
        </div>

        <div class="user-avatar">
          <div class="avatar-container">
            <div class="avatar-img">
              <img src="@/assets/images/photos/avatar.png">
            </div>
          </div>
          <div class="user-status"/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Header',
  data () {
    return {
      amount: 142,
    }
  }
}
</script>

<style lang="scss" scoped>
@import '../assets/styles/vars.scss';

.header-container {
  height: $header-height;
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 20;
  background-color: #323145;

  .header {
    background: -moz-linear-gradient(left, rgba(60,59,83,.5) 0%, rgba(36,35,51,.5) 100%);
    background: -webkit-linear-gradient(left, rgba(60,59,83,.5) 0%,rgba(36,35,51,.5) 100%);
    background: linear-gradient(to right, rgba(60,59,83,.5) 0%,rgba(36,35,51,.5) 100%);
    position: absolute;
    top: 0;
    bottom: 0;
    right: 0;
    left: 0;
    box-shadow: 0 16px 65px #242333;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: flex-end;

    .header-menu {
      display: flex;
      flex-direction: row;
      align-items: center;
      justify-content: flex-end;
      height: $header-height;

      .play-bttn {
        margin-left: 10px;
        letter-spacing: .7px;
        font-weight: 500;
        display: inline-block;
        padding: 2px;
        border-radius: 42px;
        background: -moz-linear-gradient(left, #6f6d99 0%, #9d9acc 100%);
        background: -webkit-linear-gradient(left, #6f6d99 0%,#9d9acc 100%);
        background: linear-gradient(to right, #6f6d99 0%,#9d9acc 100%);
        box-shadow: 0 15px 11px rgba(9,10,15,.15);
        text-decoration: none;
        font-size: 14px;

        .bttn-content {
          color: #fff;
          padding: 0 35px;
          border-radius: 40px;
          border: 2px solid #242333;
          background: -moz-linear-gradient(left, #242333 0%, #3c3b53 100%);
          background: -webkit-linear-gradient(left, #242333 0%,#3c3b53 100%);
          background: linear-gradient(to right, #242333 0%,#3c3b53 100%);
          height: 38px;
          line-height: 38px;
        }
      }

      .header-link {
        text-align: center;
        letter-spacing: .7px;
        text-shadow: 0 5px 10px rgba(0,0,0,.1);
        color: #ffffff;
        overflow: hidden;
        text-decoration: none;
        font-size: 14px;
        display: inline-block;
        line-height: $header-height;
        height: $header-height;
        padding: 0 33px;
        position: relative;
        font-weight: 500;

        &.selected {
          &:before {
            opacity: .9;
          }

          &:after {
            transform: none;
          }
        }

        &:hover:before {
          opacity: 1;
        }

        &:after {
          content: '';
          display: block;
          position: absolute;
          left: 0;
          bottom: 0;
          height: 2px;
          opacity: 1;
          width: 100%;
          transform: translate3d(0, 2px, 0);
          transition: transform 150ms ease-in-out;
          background: -moz-linear-gradient(left, rgba(217,79,199,1) 0%, rgba(255,144,90,1) 100%);
          background: -webkit-linear-gradient(left, rgba(217,79,199,1) 0%,rgba(255,144,90,1) 100%);
          background: linear-gradient(to right, rgba(217,79,199,1) 0%,rgba(255,144,90,1) 100%);
        }

        &:before {
          content: '';
          display: block;
          position: absolute;
          z-index: -1;
          width: 100%;
          left: 0;
          top: 0;
          height: 100%;
          opacity: 0;
          transition: opacity 150ms ease-in-out;
          background: -moz-linear-gradient(top, rgba(135,132,178,0) 0%, rgba(120,125,190,0.13) 100%);
          background: -webkit-linear-gradient(top, rgba(135,132,178,0) 0%,rgba(120,125,190,0.13) 100%);
          background: linear-gradient(to bottom, rgba(135,132,178,0) 0%,rgba(120,125,190,0.13) 100%);
        }
      }
    }

    .profile-info {
      margin-right: 20px;
      margin-left: 180px;
      display: flex;
      align-items: center;
      flex-direction: row;
      z-index: 1;

      .profile-link {
        width: 50px;
        height: $header-height;
        margin-right: 16px;
        position: relative;
        z-index: 0;

        &.leaders {
          background: url('../assets/images/icons/leaders.png') center 22px no-repeat;
        }

        &.notifications {
          background: url('../assets/images/icons/notifications.png') center 22px no-repeat;
        }

        .icon-status {
          width: 8px;
          height: 8px;
          border-radius: 100%;
          position: absolute;
          right: 12px;
          top: 21px;

          &.light {
            background: -moz-linear-gradient(45deg, rgba(80,182,180,1) 0%, rgba(66,225,128,1) 100%);
            background: -webkit-linear-gradient(45deg, rgba(80,182,180,1) 0%,rgba(66,225,128,1) 100%);
            background: linear-gradient(45deg, rgba(80,182,180,1) 0%,rgba(66,225,128,1) 100%);
            box-shadow: 0 0 2px 1px #46b393;
          }

          &.new {
            background: -moz-linear-gradient(45deg, rgba(189,71,192,1) 0%, rgba(124,53,193,1) 100%);
            background: -webkit-linear-gradient(45deg, rgba(189,71,192,1) 0%,rgba(124,53,193,1) 100%);
            background: linear-gradient(45deg, rgba(189,71,192,1) 0%,rgba(124,53,193,1) 100%);
            box-shadow: 0 0 2px 1px #a33fc7;
          }

          &:before {
            content: '';
            display: block;
            position: absolute;
            left: -4px;
            right: -4px;
            top: -4px;
            bottom: -4px;
            border-radius: 100%;
            z-index: -1;
            background-color: #282739;
          }
        }
      }

      .money-amount {
        width: 81px;
        height: 34px;
        margin-right: 16px;
        position: relative;
        border-radius: 18px;
        border: 2px solid #242333;
        box-sizing: border-box;
        font-weight: 500;
        letter-spacing: .7px;
        background: url('../assets/images/ui/money_bg.png') center center;
        box-shadow: 0 15px 11px rgba(9, 10, 15, .15);

        .money-icon {
          margin-left: -1px;
          margin-top: -2px;
          float: left;
        }

        .amount {
          text-shadow: 0 5px 10px rgba(0,0,0,.1);
          margin: 6px 15px 0 0;
          display: inline-block;
          color: #cecbff;
          font-size: 14px;

          &:first-letter {
            color: #ffffff;
          }
        }

        &:after {
          content: '';
          display: block;
          position: absolute;
          left: -4px;
          right: -4px;
          bottom: -4px;
          top: -4px;
          z-index: -1;
          background: -moz-linear-gradient(left, rgba(109,48,200,1) 0%, rgba(217,79,199,1) 100%);
          background: -webkit-linear-gradient(left, rgba(109,48,200,1) 0%,rgba(217,79,199,1) 100%);
          background: linear-gradient(to right, rgba(109,48,200,1) 0%,rgba(217,79,199,1) 100%);
          border-radius: 19px;
        }
      }

      .user-avatar {
        position: relative;

        .avatar-container {
          position: relative;
          z-index: -1;

          .avatar-img {
            width: 46px;
            height: 46px;
            border-radius: 100%;
            border: 2px solid #242333;
            background: -moz-linear-gradient(left, rgba(36,35,51,1) 0%, rgba(60,59,83,1) 100%);
            background: -webkit-linear-gradient(left, rgba(36,35,51,1) 0%,rgba(60,59,83,1) 100%);
            background: linear-gradient(to right, rgba(36,35,51,1) 0%,rgba(60,59,83,1) 100%);
            box-sizing: border-box;
            position: relative;
            box-shadow: 0 15px 11px rgba(9, 10, 15, .15);

            &:after {
              content: '';
              position: absolute;
              left: -4px;
              right: -4px;
              top: -4px;
              bottom: -4px;
              background: -moz-linear-gradient(left, rgba(111,109,153,1) 0%, rgba(157,154,204,1) 100%);
              background: -webkit-linear-gradient(left, rgba(111,109,153,1) 0%,rgba(157,154,204,1) 100%);
              background: linear-gradient(to right, rgba(111,109,153,1) 0%,rgba(157,154,204,1) 100%);
              z-index: -1;
              border-radius: 100%;
            }

            img {
              border-radius: 100%;
            }
          }
        }

        .user-status {
          width: 6px;
          height: 6px;
          position: absolute;
          right: 6px;
          bottom: 2px;
          border-radius: 100%;
          box-sizing: border-box;
          background: -moz-linear-gradient(left, rgba(36,35,51,1) 0%, rgba(60,59,83,1) 100%);
          background: -webkit-linear-gradient(left, rgba(36,35,51,1) 0%,rgba(60,59,83,1) 100%);
          background: linear-gradient(to right, rgba(36,35,51,1) 0%,rgba(60,59,83,1) 100%);
          border: 2px solid #242333;

          &:after {
            content: '';
            display: block;
            position: absolute;
            top: -6px;
            bottom: -6px;
            left: -6px;
            right: -6px;
            border: 2px solid #242433;
            background: -moz-linear-gradient(left, rgba(217,79,199,1) 0%, rgba(255,144,90,1) 100%);
            background: -webkit-linear-gradient(left, rgba(217,79,199,1) 0%,rgba(255,144,90,1) 100%);
            background: linear-gradient(to right, rgba(217,79,199,1) 0%,rgba(255,144,90,1) 100%);
            border-radius: 100%;
            z-index: -1;
          }
        }
      }
    }
  }
}
</style>
