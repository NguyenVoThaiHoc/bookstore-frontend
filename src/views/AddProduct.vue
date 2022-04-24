<template>
  <div class="container-fluid">
      <Header />
  <div class="container addProduct">
      <div class="form-container">
            <div class="alert" v-if="message" :class="alert" role="alert">
            {{ message }}
            </div>
            <h5><label for="basic-url" class="form-label">Tiêu đề sách</label></h5>
                <div class="input-group mb-3">
                    <input type="text" class="form-control" placeholder="Nhập tên quyển sách" v-model="product.title">
                </div>

            <h5><label for="basic-url" class="form-label">Tác giả</label></h5>
                <div class="input-group mb-3">
                    <input type="text" class="form-control" placeholder="Nhập tên tác giả" v-model="product.author">
                </div>

            <h5><label for="basic-url" class ="form-label">Thể loại</label></h5>
                <div class="input-group mb-3">
                    <input type="checkbox" class="checkbox" id="Khoa học" placeholder="Nhập thể loại" value="Khoa học" v-model="product.category">
                </div>
            
            <h5><label for="basic-url" class="form-label">Link ảnh bìa</label></h5>
                <div class="input-group mb-3">
                    <input type="text" class="form-control" v-model="product.cover">
                </div>

            <h5><label for="basic-url" class="form-label">Mô tả</label></h5>
                <div class="input-group mb-3">
                    <textarea class="form-control" aria-label="With textarea" rows="5" placeholder="Viết một vài mô tả về quyển sách" v-model="product.desc"></textarea>
                </div>

            <h5><label for="basic-url" class="form-label">Đơn giá</label></h5>
                <div class="input-group mb-3">
                    <input type="number" class="form-control" min ="0" v-model="product.price">
                    <span class="input-group-text"> vnđ/quyển</span>
                </div>

            <h5><label for="basic-url" class="form-label">Số lượng</label></h5>
                <div class="input-group mb-3">
                    <input type="number" class="form-control" min="1" max="9999" v-model="product.number">
                    <span class="input-group-text">quyển</span>
                </div>
            <button class="btn btn-outline-secondary" type="button" @click="addProduct">Thêm</button>
            <button class="btn btn-outline-secondary" type="button" @click="goBack">Hủy</button>
      </div>
  </div>
  </div>
  <Footer/>
</template>

<script>
import Footer from "../components/Footer.vue";
import Header from "../components/Header.vue";
import { mapGetters } from "vuex";
import ProductService from "../services/Product.service";
export default {
    name:"AddProduct",
    data(){
      return {
        product: {
            title: "",
            author: "",
            category: "",
            cover: "",
            desc: "",
            price: 0,
            number: 1
        },
        message: "",
        fail: false
      };
    },
    computed: {
        ...mapGetters([
            "loggedInUser"
        ]),

        alert() {
            if(!this.fail) return 'alert-success';
            else return 'alert-danger';
        }
    },
    methods: {
        async addProduct() {
            const [error] = await this.handle(
                ProductService.addProduct(this.product)
            );
            if(error){ 
                this.message = "Thêm sản phẩm thất bại";
                this.fail = true;
            }
            else{
                this.fail = false;
                this.message = "Thêm sản phẩm thành công";
            } 
        },

        async goBack () {
            return "/Admindashboard";
        }
    },
    
    components: {
      Header, Footer
    }
}
</script>

<style>
    .addProduct {
        width: 50%;
    }

    .checkbox {
        margin: 7px 3px 0 0;
        
    }
    .category {
        display: block;
    }
    .btn-outline-secondary {
        width: 80px;
        margin-right: 8px;
        padding: 5px 10px;
    }
</style>