<template>
  <CheckoutSidebar />
  <div class="Main_container">
    <div class="container_wrapper">
      <!-- Stepper Header -->
      <div class="CheckoutsNew_header">
        <v-stepper class="elevation-0">
          <v-stepper-header>
            <v-stepper-item title="Select a service" value="1" class="step_bar"></v-stepper-item>
            <v-stepper-item title="Upload References" value="2" class="step_bar"></v-stepper-item>
            <v-stepper-item class="step_bar" title="Review & Request Estimate" value="3"></v-stepper-item>
          </v-stepper-header>
        </v-stepper>
      </div>
      <!-- Content -->
      <div class="CheckoutsNew_content">
        <div class="WorkflowSelection">
          <div class="WorkflowSelection_viewers">
            <h3 class="mb-20">Please select a service</h3>
            <p>
              Submit your order for a custom 3D model within minutes! Choose the
              3D model type that best suits your use case to get started.
            </p>
          </div>
          <div class="WorkflowSelection_viewers_content viewers_padding">
            <div class="WorkflowSelection_viewers_content_img ">
              <img class="primary__image" ref="imageRef"
                src="https://arsenal-embeds.cgtrader.com/product-viewers/Egg_lounge_chair14248/assets/1668182817/3%20Egg_lounge_chair_360_45FOV_0005.jpg"
                alt="" />

              <v-row justify="center" class="fullScreen">
                <v-dialog v-model="dialog" persistent width="1024">
                  <template v-slot:activator="{ props }">
                    <v-btn icon class="mdi mdi-fullscreen" v-bind="props" @click="openDialog"></v-btn>
                  </template>
                  <v-card>
                    <v-card-title class="d-flex justify-end">

                      <v-btn color="blue-darken-1" variant="text" @click="dialog = false" class="rounded-circle ">
                        <span class="mdi mdi-alpha-x" style="font-size: 2.5rem;"></span>
                      </v-btn>


                    </v-card-title>
                    <v-card-text>
                      <v-container>
                        <div class="d-flex justify-center">
                          <div class="ma-4">

                            <v-img class="bg-white" width="400" height="400" :aspect-ratio="1" :src="dialogImg"
                              cover></v-img>
                          </div>
                        </div>
                      </v-container>

                    </v-card-text>

                  </v-card>
                </v-dialog>
              </v-row>
            </div>
            <h4>6 Photorealistic Product Images for E-commerce</h4>
            <p>
              This option will replace your product photography and will provide
              you with 6 images from all sides to use on your e-commerce website,
              as well as the underlying high-resolution 3D model and a 360 spinner
              that is made from these images. Please note: This model is NOT for
              use in augmented reality and similar interactive applications.
            </p>
          </div>
          <!-- Carousels img -->
          <div class="WorkflowSelection_viewers_content viewers_padding_l">
            <div class="WorkflowSelection_viewers_content_img">
              <v-sheet>

                <v-slide-group selected-class="is_active" hide-arrows v-model="model">
                  <!-- Slide img -->
                  <v-slide-group-item v-for="(item, i) in items" :key="i" v-slot="{ toggle, selectedClass }">
                    <v-img :src="item.src" :class="['ma-2 rounded', selectedClass]" width="72" height="50" cover
                      @click="selectedImage(toggle, item.src)">
                    </v-img>
                  </v-slide-group-item>
                </v-slide-group>
                <!-- Slide img click -->
                <v-expand-transition>
                  <v-sheet>
                    <div class="d-flex justify-center align-center ">
                      <v-img style="border: 1px solid rgba(30,39,50,.12);" class="roundeds" cover width="420" height="360"
                        :src="chooseImg">
                      </v-img>
                    </div>
                  </v-sheet>
                </v-expand-transition>
              </v-sheet>
            </div>
            <h4>6 Photorealistic Product Images for E-commerce</h4>
            <p>
              This option will replace your product photography and will provide
              you with 6 images from all sides to use on your e-commerce website,
              as well as the underlying high-resolution 3D model and a 360 spinner
              that is made from these images. Please note: This model is NOT for
              use in augmented reality and similar interactive applications.
            </p>
          </div>
        </div>
      </div>
      <!-- Table -->
      <div class="table100-nextcols">
        <div class="cell100 column1">Applications</div>
        <table>
          <tbody>
            <tr class="row100 body">
              <td class="cell100 column2">E-commerce
              </td>
              <td class="cell100 column3">
                <input type="checkbox" checked="checked" />
                <div class="checkmark"></div>
              </td>
              <td class="cell100 column4">
                <input type="checkbox" checked="checked" />
                <div class="checkmark"></div>
              </td>
            </tr>
            <tr class="row100 body">
              <td class="cell100 column2">
                <div class="d-flex justify-space-between">
                  <p>Metaverse and 3D games</p>
                  <p class="icon-hover"><v-icon color="rgba(30,39,50,.24) ">mdi-help-circle-outline </v-icon>
                    <v-tooltip activator="parent" location="top">Tooltip</v-tooltip>
                  </p>
                </div>
              </td>
              <td class="cell100 column3">
                <input type="checkbox" checked="checked" />
                <div class="checkmark"></div>
              </td>
              <td class="cell100 column4">-</td>
            </tr>
            <tr class="row100 body">
              <td class="cell100 column2">
                <div class="d-flex justify-space-between">
                  <p>QR code</p>
                  <p class="icon-hover"><v-icon color="rgba(30,39,50,.24) ">mdi-help-circle-outline </v-icon>
                    <v-tooltip activator="parent" location="top">Tooltip</v-tooltip>
                  </p>
                </div>
              </td>
              <td class="cell100 column3">
                <input type="checkbox" checked="checked" />
                <div class="checkmark"></div>
              </td>
              <td class="cell100 column4">-</td>
            </tr>
            <tr class="row100 body">
              <td class="cell100 column2">
                <div class="d-flex justify-space-between">
                  <p>3D ads</p>
                  <p class="icon-hover"><v-icon color="rgba(30,39,50,.24) ">mdi-help-circle-outline </v-icon>
                    <v-tooltip activator="parent" location="top">Tooltip</v-tooltip>
                  </p>
                </div>
              </td>
              <td class="cell100 column3">
                <input type="checkbox" checked="checked" />
                <div class="checkmark"></div>
              </td>
              <td class="cell100 column4">-</td>
            </tr>
            <tr class="row100 body">
              <td class="cell100 column2">Developer</td>
              <td class="cell100 column3">
                <input type="checkbox" checked="checked" />
                <div class="checkmark"></div>
              </td>
              <td class="cell100 column4">-</td>
            </tr>
          </tbody>
        </table>
        <div class="cell100 column1">What you will get?</div>
        <table>
          <tbody>
            <tr class="row100 body">
              <td class="cell100 column2">
                <div class="d-flex justify-space-between">
                  <p>AR viewer</p>
                  <p class="icon-hover"><v-icon color="rgba(30,39,50,.24) ">mdi-help-circle-outline </v-icon>
                    <v-tooltip activator="parent" location="top">Tooltip</v-tooltip>
                  </p>
                </div>
              </td>
              <td class="cell100 column3">
                <input type="checkbox" checked="checked" />
                <div class="checkmark"></div>
              </td>
              <td class="cell100 column4">-
              </td>
            </tr>
            <tr class="row100 body">
              <td class="cell100 column2 ">
                <div class="d-flex">
                  <p>Interactive 3D viewer</p>
                  <p class="icon-hover"><v-icon color="rgba(30,39,50,.24) ">mdi-help-circle-outline </v-icon>
                    <v-tooltip activator="parent" location="top">Tooltip</v-tooltip>
                  </p>
                </div>
              </td>
              <td class="cell100 column3">
                <input type="checkbox" checked="checked" />
                <div class="checkmark"></div>
              </td>
              <td class="cell100 column4"> <input type="checkbox" checked="checked" />
                <div class="checkmark"></div>
              </td>
            </tr>
            <tr class="row100 body">
              <td class="cell100 column2  ">
                <p></p>
                <div class="d-flex justify-space-between">
                  <p>JS script for easy integration</p>
                  <p class="icon-hover"><v-icon color="rgba(30,39,50,.24) ">mdi-help-circle-outline </v-icon>
                    <v-tooltip activator="parent" location="top">Tooltip</v-tooltip>
                  </p>
                </div>
              </td>
              <td class="cell100 column3">
                <input type="checkbox" checked="checked" />
                <div class="checkmark"></div>

              </td>
              <td class="cell100 column4"> <input type="checkbox" checked="checked" />
                <div class="checkmark"></div>
              </td>
            </tr>
            <tr class="row100 body">
              <td class="cell100 column2">3D model</td>
              <td class="cell100 column3"><input type="checkbox" checked="checked" />
                <div class="checkmark"></div>
                <span>(Low-Poly)</span>
              </td>
              <td class="cell100 column4"> <input type="checkbox" checked="checked" />
                <div class="checkmark"></div>
                <span>(High-Poly)</span>
              </td>
            </tr>
            <tr class="row100 body">
              <td class="cell100 column2">
                <div class="d-flex justify-space-between">
                  <p>Photorealistic images</p>
                  <p class="icon-hover"><v-icon color="rgba(30,39,50,.24) ">mdi-help-circle-outline </v-icon>
                    <v-tooltip activator="parent" location="top">Tooltip</v-tooltip>
                  </p>
                </div>
              </td>
              <td class="cell100 column3">-</td>
              <td class="cell100 column4"> <input type="checkbox" checked="checked" />
                <div class="checkmark"></div>
                <span>(6 images)</span>
              </td>
            </tr>
            <tr class="row100 body">
              <td class="cell100 column2">
                <div class="d-flex justify-space-between">
                  <p>High-res 360 turntable viewer</p>
                  <p class="icon-hover"><v-icon color="rgba(30,39,50,.24) ">mdi-help-circle-outline </v-icon>
                    <v-tooltip activator="parent" location="top">Tooltip</v-tooltip>
                  </p>
                </div>
              </td>
              <td class="cell100 column3">
                <input type="checkbox" checked="checked" />
                <div class="checkmark"></div>
              </td>
              <td class="cell100 column4">-</td>
            </tr>
            <tr class="row100 body">
              <td class="cell100 column2">
                <div class="d-flex justify-space-between">
                  <p>Modelry Quality Assurance</p>
                  <p class="icon-hover"><v-icon color="rgba(30,39,50,.24) ">mdi-help-circle-outline </v-icon>
                    <v-tooltip activator="parent" location="top">Tooltip</v-tooltip>
                  </p>
                </div>
              </td>
              <td class="cell100 column3">
                <input type="checkbox" checked="checked" />
                <div class="checkmark"></div>
              </td>
              <td class="cell100 column4"> <input type="checkbox" checked="checked" />
                <div class="checkmark"></div>
              </td>
            </tr>
            <tr class="row100 body">
              <td class="cell100 column2">
                <div class="d-flex justify-space-between">
                  <p>DAM</p>
                  <p class="icon-hover"><v-icon color="rgba(30,39,50,.24) ">mdi-help-circle-outline </v-icon>
                    <v-tooltip activator="parent" location="top">Tooltip</v-tooltip>
                  </p>
                </div>
              </td>
              <td class="cell100 column3">
                <input type="checkbox" checked="checked" />
                <div class="checkmark"></div>
              </td>
              <td class="cell100 column4"> <input type="checkbox" checked="checked" />
                <div class="checkmark"></div>
              </td>
            </tr>
            <tr class="row100 body">
              <td class="cell100 column2">Support</td>
              <td class="cell100 column3">
                <input type="checkbox" checked="checked" />
                <div class="checkmark"></div>
              </td>
              <td class="cell100 column4"> <input type="checkbox" checked="checked" />
                <div class="checkmark"></div>
              </td>
            </tr>
          </tbody>
        </table>

        <table v-for="(tableData, tableName) in data.tables" :key="tableName">
          <div class=" cell100 column1 " style="width: 550%;">Technical information</div>
          <tbody v-for="i in 6" :key="i">
            <tr class="row100 body">
              <!-- Lặp qua từng phần tử trong column1 -->
              <td class="cell100 column2">
                 <div class="d-flex justify-space-between">
                 <p >  {{ tableData.column1[i - 1] }}</p>
                  <p v-if=" ['Source file included', '4K resolution images'].includes(tableData.column1[i - 1])"
                  class="icon-hover"><v-icon color="rgba(30,39,50,.24) ">mdi-help-circle-outline </v-icon>
                    <v-tooltip activator="parent" location="top">Tooltip</v-tooltip>
                  </p>
                </div>
              </td>
 <!-- Lặp qua từng phần tử trong column2 -->
              <td class="cell100 column3">
                <v-icon v-if="tableData.column2[i - 1] === 'mdi mdi-check-circle'" style="color: #00C853;">{{
                  tableData.column2[i - 1] }}</v-icon>
                <div v-else>{{ tableData.column2[i - 1] }}</div>
              </td>

              <!-- Lặp qua từng phần tử trong column3 -->
              <td class="cell100 column4">
                <v-icon v-if="tableData.column3[i - 1] === 'mdi mdi-check-circle'" style="color: #00C853;">{{
                  tableData.column3[i - 1] }}</v-icon>
                <div v-else>{{ tableData.column3[i - 1] }}</div>
              </td>
            </tr>
          </tbody>
          <tbody>
            <tr class="row100 body">
              <td class="cell100 column2">Technical specification</td>
              <td class="cell100 column3">
                <v-dialog width="70%">
                  <template v-slot:activator="{ props }">
                    <a href="" v-bind="props" @click.prevent>View</a>
                  </template>

                  <template v-slot:default="{ isActive }">

                    <view-dialog @close="isActive.value = false"></view-dialog>
                  </template>
                </v-dialog>
              </td>
              <td class="cell100 column3">
                <v-dialog width="70%">
                  <template v-slot:activator="{ props }">
                    <a href="" v-bind="props" @click.prevent>View</a>
                  </template>

                  <template v-slot:default="{ isActive }">

                    <view-dialog @close="isActive.value = false"></view-dialog>
                  </template>
                </v-dialog>
              </td>
            </tr>

          </tbody>
        </table>
      </div>


    </div>

  </div>

  <!-- Menu bottom fixed -->
  <div v-show="showDiv" class="CheckoutsNew_bottom">
    <div class="d-flex pt-3 justify-space-between ">
      <div class="CheckoutsNew-btn_notice ">Need something more specific? <span> Contact us</span></div>
      <div class="CheckoutsNew-btn_wrap">
        <v-btn flat color="#19bcc9" class="text-white text-capitalize">
          Select interactive 3D model + AR
        </v-btn>

      </div>
      <div class=" CheckoutsNew-btn_wrap ">
        <v-btn flat color="#19bcc9" class="text-white text-capitalize ">
          Select interactive 3D model + AR
        </v-btn>

      </div>
    </div>
  </div>
  <!-- Mess -->
  <SupportMessenger />
</template>
<script>

export default {
  name: 'Index Checkouts',
  data() {
    return {
      items: [
        {
          src: 'https://arsenal-embeds.cgtrader.com/product-viewers/Egg_lounge_chair14248/assets/1668182817/3%20Egg_lounge_chair_360_45FOV_0005.jpg',
        },
        {
          src: 'https://arsenal-embeds.cgtrader.com/product-viewers/Egg_lounge_chair14248/assets/1668182817/3%20Egg_lounge_chair_360_45FOV_0001.jpg',
        },
        {
          src: 'https://arsenal-embeds.cgtrader.com/product-viewers/Egg_lounge_chair14248/assets/1668182817/3%20Egg_lounge_chair_360_45FOV_0028.jpg',
        },
        {
          src: 'https://arsenal-embeds.cgtrader.com/product-viewers/Egg_lounge_chair14248/assets/1668182817/3%20Egg_lounge_chair_360_45FOV_0009.jpg',
        },
        {
          src: 'https://arsenal-embeds.cgtrader.com/product-viewers/Egg_lounge_chair14248/assets/1668182817/3%20Egg_lounge_chair_360_45FOV_0025.jpg',
        },
        {
          src: 'https://arsenal-embeds.cgtrader.com/product-viewers/Egg_lounge_chair14248/assets/1668182817/3%20Egg_lounge_chair_360_45FOV_0017.jpg',
        },
        {
          src: 'https://arsenal-embeds.cgtrader.com/product-viewers/Egg_lounge_chair14275/assets/1668506907/4%20Egg_lounge_chair_360_45FOV_580_0001.jpg',
        },
      ],
      table: {
        column1: 'Hosted on the cloud',
        column2: 'mdi mdi-check-circle',
        column3: '-',
      },
      data: {
        "tables": {
          "table1": {
            "column1": ["Hosted on the cloud", "4K resolution images", "Textures and materials",
              "Output file formats", "Source file included", "T echnical specification"],
            "column2": ["mdi mdi-check-circle", "mdi mdi-check-circle", "mdi mdi-check-circle",
              "mdi mdi-check-circle", "-", "mdi mdi-check-circle"],
            "column3": ["-", "mdi mdi-check-circle", "mdi mdi-check-circle", "mdi mdi-check-circle",
              "mdi mdi-check-circle", "-"]
          },

        }
      },
      chooseImg: null,
      showDiv: true,
      model: 1,
      dialog: false,
      dialogImg: "",

    }
  },
  mounted() {
    window.addEventListener("scroll", this.handleScroll);
  },
  methods: {
    handleScroll() {
      const isBottom = window.innerHeight + window.scrollY >= document.body.offsetHeight - 80;
      this.showDiv = !isBottom;
    },
    selectedImage(toggle, image) {
      if (toggle) toggle();
      this.chooseImg = image;
    },
    openDialog() {
      this.dialog = true;
      const imageUrl = this.$refs.imageRef.src;
      this.dialogImg = imageUrl;
      console.log(this.dialogImg)
      // Do something with the imageUrl, e.g., update state or use it directly in the dialog
    }
  },
}
</script>
<style scoped>
.Main_container {
  width: 100%;
}

.container_wrapper {
  min-width: 90%;
  padding: 0 60px;
}

.CheckoutsNew_header {
  padding: 12px 0;
  margin-bottom: 20px;
  font-size: 12px;
}

/* set Background nav header */
.v-sheet {
  background: none;
}

.step_bar.v-stepper-item--selected {
  border-top: 4px solid #19bcc9;
}

.v-stepper-item--selected.step_bar .v-stepper-item__avatar.v-avatar {
  background: #19bcc9;
}

.step_bar {
  border-top: 4px solid rgba(30, 39, 50, 0.12);
  min-width: 380px;
}



/* content */
.WorkflowSelection {
  display: flex;
  margin-bottom: 20px;
}

.WorkflowSelection_viewers {
  width: 20%;
}

.viewers_padding {
  padding: 0 20px;
}

.viewers_padding_l {
  padding-left: 20px;
}

.WorkflowSelection_viewers h3 {
  margin-bottom: 23px;
  font-size: 20px;
  line-height: 32px;
}

.WorkflowSelection_viewers_content h4 {
  font-size: 14px;
  margin: 15px 0;

}

.WorkflowSelection_viewers_content {
  width: 40%;
}

.WorkflowSelection_viewers_content_img {
  height: 420px;
  min-width: 300px;
}

.WorkflowSelection_viewers_content_img img {
  width: 100%;
  border: 1px solid rgba(30, 39, 50, .12);
  /* min-width: 300px; */
}

/* img  */

.is_active {
  box-shadow: 0 0 0 4px rgba(25, 188, 201, .2), 0 0 0 1px #19bcc9;
}

/* table */
.table100-nextcols,
.table100-nextcols table {
  width: 100%;
}

.table100 td {
  color: #999999;
}

.cell100 {
  padding-top: 16px;
  padding-bottom: 16px;
  min-height: 60px;
  border-top: 1px solid rgba(30, 39, 50, 0.12);
  align-items: stretch;
}

.cell100 span {
  position: absolute;
  left: 53%;
  top: 17px;
  font-size: 15px;
  font-weight: 400;
}

.column1 {
  width: 100%;
  background: rgba(30, 39, 50, 0.04);
  padding-left: 10px;
}

.column2 {
  width: 20%;
  /* padding-left: 55px; */
  font-size: 16px;
  font-weight: 400;
  padding-left: 10px;
  color: rgba(30, 39, 50, 0.8);
}

.column3 {
  position: relative;
  width: 40%;
  border-left: 1px solid rgba(30, 39, 50, 0.12);
  color: rgba(30, 39, 50, 0.8);
  text-align: center;
}

.column4 {
  position: relative;
  width: 40%;
  border-left: 1px solid rgba(30, 39, 50, 0.12);
  color: rgba(30, 39, 50, 0.8);
  text-align: center;
}

/* Checkbox */


/* Hide the default checkbox */
.table100-nextcols input {
  position: absolute;
  opacity: 0;
  cursor: pointer;
  height: 0;
  width: 0;
}

.table100-nextcols {
  display: block;
  position: relative;
  font-size: 20px;
  user-select: none;
}

/* Create a custom checkbox */
.checkmark {
  position: relative;
  margin: 0 auto;
  height: 20px;
  width: 20px;
}

/* When the checkbox is checked, add a blue background */
.table100-nextcols input:checked~.checkmark {
  background-color: #00c853;
  border-radius: 25px;
  transition: 0.15s;
}

/* Create the checkmark/indicator (hidden when not checked) */
.checkmark:after {
  content: "";
  position: absolute;
  display: none;
}

/* Show the checkmark when checked */
.table100-nextcols input:checked~.checkmark:after {
  display: block;
}

/* Style the checkmark/indicator */
.table100-nextcols .checkmark:after {
  left: 0.35em;
  top: 0.12em;
  width: 6px;
  height: 12px;
  border: solid white;
  border-width: 0 0.15em 0.15em 0;
  transform: rotate(45deg);
}


/* Bottom */
.CheckoutsNew-btn_notice {
  width: 20%;
  font-size: 14px;
  font-weight: 400;
  line-height: 24px;
  padding-right: 40px;
}

.CheckoutsNew-btn_notice span {
  color: #19bcc9;
  transition-duration: .3s;
  transition-property: color;
  text-decoration: underline;
  cursor: pointer;
}

.CheckoutsNew-btn_wrap {
  width: 40%;
  padding: 0 10px;
}

.CheckoutsNew-btn_wrap button {
  width: 100%;
}

.CheckoutsNew-btn_wrap button:hover {
  background-color: #129aa6 !important;
}

.CheckoutsNew-btn_wrap span {
  color: #fff;
}

/* Menu bottom fixed */
.CheckoutsNew_bottom {
  position: sticky;
  padding: 0 60px;
  height: 68px;
  width: 100%;
  bottom: 0;
  border-top: 1px solid rgba(30, 39, 50, .12);
  background-color: #fff;
  box-shadow: 0 2px 6px 0 rgba(30, 39, 50, .12);
}

.primary__image {
  position: relative;
}

.fullScreen {
  position: absolute;
  top: 140px;
  left: 792px;

}
</style>