<script>
	import { page } from '$app/stores';
	import { goto } from '$app/navigation';
</script>

<div class="bg-white dark:bg-gray-900 min-h-screen flex items-center justify-center px-4">
	<div class="max-w-md w-full text-center">
		<div class="mb-6">
			<div class="text-8xl font-bold text-gray-200 dark:text-gray-800 select-none">
				{$page.status}
			</div>
		</div>

		<h1 class="text-2xl font-semibold text-gray-900 dark:text-gray-100 mb-2">
			{#if $page.status === 404}
				Page Not Found
			{:else if $page.status === 500}
				Server Error
			{:else if $page.status === 403}
				Access Denied
			{:else}
				Something went wrong
			{/if}
		</h1>

		<p class="text-gray-600 dark:text-gray-400 mb-8 leading-relaxed">
			{#if $page.error?.message}
				{$page.error.message}
			{:else if $page.status === 404}
				The page you&apos;re looking for doesn&apos;t exist or has been moved.
			{:else if $page.status === 500}
				We&apos;re having trouble loading this page. Please try again later.
			{:else if $page.status === 403}
				You don&apos;t have permission to access this resource.
			{:else}
				An unexpected error occurred. Please try again.
			{/if}
		</p>

		<div class="flex flex-col sm:flex-row gap-3 justify-center">
			<button
				on:click={() => goto('/')}
				class="inline-flex items-center justify-center px-5 py-2.5 text-sm font-medium text-white bg-gray-900 dark:bg-white dark:text-gray-900 rounded-full hover:bg-gray-800 dark:hover:bg-gray-100 transition-colors focus:outline-none focus:ring-2 focus:ring-gray-500 focus:ring-offset-2 dark:focus:ring-offset-gray-900"
			>
				Go to Home
			</button>

			<button
				on:click={() => history.back()}
				class="inline-flex items-center justify-center px-5 py-2.5 text-sm font-medium text-gray-700 dark:text-gray-300 bg-gray-100 dark:bg-gray-800 rounded-full hover:bg-gray-200 dark:hover:bg-gray-700 transition-colors focus:outline-none focus:ring-2 focus:ring-gray-500 focus:ring-offset-2 dark:focus:ring-offset-gray-900"
			>
				Go Back
			</button>
		</div>
	</div>
</div>
