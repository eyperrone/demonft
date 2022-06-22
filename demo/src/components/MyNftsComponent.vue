<template>
  <v-container class="container">
    <app-bar />
    <section class="pa-10" style="height: 85vh">
    <section v-if="errorMessage" style="height: 100%" class="d-flex justify-center align-center">
      <v-card class="pa-15" style="max-width: 35rem">
        <h1 class="text-center">
          Please connect your wallet and refresh the page
        </h1>
      </v-card>
    </section>
    <section style="height: 100%" class="d-flex justify-center align-center" v-if="!errorMessage && loaded">
      <v-row dense style="width: 100%">
        <v-col
          v-for="card in tokens"
          :key="card.tokenUri"
          cols="4"
        >
          <v-card>
            <v-img
              src="../assets/nftSample.jpeg"
              class="white--text align-end"
              gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)"
              height="200px"
            >
              <v-card-title v-text="card.tokenUri"></v-card-title>
            </v-img>

            <v-card-actions class="pa-5">
              <v-spacer></v-spacer>

              <v-btn color="#033856" style="color: white">
               <a :href="card.link" target="_blank" style="color: #fff !important">  View on Etherscan  </a>
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
    </section>
    </section>
  </v-container>
</template>

<script>
import AppBar from "./AppBar.vue";
import { ethers } from "ethers";
import data from "../assets/data.json";
export default {
  name: "MyNftsComponents",
  components: {
    "app-bar": AppBar,
  },
  data() {
    return {
      contract_address: "0xac7062a07a97A6cC04bdBc2A49Cec623aA424c19",
      address: "",
      walletAddress: '',
      errorMessage: false,
      connectedContract: null,
      dialog: false,
      txHash: null,
      tokens: [],
      loaded: false
    };
  },
  computed: {
    tx () {
      return "https://rinkeby.etherscan.io/tx/" + this.txHash
    }
  },
  async mounted() {
    const isLogged = sessionStorage.getItem('logged')
    if (!isLogged) {
      this.errorMessage = true
    }
    try {
      this.walletAddress = window.ethereum.selectedAddress
      const provider = new ethers.providers.Web3Provider(window.ethereum);
      const signer = provider.getSigner();
      this.connectedContract = new ethers.Contract(
        this.contract_address,
        data.abi,
        signer
      );
      const tokens = await this.getTokensDetails()
      this.tokens = tokens
      this.loaded = true
    } catch (e) {
      this.errorMessage = true
      console.log("Connect wallet");
    }
  },
  methods: {
    async getTokensDetails () {
      let tokens = []
      const totalToken = await this.connectedContract.getTotalNft()
      console.log(totalToken)
      const tot = totalToken.toNumber()
      for (let i = 1; i < tot + 1; i++) {
        const tokenOwner = await this.connectedContract.ownerOf(i)
        if (tokenOwner.toUpperCase() == this.walletAddress.toUpperCase() ) {
          const id = i
          const tokenUri = await this.connectedContract.tokenURI(i)
          const link = 'https://rinkeby.etherscan.io/token/0xac7062a07a97a6cc04bdbc2a49cec623aa424c19?a=' +  id
          let token = {}
          token.id = id
          token.tokenUri = tokenUri
          token.link = link
          tokens.push(token)
        }
      }
      return tokens
    }
  }
};
</script>
