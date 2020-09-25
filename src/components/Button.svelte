<script>
import Loading from 'svelte-material-icons/Loading.svelte';

export let text;
export let loading = false;
export let type = 'primary';

const createClass = (type) => `button__${type}`;
</script>

<button class={'button ' + createClass(type)} on:click>
  {#if loading}
    <div class="button__loading">
      <Loading />
    </div>
  {:else}
    {text}
  {/if}
</button>

<style type="text/scss">
.button {
  font-size: 16px;
  border: 0;
  font-weight: 500;
  padding: 20px 12px;
  box-shadow: 0 0 15px rgba(#000, 0.1);
  cursor: pointer;
  transition: opacity .3s, transform .2s;
  outline: 0;
  width: 100%;

  // &:hover {
  //   opacity: .85;
  // }
  &:active {
    transform: scale(0.95);
  }
  &__primary {
    background: #000000;
    color: #FFFFFF;
  }
  &__secondary {
    background: rgba(#000, 0.2);
    color: rgba(#000, 0.9);
  }
  &__loading {
    animation: spin 0.3s linear infinite;
  }
}

@keyframes spin {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
</style>