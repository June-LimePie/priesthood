<template>
    <v-container class="main-content">
      <v-row>
        <v-col cols="12">
            <br/>
            <br/>
        </v-col>
        <v-col cols="12">
            <h1>Welcome to Priesthood Equality</h1>
            <v-card flat>
                <v-card-title>What is Priesthood Equality?</v-card-title>
                <v-card-text>
                    The Church of Jesus Christ of Latter Day Saints, more commonly known as "Mormon" or "LDS"
                    church, is a religion that believes in the restoration of the priesthood.  The priesthood is the 
                    power that christ gave to his apostles to act in his name.  The LDS church believes  that this power
                    was lost after the death of the apostles and was restored to the earth by heavenly messengers.  The
                    church also believes that this power should only be available to men, specifically heterosexual cis men.
                    <br/><br/>
                    This website is a tool to help you experience the power of the priesthood.  You can use it to ordain
                    yourself or others to the priesthood.  You can also use it to ordain yourself or others to the office
                    of deacon, teacher, priest, elder, or high priest. 
                    <br/><br/>
                    This website is not affiliated with the Church of Jesus Christ of Latter Day Saints.  It is a tool
                    created by me, June, a transgender member of the church to help people experience the power of the priesthood.
                    <br/><br/>
                    If you have any questions about the site or would like to report a bug, please email me at <a href="mailto:admin@priesthoodequality.com">admin@preisthoodequality.com</a> 

                </v-card-text>
            </v-card>
        </v-col>
        <v-col cols="12">
          <p>Enter your name and choose an ordination type to begin:</p>
        </v-col>
        <v-col cols="12">
          <v-text-field
            v-model="name"
            label="Your Name"
            outlined
          ></v-text-field>
        </v-col>
        <v-col cols="12">
          <v-select
              :items="ordinationTypes"
              v-model="selectedOrdination"
              label="Ordination Type"
          ></v-select>
        </v-col>
        <v-col cols="12">
          <v-btn color="deep-purple accent-4" dark @click="generatePrayer">Generate Ordination</v-btn>
        </v-col>
        <v-col cols="12" lg="6" v-if="prayer">
          <v-col cols="12" v-if="prayer">
            <v-card color="deep-purple accent-4" dark>
              <v-card-title>Preparing for Your Ordination:</v-card-title>
              <v-card-text>To prepare for your ordination make sure that you are in a calm environment where you can feel the spirit.  When you are ready, press the play button and you will hear your ordination prayer.  The rush you feel at the end is the POWER entering your body.  Go out and exercise your preisthood!</v-card-text>
            </v-card>
          </v-col>
        </v-col>
        <v-col cols="12" lg="6" v-if="prayer">
          <v-col cols="12" v-if="prayer">
            <v-card color="deep-purple accent-4" dark>
              <v-card-title>Your Ordination:</v-card-title>
              <v-btn 
                class="mx-auto d-block mb-4"
                color="deep-purple accent-4"
                dark
                fab
                large
                @click="speakPrayer"
                >
                    <v-icon large>mdi-play</v-icon>
                </v-btn>
              <v-card-text>{{ prayer }}</v-card-text>
            </v-card>
          </v-col>
        </v-col>
      </v-row>
    </v-container>
  </template>
  
  <script>

  
  export default {
    data() {
      return {
        name: '',
        dialog: false,
        recipient: '',
        selectedOrdination: null,
        ordinationTypes: [
          'Aaronic Priesthood - Deacon',
          'Aaronic Priesthood - Teacher',
          'Aaronic Priesthood - Priest',
          'Aaronic Priesthood - Priestess',
          'Melchizedek Priesthood - Elder',
          'Melchizedek Priesthood - High Priest',
          'Melchizedek Priesthood - High Priestess',
        ],
        ordinationLookup: {
          'Aaronic Priesthood - Deacon': { priesthood: 'Aaronic Priesthood', office: 'Deacon' },
          'Aaronic Priesthood - Teacher': { priesthood: 'Aaronic Priesthood', office: 'Teacher' },
          'Aaronic Priesthood - Priest': { priesthood: 'Aaronic Priesthood', office: 'Priest' },
          'Aaronic Priesthood - Priestess': { priesthood: 'Aaronic Priesthood', office: 'Priestess' },
          'Melchizedek Priesthood - Elder': { priesthood: 'Melchizedek Priesthood', office: 'Elder' },
          'Melchizedek Priesthood - High Priest': { priesthood: 'Melchizedek Priesthood', office: 'High Priest' },
          'Melchizedek Priesthood - High Priestess': { priesthood: 'Melchizedek Priesthood', office: 'High Priestess' },
        },
        prayer: '',
      }
    },
    methods: {
      generatePrayer() {
        let ordination = this.ordinationLookup[this.selectedOrdination];
        this.prayer = `${this.name}, by the authority of the Holy ${ordination.priesthood} which I hold, and in the name of Jesus Christ, I lay my hands upon your head to confirm you and ordain you to the office of ${ordination.office} in the ${ordination.priesthood}, and confer upon you all the rights, powers, and authority pertaining to this office and calling, in the name of Jesus Christ, Amen.`;
      },
      speakPrayer() {
            if (window.responsiveVoice) {
            window.responsiveVoice.speak(this.prayer);
           }
        }
    },
  }
  </script>
  
  <style scoped>
  h1, h2 {
    color: #673ab7; /* deep-purple */
  }
  p, .v-text-field, .v-select, .v-btn {
    color: #651fff; /* deep-purple accent-4 */
  }
  .main-content {
    min-height: 90vh;
  }
  </style>
  