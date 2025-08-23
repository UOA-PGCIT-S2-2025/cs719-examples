<!-- This component is a number pad which holds a value. Each time one of the numpad buttons is clicked,
     we essentially "type" the new number to the "right" of the existing number (by multiplying the existing
     value by 10 to "shift" it left).
     
     We can easily bind to the "value" prop to access it outside of this component. -->

<script>
  export let value = 0;

  const NUMS = [1, 2, 3, 4, 5, 6, 7, 8, 9, 0];

  function handleNumberClicked(number) {
    // Update the value by multiplying it by 10 then adding the clicked number.
    value = 10 * value + number;
  }
</script>

<div>
  <!-- Loop through our NUMS array. Display a button for each number. -->
  {#each NUMS as num (num)}
    <button on:click={() => handleNumberClicked(num)}>{num}</button>
  {/each}
</div>

<style>
  div {
    display: grid;
    grid-template-columns: repeat(3, 50px);
    grid-auto-rows: 50px;
    gap: 5px;

    & :last-child {
      grid-column: 2 / 3;
    }
  }
</style>
