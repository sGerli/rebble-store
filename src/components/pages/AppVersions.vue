<template>
    <main class="text-center">
      <div class="card subsection text-left p-3 app-details" v-for="(changelog, index) in app.changelog" v-bind:key="index">
        <h2>Version {{ changelog.version }}</h2> <h3 class="float-right">{{ changelog.published_date | formatDate }}</h3><hr>
        <pre class="description">{{ changelog.release_notes }}</pre>
        </div>
    </main>
</template>

<script>
import AppTitleBar from './widgets/AppTitleBar'

export default {
  name: 'app-version',
  components: {
    AppTitleBar
  },
  props: {
    app: {}
  },
  data: function () {
    return {
      versions: {
        'versions': []
      }
    }
  },
  beforeMount: function () {
    if (this.app.title !== undefined) {
      this.setTitle(`${this.app.title} Versions`)
    }
  },
  watch: {
    'app' (to, from) {
      this.setTitle(`${this.app.title} Versions`)
    }
  }
}
</script>

<style lang="scss" scoped>
// App details container (below screenshots)
.app-details {
    &:last-of-type {
        margin-bottom: 0;
    }
}
</style>
