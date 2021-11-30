<template>
    <button id="prev" class="control prev-control" @click="$emit('prev')">
        &#x2039;
    </button>
    <button id="next" class="control next-control" @click="$emit('next')">
        &#x203A;
    </button>
</template>

<script>
    export default {
        emits: ['prev', 'next']
    }
</script>
<style>
.control{
    background: rgba(50, 75, 74, .5);
    border: none;
    display: flex;
    display: flex;
    z-index: 2;
    top: 0%;
    width: 7.5%;
    font-size: 2em;
    flex-direction: row;
    flex-wrap: nowrap;
    align-content: center;
    justify-content: center;
    align-items: center;
    height: 100%;
    position: absolute;
    font-size: 2em;
    color: #00C9C8;
    border: none;
    transition: background 0.8s ease, color 0.8s ease;
}
.control:hover{
    cursor: pointer;
    color: #003A3D;
    background: rgba(0, 201, 200, .5);
}
.next-control{
    float: right;
    left: 92.5%;
}
.control--hided{
    visibility: hidden;
}
.control--showed{
    visibility: visible;
}
</style>