<script>
  export let brightness;
  export let lightColor;
</script>

<div class="lamp">
    <div class="lamp__bulb"></div>
    <div class="lamp__stem"></div>
    <div class="lamp__basis"></div>
    <div class="lamp__light" style={`opacity: ${brightness}; background-image: ${lightColor};`}></div>
</div>
