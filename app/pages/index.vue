<script setup lang="ts">
const appConfig = useAppConfig()

const { data: versions } = await useFetch(computed(() => `https://ungh.cc/repos/${appConfig.repository}/releases`), {
  transform: (data: {
    releases: {
      name?: string
      tag: string
      publishedAt: string
      markdown: string
    }[]
  }) => {
    return data.releases.map(release => ({
      tag: release.tag,
      title: release.name || release.tag,
      date: release.publishedAt,
      markdown: release.markdown
    }))
  }
})
</script>

<template>
  <UChangelogVersions
    as="main"
    :indicator-motion="false"
    :ui="{
      root: 'py-8 sm:py-12 md:py-16 lg:py-24 xl:py-32',
      indicator: 'inset-y-0'
    }"
  >
    <UChangelogVersion
      v-for="version in versions"
      :key="version.tag"
      v-bind="version"
      :ui="{
        root: 'flex items-start',
        container: 'max-w-full sm:max-w-xl',
        header: 'border-b border-default pb-3 sm:pb-4',
        title: 'text-xl sm:text-2xl lg:text-3xl',
        date: 'text-xs/9 text-highlighted font-mono',
        indicator: 'sticky top-0 pt-8 -mt-8 sm:pt-12 sm:-mt-12 md:pt-16 md:-mt-16 lg:pt-24 lg:-mt-24 xl:pt-32 xl:-mt-32'
      }"
    >
      <template #body>
        <MDC
          v-if="version.markdown"
          :value="version.markdown"
        />
      </template>
    </UChangelogVersion>
  </UChangelogVersions>
</template>
