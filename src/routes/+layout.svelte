<script>
  import '../app.css';
  import '../twemoji.css';
</script>

<main class="text-zinc-200 flex items-start justify-center py-8 h-full">
  <div class="max-w-4xl px-8">
    <nav class="flex flex-row gap-4 items-center justify-center young-serif text-2xl pb-16">
      <a class="hover:text-emerald-400" href="/">Home</a>
      <a class="hover:text-purple-400" href="/projects">Projects</a>
      <a class="hover:text-amber-400" href="/blog">Blog</a>
    </nav>
    <slot />
  </div>
</main>
