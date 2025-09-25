<script module>
  // props
  export let name;
  export let email;
</script>

<style>
  .card {
    background: #f9f9f9;
    border-radius: 8px;
    padding: 1rem;
    margin-bottom: .5rem;
    box-shadow: 0 1px 3px rgba(0,0,0,.1);
  }
  .name {
    font-weight: bold;
  }
  .email {
    font-size: .85rem;
    color: #555;
  }
</style>

<div class="card">
  <div class="name">{name}</div>
  <div class="email">{email}</div>
</div>
