<template>
  <main class="section-main" v-scroll="handleScroll" ref="main">
    <div class="inner">

      <div class="row section-1">
        <div class="title-box">
          <img data-aos="zoom-in" data-aos-duration="800" data-aos-easing="ease-in-sine" src="../assets/image/IMG1002.png" alt="" />
        </div>

        <div class="text-box">
          <p>
            <span>대한민국에 드디어</span>
            <span><strong class="strong1">애플 공인 교육 센터</strong></span>
            <span class="q-mb-lg text-grey-8">Wow!</span>
          </p>
          <p>
            <span class="text-grey-8">macOS, Swift, iOS 개발까지</span>
            <span class="text-grey-8"><strong class="strong2" ref="strong">최신 macOS, iOS,</strong></span>
            <span class="text-grey-8"><strong class="strong3">PadOS, WatchOS</strong>는</span>
            <span>너무나 당연하죠!</span>
          </p>
        </div>
      </div>

      <section class="row section-2">
        <div class="bg-img"></div>

        <h3 data-aos="fade-up" data-aos-duration="1500" data-aos-easing="ease-in-sine">하나의 작은 발자국,</h3>
        <h4
        data-aos="fade-up" data-aos-duration="1500" data-aos-easing="ease-in-sine">하나의 거대한 도약</h4>
      </section>

      <section class="row section-3">
        <div class="text-box">
          <h3 class="text-grey-5"><strong>APPLE</strong> 공인 교육센터</h3>
          <h4 class="text-grey-5">곧 만나요.</h4>
        </div>

        <div class="img-box">
          <img src="../assets/image/hole.gif" alt="" />
        </div>
      </section>


      <div class="row section-4" ref="sPoint">
        <div class="img-box">
          <img src="../assets/image/IMG5214.png" alt="" ref="scrollImg" />
        </div>

        <div class="text-box">
          <h3 
          data-aos="fade-up"
          data-aos-duration="1000"
          data-aos-easing="ease-in-out"
          >
          What's new course?</h3>
          <h4 
          class="text-grey-8" 
          data-aos="fade-up"
          data-aos-duration="1000"
          data-aos-easing="ease-in-out"
          >
          macOS 과정</h4>
          <p data-aos="fade-up" data-aos-duration="1000" data-aos-easing="ease-in-out">
            최신 macOS 프로페셔널 운영 코스<br/>
            macOS Big Sur의 기본 세팅부터 파일시스템, 프라이버시 세팅<br/>
            드라이버 구성, 네트워킹 구성(vpn포함),<br/>
            프로페셔널 문제해결(Troubleshooting)!
          </p>
          <p data-aos="zoom-in-up" data-aos-duration="1000" data-aos-easing="ease-in-out">
            <span class="text-grey-8">여기서 끝이 아니죠 :)</span>
          </p>
          <p data-aos="zoom-in" data-aos-duration="1000" data-aos-easing="ease-in-sine" class="exam-text">
            <span>Apple의 공식</span>
            <span><strong class="strong4">Certification exam</strong>으로!</span>
          </p>
        </div>
      </div>

    </div>
  </main>
</template>
<script>
import AOS from 'aos';
import "aos/dist/aos.css";

export default {
  name: '',
  components: {},
  data() {
    return {
      sPoint: 0,
      boxHeignt: 0,
      width: 0,
    };
  },
  created() {
    AOS.init();
    this.textColor;
  },
  mounted() {
    window.addEventListener('resize', this.handleResize);
  },
  methods: {
    handleScroll(e) {
      // 메뉴 높이
      // this.boxHeight = this.$refs.sPoint.offsetHeight;

      // 메뉴 상단 위치
      this.sPoint = this.$refs.sPoint.offsetTop - 500;

      if (e > this.sPoint) {
        this.boxAnimation1(e);
      }
    },
    boxAnimation1 (e) {
      // console.log(window.innerWidth);
      if (window.innerWidth < 550) {
        Velocity(this.$refs.scrollImg, { top: '100px', width: "375px" }, {duration: 2000}, {easing: "ease-in-out"}, { loop: 1 }); 
      } else {
        Velocity(this.$refs.scrollImg, { top: '120px', width: "550px" }, {duration: 2000}, {easing: "ease-in-out"}, { loop: 1 }); 
      }
    },
    handleResize(event) {
      this.width = window.innerWidth;

      if( this.width >= 550) {
        // console.log(this.$refs.scrollImg.width);
        this.$refs.scrollImg.style.width = 550 + 'px';
      } else {
        this.$refs.scrollImg.style.width = 375 + 'px';
      }
    }
  }
}
</script>

<style scoped lang="scss">
@import '../css/main.scss';
/* @import '../css/main.css'; */
</style>
