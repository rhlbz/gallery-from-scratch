<template>
  <div id="app">
    <div class="head  relevant--blu">
      <h1 class="title">gallery</h1>
      <button
        :class="selected === null ? 'none' : 'go-back'"
        @click="goToGrid()"
      >
        &larr;
      </button>
    </div>
    <grid 
      :images="images"
      :class="selected !== null ? 'none' : ''"
      @click="changeSelected()"
    ></grid>
    <div 
      :class="selected === null ? 'none' : ''"
    >
      <gallery 
        :images="images"
        :selected="selected"
      ></gallery>
    </div>
  </div>
</template>

<script>
import Gallery from './components/gallery/Gallery.vue';
import Grid from './components/grid/Grid.vue';

export default {
  name: 'App',
  components: { Gallery, Grid },
  data: () => ({
    selected: null,
    images: [
      {
        id: 0,
        path: 'https://images.unsplash.com/photo-1552083375-1447ce886485?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1170&q=80',
      }, {
        id: 1,
        path: 'https://images.unsplash.com/photo-1420745981456-b95fe23f5753?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1170&q=80',
      }, {
        id: 2,
        path: 'https://images.unsplash.com/photo-1492724724894-7464c27d0ceb?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1074&q=80',
      }, {
        id: 3,
        path: 'https://images.unsplash.com/photo-1507525428034-b723cf961d3e?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1173&q=80',
      }, {
        id: 4,
        path: 'https://images.unsplash.com/photo-1464822759023-fed622ff2c3b?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1170&q=80',
      }, {
        id: 5,
        path: 'https://images.unsplash.com/photo-1546948630-1149ea60dc86?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1170&q=80',
      }, {
        id: 6,
        path: 'https://images.unsplash.com/photo-1438786657495-640937046d18?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1170&q=80',        
      }, {
        id: 7,
        path: "https://images.unsplash.com/photo-1497436072909-60f360e1d4b1?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1032&q=80",
      }, {
        id: 8,
        path: "https://images.unsplash.com/photo-1493246507139-91e8fad9978e?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1170&q=80",
      }, {
        id: 9,
        path: "https://images.unsplash.com/photo-1559160581-44bd4222d397?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1170&q=80",
      }, {
        id: 10,
        path: "https://images.unsplash.com/photo-1503197979108-c824168d51a8?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1633&q=80",
      }, {
        id: 11,
        path: "https://images.unsplash.com/photo-1461301214746-1e109215d6d3?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1170&q=80",
      }, {
        id: 12,
        path: "https://images.unsplash.com/photo-1480497490787-505ec076689f?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1169&q=80",
      }, {
        id: 13,
        path: "https://images.unsplash.com/photo-1506318164473-2dfd3ede3623?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1170&q=80",
      }, {
        id: 14,
        path: "https://images.unsplash.com/photo-1545105511-839f4a45a030?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1170&q=80",
      }
    ],
  }),

  methods: {
    setSelected(idx, back = false ){
      if ( back ){
        this.selected = null;
      } else if ( idx ){
        this.selected = idx;
      }
    },
    changeSelected(){
      let _targetId = event.target.id.split('-');
      const id = _targetId[_targetId.length-1];
      if ( parseInt(id) || parseInt(id) === 0)
        this.setSelected(id)
    },
    goToGrid(){
      this.setSelected(null, true);
    }
  }
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
.head{
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
  align-content: center;
  justify-content: space-between;
  align-items: center;
}
h1.title, .go-back{
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
.none{
  display: none;
}
.go-back{
  background-color: none;
  background: none;
  border: none;
  transition: color 0.4s linear;
  font-size: 2em
}
.go-back:hover{
  color: rgb(0, 201, 200);
  cursor: pointer;
}
</style>
