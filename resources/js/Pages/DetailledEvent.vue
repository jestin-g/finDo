<template>
  <app-layout>
    <template #header>Evénement Détaillé</template>

    <div
      v-for="event in this.eventList"
      v-bind:key="event.id"
      class="max-w-m rounded overflow-hidden shadow-lg bg-white mb-2"
    >
      <div class="px-6 py-4">
        <p class="text-gray-600 text-xs">
          {{ event.date_start }}
        </p>
        <div class="font-bold text-xl mb-2">{{ event.title }}</div>
        <p class="text-gray-700 text-base" v-html="event.description"></p>
      </div>
      <div>
        <img
          src="C:\Users\Aniss\finDo\public\images\5d0594d8b7279fbbbdc5b4131a3a0bb8.jpg	"
        />
      </div>
      -> images à venir
      <div class="px-6 pt-4 pb-2">
        <span
          class="inline-block bg-gray-100 rounded-full px-3 py-1 text-xs font-semibold text-gray-700 mr-2 mb-2"
          >{{ event.address_name }}, {{ event.address_street }},
          {{ event.address_city }}, {{ event.address_zipcode }}</span
        >
      </div>

      <a
        class="h-8 px-4 text-white duration-300 rounded-lg focus:shadow-outline bg-red-300 hover:bg-red-400 transition"
        :href="'/addEvent/' + event.id"
      >
        Enregistrer l'événement
      </a>

      <map-event-component></map-event-component>
      -> position geo à venir
    </div>
  </app-layout>
</template>

<script>
import AppLayout from "../Layouts/AppLayout.vue";
import MapEventComponent from "./Components/MapEventComponent";

export default {
  components: {
    AppLayout,
    MapEventComponent,
  },

  props: ["events"],

  data() {
    return {
      eventList: this.events,
    };
  },

  mounted() {
    console.log(this.eventList);
    document.getElementById("desc").innerHTML = events.description;
  },
};
</script>
