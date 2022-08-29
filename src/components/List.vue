<template>
    <div class="list">
        <h1>Products</h1>
        <hr />
        <table
            class="table table-dark table-striped table-bordered table-hover"
            aria-label="Product list"
        >
            <thead>
                <tr>
                    <th scope="col">Product</th>
                    <th scope="col">Description</th>
                    <th scope="col">Quantity</th>
                    <th scope="col">Price</th>
                    <th scope="col">Edit</th>
                    <th scope="col">Delete</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(product, index) in products" :key="index">
                    <th class="align-middle" scope="row">{{ product.name }}</th>
                    <td class="align-middle">{{ product.description }}</td>
                    <td class="align-middle">{{ product.quantity }}</td>
                    <td class="align-middle">
                        {{ product.price }} <span v-if="product.price">€</span>
                    </td>
                    <td>
                        <router-link
                            type="button"
                            class="btn btn-warning align-middle"
                            :to="{
                                name: 'edit',
                                params: { id: product.id },
                            }"
                            tag="button"
                            >Edit</router-link
                        >
                    </td>
                    <td>
                        <button
                            type="button"
                            @click="deleteProduct(product.id)"
                            class="btn btn-danger align-middle"
                        >
                            Delete
                        </button>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
import axios from "axios";

export default {
    name: "List",
    data() {
        return {
            products: [],
            error: [],
        };
    },
    methods: {
        async deleteProduct(id) {
            await axios
                .delete("http://localhost:8000/api/json/delete/" + id)
                .then(function (response) {
                    alert(response.data);
                    location.reload();
                })
                .catch((error) => {
                    alert(error.response.data);
                });
        },
    },
    async mounted() {
        await axios
            .get("http://localhost:8000/api/json/get")
            .then((response) => (this.products = response.data))
            .catch((error) => {
                alert(error.response.data);
            });
    },
};
</script>

<style scoped>
h1 {
    margin-top: 1em;
    font-size: 2em;
    text-align: center;
}

hr {
    height: 2px;
    margin-bottom: 4em;
    background-image: linear-gradient(to right, #1f2833, #ffffff, #1f2833);
}

th,
tr {
    text-align: center;
}

.list {
    padding: 3em 0 10em;
    width: 65vw;
}
</style>