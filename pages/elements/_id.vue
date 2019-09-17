<template>
  <b-container>
    <b-row>
      <b-col cols="2" class="bg-dark text-white">
        <b-nav vertical>
          <h5 class="title">
            Encyclopedia
          </h5>
          <b-nav-item v-for="related in relatedElements" :key="related.id">
            <nuxt-link :to="`${related.id}`">
              {{ related.title }}
            </nuxt-link>
          </b-nav-item>
        </b-nav>
      </b-col>
      <b-col>
        <article>
          <h1 class="title">
            {{ element.title }}
          </h1>
          <div>
            <!-- Single button triggers two "<b-collapse>" components -->
            <b-button v-b-toggle.collapse-a>
              Beginner
            </b-button>
            <b-button v-b-toggle.collapse-b>
              Advanced
            </b-button>
            <b-button v-b-toggle.collapse-c>
              Master
            </b-button>
            <b-button v-b-toggle.collapse-d>
              Wizard
            </b-button>

            <!-- Elements to collapse -->
            <b-collapse id="collapse-a" class="mt-2">
              <b-card>{{ element.level1 }}</b-card>
            </b-collapse>
            <b-collapse id="collapse-b" class="mt-2">
              <b-card>{{ element.level2 }}</b-card>
            </b-collapse>
            <b-collapse id="collapse-c" class="mt-2">
              <b-card>{{ element.level3 }}</b-card>
            </b-collapse>
            <b-collapse id="collapse-d" class="mt-2">
              <b-card>{{ element.level4 }}</b-card>
            </b-collapse>
          </div>
        </article>
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
export default {
  data () {
    return {
      id: this.$route.params.id,
      elements: [
        {
          id: 'laser',
          title: 'Laser',
          level1:
            'Beginner level stuff Lorem ipsum dolor sit amet consectetur adipisicing elit. Explicabo, ipsa nesciunt cupiditate vel, quas, fuga voluptates quod pariatur corrupti ducimus debitis sit at commodi optio praesentium iusto quidem. Maiores, omnis!',
          level2:
            'Advanced level stuff Lorem ipsum dolor sit amet consectetur adipisicing elit. Explicabo, ipsa nesciunt cupiditate vel, quas, fuga voluptates quod pariatur corrupti ducimus debitis sit at commodi optio praesentium iusto quidem. Maiores, omnis!',
          level3:
            'Master level stuff Lorem ipsum dolor sit amet consectetur adipisicing elit. Explicabo, ipsa nesciunt cupiditate vel, quas, fuga voluptates quod pariatur corrupti ducimus debitis sit at commodi optio praesentium iusto quidem. Maiores, omnis!',
          level4:
            'Wizard level stuff Lorem ipsum dolor sit amet consectetur adipisicing elit. Explicabo, ipsa nesciunt cupiditate vel, quas, fuga voluptates quod pariatur corrupti ducimus debitis sit at commodi optio praesentium iusto quidem. Maiores, omnis!'
        },
        {
          id: 'detector',
          title: 'Detector',
          level1:
            'Beginner level stuff Lorem ipsum dolor sit amet consectetur adipisicing elit. Explicabo, ipsa nesciunt cupiditate vel, quas, fuga voluptates quod pariatur corrupti ducimus debitis sit at commodi optio praesentium iusto quidem. Maiores, omnis!',
          level2:
            'Advanced level stuff Lorem ipsum dolor sit amet consectetur adipisicing elit. Explicabo, ipsa nesciunt cupiditate vel, quas, fuga voluptates quod pariatur corrupti ducimus debitis sit at commodi optio praesentium iusto quidem. Maiores, omnis!',
          level3:
            'Master level stuff Lorem ipsum dolor sit amet consectetur adipisicing elit. Explicabo, ipsa nesciunt cupiditate vel, quas, fuga voluptates quod pariatur corrupti ducimus debitis sit at commodi optio praesentium iusto quidem. Maiores, omnis!',
          level4:
            'Wizard level stuff Lorem ipsum dolor sit amet consectetur adipisicing elit. Explicabo, ipsa nesciunt cupiditate vel, quas, fuga voluptates quod pariatur corrupti ducimus debitis sit at commodi optio praesentium iusto quidem. Maiores, omnis!'
        },
        {
          id: 'mirror',
          title: 'Mirror',
          level1:
            'Beginner level stuff Lorem ipsum dolor sit amet consectetur adipisicing elit. Explicabo, ipsa nesciunt cupiditate vel, quas, fuga voluptates quod pariatur corrupti ducimus debitis sit at commodi optio praesentium iusto quidem. Maiores, omnis!',
          level2:
            'Advanced level stuff Lorem ipsum dolor sit amet consectetur adipisicing elit. Explicabo, ipsa nesciunt cupiditate vel, quas, fuga voluptates quod pariatur corrupti ducimus debitis sit at commodi optio praesentium iusto quidem. Maiores, omnis!',
          level3:
            'Master level stuff Lorem ipsum dolor sit amet consectetur adipisicing elit. Explicabo, ipsa nesciunt cupiditate vel, quas, fuga voluptates quod pariatur corrupti ducimus debitis sit at commodi optio praesentium iusto quidem. Maiores, omnis!',
          level4:
            'Wizard level stuff Lorem ipsum dolor sit amet consectetur adipisicing elit. Explicabo, ipsa nesciunt cupiditate vel, quas, fuga voluptates quod pariatur corrupti ducimus debitis sit at commodi optio praesentium iusto quidem. Maiores, omnis!'
        },
        {
          id: 'beamsplitter',
          title: 'Beam Splitter',
          level1:
            'Beginner level stuff Lorem ipsum dolor sit amet consectetur adipisicing elit. Explicabo, ipsa nesciunt cupiditate vel, quas, fuga voluptates quod pariatur corrupti ducimus debitis sit at commodi optio praesentium iusto quidem. Maiores, omnis!',
          level2:
            'Advanced level stuff Lorem ipsum dolor sit amet consectetur adipisicing elit. Explicabo, ipsa nesciunt cupiditate vel, quas, fuga voluptates quod pariatur corrupti ducimus debitis sit at commodi optio praesentium iusto quidem. Maiores, omnis!',
          level3:
            'Master level stuff Lorem ipsum dolor sit amet consectetur adipisicing elit. Explicabo, ipsa nesciunt cupiditate vel, quas, fuga voluptates quod pariatur corrupti ducimus debitis sit at commodi optio praesentium iusto quidem. Maiores, omnis!',
          level4:
            'Wizard level stuff Lorem ipsum dolor sit amet consectetur adipisicing elit. Explicabo, ipsa nesciunt cupiditate vel, quas, fuga voluptates quod pariatur corrupti ducimus debitis sit at commodi optio praesentium iusto quidem. Maiores, omnis!'
        }
      ]
    }
  },
  computed: {
    element () {
      return this.elements.find((element) => {
        return element.id === this.id
      })
    },
    relatedElements () {
      return this.elements.filter((element) => {
        return element.id !== this.id
      })
    }
  }
}
</script>

<style scoped>
</style>
