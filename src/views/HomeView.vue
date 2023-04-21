<template>
  <div class="container" style="min-height: calc( 100vh - 30px);">
    <div class="d-flex justify-content-between align-items-center">
      <h1 class="logo">點點簽</h1>
      <router-link class="history" to="/history">歷史紀錄</router-link>
    </div>
    <div class="main d-flex justify-content-center align-items-center
    border border-5 m-auto my-5">
      <div class="text-center">
        <h2>PDF,JPG</h2>
        <router-link to="/Sign">
          <button type="button" class="btn btn-secondary mt-5 mb-3">選擇檔案</button>
        </router-link>
        <p>(限10MB 內的PDF或JPG檔)</p>
      </div>
    </div>
  </div>
<Footer />
</template>

<script>
import Footer from '../components/FrontFooter.vue';

export default {
  components: {
    Footer,
  },
  methods: {

  },
};
</script>
