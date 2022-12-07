<template>
  <v-grid>
    <v-row>
      <v-col>
        <v-card class="mx-auto mt-5" max-width="400">
          <v-img height="400" width="700" :src="product.image">
          </v-img>
          <v-row justify="space-around">
          <v-card-title>
            {{ product.title }} 
          </v-card-title>
        </v-row>
          <v-card-actions>
            <a :href="product.link"> {{ product.link }} </a>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </v-grid>
</template>
<script>
export default {
  name: "HelloWorld",
  props: {
    product: {
      type: Object,
      required: true,
    },
  },
}
</script>