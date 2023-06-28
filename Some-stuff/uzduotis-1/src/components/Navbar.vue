<template>
  <nav>
    <ul>
      <img class="hamburger" src="../assets/Hamburger_icon.png" />
      <li>Home</li>
      <li>Latest News</li>
      <li>Reviews</li>
    </ul>
    <div class="contact">
      <li>Contact Us</li>
      <label class="switch">
        <input type="checkbox" @click="toggleCheckbox" />
        <div class="slider round"></div>
      </label>
    </div>
  </nav>
</template>

<script>
export default {
  name: 'NavbarMenu, App',
  el: '#app',
  data() {
    return {
      checkbox: false,
    };
  },
  methods: {
    toggleCheckbox() {
      this.checkbox = !this.checkbox;
      this.$emit('darkModeChanged', this.checkbox);
      console.log('Checkbox is ' + this.checkbox);
    },
  },
};
</script>

<style scoped>
nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 5%;
}
ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
  display: flex;
  align-items: center;
  text-align: center;
}
li {
  width: 7rem;
}
.contact {
  display: flex;
  align-items: center;
}

.contact li {
  margin-left: 1rem;
  list-style-type: none;
}
.hamburger {
  vertical-align: middle;
  width: 6vh;
  padding: 10px;
  margin-right: 5%;
}
.switch {
  position: relative;
  display: inline-block;
  width: 4rem;
  height: 2.2rem;
  display: flex;
  align-items: center;
}

.switch input {
  display: none;
}

.slider {
  position: absolute;
  cursor: pointer;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: #ccc;
  -webkit-transition: 0.4s;
  transition: 0.4s;
}

.slider:before {
  position: absolute;
  content: '';
  height: 26px;
  width: 26px;
  left: 4px;
  bottom: 4px;
  background-color: white;
  -webkit-transition: 0.4s;
  transition: 0.4s;
}

input:checked + .slider {
  background-color: #101010;
}

input:focus + .slider {
  box-shadow: 0 0 1px #101010;
}

input:checked + .slider:before {
  -webkit-transform: translateX(26px);
  -ms-transform: translateX(26px);
  transform: translateX(26px);
}

.slider.round {
  border-radius: 34px;
}

.slider.round:before {
  border-radius: 50%;
}
@media (max-width: 768px) {
  nav {
    flex-direction: column;
    align-items: flex-start;
    position: relative;
  }

  ul {
    flex-direction: column;
    align-items: flex-start;
    margin-left: 0.5rem;
    text-align: left;
  }

  li {
    padding: 0.1rem 0.2rem;
    padding-left: 0.6rem;
  }

  .contact {
    position: absolute;
    top: 0;
    right: -0.5rem;
    margin-top: 0.5rem;
    margin-right: 0.5rem;
    display: flex;
    flex-direction: column;
    align-items: flex-end;
  }

  .contact li {
    margin-bottom: 0.5rem;
    list-style-type: none;
    padding: 0.1rem 0.2rem;
  }
  .switch {
    width: 2rem;
    height: 1.1rem;
    margin-right: 1.2rem;
  }

  .slider:before {
    height: 13px;
    width: 13px;
    left: 2px;
    bottom: 2px;
  }
  input:checked + .slider:before {
    -webkit-transform: translateX(13px);
    -ms-transform: translateX(13px);
    transform: translateX(13px);
  }

  .slider.round {
    border-radius: 17px;
  }
}
</style>
