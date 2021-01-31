<template >
    <v-container>
        <h1 class="text-center">SignUp Form </h1>
        <v-row>
            <v-col>
                <v-form ref="SignUpForm" v-model="formValidty">
                    <v-text-field label="UserName" type="text" v-model="useranme" required  :rules="NameRules"></v-text-field>
                    <v-text-field 
                        label="Email" 
                        type="email"
                        v-model="email"
                        :rules="emailRules"
                        required
                        ></v-text-field>
                    <v-autocomplete 
                        label="Which Broxser You Prefer" 
                        :items="browsers"
                    ></v-autocomplete>
                    <v-file-input 
                    label="Attach profile Photo "
                    ></v-file-input>
                    <!-- <v-text-field label="Birthday" v-model="birthday" readonly></v-text-field>
                    <v-date-picker  
                        year-icon="mdi-calendar-blank"
                        prev-icon="mdi-skip-previous"
                        next-icon="mdi-skip-next"
                        v-model="birthday"></v-date-picker> -->
                    <v-row>
                        <v-col
                            cols="12"
                            sm="6"
                            md="4"
                            >
                            <v-menu
                                ref="menu"
                                v-model="menu"
                                :close-on-content-click="false"
                                :return-value.sync="date"
                                transition="scale-transition"
                                offset-y
                                min-width="auto"
                            >
                                <template v-slot:activator="{ on, attrs }">
                                <v-text-field
                                    v-model="date"
                                    label="Select Your Birthday"
                                    prepend-icon="mdi-calendar"
                                    readonly
                                    v-bind="attrs"
                                    v-on="on"
                                ></v-text-field>
                                </template>
                                <v-date-picker
                                v-model="birthday"
                                no-title
                                scrollable
                                year-icon="mdi-calendar-blank"
                                prev-icon="mdi-skip-previous"
                                next-icon="mdi-skip-next"
                                >
                                <v-spacer></v-spacer>
                                <v-btn
                                    text
                                    color="primary"
                                    @click="menu = false"
                                >
                                    Cancel
                                </v-btn>
                                <v-btn
                                    text
                                    color="primary"
                                    @click="$refs.menu.save(birthday)"
                                >
                                    OK
                                </v-btn>
                                </v-date-picker>
                            </v-menu>
                        </v-col>
                        </v-row>
                        <v-switch label="Agree With Terms & Conditions"></v-switch>
                        <v-checkbox 
                            label="Agree With Terms & Conditions"
                            v-model="agreeToTerms"
                            :rules="agreeToTermsRules"
                            required
                            ></v-checkbox>
                        <v-btn type="submit" color="primary mr-4" :disabled="!formValidty" >Register</v-btn>
                        <v-btn color="success" class="mr-4 ml-4" @click="ValidateForm" >Validate Form</v-btn>
                        <v-btn @click="RestValidation" color="warning" class="mr-4">Rest Validation</v-btn>
                        <v-btn @click="Rest" color="error">Rest</v-btn>
                </v-form>
            </v-col>
        </v-row>
    </v-container>
</template>
<script>
export default {
    data() {
        return {
            browsers : ['FireFox','Google Chrome','Microsoft Edge','Brave','Tore'],
            birthday : new Date().toISOString().substr(0, 10),
            useranme:'',
            NameRules :[
                value => !!value || 'UserName is Required',
                value => value.length > 2 || 'the Length must be > 2'
            ],
            agreeToTerms:false,
            agreeToTermsRules:[
                value =>!!value || 'Must be agree with terms and condition to Create an Account '
            ],
            email:'',
            emailRules:[
                value => !!value || 'Email Is Required',
                value => value.indexOf('@') > 2 || 'Invalid Email',
                value => value.includes('@') || 'Email Must Be Include @',
                value => value.indexOf('.') - 4 > value.indexOf('@') || 'invalide Domain Name after @',
                value => value.length -2 > value.indexOf('.') || 'invalide Domain Name after .'
            ],
            formValidty : false
        }
    },
    methods: {
        RestValidation(){
            this.$refs.SignUpForm.resetValidation()
        },
        Rest(){
            this.$refs.SignUpForm.reset()
        },
        ValidateForm(){
            this.$refs.SignUpForm.validate()
        }
    },
}
</script>
<style >
    
</style>