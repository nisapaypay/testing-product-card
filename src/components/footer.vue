<template>
  <footer class="footer-area">
    <div class="container">
      <div class="content-collapse" :class="{
        'show': show
      }">
        <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Mi bibendum neque egestas congue quisque egestas. Ut lectus arcu bibendum at varius. Proin sagittis nisl rhoncus mattis rhoncus urna neque viverra justo. Scelerisque in dictum non consectetur a erat nam at lectus. Aliquam ut porttitor leo a diam. Egestas egestas fringilla phasellus faucibus. Libero id faucibus nisl tincidunt eget nullam non nisi. Nunc sed id semper risus in. Phasellus faucibus scelerisque eleifend donec pretium vulputate sapien nec sagittis. Ultricies mi eget mauris pharetra et ultrices neque. Aliquam faucibus purus in massa tempor nec feugiat nisl pretium. Elementum sagittis vitae et leo duis ut diam quam nulla. Egestas sed sed risus pretium quam vulputate dignissim. Hendrerit gravida rutrum quisque non tellus.</p>

        <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Mi bibendum neque egestas congue quisque egestas. Ut lectus arcu bibendum at varius. Proin sagittis nisl rhoncus mattis rhoncus urna neque viverra justo. Scelerisque in dictum non consectetur a erat nam at lectus. Aliquam ut porttitor leo a diam. Egestas egestas fringilla phasellus faucibus. Libero id faucibus nisl tincidunt eget nullam non nisi. Nunc sed id semper risus in. Phasellus faucibus scelerisque eleifend donec pretium vulputate sapien nec sagittis. Ultricies mi eget mauris pharetra et ultrices neque. Aliquam faucibus purus in massa tempor nec feugiat nisl pretium. Elementum sagittis vitae et leo duis ut diam quam nulla. Egestas sed sed risus pretium quam vulputate dignissim. Hendrerit gravida rutrum quisque non tellus.</p>
      </div>
      <button class="btn-show-content" :class="{ 'show': show }" @click="show = !show">
        {{ show ? 'Collapse all' : 'Show all' }}
        <svg width="20" height="20" xmlns="http://www.w3.org/2000/svg" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" viewBox="0 0 24 24"><path d="m6 9 6 6 6-6"/></svg>
      </button>

      <p class="copyright">
        &copy; 2022 PT Global Digital Niaga
      </p>
    </div>
  </footer>
  <transition name="fade">
    <div id="pagetop" class="btn-top" v-show="scY > 300" @click="toTop">
      &uarr;
    </div>
  </transition>
</template>
<style scoped>
.footer-area {
  padding: 1rem 0;
  background-color: #d9d9d9;
}
.btn-show-content {
  color: #0095da;
  border: 0;
  background: none;
  display: flex;
  display: -ms-flexbox;
  -webkit-box-align: center;
  -ms-flex-align: center;
  align-items: center;
  margin: 0 auto;
  cursor: pointer;
  margin-top: 3rem;
}
.btn-show-content.show svg {
  transform: rotate(180deg);
}
.content-collapse {
  max-height: 180px;
  overflow: hidden;
  font-size: 14px;
}
.content-collapse.show {
  max-height: none;
}
.content-collapse p:last-child {
  margin-bottom: 0;
}
.copyright {
  margin-top: 10rem;
  text-align: center;
  font-size: 14px;
}

.btn-top {
  position: fixed;
  bottom: 1rem;
  right: 1rem;
  cursor: pointer;
  font-size: 30px;
  color: #0095DA;
  width: 40px;
  height: 40px;
  -webkit-box-shadow: 0 0 24px -4px rgb(0 0 0 / 24%);
  box-shadow: 0 0 24px -4px rgb(0 0 0 / 24%);
  background-color: #fff;
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-align: center;
  -ms-flex-align: center;
  align-items: center;
  -webkit-box-pack: center;
  -ms-flex-pack: center;
  justify-content: center;
  border-radius: 100%;
}
</style>

<script scoped>
export default {
  data () {
    return {
      show: false,
      scTimer: 0,
      scY: 0,
    }
  },
  mounted() {
    window.addEventListener('scroll', this.handleScroll);
  },
  methods: {
    handleScroll: function () {
      if (this.scTimer) return;
      this.scTimer = setTimeout(() => {
        this.scY = window.scrollY;
        clearTimeout(this.scTimer);
        this.scTimer = 0;
      }, 100);
    },
    toTop: function () {
      window.scrollTo({
        top: 0,
        behavior: "smooth"
      });
    }
  }
}
</script>