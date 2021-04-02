<template>
  <div class="form-container">
    <p id="sign-in">Sign in</p>
    <form @submit.prevent method="post" action="">
      <input
        type="text"
        name="email"
        placeholder="Email or Phone Number"
        required
        autocomplete="off"
      />
      <input type="password" name="password" placeholder="Password" required />
      <input type="submit" value="Log In" />
    </form>
    <p id="create">
      <a href="#" @click="signup">Create New Account</a>
    </p>
  </div>
</template>

<script>
export default {
  name: "Form",
  data() {
    return {};
  },
  methods: {
    signup() {
      this.$emit("signup");
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../assets/sass/vars";
@import "../assets/sass/mixins";

.form-container {
  // border: 1px solid yellow;
  width: 48rem;
  height: 50rem;
  background: rgba(white, 0.2);
  border-radius: 0.7rem;
  transition: $transition-time ease-out;
  & #sign-in {
    margin: {
      left: 3rem;
      bottom: 4rem;
    }
    font: {
      size: 3.5rem;
      weight: 500;
    }
  }
  & #create {
    text-align: center;
    font-size: 1.6rem;
  }
  & a {
    color: white;
    transition: $transition-time ease-out;
    text-decoration: none;
    text-transform: uppercase;
    &:hover {
      opacity: 0.7;
    }
  }
}

form {
  @include flex-centered-vertically;
  & input {
    margin-bottom: 2rem;
  }
  & input[type="text"],
  & input[type="password"] {
    @include input-text-or-password($width: 42.7rem, $main-color: royalblue);
  }
  & input[type="submit"] {
    @include input-submit($width: 42.7rem, $main-color: royalblue);
    text-transform: uppercase;
    font-weight: bold !important;
  }
}

@media (max-width: 1100px) {
  .form-container {
    width: 32rem; // 48rem;
    height: 50rem;
  }

  form {
    @include flex-centered-vertically;
    & input[type="text"],
    & input[type="password"] {
      @include input-text-or-password($width: 28rem, $main-color: royalblue);
    }
    & input[type="submit"] {
      @include input-submit($width: 28rem, $main-color: royalblue);
    }
  }
}
</style>