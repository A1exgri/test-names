<template>
  <div class="search">
    <input v-model="value" class="search__input" type="text" placeholder="Поиск" @input="search" />
    <img src="images/search.svg" class="search__icon" alt="search-icon">
  </div>
</template>

<script>
import searchIcon from '@/assets/images/search.svg'
    export default {
        components: {
            searchIcon
        },
        props: {
            isClear: {
                type: Boolean,
                required: false,
                default: false
            }
        },
        data: () => ({
            value: ''
        }),
        watch: {
            isClear(newValue) {
                if(newValue === true) {
                    this.value = ''
                }
            }
        },
        methods: {
            search() {
                this.$emit('search', this.value)
            }
        }
    }
</script>

<style>
.search {
  position: relative;
  max-width: 295px;
  width: 100%;
}
.search input {
  padding: 8px 12px 8px 40px;
  width: 100%;
  max-width: 275px;
  border-radius: 40px;
  border: 0;
  color: #3C4061;
  font-size: 17px;
  font-weight: 400;
  line-height: 24px;
}
.search__icon {
  position: absolute;
  left: 8px;
  top:8px;
}
</style>
