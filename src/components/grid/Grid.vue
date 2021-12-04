<template>
  <div class="grid">
    <div id="gridContent" class="grid--content">
      <grid-item 
        v-for="(image, idx) in images"
        :image="image"
        :key="`grid-item-${idx}`"
        :selected="selected"
        :idx="idx"
        @click="changeSelected(idx)"
      ></grid-item>
    </div>
  </div>
</template>

<script>
import GridItem from './GridItem.vue';

export default {
  components: { GridItem },
  props: ['images'],

  data: () => ( {
    selected: null
  }),

  methods: {
    setSelected(idx){
      this.selected = idx;
    },
    setGridContentHeight(){
      const gridContent = document.getElementById('gridContent');
      const diff = ( window.innerHeight * 15 ) / 100;
      gridContent.style.marginTop = ( window.innerHeight * 1.5 ) / 100 + 'px';
      gridContent.style.height = window.innerHeight - diff + 'px';
      gridContent.style.padding = '0px ' + window.innerHeight - diff + 'px';
    },
    changeSelected(idx){
      this.setSelected(idx)     
    }
  },

  mounted() {
    this.setGridContentHeight();
    window.addEventListener('resize', function() {
      const gridContent = document.getElementById('gridContent');
      gridContent.style.marginTop = ( window.innerHeight * 1.5 ) / 100 + 'px';
      const diff = ( window.innerHeight * 15 ) / 100;
      gridContent.style.height = window.innerHeight - diff + 'px';
      gridContent.style.padding = '0px ' + window.innerHeight - diff + 'px';
    })
  }
}

</script>
<style>
.grid{
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
  align-content: center;
  justify-content: center;
  align-items: center;
}
.grid--content {
  width: 80%;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  align-content: flex-start;
  justify-content: center;
  overflow-y: scroll;
  min-height: 250px;
  scrollbar-width: thin;
  scrollbar-color: rgba(0, 201, 200, 0.3) whitesmoke;
}
::-webkit-scrollbar {
  width: 12.5px;
}
::-webkit-scrollbar-track {
  box-shadow: inset 0 0 1px rgb(0, 201, 200); 
  border-radius: 10px;
}
::-webkit-scrollbar-thumb {
  background: rgba(0, 201, 200, 0.3); 
  border-radius: 10px;
}
::-webkit-scrollbar-thumb:hover {
  background: rgba(0, 201, 200, 0.5);
}
</style>