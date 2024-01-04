<template>
  <div class="leftContainer">
    <div id="cityNameBox">
      <div class="cityName">
        <p>{{ cityName }}</p>
        <p>{{ currentTime }}</p>
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
import axios from 'axios';
import dayjs from 'dayjs';
import 'dayjs/locale/ko';
dayjs.locale('ko'); //한국어 사용

export default {
  data() {
    return {
      //현재 시간을 나타내기 위한 Dayjs 플러그인 사용
      currentTime: dayjs().format('YYYY.MM.DD.ddd'),
      //상세 날씨 데이터를 받아주는 데이터 할당
      temp: [],
      icons: [],
      cityName: '',

      //임시 데이터
      temporaryData: [
        { title: '습도', value: '88%' },
        { title: '풍속', value: '10m/s' },
        { title: '풍향', value: 'WS' },
      ],
    };
  },
  created() {
    const API_KEY = 'e1d1521b27cafac575533bcd9d52d117';
    let initialLat = 37.5683;
    let initialLon = 126.9778;

    axios
      .get(`https://api.openweathermap.org/data/2.5/onecall?lat={initialLat}&lon={initialLon}&appid={API_KEY}`)
      .then((response) => {
        console.log(response);
        let initialCityName = response.data.timezone;
        this.cityName = initialCityName.split('/')[1]; // ['asia', 'seoul']
      })
      .catch((error) => {
        console.log(error);
      });
  },
};
</script>

<style lang="scss" scpoed>
@import '~/scss/main.scss';
@import '~/scss/mainview.scss';
</style>
