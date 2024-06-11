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
		action=""
		class="w-10/12 mx-auto shadow-2xl rounded-lg p-10 md:py-20 bg-white my-10 md:my-32 grid gap-8 border border-[#E07514]"
	>
		<div class="grid gap-7 md:w-4/6 mx-auto">
			<label for="name" class="flex flex-col gap-2">
				<span class="font-bold md:text-xl"> Your Name </span>
				<div class="flex justify-between gap-3 md:gap-8">
					<input
						type="text"
						placeholder="First name"
						class="w-full p-3 rounded shadow-inner bg-gray-50 border border-[#e0771463]"
					/>
					<input
						type="text"
						placeholder="Last name"
						class="w-full p-3 rounded shadow-inner bg-gray-50 border border-[#e0771463]"
					/>
				</div>
			</label>

			<label for="email" class="flex flex-col gap-2">
				<span class="font-bold md:text-xl"> Email Address </span>
				<input
					type="email"
					name="email"
					id="email"
					placeholder="Eg. example@email.com"
					class="w-full p-3 rounded shadow-inner bg-gray-50 border border-[#e0771463]"
				/>
			</label>

			<label for="email" class="flex flex-col gap-2">
				<span class="font-bold md:text-xl"> Phone Number </span>
				<input
					type="tel"
					name="email"
					id="email"
					placeholder="+234"
					class="w-full p-3 rounded shadow-inner bg-gray-50 border border-[#e0771463]"
				/>
			</label>
		</div>

		<button class="text-white p-4 w-full bg-black md:w-4/6 mx-auto rounded-md">Submit</button>
	</form>
</section>
