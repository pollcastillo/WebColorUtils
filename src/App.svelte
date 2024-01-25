<script>
  import ColorCard from "./components/ColorCard/ColorCard.svelte";

  const Tints = [96, 92, 83, 72, 62, 53, 48, 40, 34, 28, 15];
  const Colors = [
    {
      id: 1,
      ide_name: "red",
      name: "Red",
      hue: 0,
      saturation: 100,
      light: 53,
    },
    {
      id: 2,
      ide_name: "orange",
      name: "Orange",
      hue: 30,
      saturation: 100,
      light: 53,
    },
    {
      id: 3,
      ide_name: "yellow",
      name: "yellow",
      hue: 60,
      saturation: 100,
      light: 53,
    },
    {
      id: 4,
      ide_name: "yellowgreen",
      name: "Yellow Green",
      hue: 90,
      saturation: 100,
      light: 53,
    },
    {
      id: 5,
      ide_name: "green",
      name: "Green",
      hue: 120,
      saturation: 100,
      light: 53,
    },
    {
      id: 6,
      ide_name: "greencyan",
      name: "Green Cyan",
      hue: 150,
      saturation: 100,
      light: 53,
    },
    {
      id: 7,
      ide_name: "cyan",
      name: "cyan",
      hue: 180,
      saturation: 100,
      light: 53,
    },
    {
      id: 8,
      ide_name: "cyanblue",
      name: "Cyan Blue",
      hue: 210,
      saturation: 100,
      light: 53,
    },
    {
      id: 9,
      ide_name: "blue",
      name: "Blue",
      hue: 240,
      saturation: 100,
      light: 53,
    },

    {
      id: 10,
      ide_name: "bluemagenta",
      name: "Blue Magenta",
      hue: 270,
      saturation: 100,
      light: 53,
    },
    {
      id: 11,
      ide_name: "magenta",
      name: "Magenta",
      hue: 300,
      saturation: 100,
      light: 53,
    },
    {
      id: 12,
      ide_name: "magentared",
      name: "Magenta Red",
      hue: 330,
      saturation: 100,
      light: 53,
    },
  ];

  // SELECTED COLOR
  let selectedColor = {
    name: "name",
    hue: 0,
    saturation: 0,
    light: 0,
  };

  function setSelectedColor(data) {
    selectedColor = {
      name: data.name,
      hue: data.hue,
      saturation: data.saturation,
      light: data.light,
    };
  }
  // END SELECTED COLOR

  // Color Card functions
  function showPreview(e) {
    const selectedSwatch = e.detail.element;
    const selectedSwatchData = selectedSwatch.dataset;

    setSelectedColor(selectedSwatchData);
    // toggleSwatchPreviewVisibility();
  }
</script>

<!-- app viewport -->
<div>
  <!-- Toolbar goes here -->

  <div class="flex p-8 flex-wrap gap-8">
    {#each Colors as color}
      <ColorCard on:preview={showPreview} {...color} />
    {/each}
  </div>
</div>
