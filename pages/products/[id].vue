<template>
  <div>
    <ProductDetails :product="product" />
  </div>
</template>

<script setup>
definePageMeta({
  layout: "products",
});

const { id } = useRoute().params;
const uri = "https://unique-beijinho-f532cd.netlify.app/getproducts" + id;

//Fetch Products
const { data: product } = await useFetch(uri, { key: id });

if (!product.value) {
  throw createError({
    status: 404,
    statusMessage: "Product not found.",
    fatal: true,
  });
}
</script>

<style scoped></style>
