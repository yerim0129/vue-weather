<template>
  <div class="rightContainer">
    <div id="cityNameBox">
      <div class="cityName">
        <p>San Fransisco</p>
        <p>{{ currentTime }}</p>
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
import { ref } from 'vue';
import dayjs from 'dayjs';
import Map from '~/components/Map.vue';
import axios from 'axios';

export default {
  components: {
    Map,
  },
  //vue3 Composition API 사용
  setup() {
    let currentTime = dayjs().format('YYYY.MM.DD.ddd'); //현재시간
    let cityName = ref(''); //도시 이름
    let feeling = ref(''); //현재 온도와 체감을 나타내는 데이터

    //OptionWeather API 호출 함수
    const fetchOpenWeatherApi = () => {
      const API_KEY = 'e1d1521b27cafac575533bcd9d52d117';
      let initialLat = 37.5683;
      let initialLon = 126.9778;

      try {
        const res = axios.get();
        console.log(res);

        let initialDate = res.data.current; //초기데이터
        let initialCityName = res.data.initialCityName;
        let isfeelingLikeTemp = isInitialData.feels_like;
      } catch (error) {}
    };

    fetchOpenWeatherApi();

    return {
      currentTime,
    };
  },
};
</script>

<style lang="scss" scpoed>
@import '~/scss/main.scss';
@import '~/scss/subview.scss';
</style>
