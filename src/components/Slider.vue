<template>
<div>
    <div style="display:none">{{imgData}}</div>
    <!-- Slider -->
<slider animation="fade" :auto="false" :height="'400px'" style="overflow: initial">
  <slider-item v-for="(value, key) in imagesObj" :key="key">
      <img :src="value.img" style="display:none;">
        <div class="main-wrapper" v-bind:style="{background: 'url('+value.img+') center center', backgroundSize: 'cover'}" ref="cover" :key="key">
            <h3>{{value.title}}</h3>
            <p v-if="value.description">{{value.description}}</p>
        </div>
  </slider-item>
</slider>  
</div>
</template>

<script>
import { Slider, SliderItem } from 'vue-easy-slider'
export default {
    props: ["imgData"],
    data(){
        return{
            imagesObj: null,
        }
    },
    created(){
        this.imagesObj = this.$props.imgData        
    },
    updated(){
        this.imagesObj = this.$props.imgData
    },
    components: {
        Slider,
        SliderItem
    },
}
</script>

<style>
.main-wrapper{
    margin: 0 auto;
    width: 100%;
    height: 400px;
    position: relative;
    background-size: cover !important;
}

.main-wrapper h3{
    background: rgba(0,0,0,0.5);
    padding: 10px;
    color: white;
}

.main-wrapper p{
    position: absolute;
    bottom: 0;
    background: rgba(0,0,0,0.5);
    margin: 0;
    padding: 10px;
    color: white;
    font-size: 20px;
    width: 780px;
}
.items{
    top: -19px !important;
}
</style>
