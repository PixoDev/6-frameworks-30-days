<script lang="ts">
  import type { ListItemModel } from "./types";

  export let listItem: ListItemModel;
  export let onDeleteItem: (index: number) => void;
  const deleteItem = () => {
    onDeleteItem(listItem.index);
  };
</script>

<style>
  .list-item-card {
    width: 400px;
    background: #ccc;
    padding: 0.75rem 0.5rem;
    border-radius: 2px;
    margin-bottom: 10px;
    display: inline-flex;
    justify-content: space-between;
    align-items: center;
  }
  h3 {
    color: white;
    margin: 0;
  }

  button {
    margin: 0;
  }
</style>

<div class="list-item-card">
  <h3>{listItem.title}</h3>
  <button on:click={deleteItem}>Delete</button>
</div>
