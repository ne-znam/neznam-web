<template>
  <div>
    <header
      class="pointer-events-none relative z-50 flex flex-col"
      :style="{
        height: 'var(--header-height)',
        marginBottom: 'var(--header-mb)',
      }"
    >
      <div v-if="home">
        <div
          ref="{avatarRef}"
          class="order-last mt-[calc(theme(spacing.16)-theme(spacing.3))]"
        />
        <Container
          class="top-0 order-last -mb-3 pt-3"
          :style="{ position: 'var(--header-position)' }"
        >
          <div
            class="top-[var(--avatar-top,theme(spacing.3))] w-full"
            :style="{ position: 'var(--header-inner-position)' }"
          >
            <div class="relative">
              <AvatarContainer
                class="absolute left-0 top-3 origin-left transition-opacity"
                :style="{
                  opacity: 'var(--avatar-border-opacity, 0)',
                  transform: 'var(--avatar-border-transform)',
                }"
              />
              <Avatar
                large
                class="block h-16 w-16 origin-left"
                :style="{ transform: 'var(--avatar-image-transform)' }"
              />
            </div>
          </div>
        </Container>
      </div>

      <div
        ref="{headerRef}"
        class="top-0 z-10 h-16 pt-6"
        :style="{ position: 'var(--header-position)' }"
      >
        <Container
          class="top-[var(--header-top,theme(spacing.6))] w-full"
          :style="{ position: 'var(--header-inner-position)' }"
        >
          <div class="relative flex gap-4">
            <div
              v-if="home"
              class="flex flex-1"
            >
              <AvatarContainer>
                <Avatar />
              </AvatarContainer>
            </div>
            <div class="flex flex-1 justify-end md:justify-center">
              <MobileNavigation class="pointer-events-auto md:hidden" />
              <DesktopNavigation class="pointer-events-auto hidden md:block" />
            </div>
            <div class="flex justify-end md:flex-1">
              <div class="pointer-events-auto">
                <ModeToggle />
              </div>
            </div>
          </div>
        </Container>
      </div>
    </header>
    <div
      v-if="home"
      :style="{ height: 'var(--content-offset)' }"
    />
  </div>
</template>

<script setup>

const home = ref(false)
</script>
