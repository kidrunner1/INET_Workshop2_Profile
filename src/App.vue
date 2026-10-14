<script setup lang="ts">
import { ref } from 'vue'
import InfoCard from './components/InfoCard.vue'
import { profile } from './data/profile'

const showMore = ref(false)

const toggleMore = () => {
  showMore.value = !showMore.value
}
</script>

<template>
  <main class="min-h-screen bg-slate-950 text-slate-300">
    <section class="mx-auto max-w-5xl px-5 py-12 sm:px-6 lg:py-16">

      <!-- Profile Header -->
      <header class="mb-8 rounded-2xl border border-slate-800 bg-slate-900/60 p-6 sm:p-8">
        <div class="flex flex-col items-center gap-6 text-center sm:flex-row sm:text-left">
          <!-- Avatar -->
          <div class="flex h-24 w-24 shrink-0 items-center justify-center rounded-2xl
                   bg-slate-800 text-3xl font-bold text-blue-400">
            K
          </div>

          <!-- Profile Information -->
          <div class="flex-1">
            <p class="mb-2 text-sm font-medium text-blue-400">
              {{ profile.position }}
            </p>

            <h1 class="text-3xl font-bold tracking-tight text-white sm:text-4xl">
              {{ profile.name }}
            </h1>

            <p class="mt-2 text-sm text-slate-400">
              {{ profile.nickname }} · {{ profile.location }}
            </p>

            <p class="mx-auto mt-4 max-w-2xl leading-7 text-slate-400 sm:mx-0">
              {{ profile.bio }}
            </p>
          </div>
        </div>
      </header>

      <!-- Main Information -->
      <section class="grid gap-5 md:grid-cols-2">

        <!-- About Me -->
        <InfoCard title="About Me">
          <div class="space-y-4">
            <div>
              <p class="text-sm text-slate-500">ชื่อเล่น</p>
              <p class="mt-1 font-medium text-slate-200">
                {{ profile.nickname }}
              </p>
            </div>

            <div>
              <p class="text-sm text-slate-500">สายงาน</p>
              <p class="mt-1 font-medium text-slate-200">
                {{ profile.position }}
              </p>
            </div>

            <div>
              <p class="text-sm text-slate-500">ประเทศ</p>
              <p class="mt-1 font-medium text-slate-200">
                {{ profile.location }}
              </p>
            </div>
          </div>
        </InfoCard>

        <!-- Education -->
        <InfoCard title="Education">
          <div>
            <p class="font-semibold text-white">
              {{ profile.university }}
            </p>

            <p class="mt-2 leading-6 text-slate-400">
              {{ profile.major }}
            </p>
          </div>
        </InfoCard>

        <!-- Hobbies -->
        <InfoCard title="งานอดิเรก">
          <ul class="space-y-3">
            <li v-for="hobby in profile.hobbies" :key="hobby" class="flex items-center gap-3">
              <span class="h-1.5 w-1.5 rounded-full bg-blue-400"></span>

              <span>
                {{ hobby }}
              </span>
            </li>
          </ul>
        </InfoCard>

        <!-- Likes -->
        <InfoCard title="สิ่งที่ชอบ">
          <div class="flex flex-wrap gap-2">
            <span v-for="like in profile.likes" :key="like" class="rounded-lg border border-slate-700 bg-slate-800/60
                     px-3 py-1.5 text-sm text-slate-300">
              {{ like }}
            </span>
          </div>
        </InfoCard>

      </section>

      <!-- Show More Button -->
      <div class="my-8 flex justify-center">
        <button class="rounded-lg border border-slate-700 bg-slate-900 px-5 py-2.5
                 text-sm font-medium text-slate-300 transition
                 hover:border-slate-600 hover:bg-slate-800 hover:text-white" @click="toggleMore">
          {{ showMore ? 'ซ่อนข้อมูลเพิ่มเติม' : 'ดูข้อมูลเพิ่มเติม' }}
        </button>
      </div>

      <!-- More Information -->
      <Transition name="fade">
        <section v-if="showMore" class="space-y-5">

          <div class="grid gap-5 md:grid-cols-2">

            <!-- Strengths -->
            <InfoCard title="จุดแข็ง">
              <ul class="space-y-3">
                <li v-for="strength in profile.strengths" :key="strength" class="flex items-start gap-3">
                  <span class="mt-0.5 text-emerald-400">
                    ✓
                  </span>

                  <span>
                    {{ strength }}
                  </span>
                </li>
              </ul>
            </InfoCard>

            <!-- Dislikes -->
            <InfoCard title="สิ่งที่ไม่ชอบ">
              <ul class="space-y-3">
                <li v-for="item in profile.dislikes" :key="item" class="flex items-start gap-3">
                  <span class="mt-2 h-1.5 w-1.5 rounded-full bg-slate-500"></span>

                  <span>
                    {{ item }}
                  </span>
                </li>
              </ul>
            </InfoCard>

          </div>

          <!-- Favorites -->
          <InfoCard title="Favorites">
            <div class="grid gap-4 sm:grid-cols-2 lg:grid-cols-4">

              <div class="rounded-xl bg-slate-800/50 p-4">
                <p class="text-xs uppercase tracking-wide text-slate-500">
                  กีฬา
                </p>

                <p class="mt-2 font-medium text-white">
                  {{ profile.favorites.sport }}
                </p>
              </div>

              <div class="rounded-xl bg-slate-800/50 p-4">
                <p class="text-xs uppercase tracking-wide text-slate-500">
                  ทีม
                </p>

                <p class="mt-2 font-medium text-white">
                  {{ profile.favorites.team }}
                </p>
              </div>

              <div class="rounded-xl bg-slate-800/50 p-4">
                <p class="text-xs uppercase tracking-wide text-slate-500">
                  เกม
                </p>

                <p class="mt-2 font-medium text-white">
                  {{ profile.favorites.game }}
                </p>
              </div>

              <div class="rounded-xl bg-slate-800/50 p-4">
                <p class="text-xs uppercase tracking-wide text-slate-500">
                  อาหาร
                </p>

                <p class="mt-2 font-medium text-white">
                  {{ profile.favorites.food }}
                </p>
              </div>

            </div>
          </InfoCard>

        </section>
      </Transition>

    </section>
  </main>
</template>

<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: all 0.2s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
  transform: translateY(-8px);
}
</style>