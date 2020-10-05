<script lang="ts">
  import Lamp from "./components/Lamp.svelte";
  import BrightnessButtons from "./components/BrightnessButtons.svelte";
  import RedButton from "./components/RedButton.svelte";
  import Switcher from "./components/Switcher.svelte";

  const COLORS = [
    'linear-gradient(white, rgba(255, 255, 255, 0))',
    'linear-gradient(yellow, rgba(255, 255, 0, 0))',
    'none'
  ];

  const BRIGHTNESS_STATES = {
    MIN_BRIGHTNESS: 0.2,
    MAX_BRIGHTNESS: 1,
    STEP: 0.1,
    INITIAL_BRIGHTNESS: 0.3,
    NO: 0,
  }
  const MODES = {
    WHITE: 0,
    YELLOW: 1,
    NO: 2,
  }
  let brightness = BRIGHTNESS_STATES.INITIAL_BRIGHTNESS;
  let mode = MODES.WHITE;
  let lightColor = COLORS[mode];
  let enabled = true;

  const changeHandler = () => {
    enabled = !enabled;
    mode = enabled ? MODES.WHITE : MODES.NO;
    brightness = enabled ? BRIGHTNESS_STATES.INITIAL_BRIGHTNESS : BRIGHTNESS_STATES.NO;
    lightColor = enabled ? COLORS[0] : COLORS[2]
  }

  const toggleModeHandler = () => {
    mode = mode < 2 ? mode + 1 : MODES.WHITE;
    lightColor = COLORS[mode]
  }

  const decreaseHandler = () => {
    brightness = Math.max(BRIGHTNESS_STATES.MIN_BRIGHTNESS,
        Number((brightness - BRIGHTNESS_STATES.STEP).toFixed(1)));
  }

  const increaseHandler = () => {
    brightness = Math.min(BRIGHTNESS_STATES.MAX_BRIGHTNESS,
        Number((brightness + BRIGHTNESS_STATES.STEP).toFixed(1)));
  }

</script>

<div class="container">
    <Lamp {brightness} {lightColor}/>
    <div class="control">
        <BrightnessButtons {increaseHandler} {decreaseHandler}/>
        <RedButton {toggleModeHandler}/>
        <Switcher {changeHandler} {enabled}/>
    </div>
</div>

