<template>
  <div>
    <all-product :allProduct="allProduct" @emitAddToCart="addToCart" />
    <cart :carts="carts" />
  </div>
</template>

<script>
export default {
    data() {
        return {
            allProduct: [
                {
                    id: 1,
                    name: "Indomie Goreng Rendang",
                    desc: "Masakan instan terenak di dunia",
                    qty: 25,
                    carts_qty: 0,
                    price: 3000,
                    carts_price: 0,
                },
                {
                    id: 2,
                    name: "Mie Gelas Rendang",
                    desc: "Mie instant khusus anak kosan",
                    qty: 35,
                    carts_qty: 0,
                    price: 1500,
                    carts_price: 0,
                },
                {
                    id: 3,
                    name: "Bakmi Mewah",
                    desc: "Kalau anak kosan jangan macam2 deh",
                    qty: 45,
                    carts_qty: 0,
                    price: 5000,
                    carts_price: 0,
                },
                {
                    id: 4,
                    name: "Mie Lemonilo",
                    desc: "Mari berburu photocard",
                    qty: 55,
                    carts_qty: 0,
                    price: 7000,
                    carts_price: 0,
                }
            ],
            carts: []
        }
    },
    methods: {
        addToCart(id) {
            let produk = this.allProduct.find((item) => item.id == id);
            let cart = this.carts.find((item) => item.idProduk == id);
            let idProduk = produk.id;
            let name = produk.name;
            let price = produk.price;
            if (!cart) {
                let cartTotal = {
                    idProduk: idProduk,
                    name: name,
                    price: price,
                    qty: 1,
                    subTotal: price,
                };
                this.carts.push(cartTotal);
                console.log(cartTotal.imgUrl)
            } else {
                cart.qty++;
                cart.subTotal = cart.qty * cart.price;
            }
        },
    }
}
</script>

<style>
   
    
</style>