<template>
    <div 
        class='controls--content'
    >
        <button 
            id="prev" 
            class='control prev-control gallery-controls'
            @click="$emit('prev')"
        >
            &#x2039;
        </button>
        <button 
            id="next" 
            class='control next-control gallery-controls'
            @click="$emit('next')"
        >
            &#x203A;
        </button>
    </div>
</template>

<script>
    export default {
        props: ['forPreview'],
        emits: ['prev', 'next']
    }
</script>
<style>
.preview--controls--content{    
    position: relative;
}
.control.gallery-controls{
    background: rgba(50, 75, 74, .7);
    display: flex;
    z-index: 2;
    top: 45%;
    width: 7.5%;
    font-size: 2em;
    flex-direction: row;
    flex-wrap: nowrap;
    align-content: center;
    justify-content: center;
    align-items: center;
    height: 10%;
    position: absolute;
    color: white;
    border: none;
    transition: background 0.4s linear, color 0.4s linear;
}
.control.info-control{
    background: rgba(50, 75, 74, .7);
    display: flex;
    z-index: 2;
    top: 92.5%;
    width: 7.5%;
    font-size: 2em;
    flex-direction: row;
    flex-wrap: nowrap;
    align-content: center;
    justify-content: center;
    align-items: center;
    height: 10%;
    position: absolute;
    color: white;
    border: none;
    transition: background 0.4s linear, color 0.4s linear;
}
.control.gallery-controls:hover{
    cursor: pointer;
    color: #003A3D;
    background: rgba(0, 201, 200, .7);
}
.control.preview-controls{
    background: rgba(50, 75, 74, .7);
    display: flex;
    z-index: 2;
    width: 2%;
    font-size: 1.5em;
    flex-direction: row;
    flex-wrap: nowrap;
    align-content: center;
    justify-content: center;
    align-items: center;
    position: absolute;
    color: white;
    border: none;
    transition: background 0.8s linear, color 0.8s linear;
}
.control.preview-controls:hover{
    cursor: pointer;
    color: #003A3D;
    background: rgba(0, 201, 200, .7);
}
.next-control.gallery-controls{
    left: 92.5%;
}
.next-control.preview-controls {
    left: 67%;
}

</style>