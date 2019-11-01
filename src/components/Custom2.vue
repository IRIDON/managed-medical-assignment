<script lang="ts">
	import Base from './Base.vue';

    import { Component, Prop, Vue } from 'vue-property-decorator';

    @Component
    export default class Custom2 extends Base {
        get H() : string | null {
            const { A, B, C } = this;

            if (A && B && !C) {
                return 'T';
            }

            if (A && B && C) {
                return 'P';
            }

            if (A && !B && C) {
                return 'M';
            }

            if (!A && B && C) {
                return 'T';
            }

            return null;
        }

        calcM() : number {
            const { D, E, F } = this;

            return F + D + (D * E / 100)
        }
    }
</script>
