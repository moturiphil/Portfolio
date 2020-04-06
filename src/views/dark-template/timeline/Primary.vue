<template>
  <v-card
    color="grey lighten-4"
    light
  >
    <v-card-text>
      <content-section
        id="timeline"
        :title="detailed ? 'My Life in a Nutshell' : 'My Experiences'"
      >
        <template slot="actions">
          <div>
            <v-switch
              v-model="detailed"
              :label="detailed ? 'Detailed' : 'Summary'"
            />
          </div>
        </template>

        <v-timeline
          dense
        >
          <v-timeline-item
            v-for="(item, i) in orderedItems"
            :key="i"
            :icon="item.icon || ''"
            :class="{transparent: item.transparent}"
            large
          >
            <template
              v-if="item.iconImage"
              v-slot:icon
            >
              <v-avatar>
                <img
                  :src="publicPath(item.iconImage)"
                >
              </v-avatar>
            </template>
            <template v-slot:opposite />
            <v-layout>
              <v-flex
                v-if="$vuetify.breakpoint.smAndUp"
                md1
                sm2
                align-self-center
              >
                <span>{{ item.year }}</span>
              </v-flex>
              <v-flex
                md11
                sm10
                xs12
              >
                <v-card class="elevation-1">
                  <v-card-title class="pb-0">
                    <div>
                      <p v-if="$vuetify.breakpoint.xsOnly">
                        {{ item.year }}
                      </p>
                      <h3>{{ item.title }}</h3>
                    </div>
                  </v-card-title>
                  <v-card-text>
                    <v-layout wrap>
                      <v-flex
                        :md7="!!item.image"
                        :md12="!item.image"
                        xs12
                      >
                        <div class="mr-1">
                          <span
                            v-if="item.text"
                            class="pre"
                          >{{ item.text }}</span>
                          <!-- eslint-disable vue/no-v-html -->
                          <div
                            v-else-if="item.html"
                            v-html="item.html"
                          />
                          <!-- eslint-enable vue/no-v-html -->
                        </div>
                      </v-flex>
                      <v-flex
                        v-if="item.image"
                        md5
                        xs12
                      >
                        <div
                          class="mt-2"
                        >
                          <v-carousel
                            v-if="Array.isArray(item.image)"
                            :show-arrows="false"
                            :height="325"
                          >
                            <v-carousel-item
                              v-for="(citem,ci) in item.image"
                              :key="ci"
                              :src="publicPath(citem)"
                            />
                          </v-carousel>
                          <v-img
                            v-else
                            :max-height="item.imageHeight ? item.imageHeight : ''"
                            :src="publicPath(item.image)"
                          />
                        </div>
                      </v-flex>
                    </v-layout>
                  </v-card-text>
                </v-card>
              </v-flex>
            </v-layout>
          </v-timeline-item>
        </v-timeline>
      </content-section>
    </v-card-text>
  </v-card>
</template>

<script>
import ContentSection from '@/views/dark-template/content/Section'
export default {
  name      : 'Timeline',
  components: { ContentSection },
  data      : () => ({
    detailed: true,
    items   : [
      {
        detailed   : true,
        transparent: true,
        year       : '1996',
        title      : 'Born on Dec 28, 1996',
        html       : 'With a chance of %0.00000000000512.<br>I\'m completely aware of value of the life!',
        icon       : 'mdi-cake-variant',
      },
      {
        detailed   : true,
        transparent: true,
        year       : '2007',
        title      : 'Touched a Mouse',
        html       : 'ME: "Woooow!"<br><i>... ',
        icon       : 'mdi-mouse-variant',
      },
      {
        detailed   : true,
        year       : '2018',
        transparent: true,
        title      : 'Kabarak University Innovation Hub',
        html       : `
                <p>
                    My journey to find computer science was not quite typical
                </p>
                <p>
                    The first time, I entered the University Hub was the time I first heard all the cool companies and projects members of the Hub were working on and I was awestruck. These students, around my age, were helping to shape the way most citizens of the 21sr century interact with each other, share their lives of experience and this was enough motivation for me.
                </p>
                <p>
                    During my first year, I started attending most of the meetups:
                    <ul>
                        <li>
                            <a href="https://www.meetup.com/DSCKabarak/events/247290155/">IWD '18 Nakuru</a> - Codelab session just blew my mind away...
                        </li>
                        <li>
                            <a href="https://www.meetup.com/DSCKabarak/events/246830344/">Google Cloud Study Jam</a> - Quick intro to qwiklabs
                        </li>
                        <li>
                            <a href="https://www.meetup.com/DSCKabarak/events/246830344//">https://www.meetup.com/DSCKabarak/events/246830344/</a> - Got to be selected as an innovation Hub Lead!
                        </li>
                        <li>
                            And many other meetups I can't really remember!
                        </li>
                    </ul>
                </p>
        `,
        image      : 'img/timeline/iwd.jpeg',
        imageHeight: 200,
        icon       : 'mdi-account-multiple',
      },
      {
        detailed   : true,
        year       : '2018',
        transparent: true,
        title      : 'DSC Kabarak University',
        html       : `
                <p>
                    Selected to be a Developer Student Club Lead for the academic year 2018-19
                </p>
                <p>
                    I had the opportunity to provide students with the opportunity to:
                </p>
                <p>
                    <ul>
                        <li>
                            Grow their knowledge on developer technologies and more through peer to peer workshops and events
                        </li>
                        <li>
                            Gain relevent industry experience by solving problems for local organizations with technology based solutions
                        </li>
                        <li>
                            Showcase prototypes and solutions to their local commmunity and industry leaders.
                        </li>
                    </ul>
                </p>
        `,
        image      : 'img/timeline/tech-community.jpeg',
        imageHeight: 200,
        icon       : 'mdi-code-tags',
      },
      {
        detailed   : true,
        transparent: true,
        year       : '2018',
        title      : 'A Turning Point',
        html       : `
          This awesome year was a turning point in my life. I got a very good exposure to great technologies tools.
          </p>
          <p>
          Technically, I got familiar with and tried to be best (not yet of course!) at the following technologies:
          <ul>
          <li>git</li>
          <li>python</li>
          <li>Arduino</li>
          <li>Linux</li>
          <li>Android App Development</li>
          <li>Test Driven Development</li>
          <li>Development best practices</li>
          <li>And more ...</li>
          </ul>
          </p>
          <p>
          So please don't underestimate this card by its height in pixels. It's worth a lot to me.
          </p>
        `,
        icon: 'mdi-cake-variant',
      },
      {
        year : '2019',
        title: 'GitHub Campus Expert',
        html : `
          <p>
            I got the opportunity to gain skills relevant to improve the technical community on their campus, with training and mentorship from GitHub.
          </p>
          <p>
            I've had the opportunities to participate in exclusive events and support to help me grow the developer community at my school.
          </p>
          <p>
            Skills I've acquired include but not limited to the following:
            <ul>
              <li>Software Development</li>
              <li>Public Speaking</li>
              <li>Technical Writing</li>
              <li>Community Leadership</li>
              <li>And more ...</li>
            </ul>
          </p>
        `,
        image: 'img/timeline/expert-training.png',
        icon : 'mdi-github-circle',
      },
      {
        year : '2019',
        title: 'DSC Kabarak University Web App',
        html : `
          <p>
              Current status: <span class="green--text accent-4">Active</span>,
          </p>
          <p>
            
          </p>
          <p>
            DSC Kabarak University Web App movive is to create a local ecosystem of programmers & hackers in and around the campus. Calling into actions all students from undergraduate or graduate program to participate in our activities
            I built on top of this app has been designed and developed for Google Developers Communuty by Vrijraj Singh a  <a target="_blank" href="https://www.twitter.com/VrijrajSignh/">GDE</a>. Currently active at <a target="_blank" href="https://www.dsckabarakakuniversity.web.app">DSC Kabarak University</a>
          </p>
        `,
        image: 'img/timeline/dsckabrak.png',
        icon : 'mdi-code-braces',
      },
      {
        year : '2020',
        title: 'Organizing Vue.js Kenya',
        html : `
          <p>
              Current status: <span class="green--text accent-4">Active</span>
          </p>
          <p>
            <a target="_blank" href="https://www.downtomeet.com/Vuejs-Kenya">Vue.js Kenya</a>
          </p>
          <p>
            A group for anyone interested in "Vue.js - The Progressive JavaScript Framework". The goal is to provide monthly meetups where people give talks on Vue.js and related topics, and people can get together with other developers in the community.
          </p>
        `,
        image: 'img/timeline/vue-registrar-demo.png',
        icon : 'mdi-vuejs',
      },
    ],
  }),
  computed: {
    orderedItems () {
      const items = [...this.items].reverse()
      if (this.detailed)
        return items
      return items.filter((item) => {
        return !item.detailed
      })
    },
  },
}
</script>

<style scoped>
.title {
  border-bottom: 2px #bfbfbf solid;
  line-height: 1.5 !important;
}
.pre {
  white-space: pre;
}
.transparent{
  opacity: 0.6;
}
</style>
