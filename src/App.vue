<template>
    <div class="container">
        <Widget>
            click here!
        </Widget>
    </div>
</template>

<script lang="ts">
    import { Component, Prop, Vue } from 'vue-property-decorator';
    import Widget from '@/components/Widget.vue';

    @Component({
        components: { Widget }
    })
    export default class extends Vue {
        @Prop({ default: 'default value' }) private msg!: string;

        created() {
            console.log('created');
        }
    }
</script>

<style lang="scss" scoped>

    #app {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 60px;
    }
</style>
