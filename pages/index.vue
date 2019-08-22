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
        <content-loader
          v-if="!myData"
          :height="500"
          :width="400"
          :speed="2"
          primaryColor="#f3f3f3"
          secondaryColor="#ecebeb"
        >
          <rect x="217" y="22" rx="3" ry="3" width="117" height="6" /> 
          <rect x="223" y="42" rx="3" ry="3" width="85" height="6" /> 
          <rect x="220.61" y="84.67" rx="3" ry="3" width="136.5" height="3.5" /> 
          <rect x="220.94" y="103.67" rx="3" ry="3" width="148.8" height="4.3" /> 
          <rect x="221.55" y="128.67" rx="3" ry="3" width="162.8" height="4.3" /> 
          <circle cx="40.3" cy="49.3" r="21.3" /> 
          <circle cx="41.33" cy="107.97" r="21.15" /> 
          <circle cx="50.18" cy="48.67" r="1" /> 
          <rect x="77.18" y="23.67" rx="0" ry="0" width="118.8" height="109.2" /> 
          <rect x="23.4" y="165.45" rx="0" ry="0" width="368.16" height="6.2" /> 
          <rect x="23.4" y="185.4" rx="0" ry="0" width="368.16" height="6.2" /> 
          <rect x="105.18" y="183.67" rx="0" ry="0" width="0" height="0" />
        </content-loader>
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
import { ContentLoader } from 'vue-content-loader'
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
    ContentLoader
  },
  mounted() {
    // Just pretend this is an AJAX call. Use your imagination.
    setTimeout(() => {
      // this.myData = 'Example Data';
    }, 15000);
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
