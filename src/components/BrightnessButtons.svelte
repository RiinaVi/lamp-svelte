<script>
  export let decreaseHandler;
  export let increaseHandler;
</script>

<div class="control__brightness">
    <button id="decreaseButton" on:click={decreaseHandler}>-</button>
    <button id="increaseButton" on:click={increaseHandler}>+</button>
</div>
