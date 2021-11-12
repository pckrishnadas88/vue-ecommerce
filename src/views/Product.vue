<template>
  <div class="home container">
    <div v-if="product" class="row mt-5">
        <div class="col-md-6">
            <div id="carouselExampleIndicators" class="carousel slide" data-ride="carousel">
                <ol class="carousel-indicators">
                    <template v-for="(item, index) in product.images">
                        <li 
                        :key="item.id" 
                        data-target="#carouselExampleIndicators" 
                        :data-slide-to="index"
                        v-bind:class="{ 'active': index ===0}"
                        >
                            
                        </li>                        
                    </template>
                </ol>
                <div class="carousel-inner">
                    <template v-for="(item, index) in product.images">
                        <div 
                        :key="item.id"
                        class="carousel-item"
                        v-bind:class="{ 'active': index ===0}"                        
                        >
                        <img :src="`http://localhost:8000/product-images/${ item.image }`" class="d-block w-100" alt="...">
                        </div>
                    </template>
                
                </div>
                <button class="carousel-control-prev" type="button" data-target="#carouselExampleIndicators" data-slide="prev">
                <span class="carousel-control-prev-icon" aria-hidden="true"></span>
                <span class="sr-only">Previous</span>
                </button>
                <button class="carousel-control-next" type="button" data-target="#carouselExampleIndicators" data-slide="next">
                <span class="carousel-control-next-icon" aria-hidden="true"></span>
                <span class="sr-only">Next</span>
                </button>
            </div>
            
        </div>
        <div class="col-md-6" style="text-align:left;">
            <h1>{{ product.title }}</h1>
            <h3 class="text-primary mt-3">&#8377; {{ product.price }}</h3>
            <div class="badge badge-warning mt-4" style="font-size:21px;">{{product.category.name}}</div>
            <p class="mt-4">{{ product.description}}</p>
            <p class="mt-4">Quantity <input type="number" min="1" :max="product.quantity" value="1" size="3"></p>
            <button type="button" class="btn btn-primary mt-4"><i class="bi bi-cart-plus"></i> Add to Cart</button>
        </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
// @ is an alias to /src

export default {
  name: "Product",
  data () {
    return {
      product: null
    }
  },
  mounted () {
      console.log(this.$route.params.id )
      const API_URL = "http://localhost:8000/api/products/"+ this.$route.params.id;
    axios
      .get(API_URL)
      .then(response => {        
        this.product = response.data.data;
        console.log(response);   
      })
      .catch(function (error) {
        console.log(error);
    }) 
  },
  components: {
    //HelloWorld,
  },
};
</script>
