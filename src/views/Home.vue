<template>
  <div class="home container">
    <template v-for="(p) in products">   
     
        <div :key="p.id" class="col-md-4" style="margin-bottom:20px; float:left;">                
            <div class="card" style="width: 20rem;">
                <div class="card-body">
                  <img :src="`http://localhost:8000/product-images/${ p.images[0].image }`" class="card-img-top" >

                    <h5 class="card-title">{{ p.title.substring(0, 25) }}</h5>
                    <h5 class="card-text text-primary">&#8377; {{ p.price }}</h5>
                    <div class="badge badge-warning mt-3 mb-3" style="font-size:15px;"></div>
                    <br>
                    <a :href="`/products/${ p.id }`" class="btn btn-primary">View more details</a>
                </div>
            </div>                
        </div>
                
    </template>
  </div>
</template>

<script>
import axios from 'axios';
// @ is an alias to /src

export default {
  name: "Home",
  data () {
    return {
      products: null
    }
  },
  mounted () {
    axios
      .get("http://localhost:8000/api/products")
      .then(response => {        
        this.products = response.data.data;
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
