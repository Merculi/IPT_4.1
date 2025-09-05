<script setup>

</script>

<template>
  <h1>Newsfeed</h1>

  <div class="box">
    <div class="newsfeed">
      <div class="newsfeed__item">
        <div class="newsfeed__image">
          <img src="https://placecats.com/millie_neo/200/200" alt="">
        </div>
        <div class="newsfeed__text">
          <h2 class="newsfeed__heading">
            Lorem ipsum dolor sit amet, consetetur sadipscing elitr
          </h2>
          <p class="newsfeed__teaser">
            At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet.
          </p>
          <p class="newsfeed__meta">
            2 Minuten Lesezeit
          </p>
        </div>
      </div>

      <div class="newsfeed__item">
        <div class="newsfeed__image">
          <img src="https://placecats.com/neo_banana/200/200" alt="">
        </div>
        <div class="newsfeed__text">
          <h2 class="newsfeed__heading">
            Lorem ipsum dolor sit amet, consetetur sadipscing elitr
          </h2>
          <p class="newsfeed__teaser">
            At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet.
          </p>
          <p class="newsfeed__meta">
            4 Minuten Lesezeit
          </p>
        </div>
      </div>

      <div class="newsfeed__item">
        <div class="newsfeed__image">
          <img src="https://placecats.com/bella/200/200" alt="">
        </div>
        <div class="newsfeed__text">
          <h2 class="newsfeed__heading">
            Lorem ipsum dolor sit amet, consetetur sadipscing elitr
          </h2>
          <p class="newsfeed__teaser">
            At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet.
          </p>
          <p class="newsfeed__meta">
            1 Minute Lesezeit
          </p>
        </div>
      </div>

    </div>
  </div>
</template>

<style>
body {
  background: #0f172a;
  color: #fff;
  margin: 4rem auto;
  max-width: 620px;
  padding: 20px;
}

.box {
  box-shadow: inset 0 1px 0 0 hsla(0,0%,100%,.05);
  background: rgb(30 41 59/1);
  border-radius: 5px;
  overflow: hidden;
}

.newsfeed {
  margin: 0;
  padding: 0;
}

.newsfeed__image img {
  display: block;
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.newsfeed__text {
  padding: 20px;
}

.newsfeed__item {
  display: grid;
  grid-template-columns: 200px auto;
}

.newsfeed__heading {
  font-size: 18px;
  margin: 10px 0;
}

.newsfeed__teaser {
  font-size: 15px;
  line-height: 1.25;
}

.newsfeed__meta {
  font-size: 15px;
  line-height: 1.25;
  color: rgba(255, 255, 255, .6);
}

.newsfeed__item + .newsfeed__item {
  border-top: 1px solid hsla(0,0%,100%,.05);
}
</style>