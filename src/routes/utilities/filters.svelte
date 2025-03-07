<script lang="ts">
    import Card from '$lib/Card/Card.svelte';
	import CodeBlock from '$lib/CodeBlock/CodeBlock.svelte';
    import Badge from '$lib/Badge/Badge.svelte';
	import { filter } from '$lib/Filters/filter';

    // Avatar Placeholder
	let placeholder = 'https://i.pravatar.cc/512?img=5';
</script>

<div class="space-y-8">

	<!-- Header -->
	<header class="space-y-4">
        <div class="flex justify-start items-center space-x-4">
            <h1>Filters</h1>
            <Badge background="bg-warning-500">Experimental</Badge>
        </div>
		<p>Bring life to your elements by applying a set of unique <a href="https://developer.mozilla.org/en-US/docs/Web/SVG/Element/filter" target="_blank">SVG filters</a>. Skeleton provides built-in support for filters within certain components, such as Avatars.</p>
	</header>

	<!-- Examples -->
    <Card>
        <div class="grid grid-cols-1 md:grid-cols-3 xl:grid-cols-4 gap-4">
            <section class="text-center overflow-hidden">
                <img class="bg-surface-700 aspect-square w-full rounded-xl" src={placeholder} alt="example" />
                <h6 class="mt-2">Original</h6>
            </section>
            <section class="text-center overflow-hidden">
                <img class="bg-surface-700 aspect-square w-full rounded-xl" src={placeholder} use:filter={'Emerald'} alt="example" />
                <h6 class="mt-2">Emerald</h6>
            </section>
            <section class="text-center overflow-hidden">
                <img class="bg-surface-700 aspect-square w-full rounded-xl" src={placeholder} use:filter={'BlueNight'} alt="example" />
                <h6 class="mt-2">BlueNight</h6>
            </section>
            <section class="text-center overflow-hidden">
                <img class="bg-surface-700 aspect-square w-full rounded-xl" src={placeholder} use:filter={'XPro'} alt="example" />
                <h6 class="mt-2">XPro</h6>
            </section>
            <section class="text-center overflow-hidden">
                <img class="bg-surface-700 aspect-square w-full rounded-xl" src={placeholder} use:filter={'Summer84'} alt="example" />
                <h6 class="mt-2">Summer84</h6>
            </section>
            <section class="text-center overflow-hidden">
                <img class="bg-surface-700 aspect-square w-full rounded-xl" src={placeholder} use:filter={'Rustic'} alt="example" />
                <h6 class="mt-2">Rustic</h6>
            </section>
            <section class="text-center overflow-hidden">
                <img class="bg-surface-700 aspect-square w-full rounded-xl" src={placeholder} use:filter={'Apollo'} alt="example" />
                <h6 class="mt-2">Apollo</h6>
            </section>
            <section class="text-center overflow-hidden">
                <img class="bg-surface-700 aspect-square w-full rounded-xl" src={placeholder} use:filter={'GreenFall'} alt="example" />
                <h6 class="mt-2">GreenFall</h6>
            </section>
            <section class="text-center overflow-hidden">
                <img class="bg-surface-700 aspect-square w-full rounded-xl" src={placeholder} use:filter={'Noir'} alt="example" />
                <h6 class="mt-2">Noir</h6>
            </section>
            <section class="text-center overflow-hidden">
                <img class="bg-surface-700 aspect-square w-full rounded-xl" src={placeholder} use:filter={'NoirLight'} alt="example" />
                <h6 class="mt-2">NoirLight</h6>
            </section>
        </div>
    </Card>

	<!-- Usage -->
	<section class="space-y-4">
		<h2>Usage</h2>
        <h4>Import Filter Components</h4>
        <p>Add within scope of your filtered element. For global access, add to your root <code>__layout.svelte</code> component.</p>
		<CodeBlock language="javascript" code={`import { Emerald, BlueNight, /* ... */  } from '@brainandbones/skeleton';`} />
		<CodeBlock language="html" code={`<BlueNight />`} />
        <h4>Use Filter Action</h4>
        <p>Use the following <a href="https://svelte.dev/tutorial/actions" target="_blank">Svelte action</a> to apply a filter to any element.</p>
        <CodeBlock language="javascript" code={`import { filter } from '@brainandbones/skeleton';`} />
		<CodeBlock language="html" code={`<img use:filter={'BlueNight'} {src}>`} />
        <h4>Use Inline CSS</h4>
        <p>Use the following to apply a filter using only inline CSS.</p>
		<CodeBlock language="html" code={`<img style="filter: url({'#BlueNight'})" {src}>`} />
	</section>

    <!-- Browser support -->
    <section class="space-y-4">
		<h2>Browser Support</h2>
        <p>Please be aware that <a href="https://caniuse.com/css-filters" target="_blank">browser support</a> varies. We recommend you utilize progressive enhancement for non-supported browsers. Firefox is not supported.</p>
        <div class="grid grid-cols-1 md:grid-cols-4 gap-4">
            <Card background="bg-emerald-500" class="flex justify-center items-center px-4 min-h-[100px]">
                <h6>Chrome: Full</h6>
            </Card>
            <Card background="bg-emerald-500" class="flex justify-center items-center px-4 min-h-[100px]">
                <h6>Edge: Full</h6>
            </Card>
            <Card background="bg-orange-500" class="flex justify-center items-center px-4 min-h-[100px]">
                <h6>Safari: Partial</h6>
            </Card>
            <Card background="bg-rose-500" class="flex justify-center items-center px-4 min-h-[100px]">
                <h6>Firefox: None</h6>
            </Card>
        </div>
    </section>
</div>
