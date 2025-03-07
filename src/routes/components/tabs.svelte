<script lang="ts">
    import { writable } from 'svelte/store';

    import CodeBlock from '$lib/CodeBlock/CodeBlock.svelte';
    import DataTable from "$lib/Table/DataTable.svelte";
    import Card from "$lib/Card/Card.svelte";
    import Tab from "$lib/Tab/Tab.svelte";
    import TabGroup from "$lib/Tab/TabGroup.svelte";

    let icon = `<svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor"><path d="M4 3a2 2 0 100 4h12a2 2 0 100-4H4z" /><path fill-rule="evenodd" d="M3 8h14v7a2 2 0 01-2 2H5a2 2 0 01-2-2V8zm5 3a1 1 0 011-1h2a1 1 0 110 2H9a1 1 0 01-1-1z" clip-rule="evenodd" /></svg>`;
    
    // Stores
    let storeOne = writable('a');
    let storeTwo = writable('a');
    let storeThree = writable('a');

    // Props and Slots
    const tablePropsGroup: any = {
        headings: ['Prop', 'Type', 'Default', 'Required', 'Description'],
        source: [
            ['selected', 'Writable', '-', '&check;', 'A svelte store to keep track of tab selection.'],
            ['justify', 'string', 'justify-start', '-', `Provide a class to set the flex justification. 'justify-start' is best small screens.`],
            ['highlight', 'string', 'border-primary-500', '-', 'Provide a class to set the highlighted border color.'],
            ['color', 'string', 'text-primary-500', '-', 'Provide class to set text color.'],
        ],
    };
    const tablePropsItem: any = {
        headings: ['Prop', 'Type', 'Description'],
        source: [
            ['value', 'any', 'The value of each tab.'],
        ],
    };
    const tableSlots: any = {
        headings: ['Name', 'Description'],
        source: [
            ['lead', 'Provides a leading position, which can be used for icons.'],
        ],
    };
</script>

<div class="space-y-8">

    <!-- Header -->
    <header class="space-y-4">
        <h1>Tabs</h1>
        <p>Use tabs to quickly switch between different views.</p>
        <CodeBlock language="javascript" code={`import { TabGroup, Tab } from '@brainandbones/skeleton';`}></CodeBlock>
    </header>

    <!-- Examples -->
    <section class="space-y-4">
        <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
            <Card class="space-y-4">
                <TabGroup selected={storeOne}>
                    <Tab value="a">Tab A</Tab>
                    <Tab value="b">Tab B</Tab>
                    <Tab value="c">Tab C</Tab>
                </TabGroup>
                <div>
                    {#if $storeOne === 'a'}Content A{/if}
                    {#if $storeOne === 'b'}Content B{/if}
                    {#if $storeOne === 'c'}Content C{/if}
                </div>
            </Card>
            <Card class="space-y-4">
                <TabGroup selected={storeTwo} justify="justify-start md:justify-end" highlight="border-accent-500" color="text-accent-500">
                    <Tab value="a">Tab A</Tab>
                    <Tab value="b">Tab B</Tab>
                    <Tab value="c">Tab C</Tab>
                </TabGroup>
                <div>
                    {#if $storeTwo === 'a'}Content A{/if}
                    {#if $storeTwo === 'b'}Content B{/if}
                    {#if $storeTwo === 'c'}Content C{/if}
                </div>
            </Card>
        </div>
        <Card class="space-y-4">
            <TabGroup selected={storeThree} justify="justify-start md:justify-center" highlight="border-warning-500" color="text-warning-500">
                <Tab value="a">
                    <svelte:fragment slot="lead">{@html icon}</svelte:fragment>
                    Books
                </Tab>
                <Tab value="b">
                    <svelte:fragment slot="lead">{@html icon}</svelte:fragment>
                    Movies
                </Tab>
                <Tab value="c">
                    <svelte:fragment slot="lead">{@html icon}</svelte:fragment>
                    Television
                </Tab>
            </TabGroup>
            <div>
                {#if $storeThree === 'a'}
                    <h4>Books</h4>
                    <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. </p>
                {/if}
                {#if $storeThree === 'b'}
                    <h4>Movies</h4>
                    <p>Nisl nunc mi ipsum faucibus vitae aliquet nec. Ac ut consequat semper viverra nam libero justo laoreet. Nec sagittis aliquam malesuada.</p>
                {/if}
                {#if $storeThree === 'c'}
                    <h4>Television</h4>
                    <p>Ut sem viverra aliquet eget sit. Porttitor lacus luctus accumsan tortor posuere ac ut consequat. Vulputate enim nulla aliquet porttitor.</p>
                {/if}
            </div>
        </Card>
    </section>

    <!-- Usage -->
    <section class="space-y-4">
        <h2>Usage</h2>
        <CodeBlock language="typescript" code={`import type { Writable } from "svelte/store";
let storeTab: Writable<string> = writable('a');`}></CodeBlock>
        <CodeBlock language="html" code={`
<TabGroup selected={storeTab} justify="justify-start md:justify-center" highlight="border-accent-500" color="text-accent-500">
    <Tab value="a">Tab A</Tab>
    <Tab value="b">
        <svelte:fragment>{@html icon}</svelte:fragment>
        <span>Tab B</span>
    </Tab>
</TabGroup>
        `.trim()}></CodeBlock>
        <CodeBlock language="html" code={`
<!-- Conditionally display content -->
{#if $storeTab === 'a'}Content A{/if}
{#if $storeTab === 'b'}Content B{/if}
        `.trim()}></CodeBlock>
    </section>

    <!-- Properties -->
	<section class="space-y-4">
		<h2>Properties</h2>
        <h4>Tab Group</h4>
        <DataTable headings="{tablePropsGroup.headings}" source="{tablePropsGroup.source}"></DataTable>
        <h4>Tab</h4>
        <DataTable headings="{tablePropsItem.headings}" source="{tablePropsItem.source}"></DataTable>
	</section>
	
	<!-- Slots -->
	<section class="space-y-4">
		<h2>Slots</h2>
        <h4>Tab</h4>
        <DataTable headings="{tableSlots.headings}" source="{tableSlots.source}"></DataTable>
	</section>
    
</div>
