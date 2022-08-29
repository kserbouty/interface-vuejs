<template>
    <div class="edit-form">
        <div class="card border-dark bg-dark mb-3">
            <div class="card-header text-white bg-dark">Edit Product</div>
            <div class="card-body text-white bg-secondary">
                <div class="form-group">
                    <label for="Name">Product name :</label>
                    <input
                        v-model="product.name"
                        type="text"
                        class="form-control"
                    />
                    <div class="form-group">
                        <label for="">Description :</label>
                        <textarea
                            v-model="product.description"
                            class="form-control"
                            rows="2"
                        ></textarea>
                    </div>
                    <div class="form-row">
                        <div class="form-group col-md-6">
                            <label for="Quantity">Quantity :</label>
                            <input
                                v-model.number="product.quantity"
                                type="number"
                                class="form-control"
                            />
                        </div>
                        <div class="form-group col-md-6">
                            <label for="Price">Price :</label>
                            <input
                                v-model.number="product.price"
                                type="number"
                                class="form-control"
                            />
                        </div>
                    </div>
                    <div class="button-group">
                        <button type="button" class="btn btn-light">
                            Cancel
                        </button>
                        <button
                            @click="updateProduct()"
                            type="button"
                            class="btn btn-success"
                        >
                            Edit
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import axios from "axios";

export default {
    name: "EditForm",
    data() {
        return {
            product: [],
            error: [],
        };
    },
    methods: {
        updateProduct() {
            axios
                .patch("http://localhost:8000/api/json/update/" + this.id, {
                    name: this.product.name,
                    description: this.product.description,
                    quantity: this.product.quantity,
                    price: this.product.price,
                })
                .then(function (response) {
                    alert(response.data);
                    location.replace("/");
                })
                .catch((error) => {
                    alert(error.response.data);
                });
        },
    },
    created() {
        this.id = this.$route.params.id;
        axios
            .get("http://localhost:8000/api/json/get/" + this.id)
            .then((response) => (this.product = response.data))
            .catch((error) => {
                alert(error.response.data);
            });
    },
};
</script>

<style scoped>
.form-row {
    padding-left: 3em;
}

.button-group {
    display: flex;
    justify-content: center;
    margin-top: 2em;
}

.card-header,
.card-footer {
    text-align: center;
}

button {
    margin: 1.7em 0.7em;
}

.card-body {
    padding: 1em 4em;
}

.form-group label {
    margin-top: 2em;
}

.edit-form {
    margin: 4em;
    width: 55%;
}

#quantity,
#price {
    width: 75%;
}
</style>