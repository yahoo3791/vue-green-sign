<template>
  <div class="loading d-none">
    <div>
      <img src="@/assets/pic/上傳中.gif" style="max-width: 30vw;" alt="">
      <p class="text-center">簽名優化中...</p>
    </div>
  </div>
  <div class="w-50 bg-light m-auto mt-5 rounded-pill shadow d-flex cursor-pointer">
    <div class="w-50 text-center">
      <div class="handWrite signBtn py-3 rounded-pill"
      @click.prevent="handWrite($event)"
      @keypress="handWrite($event)">
        手寫簽名
      </div>
    </div>
    <div class="w-50 text-center">
      <div class="importSign py-3 rounded-pill"
      @click.prevent="importSign($event)"
      @keypress="importSign($event)">
        匯入簽名檔
      </div>
    </div>
  </div>
  <div class="">
    <canvas
      id="canvas"
      width="500"
      height="300"
      class="d-block mx-auto mt-5 bg-light"
      @mousedown="startPosition"
      @mouseup="finishedPosition"
      @mouseleave="finishedPosition"
      @mousemove="draw"
      @touchstart="startPosition"
      @touchend="finishedPosition"
      @touchcancel="finishedPosition"
      @touchmove="draw"
      @blur="blur"
    ></canvas>
    <img class="show-img position-relative ms-auto d-block"
    alt="" width="250" height="150" />
    <div class="text-center my-5">
      <button
        type="button"
        class="btn btn-light shadow clear px-5"
        @click="reset">清除
      </button>
      <button
        type="button"
        class="btn btn-secondary shadow save px-5 ms-3"
        @click="saveImage">建立簽名
      </button>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      isPainting: false,
    };
  },
  methods: {
    getPaintPosition(e) {
      console.log('getPaintPosition');
      const canvasSize = document.querySelector('#canvas').getBoundingClientRect();
      if (e.type === 'mousemove') {
        return {
          x: e.clientX - canvasSize.left,
          y: e.clientY - canvasSize.top,
        };
      }
      return {
        x: e.touches[0].clientX - canvasSize.left,
        y: e.touches[0].clientY - canvasSize.top,
      };
    },
    startPosition(e) {
      console.log('startPosition');
      e.preventDefault();
      this.isPainting = true;
    },
    finishedPosition() {
      console.log('finishedPosition');
      this.isPainting = false;
      document.querySelector('#canvas').getContext('2d').beginPath();
    },
    draw(e) {
      console.log('draw');
      if (!this.isPainting) return;
      const paintPosition = this.getPaintPosition(e);
      const canvas = document.querySelector('#canvas');
      const ctx = canvas.getContext('2d');
      ctx.lineTo(paintPosition.x, paintPosition.y);
      ctx.stroke();
    },
    reset() {
      console.log('reset');
      const canvas = document.querySelector('#canvas');
      const ctx = canvas.getContext('2d');
      ctx.clearRect(0, 0, canvas.width, canvas.height);
    },
    saveImage() {
      console.log('save');
      const newImg = document.querySelector('#canvas').toDataURL('image/png');
      document.querySelector('.show-img').src = newImg;
      localStorage.setItem('img', newImg);
    },
    importSign(e) {
      document.querySelector('.handWrite').classList.remove('signBtn');
      e.target.classList.add('signBtn');
    },
    handWrite(e) {
      document.querySelector('.importSign').classList.remove('signBtn');
      e.target.classList.add('signBtn');
    },
  },
};
</script>
