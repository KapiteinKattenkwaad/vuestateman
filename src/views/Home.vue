<template>
    <div class="home">
        <div class="left">
            <h2>
                {{ title }}
            </h2>
          <form @submit.prevent="addLink">
            <input class="input-link" type="text" v-model="newLink"  placeholder="Add a link">
          </form>

          <ul v-for="link in links" :key="link.index">
            <li >
              {{ link }}
              <button @click="removeLinks(index)">
                Delete
              </button>
            </li>

          </ul>

        </div>
        <div class="right">
         <Stats />
        </div>
    </div>
</template>

<style>
  .home {
    display: flex;
  }
  .left, .right {
    width: 50%;
    padding: 4rem 2rem 2rem 2rem;
    min-height: 100vh;
  }
  .left {
    background: lightpink;
  }
  .right {
    background: lightblue;
  }
  li, input {
    list-style: none;
    background: white;
    padding: 6px 12px;
    box-shadow: 5px 5px 5px rgba(0,0,0,.15);
  }

  input {
    outline: none;
    display: block;
    width: calc(100% - 4rem) ;
    border-bottom: 1px solid lightblue;
    margin: 2rem auto;
  }
</style>

<script>
    // @ is an alias to /src
    import {mapState, mapMutations, mapActions} from 'vuex'
    import Stats from './Stats'
    export default {
        name: 'Home',
      data() {
        return {
          newLink: ''
        }
      },
        components: {
          Stats
        },
        computed: {
            ...mapState([
                'title',
                'links'
            ])
        },
      methods: {
       ...mapMutations([
               'ADD_LINK',
               'REMOVE_LINK'
       ]),
        ...mapActions([
                'removeLinks'
        ]),
        removeLinks(link) {
          this.removeLinks(link)
        },
        addLink() {
         this.ADD_LINK(this.newLink)
          this.newLink = ''
        }
      },
    }
</script>
