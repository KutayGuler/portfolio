<script lang="ts">
  import { fade } from 'svelte/transition';

  let randomEmojis: Array<string> = [
    'twa-evergreen-tree',
    'twa-alien-monster',
    'twa-man-mage',
    'twa-ghost',
    'twa-pile-of-poo',
    'twa-brain',
    'twa-orangutan',
    'twa-broccoli'
  ];

  function random(min: number, max: number) {
    return Math.random() * (max - min) + min;
  }

  const [min, max_x, max_y, minDeg, maxDeg] = [0, 3000, 1000, -180, 180];

  function transform() {
    let [x, y, deg, s] = [
      random(min, max_x),
      random(min, max_y),
      random(minDeg, maxDeg),
      random(1, 2.5)
    ];

    return `translate(${x}%, ${y}%) rotate(${deg}deg) scale(${s}, ${s})`;
  }

  function interpolate(node: Element) {
    let time = node.init ? random(5, 10) : random(0, 1);
    node.style.transition = `transform ${time}s`;
    node.style.transform = transform();
    time = node.init ? time : 0;
    setTimeout(
      () => {
        node.init = true;
        interpolate(node);
      },
      time * 1000 + 1000
    );
  }
</script>

<div transition:fade class="absolute h-full w-full z-0 top-0 left-0 opacity-50">
  {#each randomEmojis as emoji, i}
    <i use:interpolate={this} class="text-md shape twa {emoji} left-0 top-0" />
  {/each}
</div>

<style>
  .shape {
    position: absolute;
    overflow: visible;
  }
</style>
