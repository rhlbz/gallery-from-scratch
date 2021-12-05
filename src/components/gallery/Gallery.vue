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
        :image="image.path"
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

  props: ['images', 'selected' ],

  data: () => ({
    current: null
  }),

  watch: {
    selected: function (val) {
      this.setCurrent(parseInt(val));
    }
  },

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
.gallery {
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
	100% { transform: translateX(calc(-150px * 7))}
}
.preview {
  background: white;
	margin: auto;
	overflow:hidden;
	position: relative;
	min-width: 480px;
	max-width: 960px;
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
  animation: scroll 60s linear infinite;
  display: flex;
  width: calc(150px * 14);
}
.preview--content > .gallery-item-preview {
  min-height: 100px;
  height: 150px;
  max-height: 150px;
  width: 150px;
}

@media screen and (max-width: 320px) {
  .gallery--content{
    max-width: 200vw;
    max-height: 50vw;
  }
  .gallery-item > img {
    width: 100%;
    height: 100%;
    max-width: 200vw;
    max-height: 50vw;
  }

  .divider, .preview {
    display: none;    
  }
}
@media screen and (min-width: 320px) and (max-width: 570px){
  .gallery--content{
    max-width: 200vw;
    max-height: 50vw;
  }
  .gallery-item > img {
    width: 100%;
    height: 100%;
    max-width: 200vw;
    max-height: 50vw;
  }

  .divider, .preview {
    display: none;    
  }
}
@media screen and (min-width: 570px) and (max-width: 768px){
  .gallery--content{
    max-width: 150vw;
    max-height: 70vw;
  }
  .gallery-item > img {
    width: 100%;
    height: 100%;
    max-width: 200vw;
    max-height: 70vw;
  }

  .divider, .preview {
    display: none;    
  }
}
@media screen and (min-width: 768px) and (max-width: 980px){
  .gallery--content{
    max-width: 150vw;
    max-height: 50vw;
  }
  .gallery-item > img {
    width: 100%;
    height: 100%;
    max-width: 150vw;
    max-height: 50vw;
  }
}
@media screen and (min-width: 989px) and (max-width: 1224px){
  .gallery-content{
    max-width: 150vw;
    max-height: 40vw;
  }
  .gallery-item > img {
    width: 100%;
    height: 100%;
    max-width: 150vw;
    max-height: 40vw;
  }
}
@media screen and (min-width: 1224px) {
  .gallery-content{
    max-width: 150vw;
    max-height: 32vw;
  }
  .gallery-item > img {
    width: 100%;
    height: 100%;
    max-width: 150vw;
    max-height: 32vw;
  }
}
</style>