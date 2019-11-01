<template>
    <div class="box">
        <main class="container" id="app">
            <section class="form">
                <div class="form-group form-check form-check-inline custom-check">
                    <input v-model="A" type="checkbox" class="form-check-input" id="fieldA">
                    <label class="form-check-label" for="fieldA">A</label>
                </div>
                <div class="form-group form-check form-check-inline custom-check">
                    <input v-model="B" type="checkbox" class="form-check-input" id="fieldB">
                    <label class="form-check-label" for="fieldB">B</label>
                </div>
                <div class="form-group form-check form-check-inline custom-check">
                    <input v-model="C" type="checkbox" class="form-check-input" id="fieldC">
                    <label class="form-check-label" for="fieldC">C</label>
                </div>
            </section>

            <section class="row">
                <div class="col">
                    <div class="form-group form-check">
                        <label>D</label>
                        <input v-model.number="D" class="form-control" type="number" placeholder="Float field" step="0.1">
                    </div>
                </div>
                <div class="col">
                    <div class="form-group form-check">
                        <label>E</label>
                        <input v-model.number="E" class="form-control" type="number" placeholder="Only int">
                    </div>
                </div>
                <div class="col">
                    <div class="form-group form-check">
                        <label>F</label>
                        <input v-model.number="F" class="form-control" type="number" placeholder="Only int">
                    </div>
                </div>
            </section>

            <section v-for="view in viewComponents" :key="view">
                <h3>{{ view }}</h3>
                <component :is="view" :A="A" :B="B" :C="C" :D="D" :E="E" :F="F" />
            </section>
        </main>
    </div>

</template>

<script lang="ts">
    import { Component, Vue } from 'vue-property-decorator';

    import Base from './components/Base.vue';
    import Custom1 from './components/Custom1.vue';
    import Custom2 from './components/Custom2.vue';

    @Component({
        components: {
            Base,
            Custom1,
            Custom2
        },
    })
    export default class App extends Vue {
        A : boolean = true;
        B : boolean = true;
        C : boolean = false;

        D : number = 0;
        E : number = 0;
        F : number = 0;

        readonly viewComponents : string[] = ['Base', 'Custom1', 'Custom2'];
    }
</script>

<style lang="scss">
    .box {
        display: flex;
        align-items: center;
        height: 100vh;
    }

    .custom-check {
        &.form-check-inline {
            margin-right: 20px;
        }
    }
</style>
