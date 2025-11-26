<script setup>
useHead({
  meta: [{ name: 'viewport', content: 'width=device-width, initial-scale=1' }],
  link: [{ rel: 'icon', href: '/favicon.ico' }],
  htmlAttrs: {
    lang: 'en'
  }
})

const title = 'Zuno Marketplace SDK'
const description
  = 'Display GitHub release notes as a beautiful changelog for Zuno Marketplace SDK.'

useSeoMeta({
  title,
  description,
  ogTitle: title,
  ogDescription: description,
  ogImage: 'https://ui.nuxt.com/assets/templates/nuxt/changelog-light.png',
  twitterImage: 'https://ui.nuxt.com/assets/templates/nuxt/changelog-light.png',
  twitterCard: 'summary_large_image'
})
</script>

<template>
  <UApp>
    <div class="min-h-screen lg:grid lg:grid-cols-2">
      <UPageSection
        title="Changelog"
        description="Display GitHub release notes as a beautiful changelog for Zuno Marketplace SDK."
        orientation="vertical"
        :links="[
          {
            label: 'Documentation',
            icon: 'i-lucide-book-open',
            variant: 'ghost',
            size: 'md',
            to: 'https://zuno-marketplace-docs.vercel.app/',
            target: '_blank'
          },
          {
            label: 'GitHub',
            icon: 'i-simple-icons-github',
            variant: 'ghost',
            size: 'md',
            to: 'https://github.com/ZunoKit/zuno-marketplace-sdk',
            target: '_blank'
          }
        ]"
        :ui="{
          root: 'border-b border-default lg:border-b-0 lg:sticky lg:inset-y-0 lg:h-screen overflow-hidden',
          container: 'h-full items-center justify-center py-8 sm:py-12 lg:py-0',
          wrapper: 'flex flex-col gap-4 sm:gap-6',
          headline: 'mb-4 sm:mb-6',
          title: 'text-left text-2xl sm:text-3xl lg:text-4xl',
          description: 'text-left text-sm sm:text-base max-w-full lg:max-w-lg',
          links: 'gap-1 justify-start -ms-2.5 flex-wrap'
        }"
      >
        <template #top>
          <SkyBg />

          <div
            class="absolute -right-1/2 z-[-1] rounded-full bg-primary blur-[200px] sm:blur-[300px] size-40 sm:size-60 lg:size-100 transform -translate-y-1/2 top-1/2"
          />
        </template>

        <template #headline>
          <AppLogo class="w-auto h-5 sm:h-6 shrink-0 text-highlighted" />
        </template>

        <template #default />
      </UPageSection>

      <section class="px-4 sm:px-6 lg:px-8 xl:px-0 xl:-ms-30 xl:flex-1">
        <UColorModeButton class="fixed top-4 right-4 z-10" />

        <NuxtPage />
      </section>
    </div>
  </UApp>
</template>
