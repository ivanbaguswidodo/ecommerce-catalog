

<template>
    <div class="product-display">
      <div class="kanan-container">
        <img :src="currentProduct ? currentProduct.image : ''" alt="img">
      </div>
      <div class="kiri-container">
        <h1>{{ currentProduct ? currentProduct.title : '' }}</h1>
        <div>
          <div class="detail-container">
            <p>{{ currentProduct ? currentProduct.category : '' }}</p>
            <div class="rate-container">
              <p>{{ currentProduct ? currentProduct.rating.rate : '' }}/5</p>
              
              <div class="rate-img-container">
                <img
                  v-for="index in 5"
                  :key="index"
                  :src="getRateImage(index)"
                  :alt="`rate-${index}`"
                />
                
              </div>
            </div>
          </div>
          <hr>
          <div class="description">
            <p>{{ currentProduct ? currentProduct.description : '' }}</p>
          </div>
          <hr>
          <div>
            <h1>{{ currentProduct ? `$${currentProduct.price}` : '' }}</h1>
            <div class="button-container">
              <a :href="currentProduct ? currentProduct.url : ''" class="btn-buy">Buy Now</a>
              <button @click="clickedNextButton()" class="btn-next">Next Product</button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>

<script>
import axios from "axios";
import ellipseIsi from "@/assets/ellipse-isi.png";
import ellipseKosong from "@/assets/ellipse-kosong.png";

const http = axios.create({
  baseURL: "https://fakestoreapi.com/",
  headers: {
    "Content-Type": "application/json"
  }
});

export default {
  name: "productDisplay",
  data() {
    return {
      currentProduct: null,
      id: 1
    };
  },
  methods: {
    
    getProduct(id) {
      return http
        .get(`/products/${id}`)
        .then(res => {
          this.currentProduct = res.data;
        })
        .catch(e => {
          console.log(e);
        });
    },
    clickedNextButton() {
      this.id += 1;
  if (this.id > 20) {
    this.id = 1;
  }
  this.getProduct(this.id);
},
    getRateImage(index) {
  if (this.currentProduct && index <= this.currentProduct.rating.rate) {
    return ellipseIsi;
  } else {
    return ellipseKosong;
  }
}
  },
  mounted() {
    this.getProduct(this.id);
  }
};
</script>

<style scoped>

.button-container .btn-buy {
        margin-right: 15px;
        background-color: #720060;
        color: #FFFF;
        border-radius: 5px;
        font-size: large;
        font-weight: 600;
        padding: 8px 70px;
    }

    .button-container .btn-next {
        border-radius: 5px;
        background-color: #FFFF;
        padding: 8px 50px;
        font-size: large;
        font-weight: 600;
        color: #720060;
        border-color: #720060;
        border: 3px solid #720060;
    }
    .product-display {
        border-radius: 10px;
        background-color: white;
        margin: 50px auto;
        width: 80%;
        height: fit-content;

        padding: 60px;
        display: flex;

        box-shadow: 10px 10px 25px rgba(0, 0, 0, 0.35); text-shadow: 10px 10px 25px rgba(0, 0, 0, 0.35);
    }

    .product-display h1 {
        font-family: 'Inter';
        font-style: normal;
        font-weight: 600;
        font-size: 28px;
        line-height: 34px;

        color: #720060;
    }

    .detail-container {
        display: flex;
        justify-content: space-between;
    }

    .rate-container {
        display: flex;
    }
    .rate-container img {
        margin: 0px 2px;
    }
    .rate-container p {
        margin-right: 10px;
    }
    .rate-img-container img{
        padding: 16px 0px;
    }


.kiri-container {
  margin: 40px;
}

@media screen and (max-width: 768px) {
  .product-display {
    flex-direction: column;
    padding: 30px;
  }

  .kanan-container {
    margin-bottom: 30px;
    text-align: center;
  }

  .kiri-container {
    margin: 0;
  }
}

@media screen and (max-width: 576px) {
  .product-display {
    width: 90%;
    padding: 20px;
  }

  .button-container {
    flex-direction: column;
    align-items: center;
    margin-top: 20px;
  }

  .button-container .btn-buy {
    font-weight:bold;
  }
}
</style>