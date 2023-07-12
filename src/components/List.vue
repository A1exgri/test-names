<template>
  <div v-if="items.length" class="list-items">
    <ListItem v-for="item in items" :key="item.id" :item="item" />
  </div>
  <div v-else class="list-items-empty">
      Не удалось найти персонажей<br> с таким именем
  </div>
</template>

<script>
import ListItem from '@/components/ListItem.vue'

export default {
    components: { ListItem },
    props: {
        items: {
            type: Array,
            required: false,
            default: () => []
        }
    }
}
</script>
<style>
.list-items {
}
.list-items-empty {
    margin-top: 48px;
    color: #C1C2C7;
    text-align: center;
    font-size: 15px;
    font-weight: 400;
    line-height: normal;
    letter-spacing: -0.327px;
}
</style>
