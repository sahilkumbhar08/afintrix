<template>
  <div class="w-full">
    <div class="grid md:grid-cols-3 my-8">
      <div class="flex mt-2 items-center">
        <p class="text-sm text-neutral-600 dark:text-neutral-400 text-center w-full">
          © Copyright {{ currYear }}. All Rights Reserved
          <span v-if="version">
            <br>Version {{ version }}
          </span>
        </p>
      </div>
      <div class="flex justify-center mt-5 md:mt-0">
        <router-link
          :to="{ name: user ? 'home' : 'index' }"
          class="flex-shrink-0 font-semibold flex items-center"
        >
          <img
            src="/logo.png"
            alt="Afintrix"
            class="h-24 w-24 shrink-0 object-contain sm:h-28 sm:w-28 lg:h-32 lg:w-32"
          >
          <span class="ml-2 text-xl text-black dark:text-white">Afintrix</span>
        </router-link>
      </div>
      <div class="flex justify-center mt-5 md:mt-0">
        <div class="grid grid-cols-1 lg:grid-cols-2 gap-x-4 gap-y-2">
          <a
            v-if="opnformConfig.links.feature_requests"
            :href="opnformConfig.links.feature_requests"
            target="_blank"
            class="text-neutral-600 dark:text-neutral-400 transition-colors duration-300 hover:text-blue-500"
          >
            Feature Requests
          </a>
          <a
            v-if="opnformConfig.links.roadmap"
            :href="opnformConfig.links.roadmap"
            target="_blank"
            class="text-neutral-600 dark:text-neutral-400 transition-colors duration-300 hover:text-blue-500"
          >
            Roadmap
          </a>
          <a
            v-if="opnformConfig.links.discord"
            :href="opnformConfig.links.discord"
            target="_blank"
            class="text-neutral-600 dark:text-neutral-400 transition-colors duration-300 hover:text-blue-500"
          >
            Discord
          </a>
          <a
            v-if="opnformConfig.links.tech_docs"
            :href="opnformConfig.links.tech_docs"
            target="_blank"
            class="text-neutral-600 dark:text-neutral-400 transition-colors duration-300 hover:text-blue-500"
          >
            Technical Docs
          </a>
          <template v-if="!useFeatureFlag('self_hosted')">
            <router-link
              :to="{ name: 'integrations' }"
              class="text-neutral-600 dark:text-neutral-400 transition-colors duration-300 hover:text-blue-500"
            >
              Integrations
            </router-link>
            <router-link
              :to="{ name: 'report-abuse' }"
              class="text-neutral-600 dark:text-neutral-400 transition-colors duration-300 hover:text-blue-500"
            >
              Report Abuse
            </router-link>
            <router-link
              :to="{ name: 'privacy-policy' }"
              class="text-neutral-600 dark:text-neutral-400 transition-colors duration-300 hover:text-blue-500"
            >
              Privacy Policy
            </router-link>

            <router-link
              :to="{ name: 'terms-conditions' }"
              class="text-neutral-600 dark:text-neutral-400 transition-colors duration-300 hover:text-blue-500"
            >
              Terms & Conditions
            </router-link>
          </template>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import opnformConfig from "~/opnform.config.js"

const { data: user } = useAuth().user()
const currYear = ref(new Date().getFullYear())

// Use the reactive version for proper template reactivity
const version = computed(() => useFeatureFlag('version'))
</script>
