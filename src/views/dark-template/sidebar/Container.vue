<template>
  <v-card
    color="grey darken-3"
    dark
  >
    <v-card-text>
      <avatar />
      <div class="text-sm-center mb-4 mt-3">
        <h1>
          Philip <span class="light-blue--text text--lighten-3">Matunda</span>
        </h1>
        <span>
          A challenge-loving web developer
        </span>
      </div>

      <sidebar-section :options="sections.info" />
      <sidebar-section :options="sections.socials" />
      <sidebar-section :options="sections.hobbies">
        <template v-slot:item="{item}">
          <v-chip>
            <v-avatar>
              <v-icon>
                {{ item.icon }}
              </v-icon>
            </v-avatar>
            {{ item.text }}
          </v-chip>
        </template>
      </sidebar-section>
      <sidebar-section :options="sections.languages">
        <template v-slot:items="{items}">
          <v-container pa-0>
            <v-layout
              wrap
              class="text-xs-center"
            >
              <template
                v-for="(item, i) in items"
              >
                <v-flex
                  :key="i"
                  md3
                  sm4
                  xs6
                >
                  <v-progress-circular
                    rotate="360"
                    size="65"
                    width="2"
                    :value="item.value"
                    color="white"
                    class="ma-2"
                  >
                    {{ item.text }}
                  </v-progress-circular>
                </v-flex>
              </template>
            </v-layout>
          </v-container>
        </template>
      </sidebar-section>
      <sidebar-section :options="sections.books">
        <template v-slot:item="{item}">
          <v-chip>
            <v-avatar>
              <v-icon>
                {{ item.icon }}
              </v-icon>
            </v-avatar>
            {{ item.text }}
          </v-chip>
        </template>
      </sidebar-section>
    </v-card-text>
  </v-card>
</template>

<script>
import Avatar from '@/views/dark-template/sidebar/Avatar'
import SidebarSection from '@/views/dark-template/sidebar/Section'
export default {
  name      : 'Sidebar',
  components: { SidebarSection, Avatar },
  data () {
    return {
      sections: {
        info: {
          title: 'INFO',
          items: [
            {
              name: 'Email',
              icon: 'mdi-email',
              text: 'philipmatunda@gmail.com',
            },
            {
              name: 'Website',
              icon: 'mdi-web',
              text: 'philipmatunda.',
            },
            {
              name: 'Birth Date',
              icon: 'mdi-cake-variant',
              text: 'Dec 28, 1996',
            },
            {
              name: 'Habitation',
              icon: 'mdi-map-marker',
              text: 'Nakuru, Kenya',
            },
          ],
        },
        socials: {
          title: 'SOCIALS',
          items: [
            {
              icon: 'mdi-github-circle',
              text: 'github.com/Phil-Reck',
              link: 'https://github.com/Phil-Reck',
            },
            {
              icon: 'mdi-linkedin-box',
              text: 'linkedin.com/in/philip-matunda',
              link: 'https://www.linkedin.com/in/philip-matunda-b83a9915b/',
            },
            {
              icon: 'mdi-twitter',
              text: 'twitter.com/matundaphilip',
              link: 'https://twitter.com/matundaphilip',
            },
            {
              icon: 'mdi-instagram',
              text: 'instagram.com/unmasked.phil',
              link: 'https://www.instagram.com/unmasked.phil/',
            },
          ],
        },
        hobbies: {
          title: 'HOBBIES',
          items: [

            {
              icon: 'mdi-bullseye',
              text: 'Getting out of comfort zone',
            },
            {
              icon: 'mdi-biohazard',
              text: 'Challenges',
            },
            {
              icon: 'mdi-bike',
              text: 'Cycling',
            },
            {
              icon: 'mdi-image-filter-hdr',
              text: 'Nature',
            },
            {
              icon: 'mdi-auto-fix',
              text: 'Hacking',
            },
            {
              icon: 'mdi-teach',
              text: 'Teaching',
            },
            {
              icon: 'mdi-car-sports',
              text: 'Sports',
            },
            {
              icon: 'mdi-music',
              text: 'Music',
            },
            {
              icon: 'mdi-account-group',
              text: 'Leadership',
            },
            {
              icon: 'mdi-book-open-page-variant',
              text: 'Books',
            },
            {
              icon: 'mdi-android-debug-bridge',
              text: 'Debugging!',
            },
          ],
        },
        languages: {
          title: 'LANGUAGES',
          items: [
            {
              text : 'English',
              value: 85,
            },
            {
              text : 'Swahili',
              value: 90,
            },
          ],
        },
        books: {
          title: 'FAVORITE BOOKS',
          items: [

            {
              icon: 'mdi-book-open-page-variant',
              text: 'Passionate Programmer - Chad Fowler',
            },
            {
              icon: 'mdi-book-open-page-variant',
              text: 'Mastery - Robert Greene',
            },
            {
              icon: 'mdi-book-open-page-variant',
              text: 'Rework - Jason Fried and David Heinemeier Hanson',
            },
            {
              icon: 'mdi-book-open-page-variant',
              text: 'Pragmatic Programmer - Andrew Hunt and David Thomas',
            },
            {
              icon: 'mdi-book-open-page-variant',
              text: 'Start With Why - Simon Sinek',
            },
          ],
        },
      },
    }
  },
}
</script>

<style scoped>
.sidebar{
    background: #2e2e2e;
}
</style>
