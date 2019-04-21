<template>
<!-- This is a component that switches between on and off and that is called through a v-model
    in another application! The switching and the styling are made in this component -->
    <div>
        <div 
            id="on"
            @click="appSwitch(true)"
            :class="{active: value}">
            On
        </div>

        <div 
            id="off"
            @click="appSwitch(false)"
            :class="{active: !value}">
            Off
        </div>
    </div>
</template>

<script>
export default {
    // For v-model to work in the calling application we HAVE to have a prop named "value"!!!
    props: ["value"],
    methods: {
        appSwitch(isOn) {
            // v-model on the calling app expects "input" as an $emit name
            // For v-model to work in the calling application we HAVE to use "input" as the $emit name!!!
            this.$emit("input", isOn);
        },
    }
}
</script>

<style scoped>
    #on, #off {
        width: 40px;
        height: 20px;
        background-color: lightgray;
        padding: 2px;
        display: inline-block;
        margin: 10px -2px;
        box-sizing: content-box;
        cursor: pointer;
        text-align: center;
    }
    #on:hover, #on.active {
        background-color: lightgreen;
    }
    #off:hover, #off.active {
        background-color: lightcoral;
    }
</style>
