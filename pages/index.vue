<template>
  <div class="limit__container d-flex align-center justify-center mx-auto flex-column">
    <v-form
      ref="form"
      v-model="valid"
      class="form__block"
      lazy-validation
    >
      <v-text-field
        v-model="name"
        :counter="12"
        :rules="nameRules"
        label="Поиск клиента в АФМ"
        required
      ></v-text-field>

      <v-btn
        :disabled="!valid"
        color="success"
        class="mr-4 mt-4"
        @click="search"
      >
        Выполнить новый поиск
      </v-btn>
    </v-form>
    <div v-if="result !== null && result.length" class="result">
      <p><strong>ID:</strong> {{ result[0].num }}</p>
      <p><strong>Имя:</strong> {{ result[0].lname }}</p>
      <p><strong>Фамилия:</strong> {{ result[0].fname }}</p>
      <p><strong>Отчество:</strong> {{ result[0].mname }}</p>
      <p><strong>Дата рождения:</strong> {{ result[0].birthdate }}</p>
      <p><strong>ИИН:</strong> {{ result[0].iin }}</p>
    </div>
    <div v-if="result !== null && result.length === 0" class="no_result">
      Клиент не обнаружен
    </div>
  </div>
</template>

<script>
import persons from '@/utils/persons.json'

export default {
  data: () => ({
    valid: true,
    result: null,
    name: '',
    nameRules: [
      v => !!v || 'Пожалуйста, введите ИИН пользователя',
      v => (v && v.length === 12) || 'Неверный ИИН',

    ],
  }),
  mounted() {

  },
  methods: {
    search() {
      this.$refs.form.validate()
      this.result = persons.persons.person.filter((person) => {
        return person.iin === Number(this.name)
      })
    },
  },
}
</script>
<style lang="scss">
.header__name {
  text-align: center;
  font-size: 42px;
}

.container {
  height: 100%;
}

.no_result {
  font-style: normal;
  font-weight: 400;
  font-size: 18px;
  text-align: center;
  margin-top: 40px;
  margin-bottom: 40px;
  line-height: 25px;
  color: #F01414;
}

.result {
  margin-bottom: 40px;
  max-width: 450px;
  width: 100%;
  margin-top: 40px;
  border: 1px solid #00805f;
  border-radius: 8px;
  padding: 15px 12px;
}

.limit__container {
  max-width: 1200px;
  margin-top: 35px;
  width: 100%;

  .form__block {
    max-width: 450px;
    width: 100%;

    button {
      margin-top: 20px;
      padding: 23px !important;
      background: #fbae16 !important;
      color: black !important;
      cursor: pointer;
      width: 100%;
      transition: 0.4s;

      &:disabled {
        background: #9b9b9b !important;
        color: white !important;
      }
    }
  }
}

@media screen and(max-width: 450px) {
  .header__name {
    font-size: 24px;
  }
}
</style>
