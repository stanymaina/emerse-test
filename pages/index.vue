<template>
  <v-layout
    column
    justify-center
    align-center
  >
    <content-loader
      mdAndUp
      v-if="!myData1"
      :height="520"
      :width="1200"
      :speed="2"
      primaryColor="#bdbdbd"
      secondaryColor="#ecebeb"
    >    
      <rect x="658" y="53" rx="4" ry="4" width="324" height="13" /> 
      <rect x="666" y="221" rx="4" ry="4" width="162" height="13" /> 
      <rect x="200" y="34" rx="5" ry="5" width="412" height="400" /> 
      <rect x="666" y="375" rx="4" ry="4" width="324" height="46" /> 
      <rect x="666" y="303" rx="4" ry="4" width="324" height="46" /> 
      <rect x="671" y="260" rx="4" ry="4" width="162" height="8" /> 
      <rect x="662" y="90" rx="4" ry="4" width="78" height="13" /> 
      <rect x="666" y="134" rx="4" ry="4" width="324" height="4" /> 
      <rect x="666" y="149" rx="4" ry="4" width="324" height="4" /> 
      <rect x="666" y="164" rx="4" ry="4" width="324" height="4" /> 
      <rect x="666" y="179" rx="4" ry="4" width="324" height="4" /> 
      <rect x="55" y="62" rx="0" ry="0" width="114" height="115" />
    </content-loader>
    <div v-else class="my-real-content">
    </div>
    <v-flex
      xs12
      sm8
      md6
    >
        <content-loader
          smAndDown
          v-if="!myData1"
          :height="520"
          :width="400"
          :speed="2"
          primaryColor="#bdbdbd"
          secondaryColor="#ecebeb"
        >
          <rect x="50" y="270" rx="4" ry="4" width="227" height="10" /> 
          <rect x="56" y="367" rx="4" ry="4" width="115" height="9" /> 
          <rect x="50" y="20" rx="5" ry="5" width="239" height="232" /> 
          <rect x="53" y="447" rx="4" ry="4" width="230" height="33" /> 
          <rect x="53" y="396" rx="4" ry="4" width="230" height="33" /> 
          <rect x="90" y="290" rx="4" ry="4" width="55" height="10" /> 
          <rect x="56" y="325" rx="4" ry="4" width="227" height="3" /> 
          <rect x="56" y="337" rx="4" ry="4" width="227" height="3" /> 
          <rect x="56" y="349" rx="4" ry="4" width="227" height="3" />
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
      <div class="content-wrapper">
        <!-- Displays if myData is not set. -->
        <v-icon v-if="!myData"></v-icon>
    
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
              label="Currencies"
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
        { abbr: 'USD', name: '$  - United States Dollar' },
        { abbr: 'KES', name: 'Ksh - Kenyan shilling' },
        { abbr: 'EUR', name: '€  - Euro' },
        { abbr: 'GBP', name: '£  - Pound sterling' },
        { abbr: 'CHF', name: 'Fr - Swiss franc' },
        { abbr: 'CAD', name: 'C$ - Canada Dollar' },
        { abbr: 'JPY', name: '¥  - Japanese yen' },
        { abbr: 'AUD', name: 'A$ - Australian dollar' },
        { abbr: 'INR', name: '₹  - Indian rupee' },
        { abbr: 'NGN', name: '₦  - Nigerian naira' }
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
      myData: null,
      myData1: null
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
      this.myData = 'Example Data';
    }, 1000);
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
