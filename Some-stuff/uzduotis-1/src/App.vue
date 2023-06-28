<template>
  <transition name="slide">
    <div
      v-show="!spinMain"
      class="main"
      :class="{ dark: darkMode, spin: spinMain }"
    >
      <navbar-menu @darkModeChanged="toggleDarkMode"></navbar-menu>
      <header-list></header-list>
      <content-list></content-list>
    </div>
  </transition>
</template>

<script>
import NavbarMenu from './components/Navbar.vue';
import HeaderList from './components/Header.vue';
import ContentList from './components/Content.vue';

export default {
  name: 'App',
  components: {
    NavbarMenu,
    HeaderList,
    ContentList,
  },
  data() {
    return {
      darkMode: false,
      spinMain: false,
    };
  },
  methods: {
    toggleDarkMode(checkboxValue) {
      if (checkboxValue !== this.darkMode) {
        if (!checkboxValue) {
          this.spinMain = true;
          setTimeout(() => {
            this.darkMode = checkboxValue;
            this.spinMain = false;
            document.body.classList.toggle('dark', this.darkMode);
          }, 1000);
        } else {
          this.darkMode = checkboxValue;
          document.body.classList.toggle('dark', this.darkMode);
        }
      }
    },
  },
};
</script>
<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  max-width: 100%;
}
@import url('https://fonts.googleapis.com/css2?family=Poppins&display=swap');
body {
  font-family: 'Poppins', sans-serif;
  background-color: #d3d3d3;
  padding: 2rem;
  transition: transform 0.5s, background-color 0.5s;
}
body.dark {
  background-color: #6b6464;
  transition: transform 0.5s, background-color 0.5s;
}
</style>

<style scoped>
.spin {
  animation: spin 1s ease-in-out;
  transition: opacity 0.5s;
}
@keyframes spin {
  0% {
    transform: rotateY(0deg);
  }
  100% {
    transform: rotateY(180deg);
  }
}
.main {
  border: 2px;
  border-radius: 2rem;
  padding: 0 2rem 2rem 2rem;
  background-color: #f9f1e6;
  transition: background-color 1s;
}

.dark {
  background-color: #2a2a2a;
  color: white;
  border: #f9f1e6;
}
span.dark {
  color: white;
}

@media (max-width: 768px) {
  .main {
    padding: 0 0.5rem 0.5rem 0.5rem;
  }
}
/* 
.slide-enter-active {
  transition-delay: 4s;
}
.slide-leave-active {
  transition-delay: 4s;
}
.slide-enter {
  opacity: 0;
  transform: translateY(20px);
}
.slide-leave-to {
  opacity: 0;
  transform: translateY(-20px);
} */

/* Su transitions atsiranda visokiu bugu pvz.: kai fonto spalva nebesikeicia ir panasiai
nepykit su vue.js tiktas pries savaite tepradejau dirbti dar nezinau visu triuku*/
</style>
