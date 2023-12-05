<template>
  <div class="rightContainer">
    <div id="cityNameBox">
      <div class="cityName">
        <p>San Fransisco</p>
        <p>Jan 28</p>
      </div>
    </div>

    <div id="contentsBox">
      <div class="buttonBox">
        <div class="buttonBackground">
          <button class="forecast">Forecast</button>
          <button class="airquality">Air Quality</button>
        </div>
      </div>
      <div class="weatherBox">
        <div class="airCondition">
          <p>매우 추움</p>
          <!-- 현재온도에 대한 체감온도를 표현 할 것임 -->
        </div>
        <div class="detail">
          <div class="title">
            <p>Detail Temperatures</p>
          </div>
          <div class="data">
            <div class="dataName">
              <p></p>
              <p></p>
            </div>

            <div class="dataValue">
              <p><span></span> &deg;</p>
            </div>
          </div>
        </div>
      </div>
    </div>

    <Map />
    <nav>
      <i class="fas fa-home"></i>
      <i class="fas fa-search-location"></i>
      <i class="fas fa-chart-line"></i>
      <i class="fas fa-cog"></i>
    </nav>
  </div>
</template>

<script>
import Map from '~/components/Map.vue';

export default {
  components: {
    Map,
  },
};
</script>

<style lang="scss" scpoed>
@import '~/scss/main.scss';
@import '~/scss/subview.scss';
</style>
