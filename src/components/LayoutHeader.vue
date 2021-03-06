<template>
  <div class="pt-2 md:py-2 bg-ui-tertiary">
    <div class="container">
      <div class="flex flex-wrap items-center justify-between -mx-2">

        <div class="flex flex-col items-center px-2 mr-auto sm:flex-row">
          <g-link
            to="/"
            class="flex items-center text-ui-primary"
            title="Home"
          >
            <Logo class="text-ui-primary" />
            <span class="hidden ml-2 text-xl font-black tracking-tighter uppercase md:block">
              {{ meta.siteName }}
            </span>
          </g-link>
        </div>

        <nav v-if="settings.nav.links.length > 0" class="main-nav mt-2 md:mt-0 ml-2 md:ml-8">
          <g-link
            v-for="link in settings.nav.links"
            :key="link.path"
            :to="link.path"
            class="block md:p-1 font-medium nav-link text-ui-typo hover:text-ui-primary"
          >
            {{ link.title }}
          </g-link>
        </nav>

        <div class="flex flex-1 justify-end">
          <div class="w-full font-bold px-2 sm:px-4 max-w-screen-sm">
            <ClientOnly>
              <SearchInput />
            </ClientOnly>
          </div>
          <div class="flex items-center justify-end pr-2">
            <a v-if="settings.github" :href="settings.github" class="ml-3" target="_blank" rel="noopener noreferrer" title="Github" name="Github">
              <GithubIcon size="1.5x" />
            </a>
            <theme-switcher class="ml-4" :theme="theme" @themeChanged="app.updateTheme" />
          </div>
        </div>

      </div>
    </div>
  </div>
</template>

<static-query>
query {
  metadata {
    siteName
    settings {
      github
      nav {
        links {
          path
          title
        }
      }
    }
  }
}
</static-query>

<script>
import ThemeSwitcher from '@/components/ThemeSwitcher'
import Logo from '@/components/Logo';
import { SunIcon, MoonIcon, GithubIcon, GlobeIcon } from "vue-feather-icons";
import SearchInput from "./SearchInput";


export default {
  components: {
    SearchInput,
    ThemeSwitcher,
    SunIcon,
    MoonIcon,
    GithubIcon,
    GlobeIcon,
    Logo
  },
  data() {
    return {
      opened: false,
    }
  },
  computed: {
    meta() {
      return this.$static.metadata;
    },
    settings() {
      return this.meta.settings;
    },
    theme () {
      return this.$store.getters.theme
    }
  },
  methods: {
    toggle () {
      this.opened = !this.opened
    }
  }
};
</script>

<style lang="scss">
header {
  svg:not(.feather-search) {
    &:hover {
      @apply text-ui-primary;
    }
  }
}

.nav-link {
  &.active {
    @apply text-ui-primary font-bold border-ui-primary;
  }
}
</style>
