<script lang="ts">
	import Base from './Base.vue';

    import { Component, Prop, Vue } from 'vue-property-decorator';

    @Component
    export default class Custom1 extends Base {
        calcP() : number {
            const { D, E } = this;

            return 2 * D + (D * E / 100);
        }
    }
</script>
