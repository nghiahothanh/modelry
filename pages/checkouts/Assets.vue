<template>
    <CheckoutSidebar />
    <div>
      <div class="NewHeader-module__title">
        <h1 class="heading_oder">Assets</h1>
            <v-text-field
              v-model="search"
              clearable
              density="compact"
              hide-details
              placeholder="Search"
              prepend-inner-icon="mdi-magnify"
              style="max-width: 360px; height: 32px; margin-left: auto; "
              variant="outlined"
            ></v-text-field>
      </div>
      <v-divider></v-divider>
      <div class="NewHeader-module__filters">
        <v-navigation >
          <v-btn 
            v-for="(b, index) in isbutton" 
            :key="index"
            :class="{ 'active-btn': index === 0, 'inactive-btn': index !== 0 }"
            variant="outlined"
            :style="{
              border: '1px solid rgba(30,39,50,.12)',
              backgroundColor: 'transparent',
              color: 'rgba(30,39,50,.8)',
              cursor: index === 0 ? 'pointer' : 'not-allowed'
            }"
            @click="index === 0 ? handleBtnClick(b) : null"
          >
            <v-icon>{{ b.icon }}</v-icon>{{ b.name }} 
            <v-tooltip
              activator="parent"
              location="top"
              style="border-radius: 0;"
              >{{ b.tooltip }}
            </v-tooltip>
        </v-btn>
        </v-navigation>
        <v-select
            variant="underlined"
            :items="items"
            label="Sort by:"
            style="max-width: 180px; margin-left: auto;"
          ></v-select>
      </div>
      <div class="EmptyList-module__wrapper">
        <div class="EmptyList-module__empty">
          <img
            src="//wildcat-static.cgtrader.com/packs/media/Pods/Customer/Images/no-files-acbdd841492121ab40ac73ed92ed7509.png"
            alt=""
          />
          <div class="EmptyList-module__title">No products</div>
        </div>
      </div>
      <div class="d-flex justify-space-between mx-8" 
        style="color: rgba(149, 153, 158, 0.8)">
        <div class="d-flex align-center " >
          <label  for="">Per page:</label>
          <v-autocomplete
            class="mx-2"
            label="10"
            :items="['10', '20', '50', '100']"
            variant="outlined"
            style="height: 50px!important;"
          ></v-autocomplete>
          <span>1 - 0 of 0 items</span>
        </div>
        <div class="d-flex align-center">
          <span>Page</span>
          <v-select
            class="mx-2 "
            label="Select"
            style="height: 50px!important;"
            :items="['']"
            variant="outlined"
          ></v-select>
          <span>of 0</span>
          <v-pagination 
            style="cursor: pointer;"
            variant="outlined"
            :length="0"
            prev-icon="mdi-arrow-left"
            next-icon="mdi-arrow-right"
          ></v-pagination>
        </div>
  
      </div>
    </div>
  </template>
    <script>
    export default {
      data: () => ({
        search: '',
        items: ['New first', 'Old first', 'Title A-Z', 'SKU', 'Batch ID'],
        isbutton: [ 
          { name: 'Upload files', icon: 'mdi-upload', tooltip: 'Upload files' },
          { name: 'Download files', icon: 'mdi-download', tooltip: 'Download all select' },
          { name: 'Export data', icon: 'mdi-file-export', tooltip: 'Export product data as scv' },
          { name: 'Order Services', icon: 'mdi-plus-circle', tooltip: 'Add Order Services' },
          { name: 'Delete', icon: 'mdi-delete', tooltip: 'Delete all select' } 
      ]
      }),
    }
  </script>
  <style scoped>
  .v-btn {
    text-transform: none;
    box-shadow: none;
  }
  .inactive-btn {
    color: rgba(145, 150, 156, 0.8) !important;
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
  .heading_search {
    max-width: 30%;
    align-items: right;
  }
  .NewHeader-module__title,
  .NewHeader-module__filters {
    display: flex;
    width: 100%;
    padding: 14px 32px;
    align-items: center;
    color: #485c66;
  }
  .NewHeader-module__filters span {
    margin-right: 10px;
  }
  .NewHeader-module__filters button {
    font-size: 12px;
    font-weight: 500;
    line-height: 20px;
    margin-right: 10px;
    height: 24px;
    padding: 4px;
    display: inline-flex;
    background-color: rgba(30, 39, 50, 0.04);
  }
  .custom-font.v-btn__prepend{
    margin-inline: 0px !important;
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
  
  </style>