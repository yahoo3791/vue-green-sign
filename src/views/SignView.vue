<template>
  <div class="w-50 bg-light m-auto mt-5 rounded-pill shadow d-flex cursor-pointer">
    <div class="w-50 text-center">
      <div class="signBtn py-3 rounded-pill">
        手寫簽名
      </div>
    </div>
    <div class="w-50 text-center">
      <div class="py-3 rounded-pill">
        匯入簽名檔
      </div>
    </div>
  </div>
  <div class="">
    <canvas
      id="canvas"
      width="500"
      height="300"
      style="border: 1px solid #000"
      @mousedown="startPosition"
      @mouseup="finishedPosition"
      @mouseleave="finishedPosition"
      @mousemove="draw"
      @touchstart="startPosition"
      @touchend="finishedPosition"
      @touchcancel="finishedPosition"
      @touchmove="draw"
      @blur="a"
    ></canvas>
    <img class="show-img" alt="show-img" width="250" height="150" style="border: 1px solid" />
    <div class="btn-group">
      <button class="clear" @click="reset">Clear</button>
      <button class="save">Save</button>
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
      } else {
        return {
          x: e.touches[0].clientX - canvasSize.left,
          y: e.touches[0].clientY - canvasSize.top,
        };
      }
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
  },
};
</script>
