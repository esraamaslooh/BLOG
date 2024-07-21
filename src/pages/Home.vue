<template>
  <q-page class="flex flex-center">
    <div class="main_page_img_container">
      <img class="main_page_img" src="/src/assets/main_page_img.jpg" />
      <div class="image_content">
        <p class="title">Technology</p>
        <p class="subtitle">
          The Impact of Technology on the Workplace: How Technology is Changing
        </p>
      </div>
    </div>

    <div class="advertisement">
      <span class="block ad_title">Advertisement</span>
      <span class="block ad_subtitle">You can place ads</span>
      <span class="block ad_dimensions">750x100</span>
    </div>

    <span class="blogs_section_title">Latest Post</span>
    <div class="blogs_section row full-width items-start">
      <div
        v-for="item in blogs"
        :key="item.id"
        class="blog_card_container raise col-12 col-lg-4 col-xl-3 col-md-6"
      >
        <q-card @click="goToBlog(item)" class="blog_card" flat bordered>
          <!-- <div class="blog_img_container"></div> -->
          <q-img class="blog_img" :src="item.img" />

          <q-card-section class="q-pb-none">
            <div class="blog_title">Technology</div>
            <div class="blog_desc">
              The Impact of Technology on the Workplace: How Technology is
              Changing
            </div>

            <div class="row blog_card_footer">
              <q-avatar size="sm">
                <img src="https://cdn.quasar.dev/img/avatar2.jpg" />
              </q-avatar>
              <span class="title">Tracey Wilson</span>
              <span class="subtitle">August 20, 2022</span>
            </div>
          </q-card-section>
        </q-card>
      </div>
    </div>
    <div class="text-center full-width q-my-xl">
      <q-btn unelevated outline no-caps @click="blogs.push(...blogs)"
        >View All Post</q-btn
      >
    </div>
    <div class="advertisement main_bottom_ad">
      <span class="block ad_title">Advertisement</span>
      <span class="block ad_subtitle">You can place ads</span>
      <span class="block ad_dimensions">750x100</span>
    </div>
  </q-page>
</template>

<script>
import { defineComponent, ref, onMounted } from "vue";
import axios from "axios";
import { useRouter } from "vue-router";

export default defineComponent({
  name: "HomePage",
  setup() {
    const router = useRouter();
    const blogs = ref([]);

    const goToBlog = (blog) => {
      router.push(`/blog-details/${blog.id}`);
      localStorage.setItem("blog_details", blog);
    };

    onMounted(async () => {
      try {
        const response = await axios.get("/src/utils/blog_posts.json");
        blogs.value = response.data;
      } catch (error) {
        console.error("Failed to fetch blogs:", error);
      }
    });

    return { blogs, goToBlog };
  },
});
</script>
