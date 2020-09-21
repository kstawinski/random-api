<script>
export let data;
</script>

<article class="card">
  <h2 class="card__title">{data.API}</h2>
  <p class="card__description">{data.Description}</p>

  <div class="card__details">
    <input type="checkbox" checked={ data.HTTPS === true } disabled> HTTPS <br />
    <input type="checkbox" checked={ data.Cors === 'yes' } disabled> Cors <br />
    <div>[ { data.Category } ]</div>
    <a href={data.Link} class="card__link" target="_blank">{data.Link}</a>
  </div>
</article>

<style type="text/scss">
.card {
  padding: 15px;

  &__title {}
  &__description {}
  &__link {}
}
</style>