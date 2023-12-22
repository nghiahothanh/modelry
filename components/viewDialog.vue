<template >
  <v-card>
    <div>
      <header class="dialog__header">
        <h3>Interactive 3D Model for Augmented Reality requirements</h3>
        <span class="mdi mdi-alpha-x closeDialog" @click="$emit('close')"></span>

      </header>
      <v-divider></v-divider>

      <p style="padding-left: 30px;">
        The following requirements will be presented to designers working on your 3D models:
      </p>



      <v-expansion-panels v-model="panel" multiple>
        <v-expansion-panel>
          <h4 @click="toggleGeneral">General</h4>
          <div v-if="isShowGeneral" class="expand-transition">
            <!-- Your HTML element goes here -->
            <v-row cols="12">
              <v-col cols="4">Units</v-col>
              <v-col cols="8" style="line-height: 30px;">
                <div class="information">
                  <span>1 unit = 1 meter </span>

                  <span class="mdi mdi-information-outline icon__inf ">
                    <div class="informationDetails">
                      Interactive 3D models can be shown on the web in an interactive 3D viewer, on social networks, in
                      augmented reality, in 3D games, and on most e-commerce platforms, such as Shopify. This option
                      includes the low-poly 3D model as well as an interactive 3D viewer.
                    </div>
                  </span>

                </div>




              </v-col>
            </v-row>
            <v-row cols="12" style="background-color: rgb(246,247,247);">
              <v-col cols="4">Modeling accuracy</v-col>
              <v-col cols="8" style="line-height: 30px;">

                <span>
                  1 cm of provided dimensions.</span>
                  <span class="mdi mdi-information-outline icon__inf ">
                    <div class="informationDetails">
                      Interactive 3D models can be shown on the web in an interactive 3D viewer, on social networks, in
                      augmented reality, in 3D games, and on most e-commerce platforms, such as Shopify. This option
                      includes the low-poly 3D model as well as an interactive 3D viewer.
                    </div>
                  </span>
              </v-col>
            </v-row>
            <v-row cols="12">
              <v-col cols="4">Visual quality</v-col>
              <v-col cols="8" style="line-height: 30px;">
                <p>Model must look identical to the actual product (as realistic and accurate as possible)</p>
                <span>Model consistency in a single family </span>
                <span class="mdi mdi-information-outline icon__inf ">
                    <div class="informationDetails">
                      Interactive 3D models can be shown on the web in an interactive 3D viewer, on social networks, in
                      augmented reality, in 3D games, and on most e-commerce platforms, such as Shopify. This option
                      includes the low-poly 3D model as well as an interactive 3D viewer.
                    </div>
                  </span>
                  
                <p><a href="">High quality, non pixelated textures</a></p>
                <a href="">Closed geometry so that the inside of the mesh is not visible</a>
                <p>Areas not visible in the reference imagery must be interpreted and logically created</p>
              </v-col>
            </v-row>

          </div>

        </v-expansion-panel>

        <v-expansion-panel>
          <h4 @click="toggleDeliverables">Deliverables</h4>
          <div v-if="isShowDeliverables" class="expand-transition">
            <!-- Your HTML element goes here -->
            <v-row cols="12">
              <v-col cols="4">Model file format</v-col>
              <v-col cols="8" style="line-height: 30px;">
                <span>.fbx (binary) </span>   <span class="mdi mdi-information-outline icon__inf ">
                    <div class="informationDetails">
                      Interactive 3D models can be shown on the web in an interactive 3D viewer, on social networks, in
                      augmented reality, in 3D games, and on most e-commerce platforms, such as Shopify. This option
                      includes the low-poly 3D model as well as an interactive 3D viewer.
                    </div>
                  </span>
              </v-col>
            </v-row>
            <v-row cols="12" style="background-color: rgb(246,247,247);">
              <v-col cols="4">Texture file format</v-col>
              <v-col cols="8" style="line-height: 30px;">

                <span>.jpg </span>
                <span class="mdi mdi-information-outline icon__inf ">
                    <div class="informationDetails">
                      Interactive 3D models can be shown on the web in an interactive 3D viewer, on social networks, in
                      augmented reality, in 3D games, and on most e-commerce platforms, such as Shopify. This option
                      includes the low-poly 3D model as well as an interactive 3D viewer.
                    </div>
                  </span>
               <p> <span>.png</span>
                <span class="mdi mdi-information-outline icon__inf ">
                    <div class="informationDetails">
                      Interactive 3D models can be shown on the web in an interactive 3D viewer, on social networks, in
                      augmented reality, in 3D games, and on most e-commerce platforms, such as Shopify. This option
                      includes the low-poly 3D model as well as an interactive 3D viewer.
                    </div>
                  </span>
                </p>
              </v-col>
            </v-row>
            <v-row cols="12">
              <v-col cols="4">Submittable files</v-col>
              <v-col cols="8" style="line-height: 30px;">
                <span>.zip archive, flat structure </span>
                <span class="mdi mdi-information-outline icon__inf ">
                    <div class="informationDetails">
                      Interactive 3D models can be shown on the web in an interactive 3D viewer, on social networks, in
                      augmented reality, in 3D games, and on most e-commerce platforms, such as Shopify. This option
                      includes the low-poly 3D model as well as an interactive 3D viewer.
                    </div>
                  </span>
              </v-col>
            </v-row>
          </div>

        </v-expansion-panel>

        <v-expansion-panel>
          <h4 @click="toggleGeometry">Geometry</h4>
          <div v-if="isShowGeometry">
            <!-- Your HTML element goes here -->
            <v-row cols="12">
              <v-col cols="4">Model orientation</v-col>
              <v-col cols="8" style="line-height: 30px;">
                <p>Models must be placed in a Z+ forward and Y+ up orientation</p>
              </v-col>
            </v-row>
            <v-row cols="12" style="background-color: rgb(246,247,247);">
              <v-col cols="4">Triangle count</v-col>
              <v-col cols="8" style="line-height: 30px;">

                <p>Simple Models - Around 20k triangles </p>
                <p>.Medium Models - Around 45k triangles</p>
                <p>Complex Models - up to 90k triangles</p>
              </v-col>
            </v-row>
            <v-row cols="12">
              <v-col cols="4">Pivots and placement</v-col>
              <v-col cols="8" style="line-height: 30px;">
                <p>Pivot positioned at the origin (0,0,0) </p>
                <p>Mesh should be centered at the origin, above the grid</p>
              </v-col>
            </v-row>
            <v-row cols="12" style="background-color: rgb(246,247,247);">
              <v-col cols="4">Topology</v-col>
              <v-col cols="8" style="line-height: 30px;">

                <span>Quad-based topology, as little triangles as possible </span>
                   <span class="mdi mdi-information-outline icon__inf ">
                    <div class="informationDetails">
                      Interactive 3D models can be shown on the web in an interactive 3D viewer, on social networks, in
                      augmented reality, in 3D games, and on most e-commerce platforms, such as Shopify. This option
                      includes the low-poly 3D model as well as an interactive 3D viewer.
                    </div>
                  </span>
                <p>Mesh should be optimized, without excessive edge loops </p>
                <p>Single mesh object (exception: transparent parts must be separate objects)</p>

              </v-col>
            </v-row>
            <v-row cols="12">
              <v-col cols="4">Transforms</v-col>
              <v-col cols="8" style="line-height: 30px;">

                <p>Transforms must be frozen</p>
              </v-col>
            </v-row>
          </div>
        </v-expansion-panel>
        <v-expansion-panel>
          <h4 @click.self="toggleUV">UV's and UV mapping</h4>
          <div v-if="isShowUV">
            <!-- Your HTML element goes here -->
            <v-row cols="12">
              <v-col cols="4">UV mapping</v-col>
              <v-col cols="8" style="line-height: 30px;">
                <p>Unwrapped UVs (Similar parts can overlap)</p>
                <p>Only 1 UV channel is allowed </p>
                <p>UV space used efficiently. Add necessary amount of padding between UV shell. </p>
              </v-col>
            </v-row>
            <v-row cols="12" style="background-color: rgb(246,247,247);">
              <v-col cols="4">UV seams</v-col>
              <v-col cols="8" style="line-height: 30px;">
                <a href="">UV seams with clean edge flow</a>
                <p>Keep visible seams to a minimum. Place seams where they would make sense in the actual product- the
                  less UV shells the better. </p>
              </v-col>
            </v-row>
          </div>
        </v-expansion-panel>
        <v-expansion-panel>
          <h4 @click.self="toggleTextures">Textures and Materials</h4>
          <div v-if="isShowTextures">
            <!-- Your HTML element goes here -->
            <v-row cols="12">
              <v-col cols="4">Model orientation</v-col>
              <v-col cols="8" style="line-height: 30px;">
                <p>Models must be placed in a Z+ forward and Y+ up orientation</p>
              </v-col>
            </v-row>
            <v-row cols="12" style="background-color: rgb(246,247,247);">
              <v-col cols="4">Triangle count</v-col>
              <v-col cols="8" style="line-height: 30px;">

                <p>Simple Models - Around 20k triangles </p>
                <p>.Medium Models - Around 45k triangles</p>
                <p>Complex Models - up to 90k triangles</p>
              </v-col>
            </v-row>
            <v-row cols="12">
              <v-col cols="4">Pivots and placement</v-col>
              <v-col cols="8" style="line-height: 30px;">
                <p>Pivot positioned at the origin (0,0,0) </p>
                <p>Mesh should be centered at the origin, above the grid</p>
              </v-col>
            </v-row>
            <v-row cols="12" style="background-color: rgb(246,247,247);">
              <v-col cols="4">Topology</v-col>
              <v-col cols="8" style="line-height: 30px;">

                <p>Quad-based topology, as little triangles as possible </p>
                <p>Mesh should be optimized, without excessive edge loops </p>
                <p>Single mesh object (exception: transparent parts must be separate objects)</p>

              </v-col>
            </v-row>
            <v-row cols="12">
              <v-col cols="4">Transforms</v-col>
              <v-col cols="8" style="line-height: 30px;">

                <p>Transforms must be frozen</p>
              </v-col>
            </v-row>
          </div>

        </v-expansion-panel>
        <v-expansion-panel>

          <h4 @click.self="toggleNaming">Naming</h4>
          <div v-if="showNaming">
            <!-- Your HTML element goes here -->
            <v-row cols="12">
              <v-col cols="4">Workflow</v-col>
              <v-col cols="8" style="line-height: 30px;">
                <a href="">PBR metalness</a>
                <p>Normal maps baked from high-poly models where needed.</p>
              </v-col>
            </v-row>
            <v-row cols="12" style="background-color: rgb(246,247,247);">
              <v-col cols="4">Texture size</v-col>
              <v-col cols="8" style="line-height: 30px;">

                <p>Only square power of two sized textures. Max resolution: 2048x2048px </p>
                <p>All texture maps together need to be up to ~7 mb (.jpg variants) depending on model complexity. The
                  less the better, but make sure the quality is consistent.

                </p>

              </v-col>
            </v-row>
            <v-row cols="12">
              <v-col cols="4">Materials</v-col>
              <v-col cols="8" style="line-height: 30px;">
                <p>Multiple materials and textures sets only where extra resolutions is needed </p>
                <p>Transparent parts must have separate materials.</p>
              </v-col>
            </v-row>

            <v-row cols="12" style="background-color: rgb(246,247,247);">
              <v-col cols="4">Required textures</v-col>
              <v-col cols="8" style="line-height: 30px;">

                <p>
                  BaseColor (sRGB)</p>
                <p>
                  AO (Linear)
                </p>
                <p>Roughness (Linear)</p>
                <p>Metalness (Linear)</p>
                <p>Normal (RGB, OpenGL tangent space)</p>
              </v-col>
            </v-row>
          </div>

        </v-expansion-panel>
        <v-expansion-panel>
          <h4 @click.self="toggleAdditional">Additional info</h4>
          <div v-if="showAdditional">
            <!-- Your HTML element goes here -->
            <v-row cols="12">
              <v-col cols="4">HDRI map</v-col>
              <v-col cols="8" style="line-height: 30px;">
                <a href="">
                  Lowpoly Standard HDRI</a>

              </v-col>
            </v-row>
            <v-row cols="12" style="background-color: rgb(246,247,247);">
              <v-col cols="4">Substance Painter Settings</v-col>
              <v-col cols="8" style="line-height: 30px;">

                <a href="">
                  Set AO intensity to 1</a>

              </v-col>
            </v-row>

          </div>
        </v-expansion-panel>
      </v-expansion-panels>
    </div>
  </v-card>
</template>

<script setup>
import { ref } from 'vue'
const isShowGeneral = ref(false);

const toggleGeneral = () => {
  isShowGeneral.value = !isShowGeneral.value;
}
const isShowDeliverables = ref(false);

const toggleDeliverables = () => {
  isShowDeliverables.value = !isShowDeliverables.value;
};

const isShowGeometry = ref(false);
const toggleGeometry = () => {
  isShowGeometry.value = !isShowGeometry.value;
};

const isShowUV = ref(false);
const toggleUV = () => {
  isShowUV.value = !isShowUV.value;
};

const isShowTextures = ref(false);
const toggleTextures = () => {
  isShowTextures.value = !isShowTextures.value;
};
const showNaming = ref(false);

const toggleNaming = () => {
  showNaming.value = !showNaming.value;
};

const showAdditional = ref(false);

const toggleAdditional = () => {
  showAdditional.value = !showAdditional.value;
};
</script>

<style lang="scss" scoped>
.dialog__header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.closeDialog {
  font-size: 3rem;
  cursor: pointer;
}

.content__general {
  width: 100%;
  height: 50px;
  font-size: 1rem;
  cursor: pointer;
  font-weight: bold;
}

h4 {
  width: 100%;
  height: 50px;
  padding-top: 15px;
  cursor: pointer;
}

.icon__inf {
  position: relative;
}

.icon__inf:hover .informationDetails {
  display: block;
}

.informationDetails {

  position: absolute;
  width: 200px;
  height: auto;
  line-height: 15px;
  background-color: rgba(30, 39, 50, 0.772);
  display: none;
  left: 2rem;
  transform: translateY(-50%);

  color: white;
  font-size: 14px;
  padding: 5px;
}

.informationDetails:before {
  content: "";
  position: absolute;
  top: 40%;

  border-left: 5px solid transparent;
  border-right: 5px solid transparent;
  border-top: 10px solid rgba(30, 39, 50, 0.772);
  transform: translateX(-13px);
  rotate: (-25deg);
}

// .informationDetails:hover{
//   position: absolute;
//   width: 200px;
//   height: 200px;
//   background-color:  rgba(30,39,50,.7);
//   left: 5%;
// }</style>