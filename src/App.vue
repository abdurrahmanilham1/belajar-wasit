<template>
  <div id="div-1">
    <b-container class="awal">
      <div>
        <div style="color: white">ilham badminton counter</div>
        <b-row class="counter-utama" style="margin: 7px">
          <b-row class="row-1">
            <b-col
              class="satu borad font-custom1"
              @click="angkaSatuTambahSatu()"
            >
              {{ angkaSatu }}
            </b-col>
            <b-col class="dua borad font-custom1" @click="angkaDuaTambahSatu()">
              {{ angkaDua }}</b-col
            >
          </b-row>

          <b-row style="margin-top: 20px">
            <b-col
              class="bertiga borad font-custom2"
              @click="angkaSatuKurangSatu()"
            >
              -1</b-col
            >
            <b-col
              class="berempat borad font-custom2"
              @click="angkaDuaKurangSatu()"
            >
              -1</b-col
            >
          </b-row>
        </b-row>

        <b-row class="row-3">
          <b-col class="satu borad font-custom1" @click="pindahBolaSatu()"
            >{{ orangPertama }}
          </b-col>
          <b-col class="dua borad font-custom1" @click="pindahBolaDua()"
            >{{ orangKedua }}
          </b-col>
          <div class="serve">serve</div>
        </b-row>

        <b-row class="row-4">
          <b-col class="satu borad" @click="$bvModal.show('modal-to-doang')"
            ><b-icon icon="arrow-repeat" font-scale="2"></b-icon>
          </b-col>
          <b-col class="dua borad" @click="arrowGantiFungsi">
            <b-icon icon="arrow-left-right" font-scale="2">{{
              orangPertama
            }}</b-icon></b-col
          >
        </b-row>
      </div>
    </b-container>
    <b-modal
      id="modal-to-doang"
      hide-header
      centered
      ok-title="ya, reset"
      ok-variant="danger"
      cancel-title="tidak jadi"
      @ok="hapusSemua()"
    >
      apakah anda yakin ingin reset
    </b-modal>
  </div>
</template>

<script>
export default {
  name: "App",
  components: {},
  data: function () {
    return {
      angkaSatu: 0,
      angkaDua: 0,
      orangPertama: "1st",
      orangKedua: "",
    };
  },

  methods: {
    angkaSatuTambahSatu() {
      if (this.angkaSatu < 30) {
        return (this.angkaSatu = this.angkaSatu + 1);
      }
    },
    angkaSatuKurangSatu() {
      if (this.angkaSatu > 0) {
        return (this.angkaSatu = this.angkaSatu - 1);
      }
    },
    angkaDuaTambahSatu() {
      if (this.angkaDua < 30) {
        return (this.angkaDua = this.angkaDua + 1);
      }
    },
    angkaDuaKurangSatu() {
      if (this.angkaDua > 0) {
        return (this.angkaDua = this.angkaDua - 1);
      }
    },
    pindahBolaSatu() {
      this.orangKedua = "";
      if (this.orangPertama === "1st") {
        return (this.orangPertama = "2nd");
      } else this.orangPertama = "1st";
    },
    pindahBolaDua() {
      this.orangPertama = "";
      if (this.orangKedua === "1st") {
        return (this.orangKedua = "2nd");
      } else this.orangKedua = "1st";
    },
    hapusSemua() {
      this.angkaSatu = 0;
      this.angkaDua = 0;
      this.orangPertama = "1st";
      this.orangKedua = "";
    },
    arrowGantiFungsi() {
      let sebentar = this.orangPertama;
      this.orangPertama = this.orangKedua;
      this.orangKedua = sebentar;

      let sebentar1 = this.angkaSatu;
      this.angkaSatu = this.angkaDua;
      this.angkaDua = sebentar1;
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@1,300&display=swap");
#div-1 {
  background-color: rgb(18, 153, 32);
  min-height: 100vh;
  font-family: "Montserrat", sans-serif;
}

.satu {
  background-color: rgb(0, 0, 0);
  color: white;
  margin-right: 4px;
  padding-top: 30px;
  padding-bottom: 30px;
  display: flex;
  align-items: center;
  justify-content: center;
}
.dua {
  background-color: rgb(0, 0, 0);
  color: white;
  margin-left: 4px;
  padding-top: 30px;
  padding-bottom: 30px;
  display: flex;
  align-items: center;
  justify-content: center;
}
.bersatu {
  background-color: rgb(0, 0, 0);
  color: white;
  margin-right: 8px;
  display: flex;
  align-items: center;
  justify-content: center;
}
.berdua {
  background-color: rgb(0, 0, 0);
  color: white;
  margin-left: 8px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.bertiga,
.berempat {
  background-color: rgb(0, 0, 0);
  color: white;
  margin-right: 6px;
  margin-left: 6px;
  display: flex;
  align-items: center;
  justify-content: center;
}
.bertiga,
.berempat {
  margin-top: 30px;
  margin-bottom: 30px;
}
.serve {
  color: white;
}
.borad {
  border-radius: 5%;
}
.counter-utama {
  background-color: rgb(10, 80, 10);
  padding: 12px 0px 6px 0px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 5%;
}
.row-3,
.row-4 {
  padding: 30px;
  padding-top: -300px;
}
.font-custom1 {
  font-size: 60px;
  font-family: "Montserrat", sans-serif;
}
.font-custom2 {
  font-size: 20;
  font-family: "Montserrat", sans-serif;
}
</style>
