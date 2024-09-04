<template>
  <div class="sort-panel">
    <v-tooltip text="Сортировать по рейтнгу (возрастание)" location="top">
      <template v-slot:activator="{ props }">
        <v-btn
          v-bind="props"
          icon="mdi-sort-ascending"
          @click="sortCards('asc')"
          variant="tonal"
          color="white"
        />
      </template>
    </v-tooltip>
    <v-tooltip text="Сортировать по рейтнгу (убывание)" location="top">
      <template v-slot:activator="{ props }">
        <v-btn
          v-bind="props"
          icon="mdi-sort-descending"
          @click="sortCards('desc')"
          variant="tonal"
          color="white"
        />
      </template>
    </v-tooltip>
    <v-tooltip text="Вернуть сортировку по умолчанию" location="top">
      <template v-slot:activator="{ props }">
        <v-btn
          v-bind="props"
          icon="mdi-sort"
          @click="sortCards('none')"
          variant="tonal"
          color="white"
        />
      </template>
    </v-tooltip>
  </div>
</template>

<script setup>
  import { ref, inject } from 'vue';

  const firstList = inject('firstList');
  const secondList = inject('secondList');
  const lastList = inject('lastList');

  const props = defineProps({
    options: {},
  });

  let cards = ref([]);

  function getLocalCards() {
    switch (props.options.id) {
      case 1:
        cards = firstList;
        break;
      case 2:
        cards = secondList;
        break;
      case 3:
        cards = lastList;
        break;
    }
  }

  function sortCards(order) {
    getLocalCards();
    if (order === 'asc') {
      cards =  cards.value.sort((a, b) => a.rating.rate - b.rating.rate);
    } else if (order === 'desc') {
      cards =  cards.value.sort((a, b) => b.rating.rate - a.rating.rate);
    } else if (order === 'none') {
      cards =  cards.value.sort((a, b) => a.id - b.id);
    }
  }
</script>

<style scoped>
  .sort-panel {
    display: flex;
    gap: 10px;
    margin-bottom: 10px;
  }
</style>
