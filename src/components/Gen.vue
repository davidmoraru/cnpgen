<template>
<section class="section">
  <div class="container">
    <form method="POST" @submit.prevent="genCNP">
      <div class="columns">
        <div class="column is-8-desktop is-offset-2-desktop">
          <div class="content">
            <h4>Generator CNP</h4>
            <hr>
            <div class="columns is-variable is-1">
              <div class="column">
                <div class="field">
                  <label class="label">Sexul</label>
                  <div class="control is-expanded">
                    <div class="select is-fullwidth">
                      <select v-model="gen.sex">
                        <option value="0">Bărbat</option>
                        <option value="1">Femeie</option>
                      </select>
                    </div>
                  </div>
                </div>
              </div>
              <div class="column">
                <div class="field">
                  <label class="label">Anul</label>
                  <div class="control is-expanded">
                    <div class="select is-fullwidth">
                      <select v-model="gen.year">
                        <option v-for="(an, index) in ani" :key="index" :value="an">{{ an }}</option>
                      </select>
                    </div>
                  </div>
                </div>
              </div>
              <div class="column">
                <div class="field">
                  <label class="label">Luna</label>
                  <div class="control is-expanded">
                    <div class="select is-fullwidth">
                      <select v-model="gen.month">
                        <option value="01">Ianuarie</option>
                        <option value="02">Februarie</option>
                        <option value="03">Martie</option>
                        <option value="04">Aprilie</option>
                        <option value="05">Mai</option>
                        <option value="06">Iunie</option>
                        <option value="07">Iulie</option>
                        <option value="08">August</option>
                        <option value="09">Septembrie</option>
                        <option value="10">Octombrie</option>
                        <option value="11">Noiembrie</option>
                        <option value="12">Decembrie</option>
                      </select>
                    </div>
                  </div>
                </div>
              </div>
              <div class="column">
                <div class="field">
                  <label class="label">Ziua</label>
                  <div class="control is-expanded">
                    <div class="select is-fullwidth">
                      <select v-model="gen.day">
                        <option v-for="(zi, index) in zile()" :key="index" :value="(zi <= 9) ? '0' + zi: zi">{{ zi }}</option>
                      </select>
                    </div>
                  </div>
                </div>
              </div>

              <div class="column">
                <div class="field">
                  <label class="label">Judeţul</label>
                  <div class="control is-expanded">
                    <div class="select is-fullwidth">
                      <select v-model="gen.state" id="stateRef">
                        <option value="40">București</option>
                        <option value="41">București S.1</option>
                        <option value="42">București S.2</option>
                        <option value="43">București S.3</option>
                        <option value="44">București S.4</option>
                        <option value="45">București S.5</option>
                        <option value="46">București S.6</option>
                        <option value="01">Alba</option>
                        <option value="02">Arad</option>
                        <option value="03">Argeș</option>
                        <option value="04">Bacău</option>
                        <option value="05">Bihor</option>
                        <option value="06">Bistrița-Năsăud</option>
                        <option value="07">Botoșani</option>
                        <option value="08">Brașov</option>
                        <option value="09">Brăila</option>
                        <option value="10">Buzău</option>
                        <option value="11">Caraș-Severin</option>
                        <option value="12">Cluj</option>
                        <option value="13">Constanța</option>
                        <option value="14">Covasna</option>
                        <option value="15">Dâmbovița</option>
                        <option value="16">Dolj</option>
                        <option value="17">Galați</option>
                        <option value="18">Gorj</option>
                        <option value="19">Harghita</option>
                        <option value="20">Hunedoara</option>
                        <option value="21">Ialomița</option>
                        <option value="22">Iași</option>
                        <option value="23">Ilfov</option>
                        <option value="24">Maramureș</option>
                        <option value="25">Mehedinți</option>
                        <option value="26">Mureș</option>
                        <option value="27">Neamț</option>
                        <option value="28">Olt</option>
                        <option value="29">Prahova</option>
                        <option value="30">Satu Mare</option>
                        <option value="31">Sălaj</option>
                        <option value="32">Sibiu</option>
                        <option value="33">Suceava</option>
                        <option value="34">Teleorman</option>
                        <option value="35">Timiș</option>
                        <option value="36">Tulcea</option>
                        <option value="37">Vaslui</option>
                        <option value="38">Vâlcea</option>
                        <option value="39">Vrancea</option>
                        <option value="51">Călărași</option>
                        <option value="52">Giurgiu</option>
                      </select>
                    </div>
                  </div>
                </div>
              </div>
            </div>
            <div class="columns">
              <div class="column">
                <div class="field is-grouped is-grouped-right">
                  <p class="control">
                    <a href="#" class="button is-small is-white" @click.prevent="randomCNP">
                      Random
                    </a>
                  </p>
                  <p class="control">
                    <button type="reset" class="button is-danger is-small" @click="resetGen">
                      Reseteaza
                    </button>
                  </p>
                  <p class="control">
                    <button type="submit" class="button is-primary is-small">
                      Genereaza
                    </button>
                  </p>

                </div>
              </div>
            </div>
          </div>
          <div class="content" v-if="salvate.length">
            <strong>CNP-uri</strong> salvate:
          </div>
          <div class="table-container">
            <table class="table is-bordered is-fullwidth" v-if="salvate.length">
              <thead>
                <tr>
                  <th>#</th>
                  <th>Sexul</th>
                  <th>Data nasterii</th>
                  <th>Judet</th>
                  <th>CNP</th>
                </tr>
              </thead>
              <tbody>
                <tr v-for="(data, index) in salvate" :key="index">
                  <td><code>{{ index+1 }}</code></td>
                  <td><code>{{ data.sex }}</code></td>
                  <td><code>{{ data.dob }}</code></td>
                  <td><code>{{ data.state }}</code></td>
                  <td><code>{{ data.cnp }}</code></td>
                </tr>
              </tbody>
            </table>
            <div v-else>
              <center><strong>CNP-uri salvate</strong><br><code>Nu este niciun CNP in baza de date <br> <a href="#" @click.prevent="genCNP">Genereaza unul nou.</a></code></center>
            </div>
          </div>
        </div>
      </div>
    </form>
  </div>
</section>
</template>

<script>
const $ = require('jquery');
import {
  ref,
  reactive,
  onMounted
} from 'vue';
export default {
  name: 'Gen',
  setup(props, ctx) {
    var zile = ref('');
    var ani = ref('');
    const stateRef = ref(null);
    const gen = reactive({
      sex: '0',
      day: '01',
      month: '01',
      year: '1980',
      state: '01',
    });

    function randomCNP(usergen = true) {
      let year = getRandom(1930, 2020);
      gen.year = year.toString();
      let month = getRandom(1, 12);
      gen.month = (month <= 9) ? '0' + month : month.toString();
      if (month % 2 == 0) {
        gen.sex = '0';
      } else {
        gen.sex = '1';
      }
      let state = getRandom(1, 46);
      gen.state = (state <= 9) ? '0' + state : state.toString();
      let days = getDaysInMonth(gen.month, gen.year);
      days = getRandom(1, days);
      gen.day = (days <= 9) ? '0' + days : days.toString();

      if (usergen)
        genCNP();
    }
    const salvate = reactive([]);

    function resetGen() {
      while (salvate.length) {
        salvate.pop();
      }
    }

    function getRandom(min = 500, max = 999) {
      min = Math.ceil(min);
      max = Math.floor(max);
      return Math.floor(Math.random() * (max - min) + min);
    }

    function range(start, end) {
      return (new Array(end - start + 1)).fill(undefined).map((_, i) => i + start);
    }
    zile = () => {
      let days = getDaysInMonth(gen.month, gen.year);
      days = range(1, days);
      return days;
    }
    ani = range(1930, 2020).reverse();

    function padZero(param, toLength) {
      for (; param.length < toLength; param = '0' + param) {}
      return param;
    }

    var getDaysInMonth = (month, year) => {
      return new Date(year, month, 0).getDate();
    };

    function genCNP() {
      var century = 0;
      if (parseInt(gen.year.toString()) < 2000) {
        century = 1;
      } else {
        century = 5;
      }
      var cnp1, cnp2, cnp, vcnp, bigTotal, checksum;
      cnp1 = "" + (century + parseInt(gen.sex));
      cnp2 = gen.year.toString().substring(2, 4) + gen.month + gen.day;
      cnp = "" + cnp1 + cnp2 + padZero(gen.state, 2) + padZero(getRandom(500, 999), 3);
      vcnp = "279146358279";
      bigTotal = 0;
      for (let i = 0; i < 12; i++) {
        bigTotal += parseInt(cnp[i]) * parseInt(vcnp[i]);
      }
      checksum = bigTotal % 11;

      if (checksum == 10) {
        checksum = 1;
      }
      cnp = cnp + checksum;
      let selected = $('#stateRef option:selected');
      salvate.push({
        sex: parseInt(gen.sex) ? 'Feminin' : 'Bărbătesc',
        dob: gen.day + '/' + lunile(gen.month) + '/' + gen.year.toString(),
        state: selected.text(),
        cnp: cnp,
      });
      $('title').html('GNP: ' + cnp);
    };

    function lunile(m) {
      m = parseInt(m) - 1;
      let array = [
        'Ian',
        'Feb',
        'Mar',
        'Apr',
        'Mai',
        'Iun',
        'Iul',
        'Aug',
        'Sept',
        'Oct',
        'Noi',
        'Dec',
      ];
      return array[m];
    }
    onMounted(() => {
      randomCNP(false);
    });
    return {
      resetGen,
      gen,
      range,
      ani,
      zile,
      genCNP,
      salvate,
      stateRef,
      randomCNP
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->

<style lang="scss" scoped>
.section {
  padding: 1.5rem 1.5rem;
}
</style>
