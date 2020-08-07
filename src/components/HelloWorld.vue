<template>
  <div class="hello">
    <h1>{{ $t("greetings.hello-firstname", { firstname }) }}</h1>

    <h2>{{ $t("shop-list.title") }}</h2>

    <p>
      <input
        v-model="productname"
        type="text"
        :placeholder="$t('shop-list.product-name')"
      />
      <button @click="add" type="button">{{ $t("actions.add") }}</button>
    </p>

    <p v-for="(product, index) of products" :key="index">
      {{ product.name }}
      <button @click="remove(product)" type="button">
        {{ $t("actions.delete") }}
      </button>
    </p>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data: () => {
    return {
      firstname: "Julian",
      productname: null,
      products: [],
    };
  },
  methods: {
    add() {
      if (!this.products.some(({ name }) => name === this.productname)) {
        this.products.push({
          name: this.productname,
        });
        this.productname = "";
      }
    },
    remove({ name }) {
      this.products = this.products.filter((product) => product.name !== name);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
