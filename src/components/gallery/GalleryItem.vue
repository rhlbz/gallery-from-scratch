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

img {
    width: 100%;
    height: 100%;
    max-width: 150vw;
    max-height: 30vw;
}

</style>
