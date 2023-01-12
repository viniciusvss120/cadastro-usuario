<template>
  <div class="home">
      <header>
        <Menu />
      </header>
      <Tabela class="tabela">
         <div class="container">
          <div class="my-5 mx-5 is-flex is-justify-content-space-between is-align-items-center is-flex-wrap-wrap">
            <div class="is-flex is-align-items-center box">
              <div class="field">
                <label class="label">Name</label>
                <div class="control">
                  <input class="input" type="text" placeholder="Vinicius Silva Souza" v-model="filtro.nome">
                </div>
              </div>

              <div class="field ml-6">
                <label class="label">Cidade</label>
                <div class="control">
                  <input class="input" type="text" placeholder="cidade" v-model="filtro.cidade">
                </div>
              </div>
              <button class="button is-success is-medium  mx-5" @click="filterUser()">Buscar</button>
            </div> 
            <button class="button is-medium edit" @click="newUser()">
              Novo Usuário
            </button>
          </div>
          <div class="table-container">
            <table class="table is-bordered is-hoverable is-fullwidth my-6">
                <thead>
                    <tr>
                        <th>Id</th>
                        <th>Nome</th>
                        <th>Cidade</th>
                        <th>Email</th>
                        <th>Telefone</th>
                        <th>viws</th>
                    </tr>
                </thead>
                <tbody>
                    <tr 
                        v-for="user in usuarios" 
                        :key="user.nome"
                    >
                        <th @click="activeModal(user.id)">{{user.id}}</th>
                        <th @click="activeModal(user.id)">{{user.nome}}</th>
                        <td @click="activeModal(user.id)">{{user.cidade}}</td>
                        <td @click="activeModal(user.id)">{{user.email}}</td>
                        <td @click="activeModal(user.id)">{{user.telefone}}</td>
                        <td>
                          <button class="button edit" @click="activeSalvar(user.id)">Editar</button>
                        </td>
                    </tr>
                </tbody>
            </table>
          </div>
        </div>
      </Tabela>
    
      <Modal
        :showModal="showModal"
      >
        <div class="modal-background" @click="desativarModal()"></div>
        <div class="modal-content">
            <form class="box">
              <div class="card-content">
                <div class="media">
                  <div class="media-left">
                    <figure class="image is-48x48">
                      <img src="https://bulma.io/images/placeholders/96x96.png" alt="Placeholder image">
                    </figure>
                  </div>
                  <div 
                    class="media-content"
                  >
                    <p class="title is-4">{{modalUser.nome}}</p>
                    <p class="subtitle is-6">{{modalUser.email}}</p>
                  </div>
                </div>  
              </div>

              <div class="field">
                <div class="control">
                  <input class="input" type="hidden" v-model="dadosUser.id">
                </div>
              </div>

              <div class="field">
                <label class="label">Nome</label>
                <div class="control">
                  <input class="input" type="text" placeholder="Vinicius Silva Souza" v-model="dadosUser.nome">
                </div>
              </div>

              <div class="field">
                <label class="label">Cidade</label>
                <div class="control">
                  <input class="input" type="text" placeholder="Jaru" v-model="dadosUser.cidade">
                </div>
              </div>

              <div class="field">
                <label class="label">Email</label>
                <div class="control">
                  <input class="input" type="email" placeholder="e.g. alex@example.com" v-model="dadosUser.email">
                </div>
              </div>

              <div class="field">
                <label class="label">Telefone</label>
                <div class="control">
                  <input class="input" type="text" placeholder="69993062435" v-model="dadosUser.telefone">
                </div>
              </div>

              <button class="button mr-5 my-2 cancelar">Fechar</button>
              <!-- <button 
                class="button my-2 edit"
                v-show="!salvar" 
                >
                  Editar
              </button> -->
              <button 
                class="button my-2 edit"
                v-show="salvar"
                @click="editUser(dadosUser.id)"  
                >
                  Salvar
              </button>
              <button class="modal-close is-large" aria-label="close" @click="desativarModal()"></button>
        </form>
        </div>
      </Modal>

      <CreateUser
        :showModal="showModalCreate"
      >
        <div class="modal-background" @click="desativarModal()"></div>
            <div class="modal-content">
              <form class="box">
                <div class="card-content">
                  <div class="media">
                    <div class="media-left">
                      <figure class="image is-48x48">
                        <img src="https://bulma.io/images/placeholders/96x96.png" alt="Placeholder image">
                      </figure>
                    </div>
                    <div 
                      class="media-content"
                    >
                      <p class="title is-4">Usuário</p>
                      <p class="subtitle is-6">usuario@gmail.com</p>
                    </div>
                  </div>  
                </div>
                
                <div class="field">
                  <label class="label">Id</label>
                  <div class="control">
                    <input class="input" type="text" disabled name="id" :value="newIdUser">
                  </div>
                </div>

                <div class="field">
                  <label class="label">Nome</label>
                  <div class="control">
                    <input class="input" type="text" placeholder="Vinicius Silva Souza" v-model="dadosUser.nome">
                  </div>
                </div>

                <div class="field">
                  <label class="label">Cidade</label>
                  <div class="control">
                    <input class="input" type="text" placeholder="Jaru" v-model="dadosUser.cidade">
                  </div>
                </div>
          
                <div class="field">
                  <label class="label">Email</label>
                  <div class="control">
                    <input class="input" type="email" placeholder="e.g. alex@example.com" v-model="dadosUser.email">
                  </div>
                </div>
          
                <div class="field">
                  <label class="label">Telefone</label>
                  <div class="control">
                    <input class="input" type="text" placeholder="69993062435" v-model="dadosUser.telefone">
                  </div>
                </div>
                <button class="button mr-5 my-2 cancelar">Fechar</button>
                <!-- <button 
                  class="button my-2 edit"
                  v-show="!salvar" 
                  >
                    Editar
                </button> -->
                <button 
                  class="button my-2 edit"
                  v-show="salvar" 
                  @click="newUser()" 
                  >
                    Salvar
                </button>
                <button class="modal-close is-large" aria-label="close" @click="desativarModal()"></button>
              </form>
            </div>
      </CreateUser>
  </div>
</template>

<script>
import Menu from '@/components/Menu.vue'
import Tabela from '@/components/Tabela.vue'
import Modal from '@/components/Modal.vue'
import CreateUser from '@/components/CreateUser.vue'

export default {
  name: 'HomeView',
  components: {
    Menu,
    Tabela,
    Modal,
    CreateUser
  },
  data () {
    return {
      modal: false,
      createModal: false,
      salvar: false,
      usuarios: [
        {
            id: 1,
            nome: 'Vinicius Silva Souza',
            cidade: 'Jaru',
            email: 'vinicius100@live.com',
            telefone: '69993062435'
        },
        {
            id: 2,
            nome: 'Lucia Silva Oliver',
            cidade: 'Jaru',
            email: 'vinicius100@live.com',
            telefone: '69993062435'

        },
        {
            id: 3,
            nome: 'Luiz Miguel Silva Souza',
            cidade: 'Jaru',
            email: 'vinicius100@live.com',
            telefone: '69993062435'

        },
      ],
      dadosUser: {
        id: null,
        nome: '',
        cidade: '',
        email: '',
        telefone: ''
      },
      filtro: {
        nome: '',
        cidade: ''
      },
      modalUser: {}
    }
  },
  computed: {
        showModal(){
            const modal = this.modal ? 'is-active' : undefined
            return modal
        },
        showModalCreate(){
            const modal = this.createModal ? 'is-active' : undefined
            return modal
        },
        newIdUser() {
          const id = this.usuarios.length + 1

          return id
        }
  },
  created(){
      // await this.enviarUsers()
      // await this.receberUsers()
      this.listUser()

  },
  methods: {
    // enviarUsers(){
    //   const users = JSON.stringify(this.usuarios)

    //   localStorage.setItem('usuarios', users)
    // },
    // receberUsers(){
    //   const users = localStorage.getItem('usuarios')

    //   const converteUsers = JSON.parse(users)

    //   this.users = converteUsers
    //   console.log(users)
    // },
    listUser(){
     const user = localStorage.getItem('usuarios')

      const newUser = JSON.parse(user)
      this.usuarios.push(newUser)

    },
    filterUser(){
      console.log(this.filtro)
      const user = this.usuarios.find(index => index.nome || index.cidade === this.filtro.nome || this.filtro. cidade)

      console.log(user)
    },
    activeModal(id){
      this.modal = true
       if(this.salvar) {
        this.salvar = false
       }  
       
      this.findUser(id)
    },
    
    findUser(id){
      const user = this.usuarios.find(index => index.id === id)

      this.modalUser = user     
      Object.assign(this.dadosUser, user)
    },

    editUser(id){
      const user = this.usuarios.find(index => index.id === id)

      if(user != undefined){
        Object.assign(user,this.dadosUser)

        console.log(user)
        localStorage.setItem('usuarios', JSON.stringify(user))
      }
    },
    newUser(){
      this.createModal = true
      this.salvar = true

      let novoUser = {
        id: this.newIdUser,
        nome: this.dadosUser.nome,
        cidade: this.dadosUser.cidade,
        email: this.dadosUser.email,
        telefone: this.dadosUser.telefone
      }


      localStorage.setItem('usuarios', JSON.stringify(novoUser))
    },
    activeSalvar(id) {
      this.modal = true
      this.salvar = true
      this.findUser(id)
    },

    desativarModal() {
      this.modal = false
      this.createModal = false
    },
  }

}
</script>

<style scoped>
    /* .tabela{
      width: 100%;
    } */
    .cancelar{
        color: #fff;
        background: red;
    }
    .edit{
      font-weight: 500;
      background: #00F700;
    }

  /* *{
    margin: 0px;
  } */
</style>
