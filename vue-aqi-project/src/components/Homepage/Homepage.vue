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
import {ref, watchEffect} from "vue";
import axios from 'axios'
import {homepageFilterGazButtons, homepageFilterHealthyButtons} from '../../Datas/Datas';

const searchQuery = ref("");

watchEffect(() => {

  async function fetchAqi() {

    const fetchAqiResponse = await axios.get(`https://api.waqi.info/feed/${searchQuery.value}/?token=${import.meta.env.VITE_API_KEY}`)
    console.log(fetchAqiResponse.data)
  }
  fetchAqi()


  console.log(searchQuery.value)
})

</script>

<template>
  <header>
    <section class="header__content">
      <article class="header__content__topLeft__block">
        <img src="../../images/picasa.png" class="header__content__topLeft__logo" alt="logo"/>
        <h3 class="header__content__topLeft__description">Air Pollution: Real-time Air Quality Index (AQI)</h3>
      </article>
      <article class="header__content__topRight__block">
        <input type="text" v-model="searchQuery" placeholder="Search anywhere" class="header__content__topRight__block__searchbar"/>
      </article>
    </section>
  </header>
  <main>
    <section class="main__content">
      <article class="main__content__bottomLeft__block">
        <div v-for="(value, index) in homepageFilterGazButtons" :key="index" :id="index" class="main__content__bottomLeft__block__btn__filter-gaz">
          <p class="main__content__bottomLeft__block__btn__filter-gaz__text">{{value}}</p>
        </div>
      </article>
      <article class="main__content__bottomCenter__block">
        <div v-for="(value, index) in homepageFilterHealthyButtons" :key="index" :id="index" class="main__content__bottomLeft__block__btn__filter-healthy">
          <p class="main__content__bottomLeft__block__btn__filter-healthy__text">{{value}}</p>
        </div>
      </article>
    </section>
    <WorldMap/>
  </main>
</template>

<style lang="scss">

.header__content {
  position: absolute;
  display: flex;
  width: 100%;
  background-color: rgba(238,238,240,0.5);
  z-index: 1;

  .header__content__topLeft__block {
    display: flex;
    flex-direction: row;
    justify-content: space-evenly;
    align-items: center;
    width: 50rem;
    height: 5rem;
    z-index: 1;

    .header__content__topLeft__logo {
      width: 50px;
      height: 50px;
    }

    .header__content__topLeft__description {
      font-weight: 800;
    }
  }
  .header__content__topRight__block {
    display: flex;
    flex-direction: row;
    justify-content: space-evenly;
    align-items: center;
    width: 50rem;
    height: 5rem;
    z-index: 1;

    .header__content__topRight__block__searchbar {
      width: 10rem;
      height: 1.25rem;
      border-width: 1.5px;
    }
  }
}

main {
  height: 100%;

  .main__content {
    position: absolute;
    display: flex;
    flex-direction: column;
    height: 100%;
    width: 100%;

    .main__content__bottomLeft__block {
      position: absolute;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: flex-start;
      width: 4rem;
      height: 12rem;
      bottom: 5rem;
      left: 5rem;
      gap: 0.75rem;
      border-radius: 35%;
      background-color: #FFFFFF;
      z-index: 1;

      .main__content__bottomLeft__block__btn__filter-gaz {
        justify-content: center;
        align-self: center;
        height: 1.5rem;
        width: 1.5rem;
        border: 1px black solid;
        background-color: lightgray;

        .main__content__bottomLeft__block__btn__filter-gaz__text {
          position: relative;
          bottom: 0.75rem;
          font-size: 1rem;
          font-weight: bold;
          width: 20rem;
          margin-left: 5rem;
        }
      }
    }
    .main__content__bottomCenter__block {
      position: absolute;
      display: flex;
      width: 40rem;
      height: 2.5rem;
      gap: 6rem;
      bottom: 5rem;
      left: 50%;
      z-index: 1;

      .main__content__bottomLeft__block__btn__filter-healthy {
        justify-content: center;
        align-self: flex-end;
        height: 1rem;
        width: 1rem;
        border-radius: 50%;
        border: 1px black solid;
        background-color: lightgray;

        .main__content__bottomLeft__block__btn__filter-healthy__text {
          position: relative;
          bottom: 0.75rem;
          font-size: 0.75rem;
          font-weight: bold;
          width: 10rem;
          margin-left: 1.5rem;
        }
      }
    }
  }
}

</style>
