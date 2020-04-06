<template>
  <v-card
    color="grey lighten-4"
    light
  >
    <v-card-text>
      <content-section
        title="Who am I?"
      >
        I am passionate about my work. Because I love what I do.
      </content-section>
      <content-section
        v-if="prouds"
        title="What am I proud of?"
      >
        <v-layout
          v-for="(proud, i) in prouds"
          :key="i"
        >
          <v-flex
            md1
            xs3
          >
            <v-icon right>
              {{ proud.icon }}
            </v-icon>
          </v-flex>
          <v-flex
            md11
            xs9
          >
            <p>
              <strong>{{ proud.text }}</strong><br>
              <small>{{ proud.source }}</small>
            </p>
          </v-flex>
        </v-layout>
      </content-section>
      <content-section
        v-if="educations"
        title="Education"
      >
        <v-layout
          v-for="(education, i) in educations"
          :key="i"
        >
          <v-flex md4>
            {{ education.from }} - {{ education.to }}
          </v-flex>
          <v-flex md8>
            <strong v-if="education.title">{{ education.title }}</strong>
            <div v-if="education.location">
              <i>{{ education.location }}</i>
            </div>
            <div v-if="education.description">
              {{ education.description }}
            </div>
          </v-flex>
        </v-layout>
      </content-section>
      <content-section
        v-if="skills"
        id="to-timeline"
        title="Skills"
      >
        <template slot="actions">
          (% are relative not absolute)
        </template>
        <v-layout wrap>
          <template
            v-for="(skill, i) in skills"
          >
            <v-flex
              v-if="skill.divider"
              :key="i"
              md12
              xs12
              mb-4
            />
            <v-flex
              v-else
              :key="i"
              md6
              xs12
            >
              <div
                class="mr-2 ml-2"
              >
                <div class="align-center">
                  <v-icon
                    small
                  >
                    {{ skill.icon }}
                  </v-icon>
                  {{ skill.title }}
                </div>
                <v-progress-linear
                  class="progress"
                  color="secondary"
                  height="3"
                  :value="skill.value"
                />
              </div>
            </v-flex>
          </template>
        </v-layout>
      </content-section>
      <content-section
        v-if="competitions"
        title="Competitions"
      >
        <v-layout
          v-for="(competition, i) in competitions"
          :key="i"
        >
          <v-flex
            md1
            xs3
          >
            <v-icon right>
              {{ competition.icon }}
            </v-icon>
          </v-flex>
          <v-flex
            md11
            xs9
          >
            <p>
              <strong>{{ competition.text }}</strong><br>
              <small>{{ competition.source }}</small>
            </p>
          </v-flex>
        </v-layout>
      </content-section>
    </v-card-text>
  </v-card>
</template>

<script>
import ContentSection from '@/views/dark-template/content/Section'
export default {
  name      : 'MainContent',
  components: { ContentSection },
  data      : () => ({
    prouds: [
      {
        icon  : 'mdi-codWhat am I proud of?e-tags',
        text  : 'Mentor DSC Kabrak',
        source: 'I am focusing on supporting the growth and development of students interested in web technologies, improving their skills towards industry requirements.',
      },
      {
        icon  : 'mdi-star-circle',
        text  : 'Pioneer Lead, DSC Kabarak',
        source: 'I participated in a full-fledged, relevant training during my tenure. I gained skills that include plannning and organizing events in addition to leadership, presentation, communication and time management skills',
      },
      {
        icon  : 'mdi-github-face',
        text  : 'GitHub Campus Expert',
        source: 'I have completed hours of training with guidance from GitHub to learn and improve upon my public speaking, technical writing, community leadership and software development to build a strong technical community, on campus',
      },
      {
        icon  : 'mdi-eventbrite',
        text  : 'Organized over 40 Events',
        source: 'As a community organizer in Campus, I have been a host to over 40 amazing events focused on Web technologies, driving the growth of open source, design thinking, Cloud technologies(GCP)...all of these were geared to solving struggles of our society. Worked together with amazing talents and students who were really passionate problem solvers.',
      },
      {
        icon  : 'mdi-microphone-variant',
        text  : 'Given a talk to over 25 Events',
        source: 'Most of my talks have been tailored around building solutions for local businesses and organizations and the tools and technologies around the same.  .',
      },
    ],
    educations: [
      {
        from       : '2017',
        to         : '2020 (not finished yet)',
        title      : 'Bachelor\'s degree, Computer Science',
        location   : 'Kabarak University',
        description: 'Became a member of University Academic Association of Computer Science',
      },
    ],
    skills: [
      {
        title: 'Python',
        icon : 'mdi-language-python',
        value: 75,
      },
      {
        title: 'JavaScript',
        icon : 'mdi-language-javascript',
        value: 85,
      },
      {
        title: 'Django Framework',
        icon : 'mdi-laravel',
        value: 50,
      },
      {
        title: 'Vue.js Framework',
        icon : 'mdi-vuejs',
        value: 90,
      },
      { divider: true },
      {
        title: 'Linux OS',
        icon : 'mdi-linux',
        value: 80,
      },
      {
        title: 'Networking',
        icon : 'mdi-network',
        value: 20,
      },
      {
        title: 'Web Application Development',
        icon : 'mdi-web',
        value: 80,
      },
      {
        title: 'Test Driven Development',
        icon : 'mdi-test-tube',
        value: 26,
      },
      {
        title: 'Continuous Integration / Continuous Delivery',
        icon : 'mdi-truck-fast',
        value: 40,
      },
      {
        title: 'Git',
        icon : 'mdi-git',
        value: 70,
      },
      { divider: true },
      {
        title: 'Google Cloud Platform',
        icon : 'mdi-cloud-braces',
        value: 40,
      },
      {
        title: 'PHP',
        icon : 'mdi-language-php',
        value: 30,
      },
      { divider: true },
      {
        title: 'Leadership',
        icon : 'mdi-account-group',
        value: 70,
      },
      {
        title: 'Digital Marketing',
        icon : 'mdi-text',
        value: 80,
      },
    ],
    competitions: [
      {
        icon  : 'mdi-newspaper',
        text  : 'Andela Fighting Fake News Hackathon-November 2018',
        source: 'Supported by BBC News, I spent 24 hours working in a team of 4 from Kabarak University to prototype solutions to solve an element of the fake news ecosystem',
      },
      {
        icon  : 'mdi-database',
        text  : 'Oracle Academy Student Hackathon-March 2019',
        source: 'I spent 48 hours collaboratively identifying probelms facing communities in a real world set-up, and then developed a prototype to solve the problem identified.',
      },
    ],
  }),
}
</script>

<style scoped>
.title {
  border-bottom: 2px #bfbfbf solid;
  line-height: 1.5 !important;
}
.progress {
  margin-top: 0.1rem;
}
</style>
