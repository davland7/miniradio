<template>
  <div class="navbar">
    <div class="navbar__logo">
      <img src="images/icon24.png" />
      {{ messages.name }}
    </div>
    <div class="navbar__tabs">
      <div @click="tab(index)" v-for="(tabNumber, index) in totalTabs" class="navbar__tab" :class="{'navbar__tab--current': currentTab === index}">
          {{ tabNumber }}
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'Tabs',
    props: [
      'currentTab',
      'totalTabs',
      'stationsPerTab'
    ],
    data () {
      return {
        messages: {
          name: chrome.i18n.getMessage('name')
        }
      }
    },
    methods: {
      tab (index) {
        this.$emit('tabClick', index)
      }
    }
  }
</script>

<style lang="scss">
  .navbar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin: 4px 0;

    &__logo {
      display: flex;
      align-items: center;
      height: 32px;
      font-size: 14px;
      font-weight: 600;
      color: var(--dark-color);

      img {
        padding: 0 6px;
      }
    }

    &__tabs {
      display: flex;
    }

    &__tab {
      display: flex;
      justify-content: center;
      align-items: center;
      margin: 0 2px;
      width: 30px;
      height: 30px;
      font-size: 18px;
      color: var(--light-color);
      border: solid 1px var(--border-color);
      border-radius: 30px;
      cursor: pointer;

      &--current,
      &:hover {
        background-color: var(--content-color);;
      }
    }
  }
</style>
