<template>
  <div class="gallery">
    <div class="gallery--content">
      <gallery-item
        v-for="(image, idx) in images"
        :image="image"
        :key="`item-${idx}`"
        :current="current"
        :idx="idx"
      ></gallery-item>
      <gallery-controls
        @prev="prev"
        @next="next"
      ></gallery-controls>
    </div>
  </div>
</template>

<script>
import GalleryItem from './GalleryItem.vue';
import GalleryControls from './GalleryControls.vue';
export default {
  components: { GalleryItem, GalleryControls },
  props: ['images'],

  data: () => ({
      current: 0,
      duration: null,
  }),
  methods: {
      setCurrent(idx){
          this.current = idx;
      },
      next(){
          const next = this.current < this.images.length - 1 ? this.current + 1 : 0
          this.setCurrent( next );
      },
      prev(){
          const previous = this.current > 0 ? this.current - 1 : this.images.length - 1
          this.setCurrent( previous );
      }

  },
  mounted() {
  },

};
</script>
<style>
.gallery{
    display: flex;
    flex-direction: column;
    flex-wrap: nowrap;
    align-content: center;
    justify-content: center;
    align-items: center;
}
.gallery--content{
    position: relative;
    max-width: 100vw;
    max-height: 40vw;
    overflow: hidden;
}


@media screen and ( min-width: 320px ) and (max-width: 570px) {
    .gallery--content{
        position: relative;
        overflow: hidden;
    }
}
</style>