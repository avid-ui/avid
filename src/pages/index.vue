<script lang="ts">
import { computed, defineComponent } from 'vue'
import { Feather, Github, Zap } from '@astel/icons'
import { useRoute } from '#imports'
export default defineComponent({
  components: { Feather, Github, Zap },
  setup() {
    const route = useRoute()

    const currentPage = computed(() => route.params.component)

    const features = ref([
      {
        title: 'Light Weight',
        description: 'Light weight UI components, each components is <2kb Brotli',
        icon: markRaw(Feather),
        link: '',
      },
      {
        title: 'Clean',
        description: 'Astel UI provides clean and minimal ui components',
        icon: markRaw(Zap),
        link: '',
      },
      {
        title: 'OSS',
        description: 'Astel is Open-source and available freely under MIT license',
        icon: markRaw(Github),
        link: 'https://github.com/astel-org/astel',
      },
    ])

    return {
      features,
      currentPage,
    }
  },
})
</script>

<template>
  <main class="flex flex-col justify-center items-center w-full">
    <div class="text-center w-full mt-24 md:mt-44">
      <h1 class="text-6xl font-bold">Astel</h1>
      <p class="text-2xl mt-4 text-[color:var(--accents-5)] font-medium">
        A sleek and minimal Vue 3 UI component library
      </p>
    </div>
    <div class="flex items-center justify-center mt-10">
      <NuxtLink to="/guide">
        <as-button size="large" type="success" variant="shadow">Get Started</as-button>
      </NuxtLink>
    </div>

    <!-- <div class="text-center mt-32 grid w-full">
      <NuxtLink
        v-for="(feature, index) in features"
        :key="index"
        :to="feature.link"
        class="grid grid-cols-3"
      >
        <as-card hoverable shadow>
          <div class="flex flex-row items-center p-2">
            <span class="border-[1px] border-[color:var(--accents-2)] rounded-full px-2 py-3">
              <component :is="feature.icon" class="mx-1" />
            </span>
            <p class="text-xl font-semibold mx-3">{{ feature.title }}</p>
          </div>
          <p class="text-left p-2 text-[color:var(--accents-6)]">
            {{ feature.description }}
          </p>
         
        </as-card>
      </NuxtLink>
    </div> -->

    <div
      class="grid md:grid-cols-3 sm:grid-cols-2 grid-cols-1 gap-4 text-center mt-32 pb-16 w-full"
    >
      <NuxtLink v-for="(feature, index) in features" :key="index" :to="feature.link">
        <as-card hoverable>
          <div class="flex flex-row items-center p-2">
            <span class="border-[1px] border-[color:var(--accents-2)] rounded-full px-2 py-3">
              <component :is="feature.icon" class="mx-1" />
            </span>
            <p class="text-xl font-semibold mx-3">{{ feature.title }}</p>
          </div>
          <p class="text-left p-2 text-[color:var(--accents-6)]">
            {{ feature.description }}
          </p>
        </as-card>
      </NuxtLink>
    </div>
  </main>
</template>
