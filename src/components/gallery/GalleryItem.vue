<template>
    <div 
        :class="isCurrent ? 'gallery-item' : 'none'"
    >
        <img 
            :src="image.path" 
            :idx="idx"
            :isCurrent="isCurrent"
            @click="zoomingIn(idx)"
        />
        <div 
            :class="clickedImg === idx ? 'zoomed-img open' : 'none'"
        >
            <button
                :class="clickedImg === idx ? 'closeZoom' : 'none'"
                @click="zoomingOut()"
            >
                &#x2715;
            </button>
            <img 
                :class="clickedImg === idx ? 'zoomed' : 'none'"
                :src="image.path" 
                :idx="idx"
                :isCurrent="isCurrent"
                @click="zoomingOut()"
            />
        </div>
    </div>
</template>

<script>
export default {
  props: ['image', 'idx', 'current'],
  data:() => ({
    clickedImg: null,
    isCurrent: null,
  }),
    watch: {
        current: function (val) {
            if ( val || val === 0 )
                this.setIsCurrent( parseInt(val) === this.idx );
        }
  },
  methods: {
    setIsCurrent(currency){
        this.isCurrent = currency;
    },
    setClickedImg(idx){
        this.clickedImg = idx;
    },
    zoomingIn(idx){
        this.setClickedImg(idx);
    },
    zoomingOut(){
        this.setClickedImg(null);
    }
  }
};
</script>

<style>

.gallery-item > img {
    width: 100%;
    height: 100%;
    max-width: 150vw;
    max-height: 30vw;
}
.gallery-item > img {
    transition: transform 0.2s linear;
}
.gallery-item > img:hover {
    cursor: zoom-in;
}
.none{
    display: none;
}
.zoomed-img.open{
    background: rgba(0,0,0,.7);
    position: fixed;
    width: 100%;
    height: 100%;
    top: 0;
    left: 0;
    z-index: 3;
}

img.zoomed{
    width: 90%;
    height: 90%;
    max-width: 100vw;
    max-height: 100vw;
    margin: 2.5% 5%;
}
img.zoomed:hover{
    cursor: zoom-out;
}
.closeZoom{
    background: none;
    border: none;
    position: fixed;
    margin-left: 93.5%;
    font-size: 2em;
    color: black;
    transition: color 0.8s linear;
}
.closeZoom:hover{
    color: #00C9C8;
    cursor: pointer;
}

</style>
