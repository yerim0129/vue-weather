<template>
  <div class="leftContainer">
    <div id="cityNameBox">
      <div class="cityName">
        <p>San Fransisco</p>
        <p>Jan 28</p>
      </div>
    </div>

    <div id="contentsBox">
      <div class="buttonBox">
        <div class="buttonBackground">
          <button class="forcecast">Forecast</button>
          <button class="airquality">Air Quality</button>
        </div>
      </div>
      <div class="weatherBox">
        <div class="weatherDegree">
          <p>10&deg;</p>
        </div>
        <div class="weatherIcon">
          <img src="~/assets/images/10d.png" alt="MainLogo" />
        </div>
        <div class="weatherData">
          <div v-for="Temporary in TemporaryData" :key="Temporary.title" class="detailData">
            <p>{{ Temporary.title }}</p>
            <p>{{ Temporary.value }}</p>
          </div>
        </div>
      </div>
    </div>

    <div id="todayWeather">
      <div class="textBox">
        <p>시간대별 날씨 정보</p>
        <p>이번주 날씨 보기</p>
      </div>
      <div class="timelyWeatherBox">
        <div class="timelyWeather">
          <div class="icon">
            <img src="~/assets/images/09d.png" alt="" />
          </div>
          <div class="data">
            <p class="time"></p>
            <p class="currentDegree">32&deg;</p>
            <div>
              <img src="~/assets/images/drop.png" alt="" />
              <p class="fall">15%</p>
            </div>
          </div>
        </div>
      </div>
    </div>
    <nav>
      <i class="fas fa-home"></i>
      <i class="fas fa-search-location"></i>
      <i class="fas fa-chart-line"></i>
      <i class="fas fa-cog"></i>
    </nav>
  </div>
</template>

<script>
export default {
  data() {
    return {
      //임시 데이터
      TemporaryData: [
        { title: '습도', value: '88%' },
        { title: '풍속', value: '10m/s' },
        { title: '습도', value: '88%' },
      ],
    };
  },
};
</script>

<style lang="scss" scpoed>
@import '~/scss/main.scss';
@import '~/scss/mainview.scss';
</style>
