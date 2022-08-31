<script>
import WorldMap from "../WorldMap.vue";
export default {
  components: {
    WorldMap
  },
  name: 'Homepage',
  data() {

  }
}
</script>

<script setup>
import axios from 'axios'
import Buttons from "../Buttons/Buttons.vue";
import {homepageButtons} from '../../Datas/Datas';

async function fetchAqi() {

  const fetchAqiResponse = await axios.get(`https://api.waqi.info/feed/france/?token=${import.meta.env.VITE_API_KEY}`)
  console.log(fetchAqiResponse.data)
}
fetchAqi()
</script>

<template>
  <header>
  </header>
  <main>
    <section class="main__content">
      <div class="main__content__topLeft__block">
        <img src="../../images/picasa.png" class="main__content__topLeft__logo" alt="logo"/>
        <h3 class="main__content__topLeft__description">Air Pollution: Real-time Air Quality Index (AQI)</h3>
      </div>
      <div class="main__content__bottomLeft__block">
        <Buttons :values=homepageButtons />
      </div>
    </section>
    <WorldMap/>
  </main>
</template>

<style lang="scss">

  main {
    height: 100%;

    .main__content {
      position: absolute;
      display: flex;
      flex-direction: column;
      height: 100%;
      width: 100%;

      .main__content__topLeft__block {
        display: flex;
        flex-direction: column;
        width: 650px;
        height: 400px;
        z-index: 1;

        .main__content__topLeft__logo {
          left: 100px;
          top: 100px;
          width: 50px;
          height: 50px;
          margin: 5rem;
        }

        .main__content__topLeft__description {
          align-self: flex-end;
          margin-top: auto;
        }
      }
      .main__content__bottomLeft__block {
        display: flex;
        justify-content: flex-end;
        width: 650px;
        height: 400px;
        bottom: 0;
        z-index: 1;
      }
    }
  }

</style>
