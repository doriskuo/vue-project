<!-- 代表組件中所有JavaSvript程式碼 -->
<script setup>
const apiurl =
  "https://awiclass.monoame.com/api/command.php?type=get&name=hahowdata";
import { onMounted, ref } from "vue";
let classDatas = ref(null);
onMounted(async () => {
  let reseponse = await fetch(apiurl);
  let data = await reseponse.json();
  classDatas.value = data;
  console.log(data);
});
</script>

<!-- 代表組件中所有html結構 -->
<template>
  <div class="classes">
    <a
      class="classbox"
      v-for="cla in classDatas"
      v-bind:href="'https://hahow.in/courses/' + cla._id"
      target="_blank"
    >
      <div
        class="teacher"
        v-bind:style="'background-image:url(' + cla.owner.profileImageUrl + ')'"
      ></div>
      <div class="top">
        <div
          class="classpicture"
          v-bind:style="'background-image:url(' + cla.coverImage.url + ')'"
        ></div>
        <div class="tag">募資中</div>
        <div class="bookbtn"><i class="fa fa-bookmark-o"></i></div>
      </div>
      <div class="bottom">
        <h1 class="classtitle">{{ cla.title }}</h1>
        <div class="texts">
          <div class="pricerow">
            <div class="preprice">
              預購價{{ cla.preOrderedPrice
              }}<span class="orange">NT${{ cla.price }}</span>
            </div>
            <div class="lastday">
              剩<span class="orange"
                >{{
                  parseInt(
                    (new Date(cla.proposalDueTime) - new Date("2016/10/14")) /
                      1000 /
                      60 /
                      60 /
                      24
                  )
                }}天</span
              >
            </div>
          </div>
          <div class="progressbar">
            <div
              class="valuebar"
              v-bind:style="
                'width:' +
                (220 * cla.numSoldTickets) /
                  cla.successCriteria.numSoldTickets +
                'px'
              "
            ></div>
          </div>
          <div class="nowpeople">
            已募資<span class="orange"
              >{{ cla.numSoldTickets }}/{{
                cla.successCriteria.numSoldTickets
              }}人</span
            >
          </div>
        </div>
        <div class="orangebar"></div></div
    ></a>
  </div>
</template>

<!-- 代表為組件中html設定的CSS樣式 -->
<style scoped>
.classbox {
  box-shadow: 0px 0px 12px rgba(0, 0, 0, 0.2);
  width: 260px;
  background-color: white;
  color: #4f4c4b;
  border-radius: 5px;
  cursor: pointer;
  display: inline-block;
  margin: 30px 15px;
  text-decoration: none;
}
.classbox:hover .bookbtn {
  bottom: 10px;
}
.classbox:hover .classpicture {
  transform: scale(1.15);
}
.classbox:hover .bottom .valuebar {
  width: 200px;
}
.classbox .teacher {
  width: 55px;
  height: 55px;
  position: absolute;
  left: 15px;
  top: -27.5px;
  border-radius: 50%;
  background-image: url("https://hahow.in/images/57ab3d5585b097070042067a");
  background-size: cover;
  border: 2px solid white;
  z-index: 9;
}

.top {
  border-radius: 5px 5px 0px 0px;
  height: 160px;
  overflow: hidden;
}
.top .tag {
  box-shadow: 0px 0px 12px rgba(0, 0, 0, 0.2);
  width: 100%;
  text-align: center;
  transform: translateX(95px) translateY(15px) rotate(45deg);
  padding: 5px 0px;
  background-color: #eb5e00;
  color: white;
  font-weight: 700;
}
.top .classpicture {
  width: 100%;
  height: 100%;
  position: absolute;
  left: 0;
  top: 0;
  background-image: url("https://hahow.in/images/574fab4f206cd60900c52a67?width=300");
  background-size: cover;
  transition: 0.5s;
}
.top .bookbtn {
  box-shadow: 0px 0px 12px rgba(0, 0, 0, 0.2);
  width: 42px;
  height: 42px;
  border-radius: 50%;
  position: absolute;
  left: 15px;
  bottom: -50px;
  background-color: #fff;
  color: #eb5e00;
  box-shadow: 0px 0px 12px rgba(0, 0, 0, 0.2);
  cursor: pointer;
  transition: bottom 0.3s;
}
.top .bookbtn i {
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  font-size: 22px;
}
.top .bookbtn:hover {
  background-color: #eb5e00;
  color: white;
}

.bottom {
  height: 184px;
  padding: 15px;
  border-radius: 0px 0px 5px 5px;
  overflow: hidden;
}
.bottom .classtitle {
  font-size: 25px;
  margin-top: 0;
}
.bottom .texts {
  font-size: 15px;
  letter-spacing: 1px;
}
.bottom .texts .orange {
  padding-left: 5px;
  color: #fa8b00;
}
.bottom .texts .nowpeople {
  text-align: center;
}
.bottom .pricerow {
  margin-bottom: 10px;
}
.bottom .pricerow .lastday {
  position: absolute;
  top: 0;
  right: 0;
}
.bottom .progressbar {
  height: 10px;
  margin-bottom: 10px;
  background-color: #e0e0db;
  border-radius: 5px;
  overflow: hidden;
}
.bottom .progressbar .valuebar {
  width: 150px;
  height: 100%;
  background-color: #fa8b00;
  border-radius: 5px 0px 0px 5px;
  transition: 0.5s;
}
.bottom .orangebar {
  height: 5px;
  width: 100%;
  position: absolute;
  bottom: 0;
  left: 0;
  background-color: #eb5e00;
}

.classes {
  margin-top: 50px;
  max-width: 1160px;
  margin-left: auto;
  margin-right: auto;
}
</style>
