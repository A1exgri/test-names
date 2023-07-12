<template>
  <main class="characters">
    <h1>Персонажи</h1>
    <Search :is-clear="isClear" @search="search"/>
    <div v-if="items.length" class="characters__count">
       {{ info.count }} персонажей
    </div>
    <List :items="items" />
    <div class="show-more">
        <button v-if="next" class="show-more" @click="showMore">
            <span>Показать еще</span>
            <img src="images/arrow_down.svg">
        </button>
    </div>
      <div v-if="isShowButton" class="clear-search">
        <div class="clear-search-wrap">
            <div>
               <button @click="clearSearch">
                 Сбросить поиск
               </button>
            </div>
        </div>
    </div>
  </main>
</template>

<script>
import List from '@/components/List.vue'
import Search from '@/components/Search.vue'
import axios from "axios";
export default {
    components: {
        List,
        Search
    },
    data: () => ({
        baseUrl: 'https://rickandmortyapi.com/api/character',
        items: [],
        info: {},
        page: 1,
        next: null,
        isClear: false,
        isShowButton: false
    }),
    async mounted() {
        await this.getItems()
    },
    computed: {},
    methods: {
        async getItems(param) {
            this.isShowButton = false
            let query = ''
            if(param && param.query) {
                query = query +'?name=' + param.query
                this.isShowButton = true
            }
            if(param && param.page) {
                query = query + '?page=' + param.page
            }
            try {
                const resp = await axios.get(`${this.baseUrl}${query}`)
                console.log('resp', resp)
                if(param && param.page) {
                    this.items = [...this.items, ...resp.data.results]
                } else {
                    this.items = resp.data.results
                }
                this.info = resp.data.info
                this.next = resp.data.info.next
                console.log('items', this.items)
            } catch (e) {
                this.items = []
                this.next = null
                console.log(e)
            }
        },
        search(data) {
            this.getItems({query: data })
        },
        clearSearch() {
            this.isClear = true
            this.isShowButton = false
            this.getItems()
        },
        showMore() {
            this.page ++
            if(this.next) {
                this.getItems({ page: this.page })
            }
        }
    }
}
</script>
<style>
.characters {
  padding: 25px;
}
.characters h1{
    font-size: 20px;
    font-weight: 400;
    line-height: 24px;
    letter-spacing: -0.01em;
    text-align: center;
    color: #221A51;
}
.characters__count{
    color: #C1C2C7;
    font-size: 15px;
    font-weight: 400;
    line-height: normal;
    letter-spacing: -0.327px;
    text-align: center;
    margin: 10px 0;
}
.show-more {
  padding-bottom: 108px;
}
.show-more button{
    color: #3C4061;
    font-size: 17px;
    font-style: normal;
    font-weight: 700;
    line-height: normal;
    letter-spacing: -0.327px;
    background: #fff;
    border-radius: 10px;
    border: 1px solid #F4F5F5;
    height: 56px;
    width: 100%;
    padding: 15px;
    cursor: pointer;
    display: flex;
    align-items: center;
}
.show-more span {
    min-width: 220px;
    text-align: center;
}
.clear-search {
    position: fixed;
    bottom:0;
    left: 0;
    right: 0;
    z-index: 2;
}
.clear-search-wrap {
    max-width: 375px;
    margin: 0 auto;
    min-height: 180px;
    border-radius: 10px 10px 40px 40px;
    background: #FFF;
    box-shadow: 0px 0px 13px 0px rgba(22, 22, 23, 0.26);
}
.clear-search-wrap div {
    padding: 25px;
}
.clear-search button {
    cursor: pointer;
    background: #CB99FA;
    border: 0;
    border-radius: 10px;
    color: #FFF;
    text-align: center;
    font-size: 20px;
    font-style: normal;
    font-weight: 900;
    line-height: 24px;
    width: 100%;
    height: 56px;
    display: flex;
    align-items: center;
    justify-content: center;
}
</style>
