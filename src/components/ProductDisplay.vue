<template>
    <div class="product-display">
        <div class="kanan-container">
            <img src="../assets/intersect.png" alt="img">
        </div>
        <div class="kiri-container">
            <h1>Lock and Love Women's Removable Hooded Faux Leather Moto Biker Jacket</h1>
            <div>
                <div class="detail-container">
                    <p>women's clothing</p>
                    <div class="rate-container">
                        <p>2.9/5</p>
                        <div class="rate-img-container">
                            <img src="../assets/ellipse-isi.png" alt="rate-1">
                            <img src="../assets/ellipse-isi.png" alt="rate-2">
                            <img src="../assets/ellipse-isi.png" alt="rate-3">
                            <img src="../assets/ellipse-kosong.png" alt="rate-4">
                            <img src="../assets/ellipse-kosong.png" alt="rate-5">
                        </div>
                    </div>
                </div>
                
                <hr>
                <div class="description">
                    <p>
                        100% POLYURETHANE(shell) 100% POLYESTER(lining) 75% POLYESTER 25% COTTON (SWEATER), Faux leather material for style and comfort / 2 pockets of front, 2-For-One Hooded denim style faux leather jacket, Button detail on waist / Detail stitching at sides, HAND WASH ONLY / DO NOT BLEACH / LINE DRY / DO NOT IRON
                    </p>
                </div>
                <hr>
                <div>
                    <h1>$29.95</h1>
                    <div class="button-container">
                        <a href="https://www.github.com" class="btn-buy">Buy Now</a>
                        <button @click="clickedNextButton()" class="btn-next">Next Product</button>
                        
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import axios from "axios";

    const http = axios.create({
        baseURL: "https://fakestoreapi.com/",
        headers: {
            "Content-Type": "application/json"
        }
    })

    export default {
        name: "productDisplay",
        data() {
            return {
                currentProduct: null,
                message : ``,
                id: 1
            };
        },
        methods: {
            getProduct(id) {
                return http
                .get(`/products/${id}`)
                .then(res => {
                    this.currentProduct = res.data;
                    console.log(res.data);
                })
                .catch(e => {
                    console.log(e);
                })
            },
            clickedNextButton() {
                this.id += 1;
                console.log("clicked")
                console.log("id = " + this.id)
            }
            
        },
        mounted() {
            this.message = '';
            this.getProduct(this.id);
        }
    }

    

    // const data = new EcommerceDataService();
    // data.get(1)
    // .then(res => {
    //     console.log(res);
    // })
</script>

<style scope>
    
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
    .button-container {
        
        font-weight:bold;
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

    .kiri-container {
        margin: 40px;
    }
</style>