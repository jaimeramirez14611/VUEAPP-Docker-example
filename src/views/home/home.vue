<!-- **************************************** --->
<!-- *********** Example ************** --->
<!-- **************************************** --->
<template>
	<section>
		<div v-if="items.length">
			<h3 class="mt-10 text-xl text-blue-700 font-bold">
				Listado de empleados( desde Coldbox API )
			</h3>
			<ul
				role="list"
				class="divide-y divide-gray-200 lg:w-6/12 w-full mx-auto mt-10 bg-gray-50 rounded-md"
			>
				<li
					v-for="empleado in items"
					:key="empleado.email"
				>
					<a
						href="#"
						class="block hover:bg-gray-50"
					>
						<div class="flex items-center px-4 py-4 sm:px-6">
							<div class="min-w-0 flex-1 flex items-center">
								<div class="flex-shrink-0">
									<img
										class="h-12 w-12 rounded-full"
										src="https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80"
										alt=""
									>
								</div>
								<div class="min-w-0 flex-1 px-4 md:grid md:grid-cols-2 md:gap-4">
									<div>
										<p class="text-sm font-medium text-indigo-600 truncate text-left"> {{ empleado.first_name }}  {{ empleado.last_name }} </p>
										<p class="mt-2 flex items-center text-sm text-gray-500">
											<!-- Heroicon name: solid/mail -->
											<svg
												class="flex-shrink-0 mr-1.5 h-5 w-5 text-gray-400"
												xmlns="http://www.w3.org/2000/svg"
												viewBox="0 0 20 20"
												fill="currentColor"
												aria-hidden="true"
											>
												<path d="M2.003 5.884L10 9.882l7.997-3.998A2 2 0 0016 4H4a2 2 0 00-1.997 1.884z" />
												<path d="M18 8.118l-8 4-8-4V14a2 2 0 002 2h12a2 2 0 002-2V8.118z" />
											</svg>
											<span class="truncate">{{ empleado.email }}</span>
										</p>
									</div>
									<div class="hidden md:block">
										<div>
											<p class="text-sm text-gray-900 text-left">
												Applied on
												<time datetime="2020-01-07">January 7, 2020</time>
											</p>
											<p class="mt-2 flex items-center text-sm text-gray-500">
												<!-- Heroicon name: solid/check-circle -->
												<svg
													class="flex-shrink-0 mr-1.5 h-5 w-5 text-green-400"
													xmlns="http://www.w3.org/2000/svg"
													viewBox="0 0 20 20"
													fill="currentColor"
													aria-hidden="true"
												>
													<path
														fill-rule="evenodd"
														d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z"
														clip-rule="evenodd"
													/>
												</svg>
												Completed phone screening
											</p>
										</div>
									</div>
								</div>
							</div>
						</div>
					</a>
				</li>
			</ul>
		</div>
	</section>
</template>

<script>
export default {
	name : "Home",
	data(){
		return { items: [] };
	},
	async created() {
		await fetch( "http://127.0.0.1:8081",
			{ "method": "GET" }
		)
			.then( response => response.json() )
			.then( ( response ) => {
				this.items = response.data;
				console.log( this.items );
			} );
	}
};

</script>
