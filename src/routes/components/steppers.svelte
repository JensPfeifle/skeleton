<script lang="ts">
    import { writable, type Writable } from 'svelte/store';

    import CodeBlock from '$lib/CodeBlock/CodeBlock.svelte';
    import DataTable from "$lib/Table/DataTable.svelte";
    import Card from "$lib/Card/Card.svelte";
    import Stepper from '$lib/Stepper/Stepper.svelte';
    import Step from '$lib/Stepper/Step.svelte';

    const active: Writable<number> = writable(0);
    const lorem: string = 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Itaque vel expedita porro vero, saepe dicta repellendus facilis ab accusamus unde, tempora ut nobis eum. Veniam, architecto corrupti.';
    const onComplete = () => { alert('Complete was triggered!'); }

    // Props and Slots
    const tablePropsStepper: any = {
        headings: ['Prop', 'Type', 'Default', 'Required', 'Description'],
        source: [
            ['active', 'Writable<number>', '0 (zero)', '&check;', 'Provide a Svelte Writable that stores the active step state.'],
            ['length', 'number', '0 (zero)', '&check;', 'Informs the component of the total number of steps.'],
            ['accent', 'string', 'bg-primary-500', '-', 'Provide a class that sets the current step numeral background color.'],
            ['background', 'string', 'bg-surface-300 dark:bg-surface-700', '-', 'Provide a class that sets timeline background color.'],
        ],
    };
    const tablePropsStep: any = {
        headings: ['Prop', 'Type', 'Default', 'Required', 'Description'],
        source: [
            ['index', 'number', '-', '&check;', 'Indicates the step index value. Should start with zero 0 (zero)'],
            ['disabled', 'boolean', 'false', '-', 'When enabled, the Next button is disabled. This prevents progress.'],
            ['done', 'boolean', 'false', '-', 'When enabled, numeric step value changes to checkmark.'],
        ],
    };

    // Slots
    const tableSlotsStepper: any = {
        headings: ['Name', 'Description'],
        source: [
            ['default', 'Accepts a set of steps to display.'],
        ],
    };
    const tableSlotsStep: any = {
        headings: ['Name', 'Description'],
        source: [
            ['title', 'Optionally provide the title for the step.'],
            ['subtitle', 'Optionally provide the subtitle for the step.'],
            ['content', 'Provide the content for the step.'],
        ],
    };

    // Events
    const tableEvents: any = {
        headings: ['Prop', 'Description'],
        source: [
            ['complete', `Triggers when the final step's <em>Complete</em> button is pressed.`],
        ],
    };
</script>

<div class="space-y-8">

    <!-- Header -->
    <header class="space-y-4">
        <h1>Stepper</h1>
        <p>Divide content into sequenced steps.</p>
        <CodeBlock language="javascript" code={`import { Stepper, Step } from '@brainandbones/skeleton';`}></CodeBlock>
    </header>

    <!-- Examples -->
    <Card>
        <Stepper {active} length={3} on:complete={onComplete}>
            <Step index={0} disabled={false} done={false}>
                <svelte:fragment slot="title"><h4>Step One</h4></svelte:fragment>
                <svelte:fragment slot="subtitle">Subtext for step one</svelte:fragment>
                <svelte:fragment slot="content"><p>{lorem}</p></svelte:fragment>
            </Step>
            <Step index={1} disabled={false} done={false}>
                <svelte:fragment slot="title"><h4>Step Two</h4></svelte:fragment>
                <svelte:fragment slot="subtitle">Subtext for step two</svelte:fragment>
                <svelte:fragment slot="content"><p>{lorem}</p></svelte:fragment>
            </Step>
            <Step index={2} disabled={false} done={false}>
                <svelte:fragment slot="title"><h4>Step Three</h4></svelte:fragment>
                <svelte:fragment slot="subtitle">Subtext for step three</svelte:fragment>
                <svelte:fragment slot="content"><p>{lorem}</p></svelte:fragment>
            </Step>
        </Stepper>
    </Card>

    <!-- Usage -->
    <section class="space-y-4">
        <h2>Usage</h2>
        <p>For the best user experience keep the number of steps to a minimum. Usually five or less.</p>
        <CodeBlock language="typescript" code={`import type { Writable } from "svelte/store";
const active: Writable<number> = writable(0);`}></CodeBlock>
        <CodeBlock language="typescript" code={`const onComplete: any = () => { /* ... */ }`}></CodeBlock>
        <CodeBlock language="html" code={`
<Stepper {active} length={3} on:complete={onComplete}>
    <Step index={0} disabled={false} done={false}>
        <svelte:fragment slot="title"><h4>Step One</h4></svelte:fragment>
        <svelte:fragment slot="subtitle">Subtext for step one</svelte:fragment>
        <svelte:fragment slot="content">The content of step one.</svelte:fragment>
    </Step>
    <Step index={1} disabled={false} done={false}>
        <svelte:fragment slot="title">Step Two</svelte:fragment>
        <svelte:fragment slot="subtitle">Subtext for step two</svelte:fragment>
        <svelte:fragment slot="content">The content of step two.</svelte:fragment>
    </Step>
</Stepper>
        `.trim()}></CodeBlock>
    </section>

    <!-- Properties -->
	<section class="space-y-4">
		<h2>Properties</h2>
        <h4>Stepper</h4>
        <DataTable headings="{tablePropsStepper.headings}" source="{tablePropsStepper.source}"></DataTable>
        <h4>Step</h4>
        <DataTable headings="{tablePropsStep.headings}" source="{tablePropsStep.source}"></DataTable>
	</section>
	
    <!-- Slots -->
	<section class="space-y-4">
		<h2>Slots</h2>
        <h4>Stepper</h4>
        <DataTable headings="{tableSlotsStepper.headings}" source="{tableSlotsStepper.source}"></DataTable>
        <h4>Step</h4>
        <DataTable headings="{tableSlotsStep.headings}" source="{tableSlotsStep.source}"></DataTable>
	</section>

    <!-- Events -->
	<section class="space-y-4">
		<h2>Events</h2>
        <h4>Stepper</h4>
        <DataTable headings="{tableEvents.headings}" source="{tableEvents.source}"></DataTable>
	</section>
    
</div>
