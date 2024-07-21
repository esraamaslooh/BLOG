<template>
  <q-layout view="lHh Lpr lFf">
    <q-header
      v-show="$q.screen.width > 1050"
      unelevated
      class="bg-white global_header full-width"
    >
      <q-toolbar>
        <div class="row full-width flex items-center">
          <div class="col-2">
            <span class="app_logo">
              <q-img
                class="logo_main_img"
                src="/src/assets/app_main_logo.jpg"
              />Meta</span
            >
            <span class="app_logo text-weight-bold">Blog</span>
          </div>
          <div class="col-10 header_right_col">
            <div class="q-mr-lg pages_toggle_container">
              <q-btn-toggle
                v-model="model"
                toggle-color="primary"
                flat
                :to="'/home'"
                text-color="black"
                no-caps
                :options="[
                  { label: 'Home', value: '/home' },
                  { label: 'Blog', value: '/blog' },
                  { label: 'Single Post', value: '/blog-details/1' },
                  { label: 'Pages', value: '/pages' },
                  { label: 'Contact', value: '/contact' },
                ]"
              />
            </div>
            <q-input class="q-mr-xl" filled dense v-model="text" label="Search">
              <template v-slot:append>
                <q-icon name="search" />
              </template>
            </q-input>
            <q-toggle
              color="black"
              size="xl"
              icon="mdi-brightness-4"
              v-model="theme"
            />
          </div>
        </div>
      </q-toolbar>
    </q-header>
    <q-drawer
      show-if-above
      :width="200"
      :breakpoint="700"
      elevated
      v-if="$q.screen.width < 1050"
    >
      <q-list class="q-pl-sm text-bold text-h6 text-left">
        <div class="text-right q-mb-lg">
          <q-toggle
            color="black"
            size="xl"
            icon="mdi-brightness-4"
            v-model="theme"
          />
        </div>
        <div class="flex items-center">
          <q-icon size="md" name="mdi-alpha-b-circle-outline" />
          <span class="app_logo text-weight-bold q-pl-sm">Meta Blog</span>
        </div>
        <q-input
          class="q-mr-sm q-mt-md"
          filled
          dense
          v-model="text"
          label="Search"
        >
          <template v-slot:append>
            <q-icon name="search" />
          </template>
        </q-input>
        <q-item class="text-center full-width" clickable v-ripple>
          Home
        </q-item>
        <q-item class="text-center full-width" clickable v-ripple>
          Blog
        </q-item>
        <q-item class="text-center full-width" clickable v-ripple>
          Single Post
        </q-item>
        <q-item class="text-center full-width" clickable v-ripple>
          Pages
        </q-item>
        <q-item class="text-center full-width" clickable v-ripple>
          Contact
        </q-item>
      </q-list>
    </q-drawer>
    <q-footer class="global_footer">
      <div class="main_footer_section">
        <div class="about-f col-md-3">
          <p class="text-bold text-h6 text-black">About</p>
          <p>
            Lorem ipsum dolor sit amet consectetur Lorem ipsum dolor sit amet
            consecteturadipisicing elit. Blanditiis amet quibusdam repellat quam
            delectus qui officia commodi illo id itaque.
          </p>
          <p>
            <span class="text-bold text-black">Email :</span>
            info@jstemplate.net
          </p>
          <p>
            <span class="text-bold text-black">Phone :</span> 880 123 456 789
          </p>
        </div>
        <div class="table col-md-4">
          <ul class="q-pl-none">
            <tr class="text-black text-bold">
              Quick line
            </tr>
            <td>
              <li>Home</li>
              <li>About</li>
              <li>Blog</li>
              <li>Archived</li>
              <li>Author</li>
              <li>Contact</li>
            </td>
          </ul>

          <ul class="q-pl-none">
            <tr class="text-black text-bold">
              Category
            </tr>
            <td>
              <li>Lifestyle</li>
              <li>Technology</li>
              <li>travel</li>
              <li>Business</li>
              <li>Economy</li>
              <li>Sports</li>
            </td>
          </ul>
        </div>

        <div class="email-f col-md-4">
          <p class="text-bold text-black text-h6 q-mb-xs">Weekly Newsletter</p>
          <p>Get blog articles and offers via email</p>
          <div>
            <q-input
              class="q-mb-sm"
              color="primary"
              outlined
              label="Your Email"
            >
              <template v-slot:append>
                <q-avatar>
                  <q-icon size="md" name="mdi-email-outline" />
                </q-avatar>
              </template>
            </q-input>
            <q-btn class="btn-f" color="primary" label="Subscribe" />
          </div>
        </div>
      </div>

      <div class="footer_links_section row">
        <div class="col-12 col-md-6">
          <div class="foot-title row">
            <div class="col-2 flex footer_logo items-end justify-end q-pr-sm">
              <q-img
                size="lg"
                class="logo_main_img"
                src="/src/assets/app_main_logo.jpg"
              />
            </div>
            <div class="col">
              <div class="logo_text_container">
                <p class="text-h5 q-mb-sm">
                  Meta <span class="text-bold">Blog</span>
                </p>
                <span>© JS Template 2023. All Rights Reserved.</span>
              </div>
            </div>
          </div>
        </div>
        <div class="col-12 col-md-6 footer_links_container">
          <span class="footer_links">Terms of Use</span>
          <span class="footer_links">Privacy Policy</span>
          <span class="footer_links_no_border">Cookie Policy</span>
        </div>
      </div>
    </q-footer>
    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from "vue";
import { useQuasar } from "quasar";

export default defineComponent({
  name: "MainLayout",

  components: {},

  setup() {
    const { $q } = useQuasar();
    return {
      model: ref("one"),
      theme: ref(false),
      $q,
    };
  },
});
</script>
