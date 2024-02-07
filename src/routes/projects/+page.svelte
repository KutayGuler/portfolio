<script lang="ts">
  import { slide } from 'svelte/transition';
  import Background from './Background.svelte';

  const technologies = {
    sveltekit: 'SvelteKit',
    typescript: 'TypeScript',
    tailwind: 'TailwindCSS',
    threlte: 'Threlte',
    daisyui: 'daisyUI',
    supabase: 'Supabase',
    tauri: 'Tauri'
  };

  interface Project {
    name: string;
    description: string;
    stack: Array<
      'typescript' | 'sveltekit' | 'tailwind' | 'daisyui' | 'threlte' | 'supabase' | 'tauri'
    >;
    classes: string;
    emoji: string;
    website?: string;
    github: string;
    reveal: boolean;
    btn_classes: string;
  }

  const projects: Array<Project> = [
    {
      name: 'Roguelighter',
      description: 'Desktop application & game engine designed for roguelike development.',
      classes: 'bg-[#1a141f] text-stone-200',
      stack: ['sveltekit', 'typescript', 'tailwind', 'threlte', 'tauri'],
      emoji: 'twa-man-mage',
      github: 'https://github.com/roguelighterengine/roguelighter',
      reveal: false,
      btn_classes: 'bg-emerald-600 text-stone-200'
    },
    {
      name: 'Emojistan',
      description: 'Web based pseudo game engine where you can make games with emojis.',
      classes: 'bg-white text-stone-900',
      stack: ['sveltekit', 'typescript', 'tailwind', 'daisyui', 'supabase'],
      emoji: 'twa-alien-monster',
      website: 'https://emojistan.app/',
      github: 'https://github.com/KutayGuler/emojistan',
      reveal: false,
      btn_classes: 'bg-purple-800 text-stone-200'
    },
    {
      name: 'Svelte Dialogue Tree',
      description: 'Svelte component library for displaying branching dialogues with type-safety.',
      classes: 'bg-gradient-to-r from-[#1f1b18] to-[#352617]',
      stack: ['sveltekit', 'typescript', 'tailwind'],
      emoji: 'twa-evergreen-tree',
      website: 'https://svelte-dialogue-tree.vercel.app/',
      github: 'https://github.com/KutayGuler/svelte-dialogue-tree',
      reveal: false,
      btn_classes: 'bg-green-700'
    }
  ];

  // TODO: add tech stack
  // TODO: recreate 3D library
</script>

<h1>Projects</h1>
<div class="flex flex-col gap-4 py-4">
  {#each projects as { name, description, stack, classes, emoji, website, github, reveal, btn_classes }}
    <div
      class="relative flex flex-col w-full rounded shadow-sm p-6 {classes} w-full max-w-xl overflow-hidden"
    >
      {#if name == 'Emojistan'}
        <Background></Background>
      {/if}
      <div class="flex flex-row gap-8 z-[1]">
        <div class="flex items-center justify-center">
          <i class="twa {emoji} text-7xl"></i>
        </div>
        <div>
          <h2>{name}</h2>
          <p class="text-xl">{description}</p>
        </div>
      </div>
      <div class="flex flex-row justify-between items-center pt-8 z-[1]">
        <button
          on:click={() => (reveal = !reveal)}
          class="{btn_classes} py-2 px-4 rounded young-serif"
          >{reveal ? 'Hide' : 'Reveal'} stack</button
        >
        <div>
          {#if website}
            <a
              target="_blank"
              rel="noopener noreferrer"
              class="hover:text-emerald-400 font-bold"
              href={website}>Website</a
            >
          {/if}
          <a
            target="_blank"
            rel="noopener noreferrer"
            class="hover:text-emerald-400 font-bold pl-2"
            href={github}>Github</a
          >
        </div>
      </div>
      {#if reveal}
        <div class="flex flex-wrap gap-2 pt-8 z-[1]" transition:slide>
          {#each stack as lib}
            <div
              class="flex flex-row gap-2 items-center bg-gray-600 text-white rounded-full px-6 py-2 text-lg"
            >
              <img class="w-6 h-6 object-contain" src="/{lib}.png" alt={technologies[lib]} />
              {technologies[lib]}
            </div>
          {/each}
        </div>
      {/if}
    </div>
  {/each}
</div>
