<!-- 代表組件中所有JavaSvript程式碼 -->
<script setup></script>

<!-- 代表組件中所有html結構 -->
<template>
  <div class="banner">
    <div class="center_banner">
      <img src="https://2017.awiclass.monoame.com/img/hahow_progress.png" />
    </div>
  </div>
</template>

<!-- 代表為組件中html設定的CSS樣式 -->
<style scoped>
.center_banner {
  display: inline-block;
  background-color: #fff;
  padding: 20px 30px;
  border-radius: 5px;
  box-shadow: 0px 0px 12px rgba(0, 0, 0, 0.3);
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
}
.center_banner img {
  width: 1000px;
}

.banner {
  height: 400px;
  background: linear-gradient(
    -45deg,
    #ffe18d 10%,
    #ffe18d 10%,
    #ffda71 10%,
    #ffda71 40%,
    #ffe18d 40%,
    #ffe18d 60%,
    #ffda71 60%,
    #ffda71 90%,
    #ffe18d 90%,
    #ffe18d 100%
  );
  background-size: 46px 46px;
  position: relative;
}
</style>
