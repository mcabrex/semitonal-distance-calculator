<script>
	import NoteInput from './NoteInput.svelte'
	let musicalAlphabet=  ['C','D','E','F','G','A','B']

	let octave1= 0
	let letter1= 'C'
	let alter1= 0
	$: note1 = `${octave1 + letter1 + alter1}`
	$: note1Semitones = semitonalCalculator(octave1,letter1,alter1)

	let octave2= 0
	let letter2= 'C'
	let alter2= 0
	$: note2 = `${octave2 + letter2 + alter2}`
	$: note2Semitones = semitonalCalculator(octave2,letter2,alter2)

	let total
	let inputs = true
	let semitonalCalculator = (octave,letter,alter) => {
		let basicScale = 'C-D-EF-G-A-B';
		let octaveTotal = +octave * 12
		let letterTotal = basicScale.indexOf(letter)
		return (octaveTotal+letterTotal+alter)
	}

	let distanceCalculator = (noteTotal1,noteTotal2) => {
		return Math.abs(noteTotal1-noteTotal2)
	}

	$: total = distanceCalculator(note1Semitones,note2Semitones)
</script>

<div>
	<h1>Semitonal Distance Calculator</h1>
	<p>Plug in note information to find the total number of semitones between two notes</p>
	<p>**Note: the 'Alter' input field is used to describe the chromatic alteration of a note in semitones (e.g., -1 for flat, 1 for sharp)</p>
	<h2>Semitonal Distance = {total}</h2>

	<NoteInput>
		<legend slot="legend">
			Note 1
		</legend>

		<input type=number bind:value={octave1} min=0 name="octave" slot="octave"/>

		<select bind:value={letter1} slot="letter">
			{#each musicalAlphabet as noteLetter}
				<option value={noteLetter}>
					{noteLetter}
				</option>
			{/each}			
		</select>

		<input type=number bind:value={alter1} name="alter" slot="alter"/>
	</NoteInput>

	<NoteInput>
		<legend slot="legend">
			Note 2
		</legend>

		<input type=number bind:value={octave2} min=0 name="octave" slot="octave"/>

		<select bind:value={letter2} slot="letter">
			{#each musicalAlphabet as noteLetter}
				<option value={noteLetter}>
					{noteLetter}
				</option>
			{/each}			
		</select>

		<input type=number bind:value={alter2} name="alter" slot="alter"/>
	</NoteInput>
</div>

<style>
	:global(body){
		background-color: rgb(51, 169, 238);
		text-align: center;
	}
</style>

