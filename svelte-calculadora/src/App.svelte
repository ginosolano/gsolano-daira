<script>
  let inputValue = '';
  let result = '';

  const handleButtonClick = (value) => {
    inputValue += value;
  };

  const handleCalculate = () => {
    try {
      result = eval(inputValue);
    } catch (error) {
      result = 'Error';
    }
  };

  const handleClear = () => {
    inputValue = '';
    result = '';
  };
</script>



<style>

	@import 'tailwindcss/base.css';
    @import 'tailwindcss/components.css';
    @import 'tailwindcss/utilities.css';
	
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #0c0300;
		text-transform: uppercase;
		font-size: 2em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>

<main>
	<h1>Calculadora Basica</h1>

	<div class="max-w-md mx-auto my-8 p-6 bg-gray-200 rounded-lg shadow-md">
		<input
		  class="w-full mb-4 p-2 border rounded"
		  bind:value={inputValue}
		  placeholder="0"
		/>
	  
		<div class="grid grid-cols-4 gap-2">
		  {#each Array.from({ length: 10 }, (_, i) => i) as num}
			<button
			  class="col-span-1 bg-blue-500 text-white p-2 rounded"
			  on:click={() => handleButtonClick(num)}
			>
			  {num}
			</button>
		  {/each}
	  
		  <button
			class="col-span-1 bg-yellow-500 text-white p-2 rounded"
			on:click={() => handleButtonClick('+')}
		  >
			+
		  </button>
	  
		  <button
			class="col-span-1 bg-yellow-500 text-white p-2 rounded"
			on:click={() => handleButtonClick('-')}
		  >
			-
		  </button>
	  
		  <button
			class="col-span-1 bg-yellow-500 text-white p-2 rounded"
			on:click={() => handleButtonClick('*')}
		  >
			*
		  </button>
	  
		  <button
			class="col-span-1 bg-yellow-500 text-white p-2 rounded"
			on:click={() => handleButtonClick('/')}
		  >
			/
		  </button>
	  
		  <button
			class="col-span-2 bg-green-500 text-white p-2 rounded"
			on:click={handleClear}
		  >
			C
		  </button>
	  
		  <button
			class="col-span-2 bg-red-500 text-white p-2 rounded"
			on:click={handleCalculate}
		  >
			=
		  </button>
		</div>
	  
		<div class="mt-4">
		  <p class="font-bold">Resultado: {result}</p>
		</div>
	  </div>
</main>
