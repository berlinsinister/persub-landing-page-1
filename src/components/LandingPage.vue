<template>
  <div>
    <!-- :style="{ height: scrollHeight }" -->
    <!-- :style="windowHeight > 969 ? { height: '100vh' } : { height: '96.9rem' }" -->
    <div
      class="container"
      :class="signUp ? 'filter' : ''"
      :style="
        windowHeight > 969 ? { height: scrollHeight } : { height: '96.9rem' }
      "
    >
      <main :class="signUp && windowWidth <= 850 ? 'none' : ''">
        <div class="info-container">
          <p id="logo"><b>Per</b>sub</p>
          <p id="title">Subscribe your daily needs</p>
          <p id="subtitle">Subscriptions marketplace</p>
        </div>
        <Form @signup="signUp = true" />
      </main>
      <footer>
        <div class="copyright-and-terms">
          <div class="copyright">
            &copy; 2021 Persub Inc, All Rights Reserved.
          </div>
          <div class="terms">
            <a href="#">Privacy Policy</a>
            &amp;
            <a href="#">Terms &amp; Conditions</a>
          </div>
        </div>
        <p>Crafted by OneSoul</p>
      </footer>
    </div>
    <div v-show="signUp" class="sign-up">
      <div class="sign-up-form">
        <SignUpForm />
        <div class="close" @click="signUp = false">&times;</div>
      </div>
    </div>
  </div>
</template>

<script>
import Form from "./Form.vue";
import SignUpForm from "./SignUpForm.vue";

export default {
  name: "Landing Page",
  components: { Form, SignUpForm },
  props: {
    index: Number,
    title: String,
    url: String,
  },
  data() {
    return {
      signUp: false,
      windowWidth: window.innerWidth,
      windowHeight: window.innerHeight,
      scrollHeight: "",
    };
  },
  mounted() {
    this.scrollHeight = document.documentElement.scrollHeight;
    this.$nextTick(() => {
      window.addEventListener("resize", this.onResize);
    });
  },
  beforeUnmount() {
    window.removeEventListener("resize", this.onResize);
  },
  methods: {
    onResize() {
      this.windowWidth = window.innerWidth;
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../assets/sass/vars";
@import "../assets/sass/mixins";

$main-and-footer-width: 136rem;

b {
  font-weight: 500;
}

.filter {
  filter: brightness(0.7) opacity(0.3);
  // blur(5px)
}

.none {
  filter: opacity(0);
}

.container {
  background: linear-gradient(0deg, rgba(black, 0.8), rgba(black, 0.8)),
    url("../assets/images/bg-1.png");
  background-size: cover;
  display: grid;
  grid-template-columns: auto;
  grid-template-rows: auto auto;
  justify-content: center;
  grid-template-areas:
    "main"
    "footer";
  width: 100%;
  // height: 96.9rem; // 100vh;
  position: relative;
  color: white;
  // & > main,
  // & > footer {
  //   border: 1px solid green;
  // }
  & main {
    grid-area: main;
    align-self: end;
    display: grid;
    grid-template-columns: auto auto;
    justify-content: space-between;
    grid-template-areas: "info" "form";
    width: $main-and-footer-width;
    // height: 50rem;
    // & > div {
    //   // border: 1px solid red;
    // }
    & .info-container {
      grid-area: info;
      align-self: center;
      & * {
        margin: 0;
        padding: 0;
      }
      & #logo {
        margin-bottom: 4.5rem;
        font-size: 3rem;
        font-weight: 300;
      }
      & #title {
        margin-bottom: 1.5rem;
        font: {
          size: 3.5rem;
          weight: 500;
        }
      }
      & #subtitle {
        font-size: 1.5rem;
      }
    }
  }
  & footer {
    grid-area: footer;
    align-self: end;
    width: $main-and-footer-width;
    height: 8rem;
    @include flex-space-between;
    & .copyright-and-terms {
      display: flex;
    }
    & a {
      color: white;
    }
  }
}

.sign-up {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100vh;
  // background: rgba(black, 0.8);
  z-index: 200;
  & .sign-up-form {
    position: absolute;
    left: 50%;
    transform: translate(-50%, 0);
    top: 15rem;
    display: flex;
    align-items: flex-start;
    & .close {
      position: absolute;
      top: 1.5rem;
      right: 3rem;
      font-size: 4rem;
      color: white;
      transition: $transition-time ease-out;
      &:hover {
        cursor: pointer;
        transform: rotate(90deg);
      }
    }
  }
}

// MEDIA
@media (max-width: 1450px) {
  .container {
    & main,
    & footer {
      width: $main-and-footer-width / $ratio;
    }
  }
}

@media (max-width: 1100px) {
  .container {
    // width: 100%;
    // height: 100vh;
    // & > main,
    // & > footer {
    //   // border: 1px solid yellow;
    // }
    // grid-gap: 5rem;
    // padding: 6rem 0 7rem 0;
    & main {
      // grid-area: main;
      // align-self: end;
      // display: grid;
      grid-template-columns: auto;
      grid-template-rows: auto auto;
      justify-content: center;
      grid-gap: 5rem;
      // grid-template-areas: "info" "form";
      width: 32rem; // $main-and-footer-width;
      & .info-container {
        & #logo {
          margin-bottom: 2.5rem;
        }
        & #title {
          font-size: 3rem;
        }
      }
    }
    & footer {
      // padding-top: 4rem;
      // height: 10rem;
      // border: 1px solid green;
      width: 32rem; // $main-and-footer-width;
      flex-direction: column;
      & .copyright-and-terms {
        display: flex;
        flex-direction: column;
        align-items: center;
      }
    }
  }
}

@media (max-width: 1100px) and (max-height: 800px) {
  .sign-up {
    & .sign-up-form {
      top: 5rem;
    }
  }
}
</style>