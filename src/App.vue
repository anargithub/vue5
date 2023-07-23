<template>
  <div>
    <slide-card
      v-for="slide in slider"
      @prev="(slideId:any)=>prevSlide(slideId)"
      @next="(slideId:any)=>nextSlide(slideId)"
      v-show="slide.view"
      :key="slide.id"
      :slideId="slide.id"
      :title="slide.title"
      :body="slide.body"
    ></slide-card>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import SlideCard from '@/components/SlideCard.vue'
const slider = ref([
  {
    id: 1,
    view: true,
    title: 'Title 1', 
    body: 'Body 1'
  },
  {
    id: 2,
    view: false,
    title: 'Title 2',
    body: 'Body 2'
  },
  {
    id: 3,
    view: false,
    title: 'Title 3',
    body: 'Body 3'
  }
])
function prevSlide(id:number) {
  if (id != 1) {
    slider.value[id-2].view = true
    slider.value[id-1].view = false
  }else{
    slider.value[slider.value.length-1].view = true
    slider.value[id-1].view = false
  }
}
function nextSlide(id:number){
  if(id != slider.value.length){
    slider.value[id].view = true
    slider.value[id-1].view = false
  }else{
    slider.value[0].view = true
    slider.value[id-1].view = false
  }
}
</script>

<style scoped></style>
