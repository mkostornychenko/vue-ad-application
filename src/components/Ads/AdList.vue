<template>
    <v-container>
        <v-layout row v-if="!loading">
            <v-flex xs12 sm6 offset-sm3>
                <h1 class="text--secondary mb-3">My Ads</h1>

                <v-card class="elevation-10 mb-2" v-for="ad in myAds" :key="ad.id">
                    <v-layout row>
                        <v-flex xs4>
                            <v-img :src="ad.imgSrc" height="100%"></v-img>
                        </v-flex>
                        <v-flex xs8>
                            <v-card-text>
                                <h2 class="text--primary">{{ ad.title }}</h2>
                                <p>{{ ad.description }}</p>
                            </v-card-text>
                            <v-card-actions>
                                <v-spacer></v-spacer>
                                <v-btn class="info" :to="'/ad/' + ad.id">Open</v-btn>
                            </v-card-actions>
                        </v-flex>
                    </v-layout>
                </v-card>
                <div v-if="myAds.length === 0" class="text-xs-center">
                    <p>You have no ads</p>
                </div>
            </v-flex>
        </v-layout>
        <div v-else>
            <v-container>
                <v-layout row>
                    <v-flex xs12 class="text-xs-center pt-5">
                        <v-progress-circular :size="100" :width="7" color="primary" indeterminate></v-progress-circular>
                    </v-flex>
                </v-layout>
            </v-container>
        </div>
    </v-container>
</template>

<script>
export default {
  computed: {
    myAds () {
      return this.$store.getters.myAds
    },
    loading () {
      return this.$store.getters.loading
    }
  }
}
</script>

<style scoped>

</style>
