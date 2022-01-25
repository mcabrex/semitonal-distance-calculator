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

	let semitonalCalculator = (octave,letter,alter) => {
		let baseScale = 'C-D-EF-G-A-B';
        //used to determine a value for the letter
		//in calculating semitonal distance it is important that the baseScale used for each note is the same

		let octaveTotal = octave * 12
        //12 semitones in an octave

		let letterTotal = baseScale.indexOf(letter)
        //letter value in semitones
        
        let semitonalTotal = octaveTotal+letterTotal+alter
		return semitonalTotal
	}

	let distanceCalculator = (noteTotal1,noteTotal2) => {
		return Math.abs(noteTotal1-noteTotal2)
	}

	$: total = distanceCalculator(note1Semitones,note2Semitones)
</script>

<h1>Semitonal Distance Calculator</h1>
<p>Plug in note information to find the total number of semitones between two notes</p>
<p>**Note: the 'Alter' input field is used to describe the chromatic alteration of a note in semitones (e.g., -1 for flat, 1 for sharp)</p>
<h2 class="semitonal-total">Semitonal Distance = {total}</h2>

<div class="note-inputs">
	<NoteInput>
		<legend slot="legend" class="input-legend">
			Note 1
		</legend>

		<input type=number bind:value={octave1} min=0 name="octave" slot="octave" class="input-field"/>
	
		<select bind:value={letter1} slot="letter" class="input-field">
			{#each musicalAlphabet as noteLetter}
				<option value={noteLetter}>
					{noteLetter}
				</option>
			{/each}			
		</select>
	
		<input type=number bind:value={alter1} name="alter" slot="alter" class="input-field"/>
	</NoteInput>
	
	<NoteInput>
		<legend slot="legend" class="input-legend">
			Note 1
		</legend>
	
		<input type=number bind:value={octave2} min=0 name="octave" slot="octave" class="input-field"/>
	
		<select bind:value={letter2} slot="letter" class="input-field">
			{#each musicalAlphabet as noteLetter}
				<option value={noteLetter}>
					{noteLetter}
				</option>
			{/each}			
		</select>
	
		<input type=number bind:value={alter2} name="alter" slot="alter" class="input-field"/>
	</NoteInput>
</div>

<style>
	:global(body){
		text-align: center;
	}
	.semitonal-total {
		color: rgb(209, 14, 14);
	}
	.note-inputs {
		display: flex;
		justify-content: center;
		flex-wrap: wrap;
	}
	.input-field {
		margin: 0.5em 0;
		border-radius: 2em;
		text-align: center;
		border-color: black;
	}
	.input-legend {
		text-align: center;
		font-weight: bold;
		font-size: 1.5em;
		font-family: Arial;
	}
</style>