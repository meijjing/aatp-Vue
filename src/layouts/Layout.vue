<template>
  <q-layout view="hHh lpr fFf">
    <q-header reveal elevated>
      <q-toolbar>

        <q-toolbar-title>
          <img :src="require('assets/image/logo.png')" alt="" class="logo" />
        </q-toolbar-title>

        <q-btn flat dense icon="menu" aria-label="Menu" @click="toggleRightDrawer" />
      </q-toolbar>

      <q-tabs v-model="tab" align="center">
        <q-route-tab :key="nav.label" v-for="nav in navs" :to="nav.to" :label="nav.label" class="q-px-lg" />
      </q-tabs>
    </q-header>

    <q-drawer
      v-model="rightDrawerOpen"
      side="right"
      overlay
      elevated
      :width="230"
      bordered
    >

      <q-list>
        <q-btn flat dense icon="close" aria-label="Menu" @click="toggleRightDrawer" class="q-ml-auto q-mb-lg close_btn" />

        <q-item :key="nav.label" v-for="nav in navs" :to="nav.to" exact clickable>
          <q-item-section>
            <q-item-label>{{ nav.label }}</q-item-label>
          </q-item-section>
        </q-item>

      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>

    <!-- <q-footer reveal elevated>
      <img :src="require('assets/image/logo.png')" alt="" class="bot-logo q-py-md" />
    </q-footer> -->
  </q-layout>

  <footer>
      <img :src="require('assets/image/logo.png')" alt="" class="bot-logo q-py-md" />
  </footer>
</template>

<script>
import { defineComponent, ref } from 'vue'
// import { openURL } from 'quasar';

export default defineComponent({
  name: 'Layout',
  data () {
    return {
      // rightDrawerOpen: false,
      navs: [
        {
          label: 'AATP',
          to: '/'
        },
        {
          label: '센터소개',
          to: '/'
        },
        {
          label: '과정',
          to: '/'
        },
        {
          label: '개발자 대회',
          to: '/'
        },
        {
          label: '문의하기',
          to: '/'
        }
      ]
    }
  },
  setup () {
    const rightDrawerOpen = ref(false)

    return {
      rightDrawerOpen,
      toggleRightDrawer () {
        rightDrawerOpen.value = !rightDrawerOpen.value
      }
    }
  },
})
</script>

<style lang="scss">
@import '../css/reset.scss';

$phone: "all and (max-width : 540px)";
$width500: "all and (max-width : 500px)";
$tablet: "all and (max-width : 768px)";
$labtop: "all and (max-width : 1024px)";



.q-header {
  .q-toolbar {
    height: 70px;
  }

  .logo {
    width: 200px;
    display: block;
    margin: 0 auto;
  }
  .q-tabs {
    background: rgba(0,0,0,.8);
  }
  aside {
    display: none!important;
  }
}

.q-btn {
  display: none!important;
  font-size: 1.375rem;
}

.close_btn {
  font-size: 1.625rem;
  font-weight: bold;
}

.q-footer {
  .bot-logo {
    width: 150px;
    display: block;
    margin: 0 auto;
  }
}

.q-item.q-router-link--active {
  color: #000;
}

footer {
  background: #1c1c1c;

  .bot-logo {
    width: 150px;
    display: block;
    margin: 0 auto;
  }
}

@media #{$width500} {
  .q-btn {
    display: block!important;
  }
  .q-header {
    .logo {
      width: 150px;
      margin: 0;
    }
    .q-tabs {
      display: none!important;
    }
    aside {
      display: block!important;
    }
  }
}
.q-item__label {
  text-align: right!important;
  font-size: 1.5rem!important;
  font-weight: 600!important;
  padding: 10px 0;
}
</style>
