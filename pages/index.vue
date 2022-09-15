<template>
  <main>
    <div>
      <b-navbar
        toggleable="lg"
        type="dark"
        variant="dark"
        class="navbar-expand-md fixed-top py-3"
      >
        <b-container>
          <b-navbar-brand href="#"> Roulette </b-navbar-brand>
          <b-navbar-toggle target="nav-collapse" />
          <b-collapse id="nav-collapse" is-nav>
            <!-- Right aligned nav items -->
            <b-navbar-nav class="ml-auto">
              <b-nav-item>
                <NuxtLink to="/"> Home </NuxtLink>
              </b-nav-item>
              <b-nav-item>
                <NuxtLink to="/ShowsList"> TV Show List </NuxtLink>
              </b-nav-item>
              <b-nav-item>
                <NuxtLink to="/Movies"> Movies </NuxtLink>
              </b-nav-item>
              <b-nav-item>
                <NuxtLink to="/MoviesList"> Movies List </NuxtLink>
              </b-nav-item>
              <b-nav-form class="form-inline mt-2 ml-2 mt-md-0">
                <b-form-input
                  size="md"
                  class="form-control mr-sm-2"
                  placeholder="Search"
                />
                <b-button
                  size="md"
                  class="btn btn-success my-2 my-sm-0"
                  type="submit"
                >
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
      <br /><br /><br /><br />
      <h5 class="localsearchmobile" style="font-weight: bold">Local Search</h5>
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
        <b-button
          size="md"
          class="d-none d-sm-block btn btn-success mb-2"
          type="submit"
        >
          Search
        </b-button>
        <b-button
          size="md"
          class="d-md-none d-lg-none btn btn-success mb-2"
          type="submit"
          style="margin-right: 17px; margin-left: 17px"
        >
          Search
        </b-button>
      </b-form>
    </div>
    <b-container>
      <br /><br /><br /><br /><br />
      <h5 style="font-weight: bold">Local Search</h5>
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
      <div class="col-md-4 d-md-none d-lg-none">
        <div
          :style="{
            'background-image': `url(${info.episode_poster})`,
            height: '250px',
            'background-size': 'contain',
            'background-attachment': 'scroll',
            'background-position': 'center center',
            'background-repeat': 'no-repeat',
          }"
        ></div>
      </div>
      <br /><br /><br /><br />
      <b-row>
        <div class="col-md-1"></div>
        <div class="col-md-4">
          <div
            class="poster"
            style="width: 240px; position: absolute; top: 10px; left: 0"
          >
            <div
              class="film-poster"
              style="
                margin-bottom: 0 !important;
                box-shadow: 0 30px 30px rgb(0, 0, 0, 0.5);
                border-radius: 0;
                padding-bottom: 148%;
              "
            >
              <img
                :src="info.episode_poster"
                style="
                  position: absolute;
                  top: 0;
                  left: 0;
                  right: 0;
                  bottom: 0;
                  width: 100%;
                  height: 100%;
                  object-fit: cover;
                "
              />
            </div>
          </div>
        </div>
        <div class="col-md-7">
          <h2
            class="heading-name"
            style="
              font-size: 2.4em;
              line-height: 1.4em;
              font-weight: 600;
              margin-bottom: 15px;
            "
          >
            {{ info.name }} - S{{ info.season }}:E{{ info.Episode }} - "{{
              info.episode_name
            }}"
          </h2>
          <div class="film-stats" style="margin-bottom: 20px">
            <div class="fs-item" style="float: left; margin-right: 30px">
              <span
                class="quality"
                style="
                  font-weight: 400;
                  color: #fff;
                  padding: 3px 8px;
                  border: 1px solid rgba(227, 14, 24, 0.5);
                  border-radius: 3px;
                  background-color: #e30e18;
                "
              >
                <strong>HD</strong>
              </span>
            </div>
            <div class="fs-item" style="float: left; margin-right: 30px">
              <span class="duration"> {{ info.episode_runtime }} min </span>
            </div>
            <div
              class="clearfix"
              style="display: block; clear: both; content: ''"
            ></div>
          </div>
          <div
            class="description"
            style="line-height: 1.6em; margin-bottom: 20px"
          >
            <div class="block mb-2">
              <strong>Overview:</strong>
            </div>
            {{ info.episode_overview }}
          </div>
          <div class="elements" style="margin-bottom: 0">
            <div class="row">
              <div class="col-xl-5 col-lg-6 col-md-8 col-sm-12">
                <div class="row-line">
                  <span class="type"><strong>Released: </strong></span>
                  {{ info.episode_air_date }}
                </div>
              </div>
              <div class="col-xl-6 col-lg-6 col-md-4 col-sm-12">
                <div class="row-line">
                  <span class="type">
                    <strong>Duration: </strong>
                  </span>
                  {{ info.episode_runtime }} min
                </div>
              </div>
              <div class="clearfix"></div>
            </div>
          </div>
          <div v-if="info" class="form-inline">
            <button class="btn btn-dark mt-4 disabled">
              <span style="font-size: 12px">
                <i class="fa fa-check"></i>
                &nbsp;&nbsp;
                <strong>Added to List</strong>
              </span>
            </button>
            &nbsp;&nbsp;
            <form
              action="{% url 'mainapp:mark-as-watched' alpha.episode_id %}"
              method="POST"
            >
              <button class="btn btn-success mt-4" type="submit">
                <span style="font-size: 12px">
                  <i class="fa fa-film"></i>
                  &nbsp;&nbsp;
                  <strong>Mark as watched</strong>
                </span>
              </button>
            </form>
          </div>
          <a v-else href="{% url 'mainapp:add-to-list' top_rated.id %}">
            <button class="btn btn-primary mt-4">
              <span style="font-size: 12px">
                <strong>Add to List</strong>
              </span>
            </button>
          </a>
        </div>
      </b-row>
    </b-container>
  </main>
</template>

<script>
import axios from 'axios'
export default {
  data () {
    return {
      info: {}
    }
  },
  mounted () {
    axios
      .get('http://127.0.0.1:8000/api/shows2')
      .then((response) => { this.info = response.data[0] })
  }
}
</script>

<style scoped>
body {
  background-color: #ededed;
  font-family: "Montserrat", sans-serif;
  font-size: 12px;
}
@media (min-width: 280px) and (max-width: 480px) {
  .localsearchmobile {
    text-align: center;
  }
}
</style>
