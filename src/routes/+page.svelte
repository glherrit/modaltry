<!-- YOU CAN DELETE EVERYTHING IN THIS PAGE -->
<script lang="ts">
	import ModalExampleForm from './ModalExampleForm.svelte';
	import { modalStore, type ModalComponent, type ModalSettings } from '@skeletonlabs/skeleton';
	import ModealExampleForm from './ModalExampleForm.svelte';

	const modalComponentRegistry: Record<string, ModalComponent> = {
		modalComponentOne: {
			// Pass a reference to your custom component
			ref: ModalExampleForm,
			// Add the component properties as key/value pairs
			props: { background: 'bg-red-500' },
			// Provide a template literal for the default component slot
			slot: '<p>Skeleton</p>'
		}
	};

	function modalAlert(): void {
		const modal: ModalSettings = {
			type: 'alert',
			title: 'Hello World!',
			body: 'This simple alert modal uses <code class="code">type: alert</code>.'
		};
		modalStore.trigger(modal);
	}

	function modalComponentForm(): void {
		const c: ModalComponent = { ref: ModalExampleForm };
		const modal: ModalSettings = {
			type: 'component',
			component: c,
			title: 'Custom Form Component',
			body: 'Complete the form below and then press submit.',
			response: (r: any) => console.log('response:', r)
		};
		modalStore.trigger(modal);
	}
</script>

<div class="container h-full mx-auto flex justify-center items-center">
	<div class="space-y-5">
		<h1 class="h1">Let's get cracking bones!</h1>
		<p>Start by exploring:</p>
		<ul>
			<li>
				<code class="code">/src/routes/+layout.svelte</code> - barebones layout, the CSS import order
				is critical!
			</li>
			<li>
				<code class="code">/src/app.postcss</code> - minimal css to make the page full screen, may not
				be relevant for your project
			</li>
			<li>
				<code class="code">/src/routes/+page.svelte</code> - this page, you can replace the contents
			</li>
		</ul>
		<br />
		<button
			class="mb-5 text-white bg-blue-600 hover:bg-blue-800 focus:ring-4 focus:ring-blue-100 font-medium rounded-lg text-sm px-4 py-2.5 text-center inline-flex items-center"
			type="button"
			on:click={modalAlert}
		>
			Source Control
		</button>
	</div>
</div>
