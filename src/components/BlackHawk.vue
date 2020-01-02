<template>
  <div class="black-hawk">
    <div
      :class="{
        'black-hawk__backgound': true,
        'black-hawk__backgound--first': true,
        'black-hawk__backgound--active': contentEnterFlag[1],
      }"
      :style="{
        backgroundImage: isMob ? 'url(https://udn.com/newmedia/cms_assets/black_hawk/imgs/mob_1.jpg)' : 'url(https://udn.com/newmedia/cms_assets/black_hawk/imgs/Web_1.jpg)}'
      }"
    />
    <div
      :class="{
        'black-hawk__backgound': true,
        'black-hawk__backgound--active': contentEnterFlag[2],
      }"
      :style="{
        backgroundImage: isMob ? 'url(https://udn.com/newmedia/cms_assets/black_hawk/imgs/mob_2.jpg)' : 'url(https://udn.com/newmedia/cms_assets/black_hawk/imgs/Web_2.jpg)}'
      }"
    />
    <div
      :class="{
        'black-hawk__backgound': true,
        'black-hawk__backgound--active': contentEnterFlag[3],
      }"
      :style="{
        backgroundImage: isMob ? 'url(https://udn.com/newmedia/cms_assets/black_hawk/imgs/mob_3.jpg)' : 'url(https://udn.com/newmedia/cms_assets/black_hawk/imgs/Web_3.jpg)}'
      }"
    />
    <div
      :class="{
        'black-hawk__backgound': true,
        'black-hawk__backgound--active': contentEnterFlag[4],
      }"
      :style="{
        backgroundImage: isMob ? 'url(https://udn.com/newmedia/cms_assets/black_hawk/imgs/mob_4.jpg)' : 'url(https://udn.com/newmedia/cms_assets/black_hawk/imgs/Web_4.jpg)}'
      }"
    />
    <div ref="content1" class="black-hawk__content black-hawk__content--first-child">
      <img
        ref="content1_img"
        class="content1_img" 
        :src="isMob ? 'https://udn.com/newmedia/cms_assets/black_hawk/imgs/mob_1.jpg' : 'https://udn.com/newmedia/cms_assets/black_hawk/imgs/Web_1.jpg'" alt=""
      >
      <div class="black-hawk__content__text-wrapper">
        <p>機號933、空軍UH-60M黑鷹直升機從松山機場起飛，預計前往宜蘭東澳營區執行春節慰勉行程。</p>
      </div>
    </div>
    <div ref="content2" class="black-hawk__content">
      <div class="black-hawk__content__text-wrapper">
        <p>飛行員失事前最後一次通聯。當時回報能見度7哩，雲高3000呎至5000呎，符合進場標準。</p>
        <p>失事飛鷹光點在距中正港328.7度17浬處消失。</p>
      </div>
    </div>
    <div ref="content3" class="black-hawk__content">
      <div class="black-hawk__content__text-wrapper">
        <p>10:30 軍聞社記者陳映竹用手機回報，被飛機殘骸壓住。</p>
        <p>宜蘭搜救隊、新北搜救隊分別集結出動，朝桶後溪光點消失處搜救。</p>
      </div>
    </div>
    <div ref="content4" class="black-hawk__content black-hawk__content--last-child">
      <div class="black-hawk__content__text-wrapper">
        <p>殘骸發現地。搜救隊回報5人生還、參謀總長沈一鳴等8人不幸罹難。</p>
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
  computed: {
    isMob() {
      return window.innerWidth < 769 ? true : false;
    }
  },
  methods: {
    handleScroll() {
      const content_1 = this.$refs.content1.getBoundingClientRect();
      const content_2 = this.$refs.content2.getBoundingClientRect();
      const content_3 = this.$refs.content3.getBoundingClientRect();
      const content_4 = this.$refs.content4.getBoundingClientRect();
      const content1_img = this.$refs.content1_img

      if (content_1.top < 0 && content_1.bottom > 0) {
        this.contentEnterFlag[1] = true;
        content1_img.style.display = "none";
      } else {
        this.contentEnterFlag[1] = false;
        content1_img.style.display = "block";
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
.black-hawk__backgound--first {
  transition: none;
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
  padding: 40px 0;
  border-radius: 5px;
}
.content1_img {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
}
</style>
