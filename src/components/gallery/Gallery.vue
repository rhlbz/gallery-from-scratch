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
        :forPreview="false"
        @prev="prev"
        @next="next"
      ></gallery-controls>
    </div>
  </div>
  <hr class="divider" />
  <div class="preview">
    <div class="preview--content">
      <gallery-preview
        v-for="(image, idx) in images"
        :image="image"
        :key="`item-preview-${idx}`"
        :current="current"
        :isCurrent="idx === current ? true : false"
        :idx="idx"
        @click="changeCurrency(idx)"
      ></gallery-preview>
    </div>
  </div>
</template>

<script>
import GalleryItem from './GalleryItem.vue';
import GalleryControls from './GalleryControls.vue';
import GalleryPreview from './GalleryPreview.vue';

export default {

  components: { GalleryItem, GalleryControls, GalleryPreview },

  props: ['images'],

  data: () => ({
    current: 0,
  }),

  methods: {
    setCurrent(idx){
      this.current = idx;
    },
    changeCurrency(idx){
      this.setCurrent(idx)
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

  mounted(){
    const _this = this;
    window.addEventListener('keyup', function(event){
      const key = event.code;
      if ( key === 'KeyA' || key === 'ArrowLeft' || key === 'NumpadSubtract' || key === 'Slash' ) {
        _this.prev();
      } else if ( key === 'KeyD' || key === 'ArrowRight' || key === 'NumpadAdd' || key === 'BracketRight' ){
        _this.next();
      }
    });
  }
};
</script>
<style>
* {
  overflow:hidden!important;
}
.gallery {
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
  align-content: center;
  justify-content: center;
  align-items: center;
}
.gallery--content {
  position: relative;
  max-width: 150vw;
  max-height: 30vw;
  overflow: hidden;
}
.divider{
  background-color: #00C9C8;
  color: #00C9C8;
  width: 70%;
  border:none;
  height: 1px;
}

@keyframes scroll {
	0% { transform: translateX(0); }
	100% { transform: translateX(calc(-250px * 7))}
}
.preview {
  background: white;
  min-height: 100px;
  height: 150px;
  max-height: 150px;
	margin: auto;
	overflow:hidden;
	position: relative;
	width: 960px;
}
.preview::after,
.preview::before{
  content: "";
  position: absolute;
  z-index: 2;
}
.preview::after{
  right: 0;
  top: 0;
  transform: rotateZ(180deg);
}
.preview::before{
  left: 0;
	top: 0;
}
.preview--content {
  animation: scroll 40s linear infinite;
  display: flex;
  width: calc(250px * 14);
}
.preview--content > .gallery-item-preview {
  min-height: 100px;
  height: 150px;
  max-height: 150px;
  width: 150px;
}



</style>