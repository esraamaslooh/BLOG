<template>
  <q-page>
    <div v-if="currentBlog" class="blog_details">
      <p class="title q-mr-auto">{{ currentBlog.category }}</p>
      <p class="text-h4 text-bold">
        {{ currentBlog.title }}
      </p>
      <div class="blog_owner">
        <q-avatar class="avatar_img" size="40px">
          <img :src="`https://cdn.quasar.dev/img/avatar1.jpg`" />
        </q-avatar>
        <span class="owner_name text-bold">{{ currentBlog.blog_owner }}</span>
        <span class="owner_date">{{ currentBlog.blog_date }}</span>
      </div>
      <img :src="currentBlog.img" alt="" />
      <p class="blog_details_section q-mt-lg">{{ currentBlog.description }}</p>

      <p class="text-h6 full-width">Research Your Destination</p>
      <p class="blog_details_section">
        {{ currentBlog.research_your_destination }}
      </p>
      <p class="text-h6 full-width">Plan Your Itinerary</p>
      <p class="blog_details_section">
        {{ currentBlog.plan_your_itinerary }}
      </p>

      <div class="traviling-div">
        <p class="traviling-p">
          “ Traveling can expose you to new environments and potential health
          risks, so it's crucial to take precautions to stay safe and healthy. ”
        </p>
      </div>

      <div class="blog_details_ad">
        <span class="block ad_title">Advertisement</span>
        <span class="block ad_subtitle">You can place ads</span>
        <span class="block ad_dimensions">750x100</span>
      </div>

      <p class="text-h6 full-width q-mt-xl">Pack Lightly and Smartly</p>
      <p class="blog_details_section">
        {{ currentBlog.pack_lightly_and_smartly }}
      </p>

      <p class="text-h6 full-width">Conclusion:</p>
      <p class="blog_details_section">
        {{ currentBlog.conclusion }}
      </p>
    </div>
  </q-page>
</template>

<script>
import { defineComponent, ref, onMounted } from "vue";
import axios from "axios";
import { useRoute } from "vue-router";

export default defineComponent({
  name: "BlogDetails",
  setup() {
    const route = useRoute();
    const blogs = ref([]);
    const currentBlog = ref(null);

    onMounted(async () => {
      try {
        const response = await axios.get("/src/utils/blog_posts.json");
        blogs.value = response.data;
        currentBlog.value = blogs.value.filter((item) => {
          return item.id == route.params.id;
        });
        currentBlog.value = currentBlog.value[0];
      } catch (error) {
        console.error("Failed to fetch blogs:", error);
      }
    });

    return { blogs, currentBlog };
  },
});
</script>
