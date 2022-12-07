<template>
  <v-container class="grey lighten-5">
    <v-grid>
      <v-row class="d-flex justify-content-between">
        <v-col cols="6" md="6">
        <HelloWorld :product="products"/> 
        <br/>  
        <v-row class="ml-4">
        <!-- <v-btn @click.prevent="Edit" style="background-color: grey" class="ma-4"> Edit </v-btn> -->
        <v-btn @click.prevent="Edit" style="background-color: grey"
      fab
      medium
    >
      <v-icon dark>
        mdi-pencil
      </v-icon>
    </v-btn>
         </v-row>
      </v-col>

      <v-col cols="6">

        <v-form ref="form" v-model="valid" lazy-validation v-if="isSubmited">
          <h3>Edit Form</h3>
          <v-text-field
            v-model="products.image"
            :rules="imageRules"
            label="Image"
            required>
        </v-text-field>

        <v-text-field
            v-model="products.title"
            :rules="titleRules"
            label="Title"
            required>
        </v-text-field>          

        <v-text-field
            v-model="products.link"
            :rules="link"
            label="Link"
            required
          >
        </v-text-field>

          <v-btn
            style="background-color: lightgreen"
            class="mx-2"
            @click="reset"
            elevation="24"
            rounded
          >
            Reset Form
          </v-btn>
        </v-form>
      </v-col>
    </v-row>
    </v-grid>
  </v-container>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'HomeView',
  components: {
    HelloWorld
  },
  data: () => ({
    isSubmited: false,
    valid: true,
    image: "",
    imageRules: [
      (v) => !!v || "Image is required",
      (v) =>
        (v && v.length <= 1000) || "Image must be less than 1000 characters",
    ],
    title: "",
    titleRules: [
      (v) => !!v || "Title is required",
      (v) => /.+@.+\..+/.test(v) || "Title must be valid",
    ],
    link: "",
    linkRules: [
      (v) => !!v || "Link is required",
      (v) => /.+@.+\..+/.test(v) || "Link must be valid",
    ],
    products: 
        {
          title: "Hello!!!",
          image: "https://cdn.vuetifyjs.com/images/cards/docks.jpg",
          link: "https://www.google.com/",
        },
  }),
  methods: {
    reset() {
      this.$refs.form.reset();
    },
    Edit(){
        this.isSubmited=true;
      }
  },
};
</script>
