<script lang='ts'>
    import Beam from "$lib/components/beams/beam.svelte";
    export let count = 40;
</script>

<div class="relative w-screen h-screen">
    <div class="beams">
        {#each Array(count) as _,i }
            <Beam index={i+1} />
        {/each}
    </div>

    <div class="absolute z-10 w-full h-full">
        <slot></slot>
    </div>
</div>
    
<style>
    .beams {
        height: 100%;
        width: 100%;
        display: grid;
        place-items: end;
        margin: 0;
        @apply gap-4 absolute z-0 left-0 top-0;
    }
</style>