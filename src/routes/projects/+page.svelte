<script lang="ts">
  const technologies = {
    sveltekit: 'SvelteKit',
    typescript: 'TypeScript',
    tailwind: 'TailwindCSS',
    threlte: 'Threlte',
    daisyui: 'daisyUI',
    supabase: 'Supabase'
  };

  interface Project {
    name: string;
    description: string;
    stack: Array<'typescript' | 'sveltekit' | 'tailwind' | 'daisyui' | 'threlte' | 'supabase'>;
    classes: string;
    emoji: string;
    website?: string;
    github: string;
  }

  const projects: Array<Project> = [
    {
      name: 'Roguelighter',
      description: 'Desktop application & game engine designed for roguelike development.',
      classes: 'bg-stone-300 text-stone-900',
      stack: ['sveltekit', 'typescript', 'tailwind', 'threlte'],
      emoji: 'twa-man-mage',
      github: 'https://github.com/roguelighterengine/roguelighter'
    },
    {
      name: 'Emojistan',
      description: 'Web based pseudo game engine where you can make games with emojis.',
      classes: 'bg-stone-300 text-stone-900',
      stack: ['sveltekit', 'typescript', 'tailwind', 'daisyui', 'supabase'],
      emoji: 'twa-alien-monster',
      website: 'https://emojistan.app/',
      github: 'https://github.com/KutayGuler/emojistan'
    },
    {
      name: 'Svelte Dialogue Tree',
      description: 'Svelte component library for displaying branching dialogues with type-safety.',
      classes: 'bg-stone-300 text-stone-900',
      stack: ['sveltekit', 'typescript', 'tailwind'],
      emoji: 'twa-evergreen-tree',
      website: 'https://svelte-dialogue-tree.vercel.app/',
      github: 'https://github.com/KutayGuler/svelte-dialogue-tree'
    }
  ];

  // TODO: add tech stack
  // TODO: recreate 3D library
</script>

<h1>Projects</h1>
<div class="flex flex-col gap-4 py-4">
  {#each projects as { name, description, stack, classes, emoji, website, github }}
    <div class="flex flex-col gap-12 w-full rounded shadow-sm p-6 {classes} w-full max-w-xl">
      <div class="flex flex-row gap-4">
        <div class="flex items-start justify-center">
          <i class="twa {emoji} text-7xl"></i>
        </div>
        <div>
          <h3>{name}</h3>
          <p class="text-xl">{description}</p>
        </div>
      </div>
      <div class="flex flex-row justify-between">
        <!-- <div class="flex flex-row gap-2">
            {#each stack as lib}
              <div
                class="flex flex-row gap-2 items-center grayscale hover:grayscale-0 duration-150 ease-out"
              >
                <img class="w-6 h-6 object-contain" src="/{lib}.png" alt={technologies[lib]} />
              </div>
            {/each}
          </div> -->
        <div>
          {#if website}
            <a class="hover:text-sky-400 font-bold" href={website}>Website</a>
          {/if}
          <a class="hover:text-sky-400 font-bold pl-2" href={github}>Github</a>
        </div>
      </div>
    </div>
  {/each}
</div>
