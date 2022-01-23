<script>
</script>

<fieldset class="note-input">
   <legend>
      <slot name="legend"></slot>
   </legend> 

   <label for="octave">
      Octave
      <slot name="octave"></slot>
   </label>

   <label for="letter">
      Letter
      <slot name="letter"></slot>
   </label>

   <label for="alter">
      Alter
      <slot name="alter"></slot>
   </label>
</fieldset>

<style>
   fieldset {
		width: fit-content;
		background-color: white;
		padding: 1em;
		margin: auto;
	}
   .note-input {
      margin: 0.5em;
   }
</style>