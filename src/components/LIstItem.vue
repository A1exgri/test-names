<template>
  <div class="list-item">
      <div class="list-item__person">
          <img :src="item.image" :alt="item.name">
          <div class="list-item__title">{{ item.name }}</div>
      </div>
      <button @click="alertInfo">
          <img src="images/alert.svg" alt="alert">
      </button>
  </div>
</template>

<script>
export default {
    props: {
        item: {
            type: Object,
            required: false,
            default: () => {}
        }
    },
    methods: {
        alertInfo() {
            alert(this.item.species)
        },
    },
}
</script>
<style>
.list-item {
    border-radius: 15px;
    border: 1px solid #F4F5F5;
    background: #FFF;
    padding: 15px;
    margin-bottom: 10px;
    display: flex;
    align-items: center;
    justify-content: space-between;
}
.list-item img{
    width: 50px;
    height: 50px;
    border-radius: 80px;
}
.list-item__person {
    display: flex;
    align-items: center;
}
.list-item__title {
    color: #1D1D1D;
    font-size: 17px;
    font-weight: 700;
    line-height: normal;
    letter-spacing: -0.327px;
    margin-left: 20px;
}
.list-item button {
    border: 0;
    background: transparent;
    cursor: pointer;
}
.list-item button img {
    height: 21px;
}
</style>