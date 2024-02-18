<script lang="ts">
	import { RecursiveTreeView, type TreeViewNode } from '@skeletonlabs/skeleton';
	let myTreeViewNodes: TreeViewNode[] = [
		{
			id: 'Click me first',
			content: 'Click me first',
			children: [
				{
					id: 'Click me second',
					content: 'Click me second'
				}
			]
		},
		{
			id: 'Click me third',
			content: 'Click me third',
			children: [
				{
					id: 'not needed to click',
					content: 'not needed to click'
				}
			]
		}
	];

	function handleToggle(e: CustomEvent<{ id: string }>) {
		const eventId = e.detail.id;
		toggledEventIds = [...toggledEventIds, eventId];
	}

	let toggledEventIds: string[] = [];
</script>

<div class="h2 p-2">Toggled events:</div>
<ol class="p-2 h-[300px]">
	{#each toggledEventIds as id, i}
		{@const is4thEvent = i === 3}
		<li class="p-2" class:text-red-500={is4thEvent}>
			{i + 1}. <code>{id}</code>
		</li>
	{/each}
</ol>

<div class="container mx-auto flex justify-center items-center">
	<RecursiveTreeView nodes={myTreeViewNodes} on:toggle={handleToggle} />
</div>
