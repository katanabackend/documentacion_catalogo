<template>
  <Layout>
    <h1>
      {{ $page.doc.title }}
    </h1>
     <div class="markdown" v-html="$page.doc.content" />
     <nav>
        <!-- To use other icons here, you need to import them in the Shortcut component -->
        <a href="/mision" text="Misión" icon="target-icon" />
        <a href="/panorama-mexico" text="Panorama de Seguridad México" icon="alert-triangle-icon" />
        <a href="/catalogo-katana" text="Catálogo" icon="shield-icon" />
        <a href="/contacto" text="Contacto" icon="message-square-icon" />
      </nav>
  </Layout>
</template>

<page-query>
query Doc ($path: String!) {
  doc: doc (path: $path) {
    title
    path
    date (format: "D. MMMM YYYY")
    timeToRead
    content
  }
}
</page-query>

<script>
export default {
  metaInfo() {
    return {
      title: this.$page.doc.title,
      meta: [
        { key: 'description', name: 'description', content: this.$page.doc.description }
      ]
    }
  }
}

</script>
<script>
import Shortcut from '~/components/Shortcut.vue'

export default {
  components: {
    Shortcut
  },
  data() {
    return {
      description: 'EQUIPOS DE PROTECCIÓN BLINDADA'
    }
  },
  metaInfo() {
    return {
      title: this.description,
      meta: [
        { key: 'description', name: 'description', content: 'EQUIPOS DE PROTECCION BLINDADA MEXICO' }
      ]
    }
  }
}
</script>


<style lang="scss" scoped>
/deep/ > p {
  opacity: .8;
}

/deep/ > h2 {
  padding-top: 100px;
  margin-top: -80px;

  @include respond-above(md) {
    font-size: 2rem;
  }
}

/deep/ > p > img {
    width: 100%;
  max-width: 512px;
  height: auto;
  }

.markdown {
  padding-bottom: 10vh;
}

</style>
