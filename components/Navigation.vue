<template>
  <nav class="navbar is-white">
    <div class="container">
      <div class="navbar-brand">
        <nuxt-link :to="{ name: 'index' }"
                   class="navbar-item">
              e-Commerce
        </nuxt-link>
        <div class="navbar-burger burger" data-target="nav">
          <span></span>
          <span></span>
          <span></span>
        </div>
      </div>
      <div class="navbar-menu">
        <template v-for="category in categories">
          <template v-if="category.children.length">
            <div :key="category.slug"
                 class="navbar-item has-dropdown is-hoverable">
              <nuxt-link :to="{ name: 'categories-slug', params: { slug: category.slug} }"
                         class="navbar-link">
                {{ category.name }}
              </nuxt-link>
              <div class="navbar-dropdown is-boxed">
                <nuxt-link :to="{ name: 'categories-slug', params: { slug: child.slug} }"
                           class="navbar-item"
                           v-for="child in category.children"
                           :key="child.slug">
                  {{ child.name }}
                </nuxt-link>
              </div>
            </div>
          </template>
          <template v-else>
            <nuxt-link :key="category.slug"
                       :to="{ name: 'categories-slug', params: { slug: category.slug} }"
                       class="navbar-item">
              {{ category.name }}
            </nuxt-link>
          </template>
        </template>
      </div>
      <div id="nav" class="navbar-menu">
        <div class="navbar-end">
          <a href="" class="navbar-item">
            Sign In
          </a>
        </div>
      </div>
    </div>
  </nav>
</template>
<script>
import { mapState } from "vuex";
export default {
  computed: mapState(["categories"])
};
</script>
