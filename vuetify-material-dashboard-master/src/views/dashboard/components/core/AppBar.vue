<template>
  <v-app-bar
    id="app-bar"
    absolute
    app
    color="transparent"
    flat
    height="75"
  >
    <v-btn
      class="mr-3"
      elevation="1"
      fab
      small
      @click="setDrawer(!drawer)"
    >
      <v-icon v-if="value">
        mdi-view-quilt
      </v-icon>

      <v-icon v-else>
        mdi-dots-vertical
      </v-icon>
    </v-btn>

    <v-toolbar-title
      class="hidden-sm-and-down font-weight-light"
      v-text="$route.name"
    />

    <v-spacer />
    <!--
    <v-text-field
      :label="$t('search')"
      color="secondary"
      hide-details
      style="max-width: 165px;"
    >
      <template
        v-if="$vuetify.breakpoint.mdAndUp"
        v-slot:append-outer
      >
        <v-btn
          class="mt-n2"
          elevation="1"
          fab
          small
        >
          <v-icon>mdi-magnify</v-icon>
        </v-btn>
      </template>
    </v-text-field> -->

    <div class="mx-3" />
    <div class="mx-3" />
  </v-app-bar>
</template>

<script>
// Components
// import { VHover, VListItem } from 'vuetify/lib'

// Utilities
  import { mapState, mapMutations } from 'vuex'

  export default {
    name: 'DashboardCoreAppBar',

    components: {
    // AppBarItem: {
    //   render (h) {
    //     return h(VHover, {
    //       scopedSlots: {
    //         default: ({ hover }) => {
    //           return h(
    //             VListItem,
    //             {
    //               attrs: this.$attrs,
    //               class: {
    //                 'black--text': !hover,
    //                 'white--text secondary elevation-12': hover,
    //               },
    //               props: {
    //                 activeClass: '',
    //                 dark: hover,
    //                 link: true,
    //                 ...this.$attrs,
    //               },
    //             },
    //             this.$slots.default,
    //           )
    //         },
    //       },
    //     })
    //   },
    // },
    },

    props: {
      value: {
        type: Boolean,
        default: false,
      },
    },

    data: () => ({
      notifications: [
        'Mike John Responded to your email',
        'You have 5 new tasks',
        "You're now friends with Andrew",
        'Another Notification',
        'Another one',
      ],
      menu: false,
    }),

    computed: {
      ...mapState(['drawer']),
    },
    mounted () {
      this.darkMode()
    },

    methods: {
      ...mapMutations({
        setDrawer: 'SET_DRAWER',
      }),
      toggle_dark_mode: function () {
        localStorage.setItem('dark_theme', this.$vuetify.theme.dark.toString())
      },
      darkMode () {
        const theme = localStorage.getItem('dark_theme')
        if (theme) {
          if (theme === 'true') {
            this.$vuetify.theme.dark = true
          } else {
            this.$vuetify.theme.dark = false
          }
        }
      },
    },
  }
</script>
