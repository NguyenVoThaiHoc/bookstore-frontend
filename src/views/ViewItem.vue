<template>
    <div>
        <Header />
        <div class="container">
            <div class="row">
                <div class="alert" v-if="message" :class="alert" role="alert">
                {{ message }}
                </div>
                <div class="col-md-4 img-cover">
                    <img :src="`${item.cover}`" height="500" width="390" alt="cover_img" srcset="">
                </div>
                <div class="col-md-8 info">
                    <h2>Tên sách: {{ item.title }}</h2>
                    <h5>Tác giả: {{ item.author }}</h5>
                    <p>Mô tả: {{ item.desc }}</p>
                    <p>Số lượng còn lại: {{ item.number }}</p>
                    <p>Thể loại: {{ item.category }}</p>
                    <p class="price">Đơn giá: {{ item.price }} vnđ/quyển</p>
                    <div class="quantity-toggle">
                        <button @click="decrement()">&mdash;</button>
                        <input type="text" :value="quantity" readonly>
                        <button @click="increment()">&#xff0b;</button>
                    </div>
                    <button type="button" class="btn btn-danger" @click="addToCart">Thêm vào giỏ hàng</button>
                </div>
            </div>
        </div>
    </div>
        <Footer />
</template>
<script>
import Header from "../components/Header.vue";
import Footer from "../components/Footer.vue";
import { mapGetters } from "vuex";
import http from "../common/http";

export default {
    name:"ViewItem",
    components: {
        Header, Footer
    },

    props: [
        "id"
    ],

    data() {
        return {
            item: null,
            quantity: 1,
            message: "",
            fail: false
        }
    },

    methods: {
        addToCart(){
            if(this.quantity > 0 && this.quantity < this.item.number){
                this.$store.dispatch('addToCart', {
                    product: this.item,
                    quantity: this.quantity
                });
                this.message = "Thêm vào giỏ hàng thành công";
                this.fail = false;
            } else{
                alert('ko co don hang');
                this.message = "Sản phẩm chưa chọn số lượng";
                this.fail = true;
            }
        },

        increment () {
            this.quantity++
        },

        decrement () {
            if(this.quantity == 1) {
                alert('Số lượng phải lớn hơn 0');
            } else {
                this.quantity--
            }
        }
    },

    computed: {
        ...mapGetters([
            "getProductInCart"
        ]),
        alert() {
            if(!this.fail) return 'alert-success';
            else return 'alert-danger';
        }
    },
    
    created() {
        http.get(`/product/${this.$route.params.id}`)
        .then(response => {
            this.item = response.data;
        });
    },
}
</script>

<style>
.row {
    justify-content: center;
}

.img-cover, .info {
    margin: 24px 18px 0 0;
}

.info{
    letter-spacing: 0.2px;
    line-height: 1.8;
    width: 30%;
}

.img-cover {
    padding: 0px;
    width: 30%;
    padding: 1.25px;
    border: 2px solid black;
    background-color: black;
}

.price {
    line-height: 2;
    font-size: 32px;
}

.quantity {
    display: flex;
}

.quantity-toggle {
  display: flex;
  margin: 8px;
}

.quantity-toggle input {
  border: 0;
  border-top: 2px solid #ddd;
  border-bottom: 2px solid #ddd;
  width: 2.5rem;
  text-align: center;
  padding: 0 0.5rem;
}

.quantity-toggle button {
  border: 2px solid #ddd;
  padding: 0.5rem;
  background: #f5f5f5;
  color: #888;
  font-size: 1rem;
  cursor: pointer;
}
</style>