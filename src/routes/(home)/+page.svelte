<script lang="ts">
	import { enhance, applyAction } from '$app/forms';
	import { superForm } from 'sveltekit-superforms';

	export let data;

	// Client API:
	const { form, errors, constraints, message } = superForm(data.form);
	let isLoading: boolean = false;
	let formSubmitted: boolean | undefined = false;
</script>

<section class="relative overflow-hidden pb-20">
	<div class="w-full h-full relative">
		<img
			src="../../images/hero-bg.png"
			alt="BTM Locations"
			class="w-full h-full bg-cover object-cover"
		/>
	</div>

	<div
		class="bg-white shadow-xl p-3 sm:p-6 mx-auto absolute -bottom-12 w-11/12 sm:w-3/4 left-0 right-0 rounded-lg mb-20"
	>
		<div class="flex justify-between items-center">
			<div class="flex flex-col items-center w-full mx-auto">
				<h3 class="text-[#E07514] font-bold text-sm sm:text-2xl">Arrival Date:</h3>
				<p class="font-semibold text-sm md:text-base">27th of July 2024</p>
			</div>
			<div>
				<hr class="w-[1px] h-10 bg-gray-400" />
			</div>
			<div class="flex flex-col items-center w-full mx-auto">
				<h3 class="text-[#E07514] font-bold text-sm sm:text-2xl">Departure Date:</h3>
				<p class="font-semibold text-sm md:text-base">3rd of August 2024</p>
			</div>
		</div>
	</div>
</section>

<section id="location" class="location relative overflow-hidden">
	<div class="w-full h-full relative">
		<img
			src="../../images/location.png"
			alt="BTM Locations"
			class="w-full h-full bg-cover object-cover"
		/>
	</div>
</section>

<section id="location" class="location2 relative overflow-hidden h-full">
	<div class="w-full h-full relative">
		<img
			src="../../images/location2.png"
			alt="BTM Locations"
			class="w-full h-full bg-cover object-cover"
		/>
	</div>
</section>

<section class="contact-form bg-gray-200">
	<form
		method="POST"
		use:enhance={() => {
			isLoading = true;
			formSubmitted = false;
			return async ({ result, update }) => {
				if (result.status !== 200) {
					isLoading = false;
					formSubmitted = undefined;
					return await update();
				}
				isLoading = false;
				formSubmitted = true;
				await applyAction(result);
			};
		}}
		class="w-10/12 mx-auto shadow-2xl rounded-lg p-10 md:py-20 bg-white my-10 md:my-32 grid gap-8 border border-[#E07514]"
	>
		<div class="grid gap-7 md:w-4/6 mx-auto">
			<label for="name" class="flex flex-col gap-2">
				<span class={`${$errors.firstName?.length ? 'text-red-500' : ''} font-bold md:text-xl`}>
					Your Name
				</span>
				<div class="flex justify-between gap-3 md:gap-8">
					<label for="firstName" class="flex flex-col w-full">
						<input
							disabled={isLoading}
							type="text"
							placeholder="First name"
							name="firstName"
							id="firstName"
							aria-invalid={$errors.firstName ? true : false}
							on:keypress={(ev) => {
								$errors.firstName = undefined;
							}}
							bind:value={$form.firstName}
							class={`${$errors.firstName?.length ? 'border border-red-500' : ''} w-full p-3 rounded shadow-inner bg-gray-50 border border-[#e0771463] focus:outline-none`}
						/>
						{#if $errors.firstName?.length}
							<p class="text-red-500 italic">{$errors.firstName}</p>
						{/if}
					</label>

					<label for="lastName" class="flex flex-col w-full">
						<input
							disabled={isLoading}
							type="text"
							placeholder="Last name"
							name="lastName"
							id="lastName"
							aria-invalid={$errors.lastName ? true : false}
							on:keypress={(ev) => {
								$errors.lastName = undefined;
							}}
							bind:value={$form.lastName}
							class={`${$errors.lastName?.length ? 'border border-red-500' : ''} w-full p-3 rounded shadow-inner bg-gray-50 border border-[#e0771463] focus:outline-none`}
						/>
						{#if $errors.lastName?.length}
							<p class="text-red-500 italic">{$errors.lastName}</p>
						{/if}
					</label>
				</div>
			</label>

			<label for="email" class="flex flex-col gap-2">
				<span class={`${$errors.email?.length ? 'text-red-500' : ''} font-bold md:text-xl`}>
					Email Address
				</span>
				<input
					disabled={isLoading}
					type="email"
					name="email"
					id="email"
					aria-invalid={$errors.email ? true : false}
					on:keypress={(ev) => {
						$errors.email = undefined;
					}}
					bind:value={$form.email}
					placeholder="Eg. example@email.com"
					class={`${$errors.email?.length ? 'border border-red-500' : ''} w-full p-3 rounded shadow-inner bg-gray-50 border border-[#e0771463] focus:outline-none`}
				/>
				{#if $errors.email?.length}
					<p class="text-red-500 italic">{$errors.email}</p>
				{/if}
			</label>

			<label for="phoneNumber" class="flex flex-col gap-2">
				<span class={`${$errors.phoneNumber?.length ? 'text-red-500' : ''} font-bold md:text-xl`}>
					Phone Number
				</span>
				<input
					disabled={isLoading}
					type="tel"
					name="phoneNumber"
					id="phoneNumber"
					placeholder="+234"
					on:keypress={(ev) => {
						$errors.phoneNumber = undefined;
					}}
					bind:value={$form.phoneNumber}
					class={`${$errors.phoneNumber?.length ? 'border border-red-500' : ''} w-full p-3 rounded shadow-inner bg-gray-50 border border-[#e0771463] focus:outline-none`}
				/>
				{#if $errors.phoneNumber?.length}
					<p class="text-red-500 italic">{$errors.phoneNumber}</p>
				{/if}
			</label>
			{#if formSubmitted}
				<p class="text-green-500 font-bold">Thank you. Form submitted successfully.</p>
			{/if}
			{#if formSubmitted === undefined}
				<p class="text-red-500 font-bold">An error has occured. Please try again</p>
			{/if}
		</div>

		<button
			disabled={isLoading}
			class={`${isLoading ? 'opacity-50' : ''} text-white p-4 w-full bg-black md:w-4/6 mx-auto rounded-md`}
			>{isLoading ? 'Submitting...' : 'Submit'}</button
		>
	</form>

	<!-- <iframe title="BTM Holidays" src="https://docs.google.com/forms/d/e/1FAIpQLSejDI7wSdQRhRGjmfBR1TN8vChB1fuw2NckrjneSbjmxdm-xg/viewform?embedded=true" width="640" height="761" frameborder="0" marginheight="0" marginwidth="0">Loading…</iframe> -->
</section>
