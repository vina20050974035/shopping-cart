<template>
    <div class="container-fluid" >
        <div class="card mx-auto mt-5 shadow-lg rounded-0" style="width: 80rem;">
            <div class="card-header">
                <h3>Keranjang Belanja</h3>
            </div>
            <div class="card-body">
                <table class="table table-primary">
                    <thead>
                    <tr>
                        <th>Nama Barang</th>
                        <th>Jumlah Barang</th>
                        <th>Harga</th>
                        <th></th>
                    </tr>
                    </thead>
                    <tbody class="table-light">
                        <tr v-for="item in carts" :key="item.idProduk">
                            <td>{{ item.name }}</td>
                            <td>{{ item.qty }}</td>
                            <td>Rp. {{ item.subTotal }}</td>
                            <td><button class="button2" @click="subtractCarts(item.idProduk)" style="border-radius: 10px; width: 5rem; font-style: oblique;">Remove</button></td>
                        </tr>
                        <tr>
                            <td><button class="button3" @click="checkout" style="border-radius: 10px; width: 5rem;">Checkout</button></td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: ['carts'],
    data() {
        return {
            total: 0
        }
    },
    methods: {
        subtractCarts(id) {
            this.carts.forEach((cart) => {
                if (cart.idProduk == id) {
                    if (cart.qty === 0) {
                        this.carts.splice(this.carts.indexOf(cart), 1);
                        console.log(cart.subTotal)
                    } else {
                        cart.qty -= 1;
                        cart.subTotal = cart.qty * cart.price;
                    }
                }
            });
        },
        checkout() {
            this.carts.forEach((cart) => {
                this.total += cart.subTotal;
            });
            if (this.carts.length !== 0) {
                alert("Total Pembelian Anda Adalah Rp." + this.total);
                location.reload();
            }
        },
    }
}
</script>

<style>
    
</style>