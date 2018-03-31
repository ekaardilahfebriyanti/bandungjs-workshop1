<template>
  <div class="hello">
  <button @click="showName()">Toggle</button>
    <h1 v-if="isNameShown">Hello, Nama Saya <span v-html="firstName"></span> {{lastName}}</h1>
    <p>
      <input type="text" name="firstName" v-model="firstName">
      <input type="text" name="lastName" v-model="lastName">
      <input type="text" name="city" v-model="address.city">
      <input type="text" name="province" v-model="address.province">

      <br>
      Masukkan tanggal lahir
      <input type="number" v-model="myBirthYear">
    </p>
    <p>saya tinggal di {{address.city}} , {{address.province}}</p>
    <p>saya sedang menempuh pendidikan di {{school.university}} , duduk di semester {{school.smstr}}</p>
    <p>Saya berumur {{ getMyAge }}</p>
    <p>
    Saya {{work ? 'Bekerja' : 'Tidak Bekerja'}}
    </p>
    <p>
    Saya {{work ? 'Bekerja' : 'Tidak Bekerja'}}
    </p>
    <p>
    saya
    <span v-if="age <10 && age>0"> masih anak kecil </span>
    <span v-else-if="age < 20 && age > 10">masih remaja</span>
    <span v-else> tua</span>
    </p>
    <p>
    <ul>
      <li v-for="listUniv in daftarUniversitas" :key="listUniv.id">
      {{listUniv.namaUniv}}
      </li>
    </ul>
    </p>

    <!-- data binding -->
    <a :href="facebookUrl" :title="title">facebook saya</a>
    <br>
    <button :disabled="buttonState">Klik here</button>
    <button v-show="buttonState">show</button>
    <button v-on:click="showPopUp(false)">Submit</button>
    <p>{{ getAddressData }}</p>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      firstName: "<strong>Eka Ardilah</strong>",
      lastName: "Febriyanti",
      myBirtYear: 1998,
      age: 17,
      work: true,
      isNameShown: false,
      address: {
        city: "Bandung",
        province: "Jawa Barat"
      },
      facebookUrl: "https://facebook.com/ekaardilah",
      title: "situs facebook Eka Ardilah Febriyanti",
      buttonState: true,
      school: {
        university: "Universitas Pasundan",
        smstr: "6"
      },
      daftarUniversitas: [
        { id: "1", namaUniv: "Universitas Brawijaya" },
        { id: "2", namaUniv: "Universitas Padjajaran" },
        { id: "3", namaUniv: "Universitas Pasundan" }
      ]
    };
  },
  methods: {
    // showPopUp(){
    //   alert("Hallo");
    // }

    showPopUp(condition) {
      if (condition) {
        alert("Hello");
      } else {
        alert("ok");
      }
    },
    showName() {
      this.isNameShown = !this.isNameShown;
    }
  },
  computed: {
    getMyAge() {
      let currentYear = new Date().getFullYear();
      let myBirthDay = 1998;
      return currentYear - myBirthDay;
    },
    getAddressData() {
      let { city, province } = this.address;
      return city + " " + province;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
