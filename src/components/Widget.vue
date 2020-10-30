<template>
    <div class="container">
        <transition name="fade">
            <div
                v-if="show"
                class="modal"
            >
                <div class="content">
                    Content ...
                </div>
                <div
                    @click="show = false"
                    class="backdrop"
                />
            </div>
        </transition>
        <div @click="open">
            <slot />
        </div>
    </div>
</template>

<script lang="ts">
    import { Component, Prop, Vue } from 'vue-property-decorator';

    @Component({
        components: {}
    })
    export default class extends Vue {
        show: any = false;
        @Prop({ default: 'default value' }) private msg!: string;

        created() {
            console.log('created');
        }

        open() {
            this.show = true;
            // debugger;
        }
    }
</script>

<style lang="scss" scoped>

    .fade-enter-active, .fade-leave-active {
        transition: opacity .5s;
    }

    .fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */
    {
        opacity: 0;
    }

    html {
        height: 100%;
    }

    body {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        margin-top: 60px;
        height: 100%;
    }

    .container {
        z-index: 200;
        position: fixed;
        background: white;
        left: 0;
        right: 0;
        bottom: 0;
        top: 0;
    }

    .content {
        z-index: 10;
        background: white;
        padding: 20px;
        width: 300px;
        height: 50%;
        align-self: center;
    }

    .modal {
        height: 100%;
        display: flex;
        align-content: center;
        justify-content: center;
    }

    .backdrop {
        z-index: 0;
        position: fixed;
        background: rgba(0, 0, 0, 0.7);
        left: 0;
        top: 0;
        right: 0;
        bottom: 0;
    }
</style>
