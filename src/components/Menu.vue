<template>
    <div>
       <nav class="navbar box is-full" role="navigation" aria-label="main navigation">
            <div class="navbar-brand">
              <a class="navbar-item" href="https://bulma.io">
                <img src="../img/image 1.png" width="112" height="28">
              </a>

              <a role="button" :class="`navbar-burger ${menu}`" @click="showMenu()" aria-label="menu" aria-expanded="false" data-target="navbarBasicExample">
                <span aria-hidden="true"></span>
                <span aria-hidden="true"></span>
                <span aria-hidden="true"></span>
              </a>
            </div>
            <div class="navbarBasicExemple" v-show="!menuHamburgue">
              <div class="navbar-start">
                <router-link to="/" class="navbar-item">
                  Home
                </router-link>
              </div>
              <div class="navbar-start">
                <router-link to="/" class="navbar-item">
                  Sobre
                </router-link>
              </div>
              <div class="navbar-start">
                <router-link to="/" class="navbar-item">
                  Contato
                </router-link>
              </div>
            </div>
            <div id="navbarBasicExample" class="navbar-menu">
              <div class="navbar-start">
                <router-link to="/" class="navbar-item">
                  Home
                </router-link>
                <router-link to="/sobre" class="navbar-item">
                  Sobre
                </router-link>
                <router-link to="/contato" class="navbar-item">
                  Contato
                </router-link>
              </div>
                <!-- <div class="navbar-item has-dropdown is-hoverable">
                  <a class="navbar-link">
                    More
                  </a>

                  <div class="navbar-dropdown">
                    <a class="navbar-item">
                      About
                    </a>
                    <a class="navbar-item">
                      Jobs
                    </a>
                    <a class="navbar-item">
                      Contact
                    </a>
                    <hr class="navbar-divider">
                    <a class="navbar-item">
                      Report an issue
                    </a>
                  </div>
                </div>
              </div> -->

              <div class="navbar-end">
                <div class="navbar-item">
                  <div class="buttons">
                    <router-link to="/login" class="button edit">
                      Log in
                    </router-link>
                  </div>
                </div>
              </div>
            </div>
        </nav>
        
    </div>
</template>

<script>
export default {
    name: 'theMenu',
    data () {
      return {
        menuHamburgue: true
      }
    },
    computed: {
      menu() {
        const menuHamburgue = this.menuHamburgue ? '' : 'is-active'

        return menuHamburgue
      }
    },
    methods: {
      showMenu() {
        this.menuHamburgue = !this.menuHamburgue
      }
    }
}
</script>

<style scoped>
    .edit{
      font-weight: 500;
      background: #00F700;
    }
</style>