<template>
  <div class="create-user">
    <form class="create-user-form" @submit.prevent="createUser">
      <div class="create-user-form__personal">
        <h3>Личные данные</h3>
        <div class="field">
          <label>Фамилия*</label>
          <input v-model.trim="formPersonal.surname" type="text" />
          <small
            v-if="
              $v.formPersonal.surname.$dirty &&
              !$v.formPersonal.surname.required
            "
            >Поле обязательное для заполнения</small
          >
        </div>
        <div class="field">
          <label>Имя*</label>
          <input v-model.trim="formPersonal.name" type="text" />
          <small
            v-if="$v.formPersonal.name.$dirty && !$v.formPersonal.name.required"
            >Поле обязательное для заполнения</small
          >
        </div>
        <div class="field">
          <label>Отчество</label>
          <input v-model.trim="formPersonal.midname" type="text" />
        </div>
        <div class="field">
          <label>Дата рождения*</label>
          <input v-model.trim="formPersonal.born" type="date" />
          <small
            v-if="$v.formPersonal.born.$dirty && !$v.formPersonal.born.required"
            >Поле обязательное для заполнения</small
          >
        </div>
        <div class="field">
          <label>Номер телефона*</label>
          <input v-model="formPersonal.phone" type="tel" v-phone />
          <small
            v-if="
              $v.formPersonal.phone.$dirty && !$v.formPersonal.phone.required
            "
            >Поле обязательное для заполнения</small
          >
          <small
            v-else-if="
              $v.formPersonal.phone.$dirty && !$v.formPersonal.phone.minLength
            "
            >Неверный формат телефона</small
          >
        </div>
        <div class="field">
          <label
            >Мужчина<input
              v-model.trim="formPersonal.gender"
              type="radio"
              name="gender"
              checked
              value="Male"
          /></label>
          <label
            >Женщина<input
              v-model.trim="formPersonal.gender"
              type="radio"
              name="gender"
              value="Female"
          /></label>
        </div>
        <div class="field">
          <label>Группа клиентов* </label>
          <select v-model.trim="formPersonal.group" multiple>
            <option v-for="elem in groupItems" :key="elem.index">
              {{ elem }}
            </option>
          </select>
          <small
            v-if="
              $v.formPersonal.group.$dirty && !$v.formPersonal.group.required
            "
            >Поле обязательное для заполнения</small
          >
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
            <input v-model.trim="formPersonal.checkbox" type="checkbox"
          /></label>
        </div>
      </div>

      <div class="create-user-form__adress">
        <h3>Адрес</h3>
        <div class="field">
          <label>Индекс</label>
          <input v-model.trim="formAdress.index" type="number" />
        </div>
        <div class="field">
          <label>Страна</label
          ><input v-model.trim="formAdress.country" type="text" />
        </div>
        <div class="field">
          <label>Область</label
          ><input v-model.trim="formAdress.region" type="text" />
        </div>
        <div class="field">
          <label>Город*</label
          ><input v-model.trim="formAdress.town" type="text" />
          <small
            v-if="$v.formAdress.town.$dirty && !$v.formAdress.town.required"
            >Поле обязательное для заполнения</small
          >
        </div>
        <div class="field">
          <label>Улица</label
          ><input v-model.trim="formAdress.street" type="text" />
        </div>
        <div class="field">
          <label>Дом</label
          ><input v-model.trim="formAdress.house" type="number" />
        </div>
      </div>

      <div class="create-user-form__document">
        <h3>Документ удостоверяющий личность</h3>
        <div class="field">
          <label>Тип документа*</label>
          <select v-model.trim="formDocument.type">
            <option v-for="elem in typeItems" :key="elem.index">
              {{ elem }}
            </option>
          </select>
          <small
            v-if="$v.formDocument.type.$dirty && !$v.formDocument.type.required"
            >Поле обязательное для заполнения</small
          >
        </div>
        <div class="field">
          <label>Серия</label
          ><input v-model.trim="formDocument.series" type="number" />
        </div>
        <div class="field">
          <label>Номер</label
          ><input v-model.trim="formDocument.number" type="number" />
        </div>
        <div class="field">
          <label>Кем выдан</label>
          <textarea
            v-model.trim="formDocument.whoIssued"
            cols="30"
            rows="5"
          ></textarea>
        </div>
        <div class="field">
          <label>Дата выдачи*</label
          ><input v-model.trim="formDocument.dateIssued" type="date" />
          <small
            v-if="
              $v.formDocument.dateIssued.$dirty &&
              !$v.formDocument.dateIssued.required
            "
            >Поле обязательное для заполнения</small
          >
        </div>
      </div>
      <button type="submit">Сохранить</button>
    </form>
    <v-popup v-if="visiblePopup" @closePopup="closePopup" :visiblePopup="visiblePopup"
      >Пользователь создан</v-popup
    >
  </div>
</template>

<script>
import vPopup from "./CreateModal.vue";
import {
  required,
  minLength,
} from "../../node_modules/vuelidate/lib/validators";
export default {
  components: {
    vPopup,
  },
  data() {
    return {
      visiblePopup: false,
      groupItems: ["VIP", "Проблемные", "ОМС"],
      typeItems: ["Паспорт", "Свидетельство о рождении", "Вод. удостоверение"],
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
        index: null,
        country: "",
        region: "",
        town: "",
        street: "",
        house: null,
      },
      formDocument: {
        type: null,
        series: null,
        number: null,
        whoIssued: "",
        dateIssued: null,
      },
    };
  },
  validations: {
    formPersonal: {
      name: { required },
      surname: { required },
      born: { required },
      phone: { required, minLength: minLength(15) },
      group: { required },
    },
    formAdress: {
      town: { required },
    },
    formDocument: {
      type: { required },
      dateIssued: { required },
    },
  },
  methods: {
    closePopup() {
      this.visiblePopup = false;
    },
    createUser() {
      if (this.$v.$invalid) {
        console.log("Validate ERROR!");
        this.$v.$touch();
        return;
      }
      this.visiblePopup = true;
      console.log(this.formPersonal, this.formAdress, this.formDocument);
    },
  },
};
</script>


<style lang="sass">
.create-user-form
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

h3
  padding: 5px 10px

button
  padding: 10px
  border-radius: 12px
  color: white
  outline: none
  background-color: rgb(12, 24, 71)
  border-color: rgb(12, 24, 71)

small
  display: block
  font-size: 12px
  color: red
  text-align-last: left
  margin-left: 60px
  margin-top: 5px

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

input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button
  -webkit-appearance: none
  margin: 0

input[type=number]
  -moz-appearance: textfield
</style>






