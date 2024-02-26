
<script setup>
import { ref } from "vue";



const items = ref([

    {
        title: "What is Html?",
        content:
        "The HyperText Markup Language or HTML is the standart markup language....",
        open: false,
    },
    {
        title: "What is Css?",
        content:
        "The HyperText Markup Language or Css is the standart markup language....",
        open: false,
    },
    {
        title: "What is JS?",
        content:
        "The HyperText Markup Language or JS is the standart markup language....",
        open: false,
    },
])



const toggleAccordion = (index) => {
    items.value = items.value.map((item,i) => ({
        ...item,
        open: i === index ? !item.open : false
    }))
}
</script>



<template>
    <div class="accordion">
        <div v-for="(item, index) in items" :key="index" class="accordion">
            <div class="accordion-header" @click="toggleAccordion(index)">
            {{ item.title }}
        <span class="arrow-icon">{{ item.open ? "⬇️" : "➡️" }}</span>
            </div>
            <div v-show="item.open" class="accordion-content">
            {{ item.content }}</div>
        </div>
    </div>
</template>

<style scoped>
/* 
.accordion-container {
    max-width: 600px;
    margin: 50px auto;
} */

.accordion{
    border: 1px solid #ddd;
    border-radius: 4px;
    overflow: hidden;
    margin-bottom: 10px;
}

.accordion-header {
    background-color: #3498db;
    color: #fff;
    padding: 15px;
    cursor: pointer;
    display: flex;
    justify-content: space-between; /*ilk öğe başına son öğeyi sonuna koymak için */
    align-items: center;
}

.arrow-icon {
    font-size: 20px;
}

.accordion-content {
    padding: 15px;
    display: none;
    border-top: 1px solid #ddd;
    background-color: #977373;
    color: #333;
}

.accordion-content[style] {
    display: block;
} 
</style>
