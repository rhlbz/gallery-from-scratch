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

.gallery-item-preview{
    margin: 12.5px;
}
.img-preview {
    width: 150px;
    height: 100px;
    transition:transform 0.2s linear;
}
.img-preview:hover{
    cursor: pointer;
    transform: scale(1.1);
}
.preview-current{
    filter:none;
}
</style>
