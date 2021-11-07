<template>
    <div class="innerForm">

        <label class="subscribeLabel">Email
            <input class="subscribeInput"
                   :class="{invalidInput:!$v.modalInput.email}"
                   type="email"
                   v-model="modalInput"
                   @input="inputValidation"
            >
        </label>

        <button class="subscribeButton"
                :disabled="!$v.modalInput.email || !$v.modalInput.required"
                @click="subscribeUser">Subscribe
            !</button>

        <!--Info section-->
        <p :class="['subscribeText', 'subscribeUnsuccess']"
                v-if="!$v.modalInput.email"
        >
            Please enter valid email
        </p>

        <p v-if="subscribeSuccess === `already exists`"
           :class="['subscribeText', 'subscribeUnsuccess']"
        >
            You have already subscribed to the newsletter
        </p>

        <p v-if="subscribeSuccess === `new one`"
           :class="['subscribeText', 'subscribeSuccess']"
        >You have successfully subscribed to the newsletter
        </p>

    </div>
</template>

<script>
    import {email, required} from "vuelidate/lib/validators";

    export default {
        data () {
            return {
                modalInput: ``,
                subscribeSuccess: null,
            }
        },
        methods: {
            /*Emails save to localStorage, emails dont save if already exist in localStorage*/
            subscribeUser () {
                if(Object.keys(localStorage).includes(this.modalInput)){
                    this.subscribeSuccess = `already exists`
                }else {
                    localStorage.setItem(this.modalInput, this.modalInput)
                    this.subscribeSuccess = `new one`
                }
                this.modalInput = ``
            },
            inputValidation () {
                this.$v.modalInput.$touch()
                this.subscribeSuccess = `default`
            }
        },
        validations: {
            modalInput: {
                required,
                email,
            }
        }
    }
</script>

<style lang="sass" scoped>

    @import "../../../assets/variables/variables"

    .innerForm
        margin-top: 40px
        z-index: 5

    .subscribeLabel
        font-family: $appFont
        font-weight: 400
        font-size: 12px
        color: $gray3

    .subscribeInput
        width: 302px
        height: 40px
        padding: 10px
        font-size: 20px
        -webkit-border-radius: 6px
        -moz-border-radius: 6px
        border-radius: 6px
        border: 1px solid $gray5
        box-sizing: border-box
        margin-top: 8px

    .invalidInput
        border: 1px solid $errorColor

    .subscribeButton
        width: 106px
        height: 40px
        background: $purpleColor
        border-radius: 35px
        border: none
        color: $whiteColor
        font-family: $appFont
        font-size: 12px
        margin-top: 16px
        margin-bottom: 19px
        &:disabled
            background: $gray2

    .subscribeText
        font-family: $appFont
        font-weight: 500
        font-size: 9px

    .subscribeSuccess
        color: $successColor

    .subscribeUnsuccess
        color: $errorColor

</style>
