<template>
    <div class="card card-item" style="width: 14rem;">
        <router-link :to="`/product/${item._id}`" style="text-decoration: none; color: inherit;">
        <img :src="`${item.cover}`" height="325" width="225" class="card-img-center cover" alt="...">
        <div class="badges-hot" v-if="item.hot">Hot</div>
        <div class="card-body">
            <p class="card-title">Tên sách: {{ item.title }}</p>
            <p class="card-author">Tên tác giả: {{ item.author }}</p>
            <p class="card-price">Đơn giá: {{ item.price }} vnđ/quyển</p>
        </div>
        </router-link>
    </div>
</template>

<script>
export default {
    name:"Item",
    props: [
        "item"
    ]
}
</script>
<style>
.card-item {
    margin: 14px;
    width: 23%;
    border: 2px solid black;
    border-radius: 0;
}

.card-img-center {
    width: 100%;
    height: 95%;
    padding: 10px;
}


.card-author, .card-title, .card-price  {
    justify-content: center;
    display: flex;
    border: 2px solid black;
    border-radius: 5px;
    background: yellow;
    margin: 10px 0;
}

.badges-hot {
    position: absolute;
    top: 6px;
    left: 8px;
    background: #f0163a;
    color: #fff;
    padding: 8px;
    border-radius: 50%;
}

</style>