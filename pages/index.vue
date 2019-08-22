<template>
  <v-layout
    column
    justify-center
    align-center
  >
    <v-flex
      xs12
      sm8
      md6
    >
      <div class="content-wrapper">
        <!-- Displays if myData is not set. -->
        <facebook-loader v-if="!myData"
          :height="475"
          :width="400"
          :speed="2"
          primaryColor="#f3f3f3"
          secondaryColor="#ecebeb"
        >
      </facebook-loader>
        <div v-else class="my-real-content">
          <div class="text-center">
            <logo />
            <vuetify-logo />
          </div>
          <div class="text-xs-center" style="width:90%;margin-top:20px;">
            <div style="text-align:left;margin-bottom:10px;">Product description</div>
            <vue-editor v-model="description" :editorToolbar="customToolbar"></vue-editor>
            <v-image-input
              v-model="imageData"
              :image-quality="0.85"
              clearable
              uploadIcon="mdi-cloud-upload-outline"
              rotateClockwiseIcon="mdi-rotate-right"
              rotateCounterclockwiseIcon="mdi-rotate-left"
              flipHorizontallyIcon="mdi-flip-horizontal"
              flipVerticallyIcon="mdi-flip-vertical"
            />
          </div>
        </div>
      </div>
      <v-card-title class="headline">
        E-merse Test Platform for Plugins
      </v-card-title>
      <v-card-text>
        <v-row align="center"> 
          <v-col class="d-flex" cols="12" sm="6">
            <v-select
              item-text="name"
              item-value="abbr"
              :items="items"
              label="Outlined style"
              outlined
            ></v-select>
          </v-col>
        </v-row>
      </v-card-text>
      <v-card-actions>
        <v-spacer />
        <v-btn
          color="primary"
          nuxt
          @click="toggleShow"
        >
          Set Avatar
        </v-btn>
      </v-card-actions>
      <v-card>
      </v-card>
    </v-flex>
  </v-layout>
</template>

<script>
import Logo from '~/components/Logo.vue'
import VuetifyLogo from '~/components/VuetifyLogo.vue'
import country from 'country-data'
import { FacebookLoader } from 'vue-content-loader'
import VImageInput from 'vuetify-image-input'

export default {
  data() {
    return {
      items: [
        { abbr: 'USD', name: 'United States Dollar' },
        { abbr: 'KES', name: 'Kenyan shilling' },
        { abbr: 'EUR', name: 'Euro' },
        { abbr: 'GBP', name: 'Pound sterling' },
        { abbr: 'CHF', name: 'Swiss franc' },
        { abbr: 'CAD', name: 'Canada Dollar' },
        { abbr: 'JPY', name: 'Japanese yen' },
        { abbr: 'AUD', name: 'Australian dollar' },
        { abbr: 'INR', name: 'Indian rupee' },
        { abbr: 'NGN', name: 'Nigerian naira' }
      ],
      customToolbar: [
        ["bold", "italic", "underline"],
        [{ list: "ordered" }, { list: "bullet" }],
      ],
      show: true,
      params: {
				token: '123456798',
				name: 'avatar'
			},
      description: '',
      productname: '',
      productprice: '',
      headers: {
				smail: '*_~'
			},
      imgDataUrl: '', // the datebase64 url of created image
      myData: null
    }
  },
  components: {
    [VImageInput.name]: VImageInput,
    Logo,
    VuetifyLogo,
    FacebookLoader
  },
  mounted() {
    // Just pretend this is an AJAX call. Use your imagination.
    setTimeout(() => {
      this.myData = 'Example Data';
    }, 3000);
  },
  methods: {
    toggleShow() {
      this.show = !this.show;
      // console.log(Object.values(country.currencies).slice(0,20))
      console.log(country.currencies)
    }
  }
}
</script>
