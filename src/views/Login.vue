<template>
    <div class=" container columns mx-auto my-6">
        <div class="column is-two-fifths mx-6 my-6">
            <div class="title is-1">
                <h2>Facilidade e a melhor experiência do mercado.</h2>
            </div>
            <div class="content is-medium">
                <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla accumsan, metus ultrices eleifend gravida, nulla nunc varius lectus, nec rutrum justo nibh eu lectus. Ut vulputate semper dui. Fusce erat odio, sollicitudin vel erat vel, interdum mattis neque. Sub<sub>script</sub> works as well!</p>
            </div>
        </div>
        <form class="box column is-two-fifths my-6 mx-6">
            <figure class="image is-128x128 my-6 mx-auto">
              <img src="../img/image 1.png">
            </figure>
            <div class="field">
              <label class="label">Email</label>
              <div class="control">
                <input class="input" type="email" placeholder="e.g. alex@example.com" v-model="dados.emal">
              </div>
            </div>
            <div class="field">
              <label class="label">Password</label>
              <div class="control">
                <input class="input" type="password" placeholder="********" v-model="dados.senha">
              </div>
            </div>
            <router-link to="/" class="button is-success">Entrar</router-link>
            <div class="field my-4">
                <div class="is-flex is-justify-content-center">
                    <a href="">Esqueci minha senha</a>
                    <span class="mx-4">|</span> 
                    <a href="">Esqueci meu usuário</a>
                </div>
                <div class="is-flex is-justify-content-center my-4 mx-6">
                    <p>
                        Não possui uma conta? <a href="">Cadastre-se aqui</a>
                    </p>
                </div>
            </div>
        </form>
        <!-- <div class="modal">
            <div class="modal-background"></div>
            <div class="modal-content is-flex">
              <figure class="image is-128x128">
                <img src="https://bulma.io/images/placeholders/256x256.png">
              </figure>
              <form class="box">
                <div class="field">
                  <label class="label">Email</label>
                  <div class="control">
                    <input class="input" type="email" placeholder="e.g. alex@example.com">
                  </div>
                </div>

                <div class="field">
                  <label class="label">Password</label>
                  <div class="control">
                    <input class="input" type="password" placeholder="********">
                  </div>
                </div>

                <button class="button is-primary">Sign in</button>
              </form>
            </div>
            <button class="modal-close is-large" aria-label="close"></button>
        </div> -->
    </div>
</template>

<script>
export default {
    name: 'theLogin',
    data () {
      return {
          dados: {
            emal: '',
            senha: ''
        }
      }
    }
}
</script>

<style scoped>
    *{
        font-family: Arial, Helvetica, sans-serif;
    }
    /* .conteiner{
        display: grid;
        grid-template-columns: 1fr 45%;
        margin: 50px auto;
        border: 1px solid #000;
    } */
</style>