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
    <section style="height: 100%" class="d-flex justify-center align-center" v-else>
      <v-row dense style="width: 100%">
        <v-col
          v-for="card in tokens"
          :key="card.title"
          :cols="card.flex"
        >
          <v-card>
            <v-img
              src="../assets/nftSample.jpeg"
              class="white--text align-end"
              gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)"
              height="200px"
            >
              <v-card-title v-text="card.title"></v-card-title>
            </v-img>

            <v-card-actions class="pa-5">
              <v-spacer></v-spacer>

              <v-btn color="#033856" style="color: white" @click="buy(card.id)">
                Buy Now
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
    </section>
    </section>
    <v-row justify="center">
    <v-dialog
      v-model="dialog"
      max-width="490"
    >
      <v-card>
        <v-card-title class="text-h5">
         <b> Operation successfully </b>
        </v-card-title>

        <v-card-text>
          Please check the status of transactions on <a :href="tx" target="_blank"> <b style="color:#033856"> <u> Ethereum etherscan </u> </b> </a>
          <br> <br>
          Trasnaction Hash: <i> {{ txHash }} </i>
        </v-card-text>

        <v-card-actions>
          <v-spacer></v-spacer>

          <v-btn
            color="green darken-1"
            text
            @click="dialog = false"
          >
            Close
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-row>
  </v-container>
</template>

<script>
import AppBar from "./AppBar.vue";
import { ethers } from "ethers";
import data from "../assets/data.json";
export default {
  name: "CollectionsComponent",
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
      tokens: [
        { id: 1, title: 'NFT Raro', flex: 4 },
        { id: 2, title: 'NFT Premium', flex: 4 },
        { id: 3, title: 'NFT Comune', flex: 4 },
      ],

    };
  },
  computed: {
    tx () {
      return "https://rinkeby.etherscan.io/tx/" + this.txHash
    }
  },
  async mounted() {
    this.walletAddress = window.ethereum.selectedAddress
    if (!this.walletAddress) {
      this.errorMessage = true
    }
    try {
      const provider = new ethers.providers.Web3Provider(window.ethereum);
      const signer = provider.getSigner();
      this.connectedContract = new ethers.Contract(
        this.contract_address,
        data.abi,
        signer
      );
    } catch (e) {
      this.errorMessage = true
      console.log("Connect wallet");
    }
  },
  methods: {
    async buy (id) {
      const token = this.tokens.find(token => token.id == id )
      const options = { value: 10000000 }
        const txHash= await this.connectedContract.mintNFT(this.walletAddress, token.title, options)
        this.txHash = txHash.hash
       console.log(this.txHash)
       this.dialog = true
    },
    
  }
};
</script>
