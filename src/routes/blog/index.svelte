<script context="module">
  export async function preload({ params, query }) {
    const res = await this.fetch(`blog.json`);
    const posts = await res.json();
    return { posts };
  }
</script>

<script>
  import { fadeIn, fadeOut } from "../../animate";
  export let posts;
</script>

<svelte:head>
  <title>Blog</title>
</svelte:head>

<div in:fadeIn out:fadeOut>
  <h1>Recent posts</h1>

  <ul>
    {#each posts as post}
      <li>
        <a rel="prefetch" href="blog/{post.slug}">{post.title} - {post.date}</a>
      </li>
    {/each}
  </ul>
</div>

<style>
  ul {
    margin: 0 0 1em 0;
    line-height: 1.5;
  }
</style>
