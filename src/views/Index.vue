<template>
  <q-layout view="hHr lpR lff">
    <q-header elevated class="top-bar-props" style="padding: 8px 0px">
      <q-toolbar>
        <!-- <q-btn dense flat round icon="menu" @click="left = !left" /> -->

        <q-toolbar-title>
          <q-avatar>
            <img src="https://cdn.quasar.dev/logo/svg/quasar-logo.svg" />
          </q-avatar>
          <span style="padding-left: 16px">Petrol Pump</span>
        </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-drawer show-if-above v-model="left" side="left" bordered>
      <!-- drawer content -->
      <q-scroll-area class="fit">
        <q-list>
          <template v-for="(menuItem, index) in menuList">
            <div
              class="menu"
              :key="index"
              clickable
              v-ripple
              @click="goToRoute(menuItem.name)"
            >
              <!-- :active="menuItem.label === 'Outbox'" -->
              <q-item-section avatar>
                <q-icon :name="menuItem.icon" class="icon" />
              </q-item-section>
              <q-item-section class="menu-text">
                {{ menuItem.label }}
              </q-item-section>
            </div>
            <!-- <q-separator :key="'sep' + index" v-if="menuItem.separator" /> -->
          </template>
        </q-list>
      </q-scroll-area>
    </q-drawer>

    <q-page-container>
      <q-page class="main-page">
        <router-view />
      </q-page>
      <!-- <img src="assets/gas-pump.png" class="image-on-all-pages" alt="" /> -->
    </q-page-container>
  </q-layout>
</template>

<script>
export default {
  components: {},
  data: function () {
    return {
      left: true,
      menuList: [
        {
          icon: "home",
          label: "Dashboard",
          name: "dashboard",
          separator: true,
        },
        {
          icon: "speed",
          label: "Meter Reading",
          name: "meter-reading",
          separator: true,
        },
        {
          icon: "today",
          label: "Daily Sales",
          name: "daily-sales",
          separator: true,
        },
        {
          icon: "attach_money",
          label: "Expenses",
          name: "expenses",
          separator: true,
        },
        {
          icon: "local_gas_station",
          label: "Machines",
          name: "machines",
          separator: true,
        },
        {
          icon: "inventory_2",
          label: "Stocks",
          name: "stocks",
          separator: true,
        },
        {
          icon: "dashboard",
          label: "Customer Ledgers",
          name: "ledgers",
          separator: true,
        },
        {
          icon: "dashboard",
          label: "Supplier Ledgers",
          name: "supplier-ledgers",
          separator: true,
        },
        {
          icon: "account_balance",
          label: "Bank Ledgers",
          name: "bank-ledgers",
          separator: true,
        },

        {
          icon: "settings",
          label: "Settings",
          name: "settings",
          separator: true,
        },
        {
          icon: "logout",
          label: "Exit",
          name: "login",
          separator: true,
        },
      ],
    };
  },
  props: {},
  methods: {
    goToRoute(content) {
      if (content !== this.$router.history.current.name) {
        this.$router.push({ name: content });
      }
    },
  },

  mounted() {
    // if(this.getProtectionStatus){
    //     this.setProtectionStatus(true);
    //     this.protectedRoute = true;
    //     if (localStorage.isAuthenticated) {
    //         this.isAuthenticated = true
    //         if (this.$router.currentRoute.name === 'index') {
    //             this.$router.push('dashboard');
    //         }
    //     } else {
    //         this.$router.replace('login')
    //     }
    // }
  },
  computed: {},
};
</script>

<style lang="scss">
.main-page {
  margin: 0 auto;
  padding: 16px 32px;
  width: 1300px;
}
.side-bar-item {
  /* border-bottom: 1px solid #e2e2e2; */
  padding: 16px 8px;
  cursor: pointer;
  font-weight: 700;
  font-size: 16px;
  text-transform: uppercase;
}
.q-drawer--left.q-drawer--bordered {
  position: fixed;
}
.image-on-all-pages {
  position: absolute;
  bottom: 30px;
  opacity: 0.2;
  height: 1000px;
  right: 30px;
  z-index: -10;
}
.top-bar-props {
  /* background: #2C4457 */
  color: #e6f3ff;
}
.menu {
  display: flex;

  padding: 10px 20px;
  &:first-child {
    margin-top: 10px;
  }
  .icon {
    color: #059ddb;
    font-size: 20px;
  }
  &-text {
    color: #2C4457;
  }
}
.menu:hover {
  background: #059ddb;
  color: #fafafa;
  border-top-left-radius: 100px;
  border-bottom-left-radius: 100px;
  .icon {
    color: #fafafa;
  }

  .menu-text {
    color: #fafafa;
  }
}
.menu:focus {
  background: #059ddb;
  color: #fafafa;
  border-top-left-radius: 100px;
  border-bottom-left-radius: 100px;
  .icon {
    color: #fafafa;
  }

  .menu-text {
    color: #fafafa;
  }
}
</style>
