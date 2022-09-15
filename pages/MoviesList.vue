<template>
  <main>
    <div>
      <b-navbar toggleable="lg" type="dark" variant="dark" class="navbar-expand-md fixed-top py-3">
        <b-container>
          <b-navbar-brand href="#">
            Roulette
          </b-navbar-brand>
          <b-navbar-toggle target="nav-collapse" />
          <b-collapse id="nav-collapse" is-nav>
            <!-- Right aligned nav items -->
            <b-navbar-nav class="ml-auto">
              <b-nav-item>
                <NuxtLink to="/">
                  Home
                </NuxtLink>
              </b-nav-item>
              <b-nav-item>
                <NuxtLink to="/ShowsList">
                  TV Show List
                </NuxtLink>
              </b-nav-item>
              <b-nav-item>
                <NuxtLink to="/Movies">
                  Movies
                </NuxtLink>
              </b-nav-item>
              <b-nav-item>
                <NuxtLink to="/MoviesList">
                  Movies List
                </NuxtLink>
              </b-nav-item>
              <b-nav-form class="form-inline mt-2 ml-2 mt-md-0">
                <b-form-input size="md" class="form-control mr-sm-2" placeholder="Search" />
                <b-button size="md" class="btn btn-success my-2 my-sm-0" type="submit">
                  Search
                </b-button>
              </b-nav-form>
              <div class="form-inline mt-2 ml-4 mt-md-0">
                <a>
                  <b-button size="md" class="btn btn-danger my-2 my-sm-0">
                    Logout
                  </b-button>
                </a>
              </div>
            </b-navbar-nav>
          </b-collapse>
        </b-container>
      </b-navbar>
    </div>
    <div class="d-md-none d-lg-none">
      <br><br><br><br>
      <h5 class="localsearchmobile" style="font-weight:bold">
        Local Search
      </h5>
      <b-form size="md" class="form-inline">
        <b-col cols="12">
          <b-form-group class="mb-2">
            <b-form-input class="form-control" placeholder="TV Show Name" />
          </b-form-group>
        </b-col>
        <b-col cols="6">
          <b-form-group class="mb-2 mx-sm-3 mb-2">
            <b-form-input placeholder="Season No." />
          </b-form-group>
        </b-col>
        <b-col cols="6">
          <b-form-group class="mb-2 mx-sm-3 mb-2">
            <b-form-input placeholder="Episode No." />
          </b-form-group>
        </b-col>
        <b-button size="md" class="d-none d-sm-block btn btn-success mb-2" type="submit">
          Search
        </b-button>
        <b-button size="md" class="d-md-none d-lg-none btn btn-success mb-2" type="submit" style="margin-right:17px;margin-left:17px;">
          Search
        </b-button>
      </b-form>
    </div>
    <b-container>
      <br><br><br><br><br>
      <h5 style="font-weight: bold;">
        Local Search
      </h5>
      <b-row>
        <b-form inline>
          <b-col>
            <b-form-group class="mb-2">
              <b-form-input class="form-control" placeholder="TV Show Name" />
            </b-form-group>
          </b-col>
          <b-col>
            <b-form-group class="mx-sm-3 mb-2">
              <b-form-input class="form-control" placeholder="Season No." />
            </b-form-group>
          </b-col>
          <b-col>
            <b-form-group class="mx-sm-3 mb-2">
              <b-form-input class="form-control" placeholder="Episode No." />
            </b-form-group>
          </b-col>
          <b-button type="submit" class="btn btn-primary mb-2">
            Search
          </b-button>
        </b-form>
      </b-row>
      <div id="info">
        <div style="padding-top:150px; padding-left:30px;padding-right: 30px;">
          <b-row>
            <div v-for="inf in info" :key="inf.id" class="col-md-2 pb-5 col-sm-4 col-xs-6">
              <center><img :src="inf.poster" class="img-fluid" style="height: 240px;width:auto"></center>
              <p class="text-center pt-2">
                {{ inf.rating }} &nbsp; {{ inf.first_air_date }}
              </p>
              <p class="text-center" style="font-size:13px;line-height:1.3em;margin-top:-15px;color:black">
                <strong>{{ inf.name }}</strong>
              </p>
            </div>
          </b-row>
        </div>
      </div>
    </b-container>
  </main>
</template>

<script>
import axios from 'axios'
export default {
  data () {
    return {
      info: null
    }
  },
  // head () {
  //   return {
  //     link: [
  //       {
  //         rel: 'stylesheet',
  //         href: 'https://fonts.googleapis.com/css2?family=Montserrat&display=swap'
  //       }
  //     ]
  //   }
  // },
  mounted () {
    axios.get('http://127.0.0.1:8000/api/movies-list').then(response => (this.info = response.data))
  }
}
</script>

<style scoped>
body{
  background-color: #ededed;
  font-family: 'Montserrat', sans-serif;
  font-size:12px;
}
@media (min-width: 280px) and (max-width: 480px) {
  .localsearchmobile {text-align:center}
}
</style>
