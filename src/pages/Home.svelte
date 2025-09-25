<script>
  import { onMount } from 'svelte';
  import UserCard from '../components/UserCard.svelte';

  let users = [];
  let loading = true;
  let name = 'Ronald';

  const handleChangeName = () => {
    name = name === 'Ronald' ? 'Gustavo' : 'Ronald';
  };

  onMount(async () => {
    const res = await fetch('https://jsonplaceholder.typicode.com/users');
    users = await res.json();
    loading = false;
  });
</script>

<main>
  <header>
    <h1>👥 Daftar Users</h1>
    <p class="subtitle">Menampilkan data dari JSONPlaceholder API</p>
  </header>

  <section class="profile">
    <p class="name">Nama Aktif: <strong>{name}</strong></p>
    <button class="btn primary" on:click={handleChangeName}>Ganti Nama</button>
    <a class="link" href="#/about">➡️ Ke Halaman About</a>
  </section>

  <section class="users">
    {#if loading}
      <p class="loading">⏳ Sedang memuat data...</p>
    {:else}
      {#each users as user}
        <UserCard name={user.name} email={user.email} />
      {/each}
    {/if}
  </section>
</main>

<style>
  main {
    max-width: 800px;
    margin: 2rem auto;
    font-family: 'Inter', sans-serif;
    padding: 1rem;
    color: #2c3e50;
  }

  header {
    text-align: center;
    margin-bottom: 2rem;
  }

  h1 {
    font-size: 2rem;
    margin-bottom: 0.25rem;
  }

  .subtitle {
    color: #7f8c8d;
    font-size: 0.9rem;
  }

  .profile {
    background: #f8f9fa;
    padding: 1rem 1.5rem;
    border-radius: 12px;
    box-shadow: 0 2px 6px rgba(0,0,0,0.05);
    margin-bottom: 2rem;
    text-align: center;
  }

  .name {
    font-size: 1rem;
    margin-bottom: 1rem;
  }

  .btn {
    padding: 0.6rem 1.2rem;
    border: none;
    border-radius: 8px;
    font-size: 0.95rem;
    cursor: pointer;
    transition: all 0.2s ease;
    margin-right: 0.5rem;
  }

  .btn.primary {
    background: #3498db;
    color: white;
  }

  .btn.primary:hover {
    background: #2980b9;
  }

  .link {
    display: inline-block;
    margin-top: 1rem;
    color: #3498db;
    text-decoration: none;
    font-size: 0.95rem;
    font-weight: 500;
  }

  .link:hover {
    text-decoration: underline;
  }

  .users {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
    gap: 1rem;
  }

  .loading {
    text-align: center;
    font-style: italic;
    color: #7f8c8d;
  }
</style>
