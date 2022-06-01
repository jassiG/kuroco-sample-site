<template>
  <main style="background-color:rgb(252,252,252)">
    <header class="hero" :style="{backgroundImage: `url(${response.details.ext_1.url})`}">
      <div class="hero__text">
        <h1>{{ response.details.ext_2 }}</h1>
        <p>{{ response.details.ext_3 }}</p>
      </div>
    </header>

    <section >
        <h2>WORKS</h2>
        <ul>
            <li v-for="n in response.details.ext_4" :key="n.slag" class="works__item">
                <img :src="n.ext_4.url" />
                <div class="works__item__text">
                    <h3>{{ n.ext_5 }}</h3>
                    <p>{{ n.ext_6 }}</p>
                </div>
            </li>
        </ul>
    </section>

    <section class="about">
        <h2>ABOUT</h2>
        <p v-html="response.details.ext_7"></p>
    </section>
  </main>
</template>

<style>
body { 
    margin: 0;
    font-size: 1em;
    line-height: 1.5;
}
ul { 
  margin: 0;
  padding: 0;
  list-style: none;
}
img { max-width: 100%; }
section {
  max-width: 1200px;
  margin: 2em auto;
  padding: 0 20px;
}
h1 {
  margin: .5em 0;
  font-size: 1.8em;
}
h2 {
  margin: 1em auto;
  font-size: 1.5em;
  text-align: center;
}
h3 {
  margin: 1em auto;
  font-size: 1.2em;
}
p {
  margin: 1em 0;
  font-size: .75em;
}
.hero {
  position: relative;
  width: 100%;
  height: 300px;
  background-position: center center;
  background-size: cover;
  /* darken the image */
  background-color: rgba(0, 0, 0, 0.8);
  color: rgb(250, 250, 250);
  text-shadow: 1px 1px 1px rgba(0, 0, 0, 0.5);
}
.hero__text {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100%;
  padding: 0 20px;
}
.works__item{
  padding: 1em;
  /* card */
  background-color: rgb(254, 254, 254);
  box-shadow: 0px 0px 5px rgba(50, 50, 50, 0.1);
  border-radius: 5px;
  /* hover */
  transition: all 0.2s ease-in-out;
}
.works__item:hover {
    box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.2);
  }
.works__item:not(:first-child) {
    margin-top: 2em;
}
@media screen and (max-width: 767px) {
  .hero::before {
      width: 100%;
      height: 300px;
      position: absolute;
      top: 0;
      left: 0;
      background-color: rgba(0,0,0,.5);
      z-index: 1;
      content: "";
  }
  .hero__text { 
      position: absolute;
      top: 0;
      left: 0;
      color: #fff;
      z-index: 10;
  }
}
@media screen and (min-width: 768px) {
  body {
      font-size: 2em;
  }
  .hero {
    height: 600px;
  }
  .hero__text {
      width: 1200px;
      align-items: flex-end;
      margin: auto;
  }
  .hero__text p { width: 600px; }
  .works__item {
      display: flex;
  }
  .works__item img {
      width: 400px;
      margin-right: 2em;
  }
  .about { text-align: center; }
}
</style>

<script>
export default {
  async asyncData({ $axios, app }) {
    try {
      const response = await $axios.$get(
        process.env.BASE_URL + '/rcms-api/3/service/3'
        )
        // console.log(response)
        return { response }
        } catch (e) {
          console.log(e.message)
          }
  },
}
</script>