<template>
<div id="app">
  <input v-model="searchQuery" placeholder="Search by category">
  
  <div class="wrapper">
    <div class="row">
      <div v-for="product in filteredProducts" :key="product.id" class="col">
        <div class="prodCard">
          <img :src="product.image" alt="Product Image">
          <h3>{{ product.prodName }}</h3>
          <p :class="[product.amount > 420000 ? 'expensive' : 'cheap']">
            R{{ product.amount.toFixed(2) }}
          </p>
          <a href="#">View Detail</a>
        </div>
      </div>
    </div>
  </div>
  
  <p v-if="filteredProducts.length === 0">Sorry, we have no products matching the search.</p>
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
          image: 'https://i.postimg.cc/SK4yzTqC/opheus-mourning-the-death-of-eurydice.jpg',
        },
        {
          id: 2, 
          prodName: 'The fall of Icarus',
          category: 'Icarus',
          amount: 450000,
          image: 'https://i.postimg.cc/FHz9bdJs/fall-of-icarus.jpg'
        },
      {
        id: 3, 
        prodName: 'Man begging for his woman back',
        category: 'man',
        amount: 500000,
        image: 'https://i.postimg.cc/NMcqn5LX/bronte-cover.jpg'
      },
      {
        id: 4,
        prodName: 'Psyche Obtaining the Elixir of Beauty from Proserpine',
        category: 'Psyche',
        amount: 782196,
        image: 'https://i.postimg.cc/5NkWFBLn/Psyche-Obtaining-the-Elixir-of-Beauty-from-Proserpine.jpg'
      }
      ],
      searchQuery: '',

      computed: {
  filteredProducts() {
    if (this.searchQuery === '') {
      return this.products;
    } else {
      return this.products.filter((product) => {
        return product.category.toLowerCase().includes(this.searchQuery.toLowerCase());
      });
    }
  }
}
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
