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
        v-for="(image, idx) in previews"
        :image="image"
        :key="`item-preview-${idx}`"
        :current="current"
        :isCurrent="idx === current ? true : false"
        :idx="idx"
        :totalImages="images.length-1"
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
      previews: [],
  }),
  methods: {
      setCurrent(idx){
          this.current = idx;
      },
      setPreviewIdx(idx){
        this.previewIdx = idx;
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
      },
      initPreviews(){
        this.previews = [...this.images];
      },
      setPreviews(previews){
        this.previews = previews;
      },

  },
  mounted() {
    this.initPreviews();
  },

};
</script>
<style>
*{
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
  border-color: rgba(0, 201, 200, 0.5);
  background-color: rgba(0, 201, 200, 0.5);
  color: rgba(0, 201, 200, 0.5);
  width: 70%;
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
  height: 100px;
  position: absolute;
  width: 200px;
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