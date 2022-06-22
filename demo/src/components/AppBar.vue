<template>
     <v-app-bar class="mt-10" elevation="0" style="background: none">
      <v-toolbar-title>
        <router-link to="/">
          <img src="../assets/logo.png" alt="" height="80" />
        </router-link>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-toolbar-title class="mr-8">
        <router-link to="/about"> About </router-link>
      </v-toolbar-title>
      <v-toolbar-title class="mr-8">
        <router-link to="/collections"> Collections </router-link>
      </v-toolbar-title>
       <v-toolbar-title v-if="logged" class="mr-8">
       <router-link to="/myNfts"> My NFTs  </router-link>
      </v-toolbar-title>
      <v-toolbar-title class="mr-8">
        <router-link to="/FAQs"> FAQs </router-link>
      </v-toolbar-title>
      <v-toolbar-title>
        <v-btn v-if="!logged && metamaskInstalled" color="#033856" style="color: white" @click="login" dark>
          Connect wallet
        </v-btn>
        <v-btn v-if="logged && metamaskInstalled" color="#033856" style="color: white">
          {{ walletAddress }}
        </v-btn>
         <v-btn v-if="!metamaskInstalled" color="#033856" style="color: white" @click="install" dark>
          Install Metamask
        </v-btn>
      </v-toolbar-title>
    </v-app-bar>
</template>

<script>


export default {
  data () {
    return {
      isMetamaskSupported: false,
      address: '',
      isLogged: false
    }
  },
    computed: {
    logged () { 
        // let logged = sessionStorage.getItem('logged')
        // if (logged && this.isLogged) {
        //     return true
        // } else {
        //     return false
        // }

        return this.isLogged
    },
    metamaskInstalled () {
       if (typeof window.ethereum !== 'undefined') {
        return true
      } else {
        return false
      }
    },
    walletAddress () {
      return this.address
    }
    },
    mounted () {
      if (typeof window.ethereum !== 'undefined') {
        console.log('Metamask is installed')
        if (window.ethereum.selectedAddress) {
          sessionStorage.setItem('logged', true)
          this.address = window.ethereum.selectedAddress
          this.isLogged = true
        }
      }

      window.ethereum.on('accountsChanged', (accounts) => {
        this.address = accounts[0]
        if (!this.address) {
          this.isLogged = false
          // window.location.reload()
        }
      })
    },
    methods: {
   async login() {
      sessionStorage.setItem('logged', true)
      const accounts = await window.ethereum.request({ method: 'eth_requestAccounts' })
      this.address = accounts[0]
      this.isLogged = true
      // window.location.reload()
    },
      logout() {
      sessionStorage.clear()
      // window.location.reload()
    },
    install () {
      window.open('https://metamask.io/', '_blank')
    }
  }
}
</script>
