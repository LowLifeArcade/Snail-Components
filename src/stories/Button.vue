<template>
    <button type="button" :class="classes" @click="onClick" :style="style">{{ label }}</button>
</template>

<script>
    export default {
        name: 'v-button',
        props: {
            label: {
                type: String,
                required: true,
            },
            primary: {
                type: Boolean,
                default: false,
            },
            size: {
                type: String,
                validator: function (value) {
                    return ['small', 'medium', 'large'].indexOf(value) !== -1;
                },
            },
            backgroundColor: {
                type: String,
            },
        },
        emits: ['click'],
        computed: {
            style() {
                return { backgroundColor: this.backgroundColor };
            },
            classes() {
                return {
                    button: true,
                    'button--primary': this.primary,
                    'button--secondary': !this.primary,
                    [`button--${this.size || 'medium'}`]: true,
                };
            },
        },
        methods: {
            onClick() {
                this.$emit('click');
            },
        },
    };
</script>

<style>
    .button {
        font-family: 'Nunito Sans', 'Helvetica Neue', Helvetica, Arial, sans-serif;
        font-weight: 700;
        border: 0;
        border-radius: 4px;
        cursor: pointer;
        display: inline-block;
        line-height: 1;
    }
    .button--primary {
        color: white;
        background-color: #1ea7fd;
    }
    .button--secondary {
        color: #333;
        background-color: transparent;
        box-shadow: rgba(0, 0, 0, 0.15) 0px 0px 0px 1px inset;
    }
    .button--small {
        font-size: 12px;
        padding: 10px 16px;
    }
    .button--medium {
        font-size: 14px;
        padding: 11px 20px;
    }
    .button--large {
        font-size: 16px;
        padding: 12px 24px;
    }
</style>


