<template>
  <div class="form-container">
    <p id="sign-up">Sign up</p>
    <p id="description">It's quick and easy</p>
    <form @submit.prevent method="post" action="">
      <div>
        <input
          type="text"
          name="name"
          id="name"
          placeholder="Name"
          autocomplete="off"
          required
        />
        <input
          type="text"
          name="surname"
          id="surname"
          placeholder="Surname"
          autocomplete="off"
          required
        />
      </div>
      <input
        type="text"
        name="email"
        id="email"
        placeholder="Mobile number or email"
        required
        autocomplete="off"
      />
      <input
        type="password"
        name="password"
        id="password"
        placeholder="Create new password"
        required
      />
      <input type="submit" value="Sign Up" />
    </form>
  </div>
</template>

<script>
export default {
  name: "Form",
};
</script>

<style lang="scss" scoped>
@import "../assets/sass/vars";
@import "../assets/sass/mixins";

.form-container {
  width: 71rem;
  height: 62rem;
  // background: rgba(white, 0.2);
  background: rgba(gray, 0.7);
  color: white;
  border-radius: 0.7rem;
  transition: $transition-time ease-out;
  & p {
    margin-left: 3rem;
  }
  & #sign-up {
    margin-bottom: 1rem;
    font-size: 3.5rem;
    font-weight: 500;
  }
  & #description {
    margin-bottom: 5rem;
    opacity: 0.7;
    font-size: 1.6rem;
    font-weight: 300;
  }
}

form {
  @include flex-centered-vertically;
  & input {
    margin-bottom: 2rem;
  }
  & > div {
    width: 65rem;
    @include flex-space-between;
    & > #name,
    & > #surname {
      @include input-text-or-password($width: 31.5rem, $main-color: #ffc64a);
    }
  }
  & > input[type="text"],
  & > input[type="password"] {
    @include input-text-or-password($width: 65rem, $main-color: #ffc64a);
  }
  & > input[type="submit"] {
    @include input-submit($width: 23rem, $main-color: #ffc64a);
    color: #2c506f !important;
    font-weight: bold !important;
    text-transform: uppercase;
    margin-top: 3rem;
  }
}

// MEDIA
@media (max-width: 800px) {
  .form-container {
    width: 32rem; // 36rem;
    height: 62rem;
    background: rgba(white, 0.2);
    border-radius: 0.7rem;
    transition: $transition-time ease-out;
    & p {
      margin-left: 3rem;
    }
    & #sign-up {
      margin-bottom: 1rem;
      font: {
        size: 3.5rem;
        weight: 500;
      }
    }
    & #description {
      margin-bottom: 4rem;
    }
  }

  form {
    @include flex-centered-vertically;
    & input {
      margin-bottom: 1rem;
    }
    & > div {
      display: flex;
      flex-direction: column;
      // width: 65rem;
      & > #name,
      & > #surname {
        @include input-text-or-password($width: 28rem, $main-color: #ffc64a);
      }
    }
    & input[type="text"],
    & input[type="password"] {
      @include input-text-or-password($width: 28rem, $main-color: #ffc64a);
    }
    & input[type="submit"] {
      @include input-submit($width: 28rem, $main-color: #ffc64a);
      margin-top: 0; // 1rem;
    }
  }
}
</style>