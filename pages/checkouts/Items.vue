<template>
  <CheckoutSidebar />
  <div>
    <div class="NewHeader-module__title">
      <h1 class="heading_oder">Order items</h1>
      <v-text-field v-model="search" clearable density="compact" hide-details placeholder="Search"
        prepend-inner-icon="mdi-magnify" style="max-width: 280px; height: 28px; margin-left: auto;"
        variant="outlined"></v-text-field>
    </div>
    <!-- Tab menu -->
    <div class="NewHeader-module__filters ">
      <v-row cols="12">

        <v-col cols="6">
          <v-row cols="12" class="pt-6">

            <v-tabs v-model="tab" class="">
              <v-tab :value="1">Ready for review 0</v-tab>
              <v-tab :value="2">In progress 0</v-tab>
              <v-tab :value="3">Finished 0</v-tab>
              <v-tab :value="4">All 0</v-tab>
            </v-tabs>
          </v-row>
          <v-row cols="12">
            <v-list class="d-flex">
              
              <v-list-item v-for="(item, index) in favorites " :key="item">
                
                <v-chip v-if="chip" class="ma-2" closable @click:close="CloseItem($event,index)" >
                  {{ item }}
              </v-chip>
              
              </v-list-item>
            </v-list>
          </v-row>
        </v-col>

        <v-col cols="2">
          <v-select v-model="selectedView" clearable :items="viewOptions" label="Status" multiple persistent-hint
            @update:modelValue="updateQuery"></v-select>
        </v-col>
        <v-col cols="2">
          <v-select v-model="favorites" :items="percents" label="Select" multiple @update:modelValue="updateQuery">


          </v-select>
        </v-col>
        <v-col cols="2">
          <v-select v-model="modelType" :items="viewModelType" label="Model Type" multiple persistent-hint
            @update:modelValue="updateQuery"></v-select>

        </v-col>
      </v-row>

    </div>

    <div class="text-center">



    </div>



    <v-checkbox label="0 selected"></v-checkbox>

    <div class="EmptyList-module__wrapper mx-8">
      <v-sheet :elevation="1">
        <div class="EmptyList-module__empty pa-8">
          <img
            src="//wildcat-static.cgtrader.com/packs/media/Pods/Customer/Images/no-files-acbdd841492121ab40ac73ed92ed7509.png"
            alt="" />
          <div class="my-2"><b>This is where you will see your 3D modeling requests</b></div>
          <p class="my-4">Start by requesting a quote for the items you want to be 3D modeled.</p>
          <v-btn class="buttonPrimary text-none elevation-0">
            <span>Request a quote</span>
          </v-btn>
        </div>
      </v-sheet>
    </div>
  </div>
</template>


<script setup>

import { ref } from 'vue';
const router = useRouter();
const favorites = ref([]);
const chip = ref(true)
const percents = ['Low-poly', 'High-poly', 'Rendering'];

const selectedView = ref([]);
const viewOptions = ['Ready For Review', 'Some Other View'];
const modelType = ref([]);
const viewModelType = ['Main model', 'Variations']
const updateQuery = () => {
  try {
    console.log('ho thanh nghia');
    console.log(selectedView.value);

    // Thử push vào router
    const queryValue = `${selectedView.value}+${favorites.value}+${modelType.value}`;
    console.log(queryValue)
    router.push({ query: { view: 'Ready For Review', query: queryValue } });
    console.log(router.fullPath)
  } catch (error) {
    // Xử lý lỗi ở đây
    console.error('Error while updating query:', error);
  }
};
const CloseItem = (event,index)=>{
  console.log(index);
  chip.value=false;
  favorites.value.splice(index, 1);
 console.log(favorites.value) 
 chip.value=true;
 updateQuery();
}


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
  max-height: 32px;
  padding: 4px 8px;
  display: inline-flex;
  background-color: rgba(30, 39, 50, 0.04);
}

.NewHeader-module__filters span {
  cursor: pointer;
  font-family: inherit;
  align-items: center;
  font-size: 12px;
  line-height: 20px;
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
</style>