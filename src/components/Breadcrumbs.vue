<template>
  <div class="breadcrumbs">
    <div class="dir-bttns">
      <a href="#" class="dir-bttn back">
        <img src="@/assets/images/icons/prev.png">
        Back
      </a>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Breadcrumbs',
  data () {
    return {

    }
  }
}
</script>

<style lang="scss" scoped>
  .breadcrumbs {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    margin-bottom: 30px;

    .dir-bttn {
      display: block;
      font-size: 18px;
      color: #fff;
      font-weight: 500;
      letter-spacing: .5px;
      text-decoration: none;

      &.back {

        img {
          margin-right: 20px;
        }
      }
    }
  }
</style>
