<template>
  <form class="create-user" @submit.prevent="createUser">
    <div class="create-user__personal">
      <h3>Личные данные</h3>
      <div class="field">
        <label>Фамилия*</label>
        <input v-model="formPersonal.surname" type="text" />
      </div>
      <div class="field">
        <label>Имя*</label>
        <input v-model="formPersonal.name" type="text" />
      </div>
      <div class="field">
        <label>Отчество</label>
        <input v-model="formPersonal.midname" type="text" />
      </div>
      <div class="field">
        <label>Дата рождения*</label>
        <input v-model="formPersonal.born" type="date" />
      </div>
      <div class="field">
        <label>Номер телефона*</label>
        <input v-model="formPersonal.phone" type="tel" />
      </div>
      <div class="field">
        <label
          >Мужчина<input
            v-model="formPersonal.gender"
            type="radio"
            name="gender"
            checked
            value="Male"
        /></label>
        <label
          >Женщина<input
            v-model="formPersonal.gender"
            type="radio"
            name="gender"
            value="Female"
        /></label>
      </div>
      <div class="field">
        <label>Группа клиентов* </label>
        <select v-model="formPersonal.group" multiple>
          <option>VIP</option>
          <option>Проблемные</option>
          <option>ОМС</option>
        </select>
      </div>
      <div class="field">
        <label> Лечащий врач </label>
        <select v-model="formPersonal.doc">
          <option>Иванов</option>
          <option>Захаров</option>
          <option>Чернышева</option>
        </select>
      </div>
      <div class="field">
        <label
          >Не отправлять СМС
          <input v-model="formPersonal.checkbox" type="checkbox"
        /></label>
      </div>
    </div>

    <div class="create-user__adress">
      <h3>Адрес</h3>
      <div class="field">
        <label>Индекс</label>
        <input type="text" />
      </div>
      <div class="field">
        <label>Страна</label><input formAdress.country type="text" />
      </div>
      <div class="field">
        <label>Область</label><input formAdress.region type="text" />
      </div>
      <div class="field">
        <label>Город*</label><input formAdress.town type="text" />
      </div>
      <div class="field">
        <label>Улица</label><input formAdress.street type="text" />
      </div>
      <div class="field">
        <label>Дом</label><input formAdress.house type="text" />
      </div>
    </div>

    <div class="create-user__document">
      <h3>Документ удостоверяющий личность</h3>
      <div class="field">
        <label>Тип документа </label>
        <select>
          <option>Паспорт</option>
          <option>Свидетельство о рождении</option>
          <option>Вод. удостоверение</option>
        </select>
      </div>
      <div class="field"><label>Серия</label><input type="text" /></div>
      <div class="field"><label>Номер</label><input type="text" /></div>
      <div class="field">
        <label>Кем выдан</label>
        <textarea cols="30" rows="5"></textarea>
      </div>
      <div class="field"><label>Дата выдачи*</label><input type="date" /></div>
    </div>
    <button type="submit">Сохранить</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      formPersonal: {
        name: "",
        surname: "",
        midname: "",
        born: null,
        phone: null,
        gender: null,
        group: [],
        doc: "",
        checkbox: false,
      },
      formAdress: {
        country: "",
        region: "",
        town: "",
        steet: "",
        home: "",
      },
      formDocument: {
        type: "",
        series: null,
        number: null,
        whoIssued: "",
        dateIssued: null,
      },
    };
  },
  methods: {
    createUser() {
      console.log(this.formPersonal, this.formAdress, this.formDocument);
    },
  },
};
</script>

<style lang="sass">
.create-user
    margin: 30px 0
    min-width: 320px
    display: inline-block
    &__personal,

    &__adress,

    &__document
        padding: 10px 0 0
        background: #fff
        border: 1px solid #ccc
        border-radius: 12px
        margin-bottom: 30px

.field
    margin-bottom: 15px
    text-align-last: center
    justify-content: center

    & label
        color: #555
        display: block
        margin-bottom: 5px
        margin-right: 10px
        align-self: center
        margin-right: 5px

    & input
        color: #777
        width: 70%
        padding: 5px 10px
        border: 1px solid #c7d0d2
        border-radius: 2px

        outline: none

    & select,

    & textarea
        padding: 5px 0
        width: 70%
        color: #777
        border: 1px solid #c7d0d2
        border-radius: 2px

        outline: none

input[type="text"]
    font-size: 16px

input[type="radio"]
    box-shadow: none
    width: auto
    margin-left: 10px

input[type="checkbox"]
    box-shadow: none
    width: auto
    margin-left: 10px

h3
    padding: 5px 10px

button
    padding: 10px
    border-radius: 12px
    color: white
    outline: none
    background-color: rgb(12, 24, 71)
    border-color: rgb(12, 24, 71)
</style>