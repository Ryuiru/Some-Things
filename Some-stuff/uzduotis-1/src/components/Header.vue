<template>
  <div :class="{ dark: darkMode }">
    <h1>Latest News</h1>
    <li>Politics</li>
    <li>Business</li>
    <li>Tech</li>
    <li>Arts</li>
    <li>Science</li>
    <li>Health</li>
    <li>Sports</li>
  </div>
</template>

<script>
export default {
  name: 'HeaderList',
  data() {
    return {
      darkMode: false,
    };
  },
};
</script>

<style scoped>
h1 {
  padding: 0 0 2rem 0.2rem;
  font-size: 3.5rem;
  font-style: normal;
}
li {
  border: 2px solid #000000;
  border-radius: 5rem;
  padding: 0.1rem 1rem;
  display: inline-block;
  margin: 0.3rem;
}
.dark li.dark-mode-initial {
  border-color: #000000;
}
.dark li {
  border-color: white;
}

@media (max-width: 768px) {
  h1 {
    font-size: 3rem;
    text-align: center;
  }
  li {
    text-align: center;
  }
}
</style>
