<template>
  <div id="navbar" :class="{ scrolled: scrolled }">
    <nav class="constrain-width">
      <div id="header">
        <img src="/favicon.ico">
        <span>Roland</span>
        <h1>Deleau</h1>
        <!-- <img src="/src/assets/title.png" alt=""> -->
      </div>
      <ul>
        <li v-for="route in routes" :key="route.path">
          <nuxt-link :to="route.path">{{ route.name }}</nuxt-link>
        </li>
      </ul>
    </nav>
  </div>
</template>

<script>
import { onMounted, onBeforeUnmount, ref } from "@nuxtjs/composition-api";

export default {
  setup() {
    const scrolled = ref(false);

    function updateIsScrolled() {
      console.log(document.firstElementChild.scrollTop)
      scrolled.value = document.firstElementChild.scrollTop > 5;
  	}
    
    const routes = ref([
      {
        name: "Start",
        path: "/",
      },
      {
        name: "Biographie",
        path: "/biographie",
      },
      {
        name: "Werke",
        path: '/werke'
      }
  	]);

    onMounted(() => {
  		updateIsScrolled();
      window.addEventListener("scroll", updateIsScrolled);
    });
    onBeforeUnmount(() => {
      window.removeEventListener("scroll", updateIsScrolled);
    });

    return { routes, scrolled, updateIsScrolled };
  }
};
</script>

<style lang="scss" scoped>
#navbar {
  position: fixed;
  top: 0;
  z-index: 10;
  color: white;
  width: 100%;
  user-select: none;
  transition: 0.3s;
  &.scrolled {
    color: $text-color;
    background-color: white;
    -webkit-box-shadow: 0px 0px 8px -1px rgba(0, 0, 0, 0.2);
    -moz-box-shadow: 0px 0px 8px -1px rgba(0, 0, 0, 0.2);
    box-shadow: 0px 0px 8px -1px rgba(0, 0, 0, 0.2);
  }
}

nav {
  height: $navbar-height;
  display: flex;
  align-items: center;
  width: 100%;
  display: flex;
  justify-content: space-between;
}

#header {
  font-family: "Times New Roman", serif;
  display: grid;
  grid-template-areas: 'logo firstname' 'logo lastname';
  justify-items: left;
  align-items: center;
  width: auto;
  h1 {
    margin: 0;
    font-size: 1.5rem;
    font-weight: lighter;
    line-height: 0.9;
    grid-area: lastname;
  }
  span {
    font-size: 0.9em;
    text-align: left;
    grid-area: firstname;
  }
  img {
    display: block;
    height: 2rem;
    padding: .2rem 0;
    margin-right: .3rem;
    background-color: white;
    border-radius: 9999px;
    grid-area: logo;
  }
}

ul {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  justify-content: space-between;
  align-items: center;

  li:not(:last-child) {
    margin-right: 2rem;
  }
}

a {
  color: white;
  text-decoration: none;
  display: block;
  font-weight: 300;

  // Dynamic animated underline
  &::after {
    display: block;
    content: "";
    position: relative;
    margin: 0 auto;
    height: 1px;
    width: 0;
    background-color: white;
    transition: 0.2s;
  }
  &:hover::after,
  &.nuxt-link-exact-active::after {
    width: 100%;
  }
  &.nuxt-link-exact-active {
    color: $accent-color-1 !important;
    &::after {
      background-color: $accent-color-1 !important;
    }
  }
}
#navbar.scrolled {
  a {
    color: $text-color;
    &::after {
      background-color: $text-color;
    }
  }
}
</style>