<script>
export let data;
</script>

<article class="card">
  <h2 class="card__title">{data.API}</h2>
  <p class="card__description">{data.Description}</p>

  <div class="card__details">
    <input type="checkbox" checked={ data.HTTPS === true } disabled> HTTPS <br />
    <input type="checkbox" checked={ data.Cors === 'yes' } disabled> Cors <br />
    <div>Category: { data.Category }</div>
    <a href={data.Link} class="card__link" target="_blank">{data.Link}</a>
  </div>
</article>

<style type="text/scss">
.card {
  padding: 25px;

  &__title {
    font-size: 18px;
    font-weight: 500;
  }
  &__description {
    margin: 5px 0 15px 0;
    color: #3a3a3a;
  }
  &__link {}
}
</style>