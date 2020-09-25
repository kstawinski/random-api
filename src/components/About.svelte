<script>
  // your script goes here
</script>

<section class="about">
  <div class="about__container">
    <h2 class="about__title">How to use me? 🚀</h2>
    <p class="about__content">
      I have two main tasks: <b>generating a random API</b> and
      <b>searching for an API</b> (against given filters).
    </p>

    <p class="about__content">
      If you are looking for inspiration and do not know what your API
      should be, I suggest you click the "Randomize API" button
      several times - you will surely find something interesting.
    </p>
      
    <p class="about__content">
      If you know what you are looking for, just set
      the appropriate filters and click the search button.
    </p>
  </div>
</section>

<style type="text/scss">
.about {
  width: 100%;
  height: 100%;
  display: flex;
  color: #22224E;
  align-items: center;

  &__title {
    font-size: 1.4em;
    margin-bottom: 20px;
    font-weight: 500;
  }
  &__content {
    line-height: 1.5;

    b {
      position: relative;
      display: inline-block;
      font-weight: 500;

      &::before {
        content: '';
        display: block;
        background: red;
        width: 100%;
        height: 7px;
        background: rgba(#E0BE36, 0.6);
        position: absolute;
        bottom: 1px;
        left: 0;
        z-index: -1;
      }
    }
    &:not(:last-child) {
      margin-bottom: 10px;
    }
  }
}
</style>
