<template>
  <v-navigation-drawer
    v-model="drawer"
    :rail="rail"
    permanent
    @click="rail = false"
    class="Nav-Sidebar text-white"
    :width="244"
    style="bottom: 0;"
  >
    <v-list-item nav>
      <div class="mb-4 ml-2">
        <nuxt-link to="/checkouts/">
          <img
            src="https://wildcat-static.cgtrader.com/packs/media/Images/logo_modelry_white-6c504447422897adb50f73464e102344.png"
            alt="Logo Modelry"
          />
        </nuxt-link>
      </div>
    </v-list-item>
    <!-- Button New -->
    <v-menu transition="scale-transition">
      <template v-slot:activator="{ props }">
        <v-list-item
          class="DropdownButton text-lg-center pr-16"
          prepend-icon="mdi-plus"
          title="New"
          v-bind="props"
        >
        </v-list-item>
      </template>
      <v-list class="custom-tooltip_sidebar pa-4" >
        <span>Order</span>
        <v-list-item
          class="my-2"
          to="/"
          title="Start from scratch"
        ></v-list-item>
        <v-divider></v-divider>
        <span>Assets</span>
        <v-list-item
          title="Asset upload"
          class="my-2"
          to="/"
        ></v-list-item>
      </v-list>
    </v-menu>

    <!------------------- List menu-------------- -->
    <v-list density="compact" nav>
      <v-list-item
        prepend-icon="mdi-file-check"
        title="Orders"
        value="Orders"
        to="/checkouts/Orders"
      >
      </v-list-item>
      <v-list-item
        prepend-icon="mdi-file-document-multiple"
        title="Items"
        value="Items"
        to="/checkouts/Items"
      >
      </v-list-item>
      <v-list-item
        prepend-icon="mdi-account"
        title="Assets"
        value="Assets"
        to="/checkouts/Assets"
      ></v-list-item>

      <v-divider></v-divider>

      <v-list-item
        prepend-icon="mdi-poll"
        title="Statistics"
        value="Statistics"
        to="/checkouts/Statistics"
      ></v-list-item>
      <v-menu transition="scale-transition">
        <template v-slot:activator="{ props }">
          <v-list-item
            prepend-icon="mdi-bell"
            title="Notifications"
            v-bind="props"
          >
          </v-list-item>
        </template>
        <v-list  class="custom-tooltip justify-center py-12">
          <v-icon class="align-content-center text-grey-lighten-2" size="98"
            >mdi-bell</v-icon
          >
          <span class="notification-text">No Notifications</span>
        </v-list>
      </v-menu>

      <v-menu transition="scale-transition">
        <template v-slot:activator="{ props }">
          <v-list-item
            prepend-icon="mdi-forum"
            title="Messages"
            v-bind="props"
          >
          </v-list-item>
        </template>
        <v-list  class="custom-tooltip justify-center py-12">
          <v-icon class="align-content-center text-grey-lighten-2" size="88"
            >mdi-email-outline</v-icon
          >
          <span class="notification-text mt-2">No new messages</span>
          <v-btn class="elevation-1 mt-4" to="../checkouts/inbox">View all</v-btn>
        </v-list>
      </v-menu>
    </v-list>
    <!-- Account Menu -->

    <div class="bottom_nav">
      <v-menu  transition="scale-transition">
      <template v-slot:activator="{ props }">
        <v-list-item
          prepend-avatar="https://randomuser.me/api/portraits/men/85.jpg"
          nav
          class="DropdownButton mb-2"
          v-bind="props"
        >
          <span>John Leider</span>
          <v-btn variant="text" icon="mdi-dots-vertical"></v-btn>
        </v-list-item>
      </template>
      <!-- Menu as Popover -->
      <v-list class="custom-tooltip_sidebar pa-4">
        <v-list-item
          prepend-avatar="https://randomuser.me/api/portraits/men/85.jpg"
          title="John Leider"
        >
          <template v-slot:append>
            <v-btn
              to="/"
              variant="text"
              icon="mdi-arrow-collapse-right"
            ></v-btn>
          </template>
        </v-list-item>
        <v-divider></v-divider>
        <v-list-item
          to="/checkouts/Settings"
          prepend-icon="mdi-cog"
          title="Settings"
        ></v-list-item>
        <v-divider></v-divider>
        <v-list-item
          prepend-icon="mdi-help-circle-outline"
          title="About"
          to="/"
        ></v-list-item>
        <v-list-item
          prepend-icon="mdi-file-check"
          title="Terms & Conditions"
        ></v-list-item>
      </v-list>
    </v-menu>

    <v-divider></v-divider>

    <v-list-item
      variant="text"
      @click.stop="rail = !rail"
      prepend-icon="mdi-arrow-collapse-left"
      title="Collapse"
      value="Collapse"
    >
    </v-list-item>
    </div>
  </v-navigation-drawer>
</template>

<script>
export default {
  name: "CheckoutSiderbar",
  data() {
    return {
      drawer: true,
      rail: false,
      show: false,
      showMessages: false,
    };
  },
  methods: {
    toggleTooltip() {
      this.show = !this.show;
      if (this.show) {
        document.addEventListener("click", this.handleDocumentClick);
      } else {
        document.removeEventListener("click", this.handleDocumentClick);
      }
    },
    togglesidebar() {
      this.sidebar = !this.sidebar;
    },
    handleDocumentClick(event) {
      const tooltip = this.$refs.tooltip.$el;
      if (!tooltip.contains(event.target)) {
        this.show = !this.show;
      }
    },
    
  },
};
</script>

<style scoped>
a {
  text-decoration: none;
}

.DropdownButton {
  cursor: pointer;
  margin: 0 10px 10px 10px;
  border-radius: 4px;
  border: 1px solid hsla(0, 0%, 100%, 0.2);
}
.Nav-Sidebar .v-list-item-title {
  color: #fff;
}
.v-list-item > .v-icon--size-default {
  font-size: calc(var(--v-icon-size-multiplier) * 0.2em);
}

.Nav-Sidebar {
  top: 0;
  height: 100% !important;
  background: #1e2732;
  padding: 20px 0 0px;
  transition: width 0.1s linear;
}
.notification-text {
  display: block;
}


.v-navigation-drawer--rail .DropdownButton span,
.v-navigation-drawer--rail .DropdownButton button,
.v-navigation-drawer--rail .v-list-item__content {
  display: none;
}
.custom-tooltip{
  text-align: center;
  width: 420px;
  min-height: 270px;
  font-size: 20px;
  font-weight: 600;
  color: rgb(30, 39, 50);
  background-color: #fff ;
}
.custom-tooltip:hover {
  box-shadow: 0 4px 16px rgba(30, 39, 50, 0.04),
    0 6px 8px rgba(30, 39, 50, 0.04), 0 8px 12px rgba(30, 39, 50, 0.04),
    0 0 0 8px rgba(25, 188, 201, 0.1), inset 0 0 0 1px rgba(25, 188, 201, 0.4) !important;
}
.custom-tooltip_sidebar {
  background-color: #fff;
  width: 310px;
  height: auto;
  color: rgb(30, 39, 50);
  border-radius: 4px;
  margin-left: 12px;
}
.custom-tooltip_sidebar span {
  color: rgba(30, 39, 50, 0.4);
  font-size: 12px;
  font-weight: 600;
}
.custom-tooltip_sidebar:hover {
  box-shadow: 0 4px 16px rgba(30, 39, 50, 0.04),
    0 6px 8px rgba(30, 39, 50, 0.04), 0 8px 12px rgba(30, 39, 50, 0.04),
    0 0 0 8px rgba(25, 188, 201, 0.1), inset 0 0 0 1px rgba(25, 188, 201, 0.4) !important;
}

.bottom_nav {
  position: absolute;
  bottom: 0;
}
</style>
