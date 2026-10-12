<script setup lang="ts">
import { ref } from 'vue'
import InfoCard from './components/InfoCard.vue'
import { profile } from './data/profile'

// Show more state
const showMore = ref(false)

const toggleMore = () => {
  showMore.value = !showMore.value
}
</script>

<template>
  <main class="min-h-screen bg-slate-950 text-slate-300">
    <section class="mx-auto max-w-5xl px-6 py-16">

      <!-- Profile -->
      <div class="mb-12 text-center">
        <div
          class="mx-auto mb-5 flex h-28 w-28 items-center justify-center rounded-full bg-blue-500 text-4xl font-bold text-white">
          K
        </div>

        <h1 class="text-4xl font-bold text-white">
          {{ profile.name }}
        </h1>

        <p class="mt-2 text-blue-400">
          {{ profile.nickname }} · {{ profile.position }}
        </p>

        <p class="mx-auto mt-4 max-w-2xl text-slate-400">
          {{ profile.bio }}
        </p>

        <button class="mt-6 rounded-lg bg-blue-500 px-5 py-2 text-white transition hover:bg-blue-600"
          @click="toggleMore">
          {{ showMore ? 'ซ่อนข้อมูล' : 'ดูข้อมูลเพิ่มเติม' }}
        </button>
      </div>

      <!-- Main Information -->
      <div class="grid gap-6 md:grid-cols-2">
        <InfoCard title="Education">
          <p class="font-medium text-white">
            {{ profile.university }}
          </p>

          <p class="mt-2 text-slate-400">
            {{ profile.major }}
          </p>
        </InfoCard>

        <InfoCard title="About Me">
          <div class="space-y-2">
            <p>
              <span class="text-slate-500">ชื่อเล่น:</span>
              {{ profile.nickname }}
            </p>

            <p>
              <span class="text-slate-500">สายงาน:</span>
              {{ profile.position }}
            </p>

            <p>
              <span class="text-slate-500">ประเทศ:</span>
              {{ profile.location }}
            </p>
          </div>
        </InfoCard>

        <InfoCard title="งานอดิเรก">
          <ul class="space-y-2">
            <li v-for="hobby in profile.hobbies" :key="hobby">
              • {{ hobby }}
            </li>
          </ul>
        </InfoCard>

        <InfoCard title="สิ่งที่ชอบ">
          <div class="flex flex-wrap gap-2">
            <span v-for="like in profile.likes" :key="like" class="rounded-full bg-blue-500/10 px-3 py-1 text-blue-400">
              {{ like }}
            </span>
          </div>
        </InfoCard>
      </div>

      <!-- More Information -->
      <div v-if="showMore" class="mt-6 space-y-6">
        <div class="grid gap-6 md:grid-cols-2">
          <InfoCard title="จุดแข็ง">
            <ul class="space-y-2">
              <li v-for="strength in profile.strengths" :key="strength">
                ✓ {{ strength }}
              </li>
            </ul>
          </InfoCard>

          <InfoCard title="สิ่งที่ไม่ชอบ">
            <ul class="space-y-2">
              <li v-for="item in profile.dislikes" :key="item">
                • {{ item }}
              </li>
            </ul>
          </InfoCard>
        </div>

        <InfoCard title="Favorites">
          <div class="grid gap-6 sm:grid-cols-2 lg:grid-cols-4">
            <div>
              <p class="text-sm text-slate-500">กีฬา</p>
              <p class="font-medium text-white">
                {{ profile.favorites.sport }}
              </p>
            </div>

            <div>
              <p class="text-sm text-slate-500">ทีม</p>
              <p class="font-medium text-white">
                {{ profile.favorites.team }}
              </p>
            </div>

            <div>
              <p class="text-sm text-slate-500">เกม</p>
              <p class="font-medium text-white">
                {{ profile.favorites.game }}
              </p>
            </div>

            <div>
              <p class="text-sm text-slate-500">อาหาร</p>
              <p class="font-medium text-white">
                {{ profile.favorites.food }}
              </p>
            </div>
          </div>
        </InfoCard>
      </div>

    </section>
  </main>
</template>