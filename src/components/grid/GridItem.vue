<template>
    <div class="grid-item">
        
        <img
            :src="image.path"
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
    transition: filter 0.4s linear;
}
.grid-item > img:hover{
    cursor:pointer;
}

.none{
    display: none;
}
</style>