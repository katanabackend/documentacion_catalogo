<template>
  <Layout :sidebar="false">
    <div class="content">
      <h1>{{ $static.metadata.siteName }} | {{ this.description }}</h1>
      <nav>
        <!-- To use other icons here, you need to import them in the Shortcut component -->
        <Shortcut link="/mision" text="Misión" icon="target-icon" />
        <Shortcut link="/panorama-mexico" text="Panorama de Seguridad México" icon="alert-triangle-icon" />
        <Shortcut link="/catalogo-katana" text="Catálogo" icon="shield-icon" />
        <Shortcut link="/contacto" text="Contacto" icon="message-square-icon" />
      </nav>
      
    </div>
  </Layout>
</template>

<static-query>
query {
  metadata {
    siteName
  }
}
</static-query>

<script>
import Shortcut from '~/components/Shortcut.vue'

export default {
  components: {
    Shortcut
  },
  data() {
    return {
      description: 'EQUIPOS DE PROTECCION BLINDADA '
    }
  },
  metaInfo() {
    return {
      title: this.description,
      meta: [
        { key: 'description', name: 'description', content: 'KATANA' }
      ]
    }
  }
}
</script>

<style lang="scss" scoped>
.content {
  display: flex;
  flex-direction: column;
}

h1 {
  text-align: center;
  max-width: 400px;
  margin: 1.5em auto 1.5em;

  @include respond-above(md) {
    max-width: 800px;
  }
}

h2 {
  font-size: 1.4rem;
  margin: 0;
}

nav {
  display: flex;
  justify-content: space-between;
  flex-direction: column;

  @include respond-above(sm) {
    flex-direction: row;
  }
}

.git {
  margin: 3em 0 0;
  align-self: center;

  @include respond-above(md) {
    margin: 5em 0 0;
  }
}
</style>
