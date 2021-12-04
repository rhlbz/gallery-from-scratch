<template>
    <div class="album-item">
        
        <img
            :src="image"
            :idx="idx"
            :selected="selected"
            :id="`img-${idx}`"
            @click="changeSelected(idx)"
        />
        
    </div>
</template>

<script>
export default {
    data:() => ({
        hovering: false
    }),
    props: ['image', 'idx', 'selected'],

    mounted() {
        console.log(" this.images ", this.image)
        console.log(" this.image ", this.imag)
        console.log(" this.idx ", this.image)
    },
    methods: {
        changeSelected(idx){
            this.$emit('clicked', idx);
        },
        hover(bool){
            this.hovering = bool;
        }

    }
}
</script>
<style>
.grid-item {
    max-width: 300px;
    max-height: 200px;
    min-width: 150px;
    min-height: 100px;
    display: flex;
    flex-wrap: nowrap;
    align-content: center;
    flex-direction: column;
    align-items: center;
    justify-content: flex-end;
}
.grid-item > img {
    width: 97.5%;
    height: 97.5%;
    max-width: 150vw;
    max-height: 30vw;
    border: 2.5px solid white;
}
.none{
    display: none;
}

</style>