<template>
  <div class="loading d-none">
    <div>
      <img src="@/assets/pic/上傳中.gif" style="max-width: 30vw;" alt="">
      <p class="text-center">上傳中...</p>
    </div>
  </div>
  <div class="container overflow-hidden" style="min-height: calc(100vh - 30px)">
    <div class="d-flex justify-content-between align-items-center mt-3">
      <h1 class="logo"><img src="../assets/pic/logo.png" alt="logo" /></h1>
      <router-link class="history" to="/history">歷史紀錄</router-link>
    </div>
    <div class="main main-bg mx-auto">
      <div
        class="main-spacing h-100 d-flex flex-column flex-md-row
        justify-content-between align-items-center"
      >
        <div class="content d-none d-md-block">
          <img class="pb-2" src="../assets/pic/小綠簽.png" alt="主頁內文標題" />
          <p class="mb-1">護樹、永續、減碳的綠色生活</p>
          <p class="mb-1">響應環保無紙化電子簽署，</p>
          <p class="mb-1">省時便利又環保。</p>
        </div>
        <canvas id="canvas" style="border: 1px solid #000"></canvas>
        <div id="upload" class="upload-bg text-center">
          <h2><img src="../assets/pic/pdficon.png" alt="pdficon" /></h2>
          <!-- <img class="upload-btn position-relative cursor-pointer mt-4 mb-3 px-5"
            style="z-index: 1;" src="../assets/pic/button.png" alt=""> -->
          <label for="file" class="upload-btn position-relative cursor-pointer mt-4 mb-3 px-5">
            <img
              class="upload-btn position-relative cursor-pointer mt-4 mb-3 px-5"
              style="z-index: 1"
              src="../assets/pic/button.png"
              alt=""
            />
            <input
              @change="canvas"
              type="file"
              id="file"
              class="d-none"
              accept="application/pdf"
              placeholder="選擇PDF檔案"
            />
          </label>
          <!-- <label
                for="file"> -->
          <!-- <input
                @change="canvas"
                type="file"
                id="file"
                class="btn btn-secondary mt-5 mb-3 w-50"
                accept="application/pdf"
                placeholder="選擇PDF檔案" /> -->
          <!-- </label> -->
          <p>(限10MB 內的PDF或JPG檔)</p>
        </div>
      </div>
    </div>
    <!-- <div class="">
      <canvas id="canvas" style="border: 1px solid #000" />
    </div> -->
  </div>
  <div class="leaf-left"></div>
  <div class="leaf-right"></div>
  <div class="color-block"></div>
  <Footer />
</template>

<script>
import Footer from '../components/FrontFooter.vue';
import '../methods/pdf';

export default {
  components: {
    Footer,
  },
  methods: {
    // canvas(e) {
    //   console.log('cc');
    //   const canvas = new fabric.Canvas('canvas');
    //   canvas.requestRenderAll();
    //     const pdfData =  printPDF(e.target.files[0]);
    //     const pdfImage =  pdfToImage(pdfData);
    //   // 透過比例設定 canvas 尺寸
    //   canvas.setWidth(pdfImage.width / window.devicePixelRatio);
    //   canvas.setHeight(pdfImage.height / window.devicePixelRatio);
    //   // 將 PDF 畫面設定為背景
    //   canvas.setBackgroundImage(pdfImage, canvas.renderAll.bind(canvas));
    // },
  },
  mounted() {
    document.querySelector('#upload').addEventListener('drop', (e) => {
      console.log(e);
      e.preventDefault();
    });
    document.querySelector('#upload').addEventListener('dragenter', (e) => {
      e.preventDefault();
    });

    document.querySelector('#upload').addEventListener('dragover', (e) => {
      e.preventDefault();
    });

    document.querySelector('#upload').addEventListener('dragleave', (e) => {
      e.preventDefault();
    });
  },
};
</script>
