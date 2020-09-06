<template>
  <div class="layout__root" :style="rootStyle">
    <header class="header">
      <div class="header__left">
        <Logo v-if="showLogo" />
      </div>

      <div class="header__right">
        <!-- <ToggleTheme /> -->
      </div>
    </header>

    <main class="main">
      <slot />
    </main>

    <footer class="footer">
      <span class="footer__copyright"
        >© Biocentro Güembé {{ new Date().getFullYear() }}</span
      >
      <!-- <span class="footer__links">
        Powered by
        <a href="//www.suits.at">SUITS</a>
      </span>-->
    </footer>
  </div>
</template>

<script>
import Logo from "~/components/Logo.vue";
// import ToggleTheme from "~/components/ToggleTheme.vue";

export default {
  props: {
    showLogo: { default: true },
    backgroundImage: { default: null },
  },
  components: {
    Logo,
    // ToggleTheme,
  },
  computed: {
    rootStyle() {
      return {
        backgroundImage: this.backgroundImage
          ? this.backgroundImage
          : "/images/uploads/portada.jpg",
      };
    },
  },
};
</script>

<style lang="scss">
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  min-height: var(--header-height);
  padding: 0 calc(var(--space) / 2);
  top: 0;
  z-index: 10;

  &__left,
  &__right {
    display: flex;
    align-items: center;
  }

  @media screen and (min-width: 1300px) {
    //Make header sticky for large screens
    position: sticky;
    width: 100%;
  }
}

.main {
  margin: 0 auto;
  padding: 1.5vw 15px 0;
}

.footer {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: calc(var(--space) / 2);
  text-align: center;
  font-size: 0.8em;

  > span {
    margin: 0 0.35em;
  }

  a {
    color: currentColor;
  }
}

.layout__root {
  position: relative;

  &::before {
    content: " ";
    background-image: url("/images/uploads/portada.jpg");
    background-attachment: fixed;
    background-size: cover;
    position: absolute;
    z-index: -2;
    left: 0;
    right: 0;
    top: 0;
    bottom: 0;
  }

  &::after {
    content: " ";
    background: #fff;
    opacity: 0.8;
    position: absolute;
    z-index: -1;
    left: 0;
    right: 0;
    top: 0;
    bottom: 0;
  }
}
</style>
