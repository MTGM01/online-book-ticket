<script>
export default {
  name: 'OnlineTicket',
  data() {
    return {
      countries: {
        iran: ['Tabriz', 'Tehran', 'Mashhad', 'Yazd', 'Gilan', 'Esfahan', 'Shiraz'],
        india: ['Mumbai', 'Delhi', 'Pune', 'Surat', 'Chennai', 'Kanpur', 'Jaipur'],
        turkey: ['Istanbul', 'Ankara', 'Izmir', 'Bursa', 'Antalya', 'Adana', 'Van'],
        southKorea: ['Andong', 'Ansan', 'Asan', 'Busan', 'Bucheon', 'Changwon', 'Cheonan'],
        russia: ['Moscow', 'Saint Petersburg', 'Kazan', 'Samara', 'Perm', 'Krasnoyarsk', 'Tomsk'],
        china: ['Pekan', 'Shanghai', 'Beijing', 'Foshan', 'Hohhot', 'Zibo', 'Hefei'],
        germany: ['Berlin', 'Hamburg', 'Frankfurt', 'Stuttgart', 'Cologne', 'Munich', 'Bremen'],
        italy: ['Rome', 'Milan', 'Turin', 'Naples', 'Palermo', 'Genoa', 'Bologna'],
        spain: ['Algeciras', 'Puerto Real', 'San Fernando', 'Cadiz', 'Cabra', 'Montilla', 'Lucena'],
        england: ['London', 'Westminster', 'Birmingham', 'Leeds', 'Manchester', 'Bristol', 'Wakefield'],
        sweden: ['Arboga', 'Avesta', 'Boden', 'Bollnas', 'Alingsas', 'Boras', 'Eksjo'],
        usa: ['New York', 'Chicago', 'San Diego', 'Los Angeles', 'Columbus', 'San Francisco', 'Dallas'],
        panama: ['Colon', 'David', 'Santiago', 'Bugaba', 'Anton', 'Capira', 'Chame'],
        saintLucia: ['Anse La Raye', 'Bocage', 'Bisee', 'Canaries', 'Dennery', 'Laborie', 'Praslin'],
        jamaica: ['ocho Rios', 'Linstead', 'Morant Bay', 'Hayes', 'Santa Cruz', 'Port Antonio', 'Mandeville'],
        canada: ['Alberta', 'Manitoba', 'YUkon', 'Nunavut', 'Ontario', 'New Brunswick', 'British Columbia']
      },
      cities: ['Tabriz', 'Tehran', 'Mashhad', 'Yazd', 'Gilan', 'Esfahan', 'Shiraz'],
      formData: {
        country: 'iran',
        city: 'Tabriz'
      }
    }
  },
  methods: {
    selectedCountryHandler(objectEvent) {
      this.cities = [...this.countries[objectEvent.target.value]]
      this.formData = {
        ...this.formData,
        country: objectEvent.target.value
      }
    },
    inputAndSelectHandler(objectEvent) {
      this.formData = {
        ...this.formData,
        [objectEvent.target.name]: objectEvent.target.value
      }
    },
    sendData() {
      console.log(this.formData)
      this.formData = {}
      // window.location.reload()
    }
  }
}
</script>

<template>

  <section class="container">

    <form class="ticket-form" @submit.prevent>

      <div class="form-elements-container">
        <input type="text" :value="formData.firstName" placeholder="First Name" name="firstName" id="firstName"
          @keyup="inputAndSelectHandler" />
        <input type="text" :value="formData.lastName" placeholder="Last Name" name="lastName" id="lastName"
          @keyup="inputAndSelectHandler" />
        <input type="tel" :value="formData.phoneNumber" placeholder="Phone Number" maxlength="11" minlength="11"
          name="phoneNumber" id="phoneNumber" @keyup="inputAndSelectHandler" />
        <input type="email" :value="formData.email" placeholder="Email" name="email" id="email"
          @keyup="inputAndSelectHandler" />

        <select name="country" id="country" @change="selectedCountryHandler" required>

          <optgroup label="Asia Countries">
            <option value="iran">Iran</option>
            <option value="india">India</option>
            <option value="turkey">Turkey</option>
            <option value="southKorea">South Korea</option>
            <option value="russia">Russia</option>
            <option value="china">China</option>
          </optgroup>

          <optgroup label="Europe Countries">
            <option value="germany">Germany</option>
            <option value="italy">Italy</option>
            <option value="spain">Spain</option>
            <option value="england">England</option>
            <option value="sweden">Sweden</option>
          </optgroup>

          <optgroup label="American Countries">
            <option value="usa">United States of America</option>
            <option value="panama">Panama</option>
            <option value="saintLucia">Saint Lucia</option>
            <option value="jamaica">Jamaica</option>
            <option value="canada">Canada</option>
          </optgroup>

        </select>

        <select name="city" id="city" @change="inputAndSelectHandler" required>

          <option v-for="(city, i) in cities" :key="i" :value="city">{{ city }}</option>

        </select>

      </div>

      <button type="submit" class="btn-ticket" @click="sendData">
        Book Ticket
      </button>

    </form>

  </section>

</template>

<style scoped>
.container,
.ticket-form,
.btn-ticket {
  font-weight: 700;
  font-family: Georgia, 'Times New Roman', Times, serif;
  font-size: 25px;
}

#firstName,
#lastName,
#phoneNumber,
#email {
  border: none;
  outline: none;
  padding: 15px 10px;
  width: 18vw;
  border-radius: 10px;
}

#country,
#city {
  border: none;
  outline: none;
  padding: 15px 10px;
  width: 19vw;
  border-radius: 10px;
}

.container {
  background-color: rgba(87, 82, 82, 0.478);
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  width: 70%;
  margin: 10% auto;
  padding: 40px 20px;
  border-radius: 10px;
}

.ticket-form {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 50px;
  padding: 20px 40px;
  width: 80%;
}

.form-elements-container {
  display: flex;
  flex-wrap: wrap;
  align-items: flex-start;
  justify-content: space-evenly;
  row-gap: 50px;
  width: 100%;
}

.btn-ticket {
  background-color: rgb(166, 149, 50);
  border: none;
  outline: none;
  border-radius: 10px;
  padding: 10px 25px;
  color: white;
  cursor: pointer;
}
</style>