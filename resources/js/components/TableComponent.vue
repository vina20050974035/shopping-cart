<template>
  <div>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-GLhlTQ8iRABdZLl6O3oVMWSktQOp6b7In1Zl3/Jr59b6EGGoI1aFkw7cmDA6j6gD" crossorigin="anonymous">
    <div class="container-fluid" >
        <div class="card mx-auto mt-5 shadow-lg rounded-0" style="width: 80rem;">
            <div class="card-header">
                <h3>Semua Produk</h3>
            </div>
            <div class="card-body">
                <table class="table table-primary">
                    <thead>
                    <tr>
                        <th>No</th>
                        <th>Nama Barang</th>
                        <th>Deskripsi</th>
                        <th>Harga</th>
                        <th>Stok</th>
                        <th></th>
                    </tr>
                    </thead>
                    <tbody class="table-light">
                    <tr v-for="item in allProduct" :key="item.id">
                        <td>{{ item.id }}</td>
                        <td>{{ item.name }}</td>
                        <td>{{ item.desc }}</td>
                        <td>{{ item.price }}</td>
                        <td>{{ item.qty }}</td>
                        <td><button class="button1" @click="addToCart(item.id)" style="border-radius: 10px;">Masukkan Keranjang</button></td>
                    </tr>
                    </tbody>
                </table>
            </div>
        </div>
    </div>
  </div>
</template>

<script>
export default {
    props: ['allProduct'],
    methods: {
        addToCart(id) {
            this.$emit("emitAddToCart", id);
        },
    }
}
</script>

<style>
    
</style>