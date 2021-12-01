<template>
  <div id="app">
    <h1 class="title relevant--blu">gallery</h1>
    <gallery :images="images"></gallery>
  </div>
</template>

<script>
import Gallery from './components/gallery/Gallery.vue';

export default {
  name: 'App',
  components: { Gallery },
  data: () => ({
    images: [
      'https://images.pexels.com/photos/311458/pexels-photo-311458.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=650&w=940',
      'https://images.pexels.com/photos/8356485/pexels-photo-8356485.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=750&w=1260',
      'https://images.pexels.com/photos/7263343/pexels-photo-7263343.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=650&w=940',
      'https://images.pexels.com/photos/10323136/pexels-photo-10323136.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=650&w=940',
      'https://images.pexels.com/photos/8356326/pexels-photo-8356326.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=650&w=940',
      'https://images.pexels.com/photos/2662116/pexels-photo-2662116.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=650&w=940',
      "https://images.pexels.com/photos/15286/pexels-photo.jpg?auto=compress&cs=tinysrgb&dpr=2&h=650&w=940",
      "https://images.pexels.com/photos/3244513/pexels-photo-3244513.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=650&w=940",
      "https://images.pexels.com/photos/2113566/pexels-photo-2113566.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=650&w=940",
      "https://images.pexels.com/photos/2387873/pexels-photo-2387873.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=650&w=940",
      "https://images.pexels.com/photos/3064079/pexels-photo-3064079.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=650&w=940",
      "https://images.pexels.com/photos/3509971/pexels-photo-3509971.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=650&w=940",
      "https://images.pexels.com/photos/4072840/pexels-photo-4072840.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=650&w=940",
      "https://images.pexels.com/photos/2559941/pexels-photo-2559941.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=650&w=940",
      "https://images.pexels.com/photos/2387418/pexels-photo-2387418.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=650&w=940"
    ],
  }),
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Lobster&display=swap');
#app {
  font-family: 'Lobster', cursive;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #324b4a;
  margin: 0% 1%;
}
h1.title{
  margin-block-start: 0.1em;
  margin-block-end: 0.1em;
}
.title {
  padding-left: 2.5%;
  font-size: 3.5em;
}
.relevant--blu {
  background: linear-gradient(
    36deg,
    rgb(0, 201, 200) 0%,
    rgb(0, 201, 200) 100%
  );
  background-repeat: no-repeat;
  background-size: 100% 10%;
  background-position: 0% 90%;
  border: none;
  text-decoration: none;
}
</style>
