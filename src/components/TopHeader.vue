<template>
    <section class="hero">     <!-- Heading -->
      <div class="header">
          <h1>{{ header || 'My Shopping List' }}</h1>
         <!-- <button class="btn-secondary" @click="toggle">Add Item</button> -->
      </div>
    </section>
</template>

<script>
export default {
    data () {
        return {
            header: ''
        }
    }
}
</script>

<style scoped>
    .hero {
        background-image: url('@/assets/grocery-app-bg.png');
        height: 200px;
        background-color: rgb(251 191 36);
        background-size: cover;
        padding: 1rem;
    }
    .hero h1 {
        font-size: 1.45rem;
        font-weight: 700;
        color: rgb(28 25 23);
    }
</style>
