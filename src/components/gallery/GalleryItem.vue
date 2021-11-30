<template>
    <div class="gallery-item" v-show="current === idx">
        <img 
            :src="image" 
            :idx="idx"
            :isCurrent="isCurrent"
        />
    </div>
</template>

<script>
export default {
  props: ['image', 'idx', 'current', 'isCurrent'],
};
</script>

<style>
.gallery-item{
}
.rect{
    background-color: red;
    height: 50px;
    width: 50px
}

img {
    width: 100%;
    height: 100%;
    max-width: 100vw;
    max-height: 40vw;
}

.slide-in-enter-active,
.slide-in-leave-active{
    transition: all 1s ease-in-out;
}

.slide-in-enter-from{
    transform: translateX(0%)
}
.slide-in-leave-to{
    transform: translateX(-100%)
}

</style>
