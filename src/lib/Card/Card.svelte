<script lang="ts">
    export let background: string = 'bg-surface-200 dark:bg-surface-800 space-y-4';
    export let color: string = undefined;

    // Base Classes
    let cBaseCard: string = `p-4 rounded-lg`;

    // Reactive
    $: classesCard = `${cBaseCard} ${background} ${color}`;
</script>

<div class="card {classesCard} {$$props.class}">

    <!-- Header -->
    {#if $$slots.header}
    <header><slot name="header"></slot></header>
    {/if}

    <!-- Body -->
    <slot />

    <!-- Footer -->
    {#if $$slots.footer}
    <footer><slot name="footer"></slot></footer>
    {/if}

</div>
