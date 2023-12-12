<template>
 <div class="wrapper">
    <div class="row" v-if="products.length">
      <div class="prodCard" v-for="product in products" :key="product.id">
        <div class="card-header">
          <h3>{{ product.prodName }}</h3>
        </div>
        <div class="card-body">
          <img @mouseenter="onMouseEnter" @mouseleave="onMouseLeave" :src="product.image" :alt="product.prodName" loading="lazy">
          <p :class="product.amount > 420000 ? 'expensive' : 'cheap' ">R{{ product.amount.toFixed(2) }}</p>
        </div>
        <div class="card-footer">
          <a href="#" type="button">View Detail</a>
        </div>
      </div>
    </div>
    <div v-else>
      <h2>Sorry, we are out of stock.</h2>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return{
      products: [ 
        {
          id: 1, 
          prodName: 'Opheus and Eurydice',
          category: 'Opheus and Eurydice',
          amount: 250000,
          image: 'https://freeimage.host/i/JuH7Jqb',
        },
        {
          id: 2, 
          prodName: 'The fall of Icarus',
          category: 'Icarus',
          amount: 450000,
          image: 'https://freeimage.host/i/JuHOOEx'
        },
      {
        id: 3, 
        prodName: 'Man begging for his woman back',
        category: 'man',
        amount: 500000,
        image: 'https://freeimage.host/i/JuHswAb'
      }
      ]
    }

  }
 
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.wrapper :is(.row) {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
}
.prodCard {
  width: 18rem;
}

.prodCard :is(>*, img) {
  width: 100%;
  aspect-ratio: 1/1;
}

.expensive {
  font-weight: bolder;
  color: rgb(241, 179, 227);
}

.cheap {
  color: black;
}
</style>
