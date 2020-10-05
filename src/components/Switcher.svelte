<script>
  export let changeHandler;
  export let enabled = true;
</script>

<label class="control__switch">
    <input id="checkbox" type="checkbox" bind:checked={enabled} on:change={changeHandler}/>
    <span class="control__switch__slider"></span>
</label>
