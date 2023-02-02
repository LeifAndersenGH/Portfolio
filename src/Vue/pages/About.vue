<script src="https://www.amcharts.com/lib/3/ammap.js" type="text/javascript"></script>
<script src="https://www.amcharts.com/lib/3/maps/js/usaHigh.js" type="text/javascript"></script>
<script src="https://www.amcharts.com/lib/3/themes/light.js" type="text/javascript"></script>

<template>
  <section id="about" class="dark-section">
    <div class="container-fluid">
      <h1 class="section-header">{{ heading }}</h1>
      <h2 class="tagline" :v-if="about.tagline !==''">{{about.tagline}}</h2>
      <div class="row">
        <div
          class="col-sm-12 col-md-4 flex-col"
          data-aos="fade-right"
          data-aos-duration="1000"
        >
          <img
            class="profile-pic"
            src="../../assets/images/profile-pic.jpg"
            alt="profile picture"
          />
        </div>
        <div
          class="col-sm-12 col-md-4 flex-col"
          data-aos="fade-right"
          data-aos-duration="1000"
        >
          <p id="about-content">
            <span id="greeting">I'm {{ name }}! </span>
            <span id="bio" v-html="about.bio"></span>
          </p>
        </div>

        <div
          class="col-sm-12 col-md-4 flex-col"
          data-aos="fade-right"
          data-aos-duration="1000"
        >
          <ul class="list-group list-group-flush">
            <li v-for="item in facts" :key="item.name" class="list-group-item">
              <h3 class="d-inline">{{ item.name }}: </h3>
              <br class="d-md-none" />{{ item.value }}
            </li>
          </ul>
        </div>
      </div>

      

    </div>

    <Arrow />
  </section>

</template>

<script>
import data from "../../data/data.json";
import Arrow from "../components/Arrow.vue";

export default {
  name: "About",
  components: {
    Arrow, // <-- Add a comma here
  },
  props: {},
  data() {
    return {
      about: data.about,
      name: data.main.name.first,
      facts: data.about.facts,
      heading: data.main.headings.about,
    };
  },
  mounted() { // <-- Add a new function here
    let map = AmCharts.makeChart("mapdiv", {
      type: "map",
      theme: "light",
      panEventsEnabled: true,
      backgroundColor: "#535364",
      backgroundAlpha: 1,
      zoomControl: {
        zoomControlEnabled: true
      },
      dataProvider: {
        map: "usaHigh",
        getAreasFromMap: true,
        areas: [
          {
            id: "US-AK",
            showAsSelected: true
          },
          {
            id: "US-CA",
            showAsSelected: true
          },
          {
            id: "US-MA",
            showAsSelected: true
          },
          {
            id: "US-NC",
            showAsSelected: true
          },
          {
            id: "US-NY",
            showAsSelected: true
          },
          {
            id: "US-VA",
            showAsSelected: true
          },
          {
            id: "US-WA",
            showAsSelected: true
          }
        ]
      },
      areasSettings: {
        autoZoom: true,
        color: "#B4B4B7",
        colorSolid: "#84ADE9",
        selectedColor: "#84ADE9",
        outlineColor: "#666666",
        rollOverColor: "#9EC2F7",
        rollOverOutlineColor: "#000000"
      }
    });
  }
};














</script>

<style lang="scss"></style>

