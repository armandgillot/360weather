<template>
  <div class="HelloWorld">
    <h1>{{ msg }}</h1>

    <div class="">
      <p>Prévision météo sur 5 jours</p>

      <div class="input-group mb-3 formulaire d-flex justify-content-center">
        <input
          type="text"
          class="form-control-lg"
          placeholder="Choisir une ville"
          aria-label="Choisir une ville"
          aria-describedby="button-addon2"
          v-model="city"
        />
        <button
          class="btn btn-outline-secondary"
          type="button"
          id="button-addon2"
          @click="loadWeather()"
        >
          Valider
        </button>
      </div>
    </div>

    <div
      class="row mt-4 d-flex justify-content-center g-0"
      v-if="weather.length > 1"
    >
      <div class="col-md-6 ">

        <div class="accordion" id="accordionExample">
          <div class="accordion-item">
            <h2 class="accordion-header" id="headingOne">
              <button
                class="accordion-button collapsed"
                type="button"
                data-bs-toggle="collapse"
                data-bs-target="#collapseOne"
                aria-expanded="false"
                aria-controls="collapseOne"
              >
                {{ displayDay1 }}
              </button>
            </h2>
            <div
              id="collapseOne"
              class="accordion-collapse collapse"
              aria-labelledby="headingOne"
              data-bs-parent="#accordionExample"
            >
              <div class="accordion-body">
                <div class="list-group">
                  <div
                    class="list-group-item list-group-item-action"
                    aria-current="true"
                    v-for="(weatherData1, idx) in weatherData1"
                    v-bind:key="idx"
                  >
                    <div class="d-flex w-100 justify-content-between">
                      <img alt="" :src="weatherData1.weather[0].icon" />
                      <h5 class="mb-1 description">
                        {{ weatherData1.weather[0].description }}
                      </h5>
                      <small>{{ weatherData1.dt }}</small>
                    </div>
                    <p class="mb-1">Température : {{ weatherData1.main.temp }}°C</p>
                    <small>Humidité : {{ weatherData1.main.humidity }}%</small>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div class="accordion-item">
            <h2 class="accordion-header" id="headingTwo">
              <button
                class="accordion-button collapsed"
                type="button"
                data-bs-toggle="collapse"
                data-bs-target="#collapseTwo"
                aria-expanded="false"
                aria-controls="collapseTwo"
              >
                {{ displayDay2 }}
              </button>
            </h2>
            <div
              id="collapseTwo"
              class="accordion-collapse collapse"
              aria-labelledby="headingTwo"
              data-bs-parent="#accordionExample"
            >
              <div class="accordion-body">
                <div class="list-group">
                  <div
                    class="list-group-item list-group-item-action"
                    aria-current="true"
                    v-for="(weatherData2, idx) in weatherData2"
                    v-bind:key="idx"
                  >
                    <div class="d-flex w-100 justify-content-between">
                      <img alt="" :src="weatherData2.weather[0].icon" />
                      <h5 class="mb-1 description">
                        {{ weatherData2.weather[0].description }}
                      </h5>
                      <small>{{ weatherData2.dt }}</small>
                    </div>
                    <p class="mb-1">Température : {{ weatherData2.main.temp }}°C</p>
                    <small>Humidité : {{ weatherData2.main.humidity }}%</small>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div class="accordion-item">
            <h2 class="accordion-header" id="headingThree">
              <button
                class="accordion-button collapsed"
                type="button"
                data-bs-toggle="collapse"
                data-bs-target="#collapseThree"
                aria-expanded="false"
                aria-controls="collapseThree"
              >
                {{ displayDay3 }}
              </button>
            </h2>
            <div
              id="collapseThree"
              class="accordion-collapse collapse"
              aria-labelledby="headingThree"
              data-bs-parent="#accordionExample"
            >
              <div class="accordion-body">
                <div class="list-group">
                  <div
                    class="list-group-item list-group-item-action"
                    aria-current="true"
                    v-for="(weatherData3, idx) in weatherData3"
                    v-bind:key="idx"
                  >
                    <div class="d-flex w-100 justify-content-between">
                      <img alt="" :src="weatherData3.weather[0].icon" />
                      <h5 class="mb-1 description">
                        {{ weatherData3.weather[0].description }}
                      </h5>
                      <small>{{ weatherData3.dt }}</small>
                    </div>
                    <p class="mb-1">Température : {{ weatherData3.main.temp }}°C</p>
                    <small>Humidité : {{ weatherData3.main.humidity }}%</small>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div class="accordion-item">
            <h2 class="accordion-header" id="headingFour">
              <button
                class="accordion-button collapsed"
                type="button"
                data-bs-toggle="collapse"
                data-bs-target="#collapseFour"
                aria-expanded="false"
                aria-controls="collapseFour"
              >
                {{ displayDay4 }}
              </button>
            </h2>
            <div
              id="collapseFour"
              class="accordion-collapse collapse"
              aria-labelledby="headingFour"
              data-bs-parent="#accordionExample"
            >
              <div class="accordion-body">
                <div class="list-group">
                  <div
                    class="list-group-item list-group-item-action"
                    aria-current="true"
                    v-for="(weatherData4, idx) in weatherData4"
                    v-bind:key="idx"
                  >
                    <div class="d-flex w-100 justify-content-between">
                      <img alt="" :src="weatherData4.weather[0].icon" />
                      <h5 class="mb-1 description">
                        {{ weatherData4.weather[0].description }}
                      </h5>
                      <small>{{ weatherData4.dt }}</small>
                    </div>
                    <p class="mb-1">Température : {{ weatherData4.main.temp }}°C</p>
                    <small>Humidité : {{ weatherData4.main.humidity }}%</small>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div class="accordion-item">
            <h2 class="accordion-header" id="headingFive">
              <button
                class="accordion-button collapsed"
                type="button"
                data-bs-toggle="collapse"
                data-bs-target="#collapseFive"
                aria-expanded="false"
                aria-controls="collapseFive"
              >
                {{ displayDay5 }}
              </button>
            </h2>
            <div
              id="collapseFive"
              class="accordion-collapse collapse"
              aria-labelledby="headingFive"
              data-bs-parent="#accordionExample"
            >
              <div class="accordion-body">
                <div class="list-group">
                  <div
                    class="list-group-item list-group-item-action"
                    aria-current="true"
                    v-for="(weatherData5, idx) in weatherData5"
                    v-bind:key="idx"
                  >
                    <div class="d-flex w-100 justify-content-between">
                        <img alt="" :src="weatherData5.weather[0].icon" />
                      <h5 class="mb-1 description">
                        {{ weatherData5.weather[0].description }}
                      </h5>
                      <small>{{ weatherData5.dt }}</small>
                    </div>
                    <p class="mb-1">Température : {{ weatherData5.main.temp }}°C</p>
                    <small>Humidité : {{ weatherData5.main.humidity }}%</small>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import moment from "moment";
import "moment/locale/fr";
moment.locale("fr");

export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data: function () {
    return {
      weather: [],
      apiKey: "9da6b63f214e77766e16f592bdb466ed",
      city: "",
      weatherData1: [],
      weatherData2: [],
      weatherData3: [],
      weatherData4: [],
      weatherData5: [],
      displayDay1: "",
      displayDay2: "",
      displayDay3: "",
      displayDay4: "",
      displayDay5: "",
    };
  },
  methods: {
     cleanUpSpecialChars(str) {
      str = str.replace(/é|è|ê/g, "e");
      return str;
    },
    loadWeather() {
      axios
        .get(
          `https://api.openweathermap.org/data/2.5/forecast?q=${this.cleanUpSpecialChars(this.city)}&lang=fr&units=metric&appid=${this.apiKey}`
        )
        .then(
          function (response) {
            this.weather = response.data.list;
            this.city = response.data.city.name

            for (let i = 0; i < this.weather.length; i++) {
              this.weather[i].dt = moment(this.weather[i].dt_txt).format("LT");
              this.weather[
                i
              ].weather[0].icon = `https://openweathermap.org/img/w/${this.weather[i].weather[0].icon}.png`;
            }

            this.weatherData1 = this.weather.filter(
              (i) => moment(i.dt_txt).dayOfYear() == moment().dayOfYear()
            );
            this.weatherData2 = this.weather.filter(
              (i) => moment(i.dt_txt).dayOfYear() == moment().dayOfYear() + 1
            );
            this.weatherData3 = this.weather.filter(
              (i) => moment(i.dt_txt).dayOfYear() == moment().dayOfYear() + 2
            );
            this.weatherData4 = this.weather.filter(
              (i) => moment(i.dt_txt).dayOfYear() == moment().dayOfYear() + 3
            );
            this.weatherData5 = this.weather.filter(
              (i) => moment(i.dt_txt).dayOfYear() == moment().dayOfYear() + 4
            );
            // console.log(this.weather);
            if (this.weatherData1.length > 0) {
              this.displayDay1 = moment(this.weatherData1[0].dt_txt).format(
                "dddd"
              );
            } else {
              this.displayDay1 =
                "Aujourd'hui : Plus de données météo pour aujourdui, il est trop tard, réessayez après minuit ou voir les jours suivants ci dessous";
            }
            this.displayDay2 = moment(this.weatherData2[0].dt_txt).format(
              "dddd"
            );
            this.displayDay3 = moment(this.weatherData3[0].dt_txt).format(
              "dddd"
            );
            this.displayDay4 = moment(this.weatherData4[0].dt_txt).format(
              "dddd"
            );
            // if (this.weatherData5.length > 0) {
            this.displayDay5 = moment(this.weatherData5[0].dt_txt).format(
              "dddd"
            );
            // } else {
            //   this.displayDay5 = "données météo encore indispos pour ce jour..";
            // }
          }.bind(this)
        );
    },
    
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.description::first-letter {
  text-transform: uppercase;
}
</style>
