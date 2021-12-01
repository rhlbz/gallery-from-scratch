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
      {
        id: 0,
        path: 'https://images.pexels.com/photos/2662116/pexels-photo-2662116.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=750&w=1260',
        author: 'Jaime Reimer'
      }, {
        id: 1,
        path: 'https://images.pexels.com/photos/2693529/pexels-photo-2693529.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=750&w=1260',
        author: 'Aarti Vijay',
      }, {
        id: 2,
        path: 'https://images.pexels.com/photos/7587337/pexels-photo-7587337.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=750&w=1260',
        author: 'Polina Kovaleva',
      }, {
        id: 3,
        path: 'https://images.pexels.com/photos/311458/pexels-photo-311458.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=750&w=1260',
        author: 'Scott Webb'
      }, {
        id: 4,
        path: 'https://images.pexels.com/photos/7604425/pexels-photo-7604425.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=750&w=1260',
        author: 'Hazel Marie',
      }, {
        id: 5,
        path: 'https://images.pexels.com/photos/3484061/pexels-photo-3484061.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=750&w=1260',
        author: 'Andy Vu'
      }, {
        id: 6,
        path: 'https://images.pexels.com/photos/2387418/pexels-photo-2387418.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=750&w=1260',        
        author: 'Ezra  Comeau'
      }, {
        id: 7,
        path: "https://images.pexels.com/photos/1287145/pexels-photo-1287145.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=750&w=1260",
        author: 'eberhard grossgasteiger'
      }, {
        id: 8,
        path: "https://images.pexels.com/photos/924824/pexels-photo-924824.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=750&w=1260",
        author: 'Jakub Novacek'
      }, {
        id: 9,
        path: "https://images.pexels.com/photos/8356485/pexels-photo-8356485.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=750&w=1260",
        author: 'Mikhail Nilov'
      }, {
        id: 10,
        path: "https://images.pexels.com/photos/8356326/pexels-photo-8356326.jpeg?auto=compress&cs=tinysrgb&h=750&w=1260",
        author: 'Mikhail Nilov'        
      }, {
        id: 11,
        path: "https://images.pexels.com/photos/534164/pexels-photo-534164.jpeg?auto=compress&cs=tinysrgb&h=750&w=1260",
        author: 'eberhard grossgasteiger'
      }, {
        id: 12,
        path: "https://images.pexels.com/photos/7263343/pexels-photo-7263343.jpeg?auto=compress&cs=tinysrgb&h=750&w=1260",
        author: 'Rachel Claire'
      }, {
        id: 13,
        path: "https://images.pexels.com/photos/853199/pexels-photo-853199.jpeg?auto=compress&cs=tinysrgb&h=750&w=1260",
        author: 'Artem Beliaikin'
      }, {
        id: 14,
        path: "https://images.pexels.com/photos/618833/pexels-photo-618833.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=750&w=1260",
        author: 'Sagui Andrea'
      }
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
  margin-block-start: 0em;
  margin-block-end: 0em;
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
