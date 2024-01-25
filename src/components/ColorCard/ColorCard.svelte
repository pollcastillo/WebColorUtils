<script>
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();

  export let name = "Color";
  export let hue = 0;
  export let saturation = 100;
  export let light = 100;
  export let id = 0;
  export let ide_name;

  function clickToPreview(e) {
    const element = e.currentTarget;
    dispatch("preview", {
      element,
    });
  }

  /**
   * @param {number} h
   * @param {number} s
   * @param {number} l
   */
  function hslToHex(h, s, l) {
    l /= 100;
    const a = (s * Math.min(l, 1 - l)) / 100;
    const f = (n) => {
      const k = (n + h / 30) % 12;
      const color = l - a * Math.max(Math.min(k - 3, 9 - k, 1), -1);
      return Math.round(255 * color)
        .toString(16)
        .padStart(2, "0"); // convert to Hex and prefix "0" if needed
    };
    return `#${f(0)}${f(8)}${f(4)}`;
  }
</script>

<div
  class="flex flex-col p-1 shadow-sm rounded-2xl border border-gray-300 bg-white w-fit dark:bg-gray-800 dark:border-gray-700"
>
  <!-- HEAD -->
  <div id="{id}{ide_name}">
    <button
      on:click={clickToPreview}
      class="block h-32 w-48 rounded-xl appearance-none"
      style="background-color: hsl({hue} {saturation}% {light}%);"
      data-name={name}
      data-hue={hue}
      data-saturation={saturation}
      data-light={light}
    ></button>
  </div>
  <!-- BODY -->
  <div class="flex items-center justify-between p-1 dark:text-white">
    <p class="text-xs font-bold">{name}</p>
    <p class="text-xs">500</p>
  </div>
  <!-- FOOTER -->
  <div class="text-xs font-bold p-1 text-gray-800 dark:text-gray-300">
    <p>
      Hex: <span class="font-mono font-normal"
        >{hslToHex(hue, saturation, light)}</span
      >
    </p>
    <p>RGB: <span class="font-mono font-normal">255 0 0</span></p>
    <p>
      HSL: <span class="font-mono font-normal"
        >{hue} {saturation}% {light}%</span
      >
    </p>
  </div>
</div>
