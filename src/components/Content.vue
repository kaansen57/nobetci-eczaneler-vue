<template>
  <div class="container-fluid ">
    <Header></Header>
    <h1 class="mb-5 text-center">{{ city }} Nöbetçi Eczaneler</h1>
    <TurkeyMap></TurkeyMap>
    <Result></Result>
  </div>
</template>

<script>
import { ref, reactive, computed, watch } from "vue";
import { useStore } from "vuex";
import TurkeyMap from "./TurkeyMap";
import Header from "./Header";
import Result from "./Result";
export default {
  components: {
    TurkeyMap,
    Header,
    Result,
  },
  setup() {
    const store = useStore();
    const dutyPharmacy = computed(() => store.getters.getData);
    const city = computed(() => store.getters.getSelectedCityText);
    return {
      city,
      dutyPharmacy,
    };
  },
};
</script>
<style>
.container-fluid {
  padding: 0 !important;
}
</style>