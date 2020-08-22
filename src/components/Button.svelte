<script>
export let text;
</script>

<button class="button" on:click>
{text}
</button>

<style type="text/scss">
.button {
  font-size: 16px;
  background: #000000;
  border: 0;
  color: #FFFFFF;
  font-weight: 500;
  padding: 15px 20px;
  box-shadow: 0 0 15px rgba(#000, 0.1);
  cursor: pointer;
  transition: opacity .3s, transform .2s;
  outline: 0;

  &:hover {
    opacity: .85;
  }
  &:active {
    transform: scale(0.95);
  }
}
</style>