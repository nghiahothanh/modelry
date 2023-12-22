<template>
  <CheckoutSidebar />
  <div class="px-8 py-10">
    <!-- Form members -->
    <v-sheet class="settings_main" :elevation="1">
      <div class="mt-2 pa-12">
        <div class="d-flex justify-space-between mb-6">
          <h3>Nghia <span>1 members</span></h3>
          <v-btn
            class="buttonPrimary"
            prepend-icon="mdi-account-plus"
            variant="tonal"
            @click="dialogMembers = true"
          >
            Invite Members
          </v-btn>
          <v-dialog v-model="dialogMembers">
            <v-card class="edit-user_content">
              <div class="d-flex justify-space-between mb-6 mt-3">
                <span>Invite Members</span>
                <v-icon block @click="dialogMembers = false">mdi-close</v-icon>
              </div>
              <v-divider></v-divider>
              <div class="my-3">
                <v-row v-for="i in 6" :key="i">
                  <v-col cols="8">
                    <input
                      id="workspace-id"
                      type="text"
                      placeholder="johnsmith@gmail.com"
                  /></v-col>
                  <v-col cols="4"
                    ><v-select
                      id="workspace-id"
                      variant="outlined"
                      type="text"
                      placeholder="Observer"
                      :items="['Admin', 'QA', 'Observer', 'Vendor', 'External QA',]"
                    ></v-select
                  ></v-col>
                </v-row>
              </div>
              <v-divider></v-divider>
              <v-card-actions class="justify-end">
                <v-btn @click="dialogMembers = false" variant="outlined"
                  >Cancel</v-btn
                >
                <v-btn disabled variant="tonal">Save changes</v-btn>
              </v-card-actions>
            </v-card>
          </v-dialog>
        </div>
        <v-row no-gutters class="pb-4">
          <v-col>
            <p class="px-6">Username</p>
          </v-col>
          <v-col>
            <p>Email</p>
          </v-col>
          <v-col>
            <p>Role</p>
          </v-col>
        </v-row>
        <v-row
          no-gutters
          style="border: 1px solid #ccc; max-height: 80px"
          class="py-4 px-3 align-center"
        >
          <v-col>
            <p>nghiahothanh <i>(You)</i></p>
          </v-col>
          <v-col>
            <p>nghia.hothanh.319@gmail.com</p>
          </v-col>
          <v-col class="d-flex align-center">
            <v-select
              disabled
              chips
              label="Admin"
              :items="['']"
              variant="outlined"
            ></v-select>
            <v-menu transition="scale-transition">
              <template v-slot:activator="{ props }">
                <v-btn
                  class="mx-8"
                  variant="text"
                  icon="mdi-dots-vertical"
                  v-bind="props"
                ></v-btn>
              </template>
              <v-list>
                <v-list-item>
                  <v-btn prepend-icon="mdi-pencil">Edit user info</v-btn>
                  <v-dialog v-model="dialogEditinfo" activator="parent">
                    <v-card class="edit-user_content">
                      <div class="d-flex justify-space-between mb-6 mt-3">
                        <span>Edit uer info</span>
                        <v-icon block @click="dialogEditinfo = false"
                          >mdi-close</v-icon
                        >
                      </div>
                      <v-divider></v-divider>
                      <div class="my-3">
                        <label class="label_caption">Email</label>
                        <input id="workspace-id" variant="outlined" type="text" value="abc@gmail.com" readonly> 
                        <label class="label_caption">Username</label>
                        <input id="workspace-id" variant="outlined" type="text" v-model="usernameValue">
                      </div>
                      <v-divider></v-divider>
                      <v-card-actions class="justify-end">
                        <v-btn
                          @click="dialogEditinfo = false"
                          variant="outlined"
                          >Cancel</v-btn
                        >
                        <v-btn :class="{ 'buttonPrimary': shouldAddClass }" variant="tonal">Save changes</v-btn>
                      </v-card-actions>
                    </v-card>
                  </v-dialog>
                </v-list-item>
                <v-list-item
                  ><v-btn disabled variant="plain" prepend-icon="mdi-delete"
                    >Delete</v-btn
                  ></v-list-item
                >
              </v-list>
            </v-menu>
          </v-col>
        </v-row>
      </div>
    </v-sheet>
    <!-- Form Workspaces -->
    <v-sheet class="settings_main" :elevation="1">
      <div class="mt-2 pa-12">
        <div class="d-flex justify-space-between mb-6">
          <h3>Workspaces</h3>
          <v-btn 
            class="buttonPrimary" 
            prepend-icon="mdi-plus" 
            variant="tonal"
            @click="dialogNewWordspace = true"
          >New Workspace</v-btn>
          <v-dialog v-model="dialogNewWordspace">
            <v-card class="edit-user_content">
              <div class="d-flex justify-space-between mb-6 mt-3">
                <span>Create your workspace</span>
                <v-icon block @click="dialogNewWordspace = false">mdi-close</v-icon>
              </div>
              <v-divider></v-divider>
              <div class="my-3">
                <p>Enter your company details to create a workspace.</p>
                <label class="label_caption_title">Workspace name *</label>
                <input id="workspace-id" v-model="workspaceName" variant="outlined" placeholder="abc">
                <label class="label_caption_title">Reference code in external system (Optional)</label>
                <input
                  id="workspace-id"
                  v-model="referenceCode"
                  variant="outlined"
                  placeholder="4fgfdgfd"
                >
              </div>
              <v-divider></v-divider>
              <v-card-actions class="justify-end">
                <v-btn :class="{ 'buttonPrimary': isValid }" :disabled="!isValid" variant="tonal">Create Workspace</v-btn>
              </v-card-actions>
            </v-card>
          </v-dialog>
        </div>
        <p class="mb-4">
          You can find all of the workspaces you belong to listed here. Click on
          the <b>New Workspace</b> button to create a new company workspace. If
          you wish to join an existing workspace, contact the responsible person
          in the company and ask for an invite.
        </p>
        <v-row no-gutters class="pb-4">
          <v-col>
            <p class="px-6">Workspace Name</p>
          </v-col>
          <v-col>
            <p>Role</p>
          </v-col>
        </v-row>
        <v-row
          no-gutters
          style="border: 1px solid #ccc; max-height: 80px"
          class="py-4 px-3 align-center"
        >
          <v-col>
            <p>Nghia <i>(Currently Active)</i></p>
          </v-col>
          <v-col class="d-flex align-center justify-space-between">
            <span>Admin</span>
            <v-menu transition="scale-transition">
              <template v-slot:activator="{ props }">
                <v-btn
                  class="mx-8"
                  variant="text"
                  icon="mdi-dots-vertical"
                  v-bind="props"
                ></v-btn>
              </template>
              <v-list>
                <v-list-item>
                  <v-btn prepend-icon="mdi-pencil">Edit workspace info</v-btn>
                  <v-dialog v-model="dialogEditWorkspace" activator="parent">
                    <v-card class="edit-user_content">
                      <div class="d-flex justify-space-between mb-6 mt-3">
                        <span>Edit workspace info</span>
                        <v-icon block @click="dialogEditWorkspace = false">mdi-close</v-icon>
                      </div>
                      <v-divider></v-divider>
                      <div class="my-3">
                        <label class="label_caption_title"
                          >Workspace name *</label
                        >

                        <input id="workspace-id" variant="outlined" type="text" value="abc">
                        <label class="label_caption_title"
                          >Reference code in external system (Optional)</label
                        >
                        <input id="workspace-id" variant="outlined" type="text" value="dfdfdf">
                      </div>
                      <v-divider></v-divider>
                      <v-card-actions class="justify-end">
                        <v-btn @click="dialogEditWorkspace = false" variant="outlined"
                          >Cancel</v-btn
                        >
                        <v-btn class="buttonPrimary" variant="tonal"
                          >Save changes</v-btn
                        >
                      </v-card-actions>
                    </v-card>
                  </v-dialog>
                </v-list-item>
                <v-list-item
                  ><v-btn prepend-icon="mdi-account-minus"
                    >Leave workspace</v-btn
                  ></v-list-item>
                  <v-dialog v-model="dialogLeaveWorkspace" activator="parent">
                    <v-card class="edit-user_content">
                      <div class="d-flex justify-space-between mb-6 mt-3">
                        <span>Do you want to leave duy workspace?</span>
                        <v-icon block @click="dialogLeaveWorkspace = false">mdi-close</v-icon>
                      </div>
                      <v-divider></v-divider>
                      <div class="my-3">
                        <p>Are you sure you want to do this? Please confirm your action.</p>
                      </div>
                      <v-divider></v-divider>
                      <v-card-actions class="justify-end">
                        <v-btn @click="dialogLeaveWorkspace = false" variant="outlined">Cancel</v-btn>
                        <v-btn class="buttonPrimary" variant="tonal">Leave Workspace</v-btn>
                      </v-card-actions>
                    </v-card>
                  </v-dialog> 
              </v-list>
            </v-menu>
          </v-col>
        </v-row>
      </div>
    </v-sheet>
    <!-- Form API Token -->
    <v-sheet class="settings_main" :elevation="1">
      <div class="mt-2 pa-12">
        <div class="d-flex justify-space-between mb-6">
          <h3>API Token</h3>
          <v-btn
          :class="{ 'buttonPrimary': !generatedToken }"
            prepend-icon="mdi-database-outline"
            variant="outlined"
            @click="generateNewToken"
            >Generate New Token</v-btn>
        </div>
        <v-row no-gutters class="pb-4 align-center justify-space-between">
          <v-col style="max-width: 20%; margin-left: 20px">
            <p>Workspace Name</p>
            <input id="workspace-id" type="text" readonly value="11486" />
          </v-col>
          <v-col style="max-width: 60%; margin-left: 20px">
            <p>API Token</p>
            <input
              id="workspace-id"
              type="text"
              readonly
              :value="generatedToken"
              placeholder="Generated API token"
            />
          </v-col>
          <v-btn 
            class="mt-6 ml-4" 
            variant="outlined" 
            :class="{ 'buttonPrimary': generatedToken }" 
            :disabled="!generatedToken"
            @click="CopyToken = true"
            >Copy Token
          </v-btn>
          <!-- Event click Copy Token -->
          <v-snackbar v-model="CopyToken">
            API Token is copied!
            <template v-slot:actions>
              <v-icon @click="CopyToken = false">mdi-close</v-icon>
            </template>
          </v-snackbar>
        </v-row>
        <v-divider></v-divider>
        <div class="mt-2">
          <a style="color: #19bcc9" target="_bank">
            <v-icon color="#19bcc9">mdi-database-outline</v-icon> API
            Documentation</a
          >
        </div>
      </div>
    </v-sheet>
  </div>
</template>

<script>
export default {
  data() {
    return {
      // Form members
      dialogMembers: false,
      dialogEditinfo: false,
      usernameValue: "abc",
      // Form Workspaces
      dialogEditWorkspace: false,
      dialogLeaveWorkspace: false,
      dialogNewWordspace: false,
      workspaceName: '',
      referenceCode: '',
      // Form API Token
      isButtonPrimary: true,
      generatedToken: "",
      CopyToken: false,
    };
  },
  computed: {
    shouldAddClass() {
      return this.usernameValue != "abc";
    },
    isValid() {
      return this.workspaceName.trim() !== '' || this.referenceCode.trim() !== '';
    }
  },
  methods: {
    generateNewToken() {
      const characters = "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789";
      let token = "";
      for (let i = 0; i < 24; i++) {
        const randomIndex = Math.floor(Math.random() * characters.length);
        token += characters.charAt(randomIndex);
      }

      // Update the input field value
      this.generatedToken = token;
    },
  },
};
</script>

<style scoped>
.buttonPrimary {
  background-color: #19bcc9;
  color: #fff;
  transition: 0.25s;
}

.buttonPrimary:hover {
  background-color: #159ca9;
}
.settings_main {
  margin-bottom: 32px;
}
.settings_main i {
  color: rgba(30, 39, 50, 0.32);
  font-size: 16px;
  font-weight: 400;
}
.v-list {
  padding: 0;
}

.edit-user_content {
  max-width: 576px;
  width: 90%;
  height: auto;
  padding: 12px;
  border-radius: 16px !important;
  margin: 0 auto;
}
.edit-user_content span {
  font-size: 14px;
  font-weight: 600;
}

.label_caption {
  margin: 0 12px 8px;
  color: rgba(30, 39, 50, 0.4);
  font-size: 12px;
  font-weight: 600;
}
.label_caption_title {
  margin: 0 12px 8px;
  color: rgb(30, 39, 50);
  font-style: normal;
  font-size: 12px;
  font-weight: 600;
  line-height: 16px;
}
#workspace-id {
  width: 100%;
  height: 46px;
  margin: 0;
  outline: none;
  border: 1px solid rgba(30, 39, 50, 0.12);
  border-radius: 4px;
  background-color: #fff;
  padding-right: 16px;
  padding-left: 16px;
  color: #1e2732;
  font-size: 16px;
  font-weight: 400;
  transition-duration: 0.3s;
  transition-property: border-color, box-shadow;
  -webkit-appearance: none;
  appearance: none;
}
#workspace-id::placeholder {
  color: #ccc;
}
#workspace-id:focus,
#workspace-id:focus {
    box-shadow: 0 0 0 3px rgba(25,188,201,.2),inset 0 0 0 1px #19bcc9 !important;
}

</style>