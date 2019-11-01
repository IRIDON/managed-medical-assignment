<template>
    <p>
        <span v-if="H !== null">
            <strong>{{ H }}</strong> - {{ K }}
        </span>
        <span v-else>Error</span>
    </p>
</template>

<script lang="ts">
    import { Component, Prop, Vue } from 'vue-property-decorator';

    @Component
    export default class Base extends Vue {
        @Prop() A!: boolean;
        @Prop() B!: boolean;
        @Prop() C!: boolean;

        @Prop() D!: number;
        @Prop() E!: number;
        @Prop() F!: number;

        calcM() : number {
            const { D, E } = this;

            return D + (D * E / 10);
        }

        calcP() : number {
            const { D, E, F } = this;

            return D + (D * (E - F) / 25.5);
        }

        calcT() : number {
            const { D, F } = this;

            return D - (D * F / 30);
        }

        get H() : string | null {
            const { A, B, C } = this;

            if (A && B && !C) {
                return 'M';
            }

            if (A && B && C) {
                return 'P';
            }

            if (!A && B && C) {
                return 'T';
            }

            return null;
        }

        get K() : number {
            switch (this.H) {
                case 'M':
                    return this.calcM();
                case 'P':
                    return this.calcP();
                case 'T':
                    return this.calcT();
                default:
                    return 0;
            }
        }
    }
</script>
