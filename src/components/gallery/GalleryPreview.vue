<template>

    <div class="gallery-item-preview">
        <img 
            :class="isCurrent ? 'img-preview preview-current' : 'img-preview' "
            :src="image" 
            :idx="idx"
            :isCurrent="isCurrent"
            @click="changeCurrency(idx)"
        />
    </div>
</template>

<script>
export default {
  props: ['image', 'idx', 'current', 'isCurrent', 'totalImages'],
  methods: {
    changeCurrency(idx) {       
    this.$emit('clicked', idx)         
    }
  },
};
</script>

<style>
*{
    overflow:hidden!important;
}
.gallery-item-preview{
    margin: 12.5px;
}
.img-preview {
    width: 100px;
    height: 50px;
    filter: grayscale(100%);
    transition: filter 0.2s ease, transform 0.2s ease;
}
.img-preview:hover{
    cursor: pointer;
    transform: scale(1.5);
    filter: grayscale(0%);
}
.img-preview:hover > .preview-current{
    filter: grayscale(100%);
}
.preview-current{
    filter:none;
}
</style>
