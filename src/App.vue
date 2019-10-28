<template>
    <div class="container">
        <div class="row">
            <div class="col-xs-12">
                <br>
                <button class="btn btn-primary" @click="selectComponent('appBlue')">Load Blue Template</button>
                <button class="btn btn-success" @click="selectComponent('appGreen')">Load Green Template</button>
                <button class="btn btn-danger" @click="selectComponent('appRed')">Load Red Template</button>
                <hr>
                <component :is="selectedComponent">
                    <h2 :slot="selectedComponent">You have selected {{ selectedColour }} component</h2>
                </component>
            </div>
        </div>
    </div>
</template>

<script>
    import Blue from './components/Blue.vue';
    import Green from './components/Green.vue';
    import Red from './components/Red.vue';

    export default {
        components: {
            appBlue: Blue,
            appGreen: Green,
            appRed: Red
        },
        data() {
            return {
                selectedComponent: 'appBlue'
            }
        },
        methods: {
            selectComponent (comp) {
                this.selectedComponent = comp;
            }
        },
        computed: {
            selectedColour() {
                return (this.selectedComponent).substring(3);
            }
        },
    }
</script>

<style>
</style>
