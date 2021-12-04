<template>

    
    <album-item
        v-for="(item, idx) in images"
        :key="idx"
        :idx="idx"
        :class="selected !== null ? 'none' : ''"
        :image="item"
        @click="changeAlbum()"
    ></album-item>


</template>

<script>
import AlbumItem  from './AlbumItem.vue';

export default {
    components: { AlbumItem },
    props: ['images'],
    data: () => ({
        album: null,
    }),

    methods: {
        setAlbum(idx, back = false){
            if ( back ){
                this.album = null
            } else if ( idx ){
                this.album = idx
            }
        },
        changeAlbum(){
            let _targetId = event.target.id.split('-');
            const id = _targetId[_targetId.length-1];
            if ( parseInt(id) || parseInt(id) === 0)
                this.setAlbum(id)
        },
        goToAlbums(){
            this.setAlbum(null, true);
        }
    },

    mounted() {
        console.log(" this.images ", this.images)
    }
}
</script>

<style>

</style>