<template>
  <div class="footer">
      <div class="footer-wrap">
          <ul class="footer-menu">
              <li v-for="m in menu" :key="m.id" class="footer-menu__item">
                  <router-link :to="m.link" class="footer-menu__item-link" :class="{active : m.isActive}">
                    <div class="footer-menu__item-img">
                      <img :src="`images/${m.icon}`" :alt="m.title">
                      <span v-if="m.isDot" class="dot">
                        <span />
                      </span>
                    </div>
                      <div class="footer-menu__item-title">{{ m.title }}</div>
                  </router-link>
              </li>
          </ul>
      </div>
  </div>
</template>

<script>
export default {
    data: () => ({
        menu: [
            {id: 1, title: 'карта', link: '/about', icon: 'map.svg'},
            {id: 1, title: 'чаты', link: '/about', icon: 'chat.svg', isDot: true},
            {id: 1, title: 'мои встречи', link: '/', icon: 'clock.svg', isActive:true, isDot: true },
            {id: 1, title: 'профиль', link: 'about', icon: 'profile.svg'},
        ]
    })
}
</script>
<style>
    .footer {
        left: 0;
        right: 0;
        position: fixed;
        bottom: 0;
        z-index: 3;
    }
    .footer-wrap {
        background: #fff;
        box-shadow: 0px 0px 13px 0px #16161742;
        max-height: 80px;
        border-radius: 40px 40px 30px 30px;
        max-width: 375px;
        width: 100%;
        margin: 0 auto;
    }
    .footer-menu {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin: 0;
        padding: 18px 44px;
        list-style: none;
    }
    .footer-menu__item {
    }
    .footer-menu__item a {
        display: flex;
        flex-direction: column;
        align-items: center;
        text-decoration: none;
    }
    .footer-menu__item-title {
        font-size: 12px;
        font-weight: 400;
        line-height: 14px;
        letter-spacing: -0.32708659768104553px;
        text-align: center;
        color: #1D1D1D;
    }
    .footer-menu__item-img {
      position: relative;
    }
    .footer-menu__item-img .dot {
      width: 11px;
      height: 11px;
      background: #fff;
      border-radius: 11px;
      position: absolute;
      top: 0;
      right: 0;
      z-index: 4;
      display: flex;
      align-items: center;
      justify-content: center;
    }
    .footer-menu__item-img .dot span {
      width: 7px;
      height: 7px;
      border-radius: 7px;
      background: #EF7958;
    }
    .footer-menu__item-link.active .dot span{
      background: #000;
    }
    .footer-menu__item-link:hover div, .footer-menu__item-link.active div {
        color: #EF7958;
    }
    .footer-menu__item-link:hover svg, .footer-menu__item-title-link.active svg {
        fill: #EF7958;
    }
</style>
