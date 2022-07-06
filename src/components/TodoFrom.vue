<template>
    <v-dialog v-model="dialog" persistent max-width="400px">
        <template v-slot:activator="{ on, attrs }">
            <v-btn color="#005466" dark v-bind="attrs" v-on="on">
                Add new User
            </v-btn>
        </template>
        <v-card>
            <v-card-title>
                <span class="text-h5">User Profile</span>
            </v-card-title>
            <v-card-text>
                <v-container>
                    <v-text-field v-model="userData.FullName" class="mb-3" label="Full Name*" dense hide-details outlined></v-text-field>
                    <v-text-field v-model="userData.username" class="mb-3" hide-details outlined dense label="Username"></v-text-field>

                    <div>
                        <v-btn class="py-10 text-truncate" color="#005466" style="width:100%" outlined depressed
                            :loading="isSelecting" @click="fileUpload">
                            <v-icon class="mr-2">
                                mdi-cloud-upload
                            </v-icon>
                            {{ seletedFileName }}
                        </v-btn>
                        <input ref="uploader" class="d-none" type="file" accept="image/*" @change="onFileChanged">
                    </div>

                </v-container>
            </v-card-text>

            <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn color="blue darken-1" text @click="dialog = false">
                    Close
                </v-btn>
                <v-btn color="blue darken-1" text @click="submitData">
                    Save
                </v-btn>
            </v-card-actions>

        </v-card>

    </v-dialog>
</template>

<script>
    export default {
        name: "TodoFrom",

        data: () => {
            return {
                dialog: false,
                isSelecting: false,
                selectedFile: null,

                userData: {
                    FullName: null,
                    username: null
                }
            }
        },

        methods: {
            fileUpload() {
                this.isSelecting = true
                window.addEventListener('focus', () => {
                    this.isSelecting = false
                }, {
                    once: true
                })

                this.$refs.uploader.click()
            },
            onFileChanged(e) {
                this.selectedFile = e.target.files[0]
            },

            submitData(){
                let url = URL.createObjectURL(this.selectedFile)
                const user = {
                    id: Date.now(),
                    name: this.userData.FullName,
                    username: this.userData.username,
                    avator: url
                }
                this.$emit('submittedData', user);
                this.dialog = false
            }
        },

        computed: {
            seletedFileName() {
                return this.selectedFile ? this.selectedFile.name : "upload image"
            }
        }
    }
</script>