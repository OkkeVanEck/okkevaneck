<template>
  <PageSectionWrapper :id="aboutData.id" :title="aboutData.title" :subtitle="aboutData.subtitle">
    <div class="row">
      <!-- Image -->
      <div class="col col-12 col-md-6 text-center">
        <img :src="aboutData.content.image" alt="logo" class="img img-fluid">
      </div>

      <!-- Texts -->
      <div class="col col-12 col-md-6">
        <template v-for="paragraph in aboutData.content.paragraphs">
          <p v-html="paragraph"></p>
        </template>

        <!-- Social Icons with Links -->
        <div style="justify-content: center; display: flex">
          <template v-for="item in socialData.links.items">
            <a class="btn btn-social mx-2" :href="item.href" :aria-label="item.icon">
              <i :class="item.icon"></i>
            </a>
          </template>
        </div>
      </div>
    </div>
  </PageSectionWrapper>
</template>

<script setup>
import agencyData from '../data/agency.json'
import PageSectionWrapper from "../components/PageSectionWrapper.vue"
const aboutData = agencyData.about
const socialData = agencyData.social
</script>

<style scoped lang="scss">
  @import "../scss/_theming.scss";

  .img {
    border: 3px solid #000000;
    max-height: 160px;
  }

  .col {
    padding-left: 1rem;
    padding-right: 1rem;
    padding-bottom: 1rem;

    p {
      text-align: justify;
    }
  }

  .btn-social {
    color: $dark-faded;
    border-color: $dark-faded;
    border-radius: 100%;
    border-width: 2px;
    font-size: 1.3rem;

    &:hover {
      background-color: white;
      color: $primary;
      border-color: $primary;
    }
  }

  @include media-breakpoint-up(md) {
    .img {
      max-height: 300px;
    }
  }

  @include media-breakpoint-up(lg) {
    .img {
      max-height: 300px;
    }

    .col {
      padding-left: 2rem;
      padding-right: 2rem;
    }
  }
</style>
