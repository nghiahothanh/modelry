<template>
  <CheckoutSidebar />
  <div>
    <div class="NewHeader-module__title">
      <h1 class="heading_oder">Orders</h1>
    </div>
    <div class="NewHeader-module__filters">
      <v-tabs v-model="tab" class="text-btn" :transition="false">
        <v-tab :value="1">Active 0</v-tab>
        <v-tab :value="2">Complete 0</v-tab>
        <v-tab :value="3">Drafts 0</v-tab>
        <v-tab :value="4">All 0</v-tab>
      </v-tabs>
    </div>
    <div class="EmptyList-module__wrapper">
      <div class="EmptyList-module__empty">
        <img
          src="//wildcat-static.cgtrader.com/packs/media/Pods/Customer/Images/no-files-acbdd841492121ab40ac73ed92ed7509.png"
          alt=""
        />
        <div class="EmptyList-module__title">Welcome to Modelry!</div>
        <div class="EmptyList-module__text">
          Let's get started with your 3D product visualization requests.
        </div>
        <v-btn class="EmptyList-btn text-none elevation-0">
          <span>Request a quote</span>
        </v-btn>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: "Orders",
  data: () => ({
      tab: null,
    }),
};
</script>

<style scoped>
.v-btn {
  text-transform: none;
  box-shadow: none;
  border-radius: 4px !important;
  font-weight: 600;
}
.heading_oder {
  font-size: 20px;
  line-height: 28px;
  margin: 0;
  color: #1e2732;
  letter-spacing: normal;
  font-style: normal;
  font-weight: 600;
  padding: 12px 0 0px;
}
.NewHeader-module__title,
.NewHeader-module__filters {
  display: flex;
  width: 100%;
  padding: 14px 32px;
  border-bottom: 1px solid rgba(30, 39, 50, 0.12);
  align-items: center;
  color: #485c66;
}
.NewHeader-module__filters button {
  margin-right: 10px;
  height: 32px;
  padding: 4px 8px;
  display: inline-flex;
  background-color: rgba(30, 39, 50, 0.04);
}
.NewHeader-module__filters span {
  cursor: pointer;
  font-family: inherit;
  align-items: center;
  font-size: 14px;
  line-height: 20px;
  font-weight: 600;
}
.NewHeader-module__filters .v-tab--selected {
  background-color: rgba(30, 39, 50, 0.7);
  color: #fff;
  border: none;
}
.btn {
  text-transform: initial !important;
}

.btn span.v-btn__content {
  text-transform: initial !important;
}
.EmptyList-module__wrapper {
  margin: 50px 0;
  text-align: center;
}
.EmptyList-module__empty img {
  max-width: 400px;
  max-height: 200px;
}

.EmptyList-module__title {
  /* max-width: 550px; */
  margin: 10px 0 0;
  color: #1e2732;
  font-size: 18px;
  font-weight: 600;
  line-height: 1.5;
}
.EmptyList-module__text {
  color: #1e2732;
  font-size: 14px;
  margin: 10px 0;
}
.EmptyList-btn {
  border: 1px solid #19bcc9;
  background-color: #19bcc9;
  color: #fff;
}
</style>