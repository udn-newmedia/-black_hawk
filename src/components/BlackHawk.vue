<template>
  <div class="black-hawk">
    <div
      id="black-hawk__backgound-1"
      :class="{
        'black-hawk__backgound': true,
        'black-hawk__backgound--active': contentEnterFlag[1],
      }"
    />
    <div
      id="black-hawk__backgound-2"
      :class="{
        'black-hawk__backgound': true,
        'black-hawk__backgound--active': contentEnterFlag[2],
      }"
    />
    <div id="black-hawk__content-1" class="black-hawk__content">
      <div class="black-hawk__content__text-wrapper">
        <p>寒 雨 連 江 夜 入 吳</p>
        <p>平 明 送 客 楚 山 孤</p>
        <p>洛 陽 親 友 如 相 問</p>
        <p>一 片 冰 心 在 玉 壺</p>
      </div>
    </div>
    <div id="black-hawk__content-2" class="black-hawk__content">
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
      }
    };
  },
  methods: {
    handleScroll() {
      const content_1 = document.getElementById('black-hawk__content-1').getBoundingClientRect();
      const content_2 = document.getElementById('black-hawk__content-2').getBoundingClientRect();

      if (content_1.top < window.innerHeight && content_1.bottom > 0) {
        this.contentEnterFlag[1] = true;
      } else {
        this.contentEnterFlag[1] = false;
      }

      if (content_2.top < window.innerHeight && content_2.bottom > 0) {
        this.contentEnterFlag[2] = true;
      } else {
        this.contentEnterFlag[2] = false;
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
#black-hawk__backgound-1 {
  background-image: url('https://s.newtalk.tw/album/news/349/5e0d6d464349f.jpg');
}
#black-hawk__backgound-2 {
  background-image: url('https://s.newtalk.tw/album/news/349/5e0d56a697b60.jpg');
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
  transition: .333s ease-in-out;
}
.black-hawk__backgound--active {
  z-index: 10;
  opacity: 1;
}
.black-hawk__content {
  position: relative;
  z-index: 20;
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}
.black-hawk__content:last-child {
  margin-bottom: 50vh;
}
.black-hawk__content__text-wrapper {
  position: relative;
  background-color: #ffffff;
}
</style>
