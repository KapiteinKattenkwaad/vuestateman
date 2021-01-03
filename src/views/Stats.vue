<template>
    <div class="stats">
        <h2>
            Components
        </h2>
        <p>
            There are currently
            {{ countLinks }}
            links
        </p>
        <button @click="removeAllLinks">
            Remove all
        </button>
        <p>
            {{ msg }}
        </p>
    </div>
</template>

<script>
    // @ is an alias to /src
    import { mapGetters, mapMutations, mapActions } from 'vuex'

    export default {
        name: 'Home',
        components: {},
        data() {
            return {
                msg: ''
            }
        },
        computed: {
            ...mapGetters([
                'countLinks',
                'linksUpper'
            ])
        },
        methods: {
            ...mapMutations(['REMOVE_ALL']),
            ...mapActions(['removeAll']),
            removeAllLinks() {
                this.removeAll().then(() => {
                    this.msg = 'they have been removed!'
                })
            }
        },
    }
</script>
