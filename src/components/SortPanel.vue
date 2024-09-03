<template>
  <div class="sort-panel">
    <v-tooltip text="Сортировать по рейтнгу (возрастание)" location="top">
      <template v-slot:activator="{ props }">
        <v-btn
          v-bind="props"
          icon="mdi-sort-ascending"
          @click="$emit('sort', 'asc')"
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
          @click="$emit('sort', 'desc')"
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
          @click="$emit('sort', 'none')"
          variant="tonal"
          color="white"
        />
      </template>
    </v-tooltip>
  </div>
</template>

<script setup>
</script>

<style scoped>
  .sort-panel {
    display: flex;
    gap: 10px;
    margin-bottom: 10px;
  }
</style>
