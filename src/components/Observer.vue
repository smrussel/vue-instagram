<script setup>
import {ref,onMounted} from "vue"

const observer = ref(null)
const root = ref(null)

const emits = defineEmits(["intersect"])

onMounted(()=>{
    observer.value = new IntersectionObserver(([entry])=>{
        // console.log(entry)
        if(entry && entry.isIntersecting){
            emits("intersect")
        }

    })

    observer.value.observe(root.value)
})

</script>

<template>
    <div class="observer" ref="root">

    </div>
</template>

<style scoped>
.observer{
    height: 30px;
}
</style>