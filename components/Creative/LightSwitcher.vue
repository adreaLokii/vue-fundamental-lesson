<template>
  <div>
    <form class="flex items-center">
      <label for="brightness" class="hidden">Brightness</label>
      <input type="range" id="brightness" name="brightness" min="1" max="100" value="100">
    </form>
  </div>
</template>

<script>
export default {
  name: "LightSwitcher",
  mounted () {
      let slider = document.getElementById("brightness");
      slider.addEventListener("input",adjustSlider);
      adjustSlider(slider);
    function adjustSlider(e) {
      let body = document.body,
          switchLightMin = 40,
          switchLightMax = 100,
          tar = e.target || e,
          pct = +tar.value / +tar.max,
          L1 = pct * (switchLightMax - switchLightMin) + switchLightMin,
          L2 = L1 - 10,
          L3 = L1  - 37,
          L = [L1,L2,L3],
          thumbHueMin = 0,
          thumbHueMax = 120,
          thumbHue = pct * (thumbHueMax - thumbHueMin) + thumbHueMin,
          thumbSat = 90.4,
          thumbLight = 44.9,
          thumbHSL = `${thumbHue},${thumbSat}%,${thumbLight}%`;

      // update the slider shade
      L.forEach((light,i) => {
        if (light < 0)
          light = 0;
        if (light < 25) {
          body.style.color = '#ccc'
        } else {
          body.style.color = 'inherit'
        }

        console.log(light, 'light!!!')
        body.style.setProperty(`--l${i + 1}`,`hsl(228,9.8%,${light}%)`);
      });
      // update the thumb icon hue
      body.style.setProperty(`--p`,`hsl(${thumbHSL})`);
      body.style.setProperty(`--pT`,`hsla(${thumbHSL},0)`);
    }
  }
}
</script>

<style lang="sass">
@mixin thumb()
  $bg1: linear-gradient(var(--p),var(--p)) 70% 50% / 20% 5% no-repeat
  $bg2: linear-gradient(var(--l2),var(--l2)) 70% 50% / 20% 15% no-repeat
  $bg3: radial-gradient(100% 100% at 50% 50%,var(--pT) 14%,var(--p) 15% 19%,var(--pT) 20%)
  border: 0
  background: $bg1, $bg2, $bg3, var(--l2)
  border-radius: 50%
  box-shadow: -0.25em 0 0.5em var(--l3), 0.25em 0 0.5em var(--l1)
  width: 1.5em
  height: 1.5em
  -webkit-appearance: none
  -moz-appearance: none
  appearance: none

// normal styles
body
  --l1: hsl(228,9.8%,100%)
  --l2: hsl(228,9.8%,90%)
  --l3: hsl(228,9.8%,63%)
  --p: hsl(120,90.4%,44.9%)
  --pT: hsla(120,90.4%,44.9%,0)
  background-color: var(--l2)
form, input[type=range]
  margin: auto
form
  height: 6em
input[type=range], label
  -webkit-tap-highlight-color: transparent
input[type=range]
  background-color: transparent
  border-radius: 0.75em
  box-shadow: -0.1em -0.1em 0.1em var(--l3) inset, 0.1em 0.1em 0.1em var(--l1) inset
  cursor: pointer
  transform: rotate(-90deg)
  height: 1.5em
  width: 6em
  -webkit-appearance: none
  -moz-appearance: none
  appearance: none
  &:focus
    outline: transparent
  &::-webkit-slider-thumb
    @include thumb()
  &::-moz-range-thumb
    @include thumb()
  &::-moz-focus-outer
    border: 0
</style>