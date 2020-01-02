<template>
  <div class="black-hawk">
    <div
      :class="{
        'black-hawk__backgound': true,
        'black-hawk__backgound--active': contentEnterFlag[1],
      }"
      style="backgroundImage: url('https://udn.com/newmedia/cms_assets/black_hawk/imgs/Web_1.jpg')"
    />
    <div
      :class="{
        'black-hawk__backgound': true,
        'black-hawk__backgound--active': contentEnterFlag[2],
      }"
      style="backgroundImage: url('https://udn.com/newmedia/cms_assets/black_hawk/imgs/Web_2.jpg')"
    />
    <div
      :class="{
        'black-hawk__backgound': true,
        'black-hawk__backgound--active': contentEnterFlag[3],
      }"
      style="backgroundImage: url('https://udn.com/newmedia/cms_assets/black_hawk/imgs/Web_3.jpg')"
    />
    <div
      :class="{
        'black-hawk__backgound': true,
        'black-hawk__backgound--active': contentEnterFlag[4],
      }"
      style="backgroundImage: url('https://udn.com/newmedia/cms_assets/black_hawk/imgs/Web_4.jpg')"
    />
    <div ref="content1" class="black-hawk__content black-hawk__content--first-child">
      <div class="black-hawk__content__text-wrapper">
        <p>寒 雨 連 江 夜 入 吳</p>
        <p>平 明 送 客 楚 山 孤</p>
        <p>洛 陽 親 友 如 相 問</p>
        <p>一 片 冰 心 在 玉 壺</p>
      </div>
    </div>
    <div ref="content2" class="black-hawk__content">
      <div class="black-hawk__content__text-wrapper">
        <p>閨 中 少 婦 不 知 愁 </p>
        <p>春 日 凝 妝 上 翠 樓</p>
        <p>忽 見 陌 頭 楊 柳 色</p>
        <p>悔 教 夫 婿 覓 封 侯</p>
      </div>
    </div>
    <div ref="content3" class="black-hawk__content">
      <div class="black-hawk__content__text-wrapper">
        <p>閨 中 少 婦 不 知 愁 </p>
        <p>春 日 凝 妝 上 翠 樓</p>
        <p>忽 見 陌 頭 楊 柳 色</p>
        <p>悔 教 夫 婿 覓 封 侯</p>
      </div>
    </div>
    <div ref="content4" class="black-hawk__content black-hawk__content--last-child">
      <div class="black-hawk__content__text-wrapper">
        <p>閨 中 少 婦 不 知 愁 </p>
        <p>春 日 凝 妝 上 翠 樓</p>
        <p>忽 見 陌 頭 楊 柳 色</p>
        <p>悔 教 夫 婿 覓 封 侯</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'BlackHawk',
  data() {
    return {
      contentEnterFlag: {
        1: false,
        2: false,
        3: false,
        4: false
      }
    };
  },
  methods: {
    handleScroll() {
      const content_1 = this.$refs.content1.getBoundingClientRect();
      const content_2 = this.$refs.content2.getBoundingClientRect();
      const content_3 = this.$refs.content3.getBoundingClientRect();
      const content_4 = this.$refs.content4.getBoundingClientRect();

      if (content_1.top < 0 && content_1.bottom > 0) {
        this.contentEnterFlag[1] = true;
      } else {
        this.contentEnterFlag[1] = false;
      }

      if (content_2.top < window.innerHeight * 0.5 && content_2.bottom > 0) {
        this.contentEnterFlag[2] = true;
      } else {
        this.contentEnterFlag[2] = false;
      }

      if (content_3.top < window.innerHeight * 0.5 && content_3.bottom > 0) {
        this.contentEnterFlag[3] = true;
      } else {
        this.contentEnterFlag[3] = false;
      }

      if (content_4.top < window.innerHeight * 0.5 && content_4.bottom > 0) {
        this.contentEnterFlag[4] = true;
      } else {
        this.contentEnterFlag[4] = false;
      }
    },
  },
  mounted() {
    window.addEventListener('scroll', () => {
      this.handleScroll();
    });
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.black-hawk {
  background-color: #dedede;
}
.black-hawk__backgound {
  pointer-events: none;
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background-size: cover;
  opacity: 0;
  transition: .5s ease-in-out;
}
.black-hawk__backgound--active {
  opacity: 1;
}
.black-hawk__content {
  /* border: solid 1px red; */
  position: relative;
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}
.black-hawk__content--first-child {
  padding-top: 100vh;
  align-items: flex-start;
}
.black-hawk__content--last-child {
  margin-bottom: 100vh;
  align-items: flex-end;
}
.black-hawk__content__text-wrapper {
  position: relative;
  background-color: #ffffff;
}
</style>
