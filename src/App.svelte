<script>
  import gsap from "gsap";
import data from "./data.json";

  gsap.from(".post", { y: 200 })

  // Variables
  let author = '';
  let post = '';
  let title = '';

  let posts = data.data;

  $: id = posts.length + 1
  $: newPost = {
    id : id,
    author: author, 
    body: post,
    title: title
  }

  let modal = false;

  function addPost() {
    posts = [...posts, newPost];
    modal = false;
    console.log(posts)

    document.querySelector("form").reset()
  }
</script>

<main
  class="min-h-screen w-full bg-slate-700 text-white flex flex-col-reverse py-[5rem] items-center justify-center"
>
  {#if modal === true}
  <div class="p-4 absolute top-[50%] left-[50%] translate-x-[-50%] translate-y-[-50%] sm:right-[1rem] sm:top-[1rem] sm:translate-x-0 sm:translate-y-0 w-full max-w-xs z-30 bg-slate-200 rounded-md shadow border-2 text-slate-800">
    <h1 class="px-7">Add Post</h1>
    <form on:submit|preventDefault="{addPost}" class="form-control py-4 space-y-2">
      <div>
        <label for="author" class="label">
          <span class="label-text">Author</span>
        </label>
        <input
          id="author"
          type="text"
          bind:value="{author}"
          placeholder="username"
          class="input input-bordered w-full max-w-xs"
          required
        />
      </div>
      <div>
        <label for="title" class="label">
          <span class="label-text">Post Title</span>
        </label>
        <input
          id="title"
          type="text"
          bind:value="{title}"
          placeholder="title"
          class="input input-bordered w-full max-w-xs"
          required
        />
      </div>
      <div>
        <label for="post_body" class="label">
          <span class="label-text">Body</span>
        </label>
        <textarea
          id="post_body"
          type="text"
          bind:value="{post}"
          placeholder="Body"
          class="textarea h-24 textarea-bordered w-full max-w-xs"
          required
        />
      </div>
      <button class="btn btn-primary" type="submit">Add Post</button>
    </form>
  </div>
  {/if}

  <button on:click="{() => {modal = !modal}}" class="btn btn-primary z-40">Add Post</button>

  <div
    class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 w-full max-w-[750px] mx-auto gap-3 p-4"
  >
    <h1>Posts</h1>
    {#each posts.reverse() as post}
      <div
        class="card post bordered p-4 pb-0 bg-slate-800 transition border-slate-600 border-4 rounded-md  hover:shadow-lg cursor-pointer shadow-slate-900"
      >
        <h2 class="tracking-wider">{post.title}</h2>
        <p>{post.body}</p>
        <div class="w-full flex items-center justify-between py-4">
          <span class="badge badge-success py-3 ">By: {post.author}</span>
        </div>
      </div>
    {/each}
  </div>
</main>

<style>
</style>
