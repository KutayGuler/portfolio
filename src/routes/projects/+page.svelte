<script lang="ts">
  const technologies = {
    typescript: ['TypeScript', 'logo']
  };

  interface Project {
    name: string;
    description: string;
    stack: Array<
      'typescript' | 'sveltekit' | 'tailwind' | 'daisyui' | 'skeletonui' | 'threlte' | 'supabase'
    >;
    classes: string;
  }

  const projects: Array<Project> = [
    {
      name: 'Svelte Dialogue Tree',
      description: 'A component library for displaying branching dialogues with type-safety.',
      classes: 'bg-stone-300 text-[#26211d] shadow-stone-100'
    }
  ];
  // roguelighter
  // emojistan
  // svelte-dialogue-tree
</script>

<h1>Projects</h1>
<div class="flex flex-col gap-4 py-4">
  {#each projects as { name, description, stack, classes }}
    <div class="flex flex-row w-full h-32 rounded shadow-sm p-4 {classes}">
      <div class="w-1/2">
        <h3>{name}</h3>
        <p>{description}</p>
      </div>
      <div class="w-1/2">Stack</div>
    </div>
  {/each}
</div>
