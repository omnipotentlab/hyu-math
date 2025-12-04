<script lang="ts">
	export let title = '제 10장, 벡터 그리고 어쩌구';
	export let subtitle = '그런 내용이 있다.';
	export let proficiencyLevel = 'intermediate';
	export let responseStyle = 'question_guidance';

	let showProficiencyDropdown = false;
	let showResponseStyleDropdown = false;

	const proficiencyLevels = {
		initial: '초급',
		intermediate: '중급',
		advanced: '고급'
	};

	const responseStyles = {
		question_guidance: '질문식 유도',
		problem_bank: '문제 은행',
		detailed_lecture: '자세한 강의'
	};

	const setProficiencyLevel = (level) => {
		proficiencyLevel = level;
		showProficiencyDropdown = false;
	};

	const setResponseStyle = (style) => {
		responseStyle = style;
		showResponseStyleDropdown = false;
	};
</script>

<div
	class="w-full px-4 py-4 border-b border-gray-200 dark:border-gray-700 bg-white dark:bg-gray-900 flex justify-between items-center gap-6"
>
	<!-- Title and Subtitle Section (Left) -->
	<div class="flex flex-col justify-start gap-1">
		<h2 class="text-lg font-semibold text-gray-900 dark:text-white leading-none">{title}</h2>
		<p class="text-xs text-gray-600 dark:text-gray-400 leading-none">{subtitle}</p>
	</div>

	<!-- Buttons Section (Right) -->
	<div class="flex items-center gap-3">
		<!-- Proficiency Level Dropdown -->
		<div class="relative">
			<button
				on:click={() => {
					showProficiencyDropdown = !showProficiencyDropdown;
					showResponseStyleDropdown = false;
				}}
				class="px-3 py-2 text-sm font-medium text-gray-700 dark:text-gray-300 bg-gray-100 dark:bg-gray-800 rounded-md hover:bg-gray-200 dark:hover:bg-gray-700 transition-colors duration-200 flex items-center gap-2 min-w-fit whitespace-nowrap"
			>
				<span>수준</span>
				<span class="font-semibold">{proficiencyLevels[proficiencyLevel]}</span>
				<svg
					class="w-4 h-4 transition-transform duration-200 {showProficiencyDropdown
						? 'rotate-180'
						: ''}"
					fill="none"
					stroke="currentColor"
					viewBox="0 0 24 24"
				>
					<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 14l-7 7m0 0l-7-7m7 7V3" />
				</svg>
			</button>

			{#if showProficiencyDropdown}
				<div
					class="absolute top-full mt-2 left-0 bg-white dark:bg-gray-800 border border-gray-200 dark:border-gray-700 rounded-md shadow-lg z-50 min-w-max"
				>
					{#each Object.entries(proficiencyLevels) as [key, label]}
						<button
							on:click={() => setProficiencyLevel(key)}
							class="w-full px-4 py-2 text-left text-sm text-gray-700 dark:text-gray-300 hover:bg-gray-100 dark:hover:bg-gray-700 transition-colors duration-200 {proficiencyLevel ===
							key
								? 'bg-blue-50 dark:bg-blue-900 text-blue-600 dark:text-blue-400 font-semibold'
								: ''} first:rounded-t-md last:rounded-b-md"
						>
							{label}
						</button>
					{/each}
				</div>
			{/if}
		</div>

		<!-- Response Style Dropdown -->
		<div class="relative">
			<button
				on:click={() => {
					showResponseStyleDropdown = !showResponseStyleDropdown;
					showProficiencyDropdown = false;
				}}
				class="px-3 py-2 text-sm font-medium text-gray-700 dark:text-gray-300 bg-gray-100 dark:bg-gray-800 rounded-md hover:bg-gray-200 dark:hover:bg-gray-700 transition-colors duration-200 flex items-center gap-2 min-w-fit whitespace-nowrap"
			>
				<span>응답 스타일</span>
				<span class="font-semibold">{responseStyles[responseStyle]}</span>
				<svg
					class="w-4 h-4 transition-transform duration-200 {showResponseStyleDropdown
						? 'rotate-180'
						: ''}"
					fill="none"
					stroke="currentColor"
					viewBox="0 0 24 24"
				>
					<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 14l-7 7m0 0l-7-7m7 7V3" />
				</svg>
			</button>

			{#if showResponseStyleDropdown}
				<div
					class="absolute top-full mt-2 right-0 bg-white dark:bg-gray-800 border border-gray-200 dark:border-gray-700 rounded-md shadow-lg z-50 min-w-max"
				>
					{#each Object.entries(responseStyles) as [key, label]}
						<button
							on:click={() => setResponseStyle(key)}
							class="w-full px-4 py-2 text-left text-sm text-gray-700 dark:text-gray-300 hover:bg-gray-100 dark:hover:bg-gray-700 transition-colors duration-200 {responseStyle ===
							key
								? 'bg-blue-50 dark:bg-blue-900 text-blue-600 dark:text-blue-400 font-semibold'
								: ''} first:rounded-t-md last:rounded-b-md"
						>
							{label}
						</button>
					{/each}
				</div>
			{/if}
		</div>
	</div>
</div>

<style>
</style>
