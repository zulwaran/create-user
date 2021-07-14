<template>
  <form class="create-user">
    <div class="create-user__personal">
      <div class="field">
        <label>Фамилия*</label>
        <input type="text" />
      </div>
      <div class="field">
        <label>Имя*</label>
        <input type="text" />
      </div>
      <div class="field">
        <label>Отчество</label>
        <input type="text" />
      </div>
      <div class="field">
        <label>Дата рождения*</label>
        <input type="date" />
      </div>
      <div class="field">
        <label>Номер телефона*</label>
        <input type="tel" />
      </div>
      <div class="field">
        <label
          >Мужчина<input type="radio" name="gender" checked value="Male"
        /></label>
        <label
          >Женщина<input type="radio" name="gender" value="Female"
        /></label>
      </div>
      <div class="field">
        <label>Группа клиентов* </label>
        <select multiple>
          <option>VIP</option>
          <option>Проблемные</option>
          <option>ОМС</option>
        </select>
      </div>
      <div class="field">
        <label> Лечащий врач </label>
        <select>
          <option>Иванов</option>
          <option>Захаров</option>
          <option>Чернышева</option>
        </select>
      </div>
      <div class="field">
        <label>Не отправлять СМС <input type="checkbox" /></label>
      </div>
    </div>

    <div class="create-user__adress">
      <div class="field">
        <label>Индекс</label>
        <input type="text" />
      </div>
      <div class="field"><label>Страна</label><input type="text" /></div>
      <div class="field"><label>Область</label><input type="text" /></div>
      <div class="field"><label>Город*</label><input type="text" /></div>
      <div class="field"><label>Улица</label><input type="text" /></div>
      <div class="field"><label>Дом</label><input type="text" /></div>
    </div>

    <div class="create-user__document">
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
        <textarea name="" id="" cols="30" rows="5"></textarea>
      </div>
      <div class="field"><label>Дата выдачи*</label><input type="date" /></div>
    </div>
  </form>
</template>

<script>
export default {};
</script>

<style>
.create-user {
  margin: 30px 0;
  min-width: 320px;
  background: #fff;
  border: 1px solid #ccc;
  box-shadow: 0 1px 2px rgb(0 0 0 / 10%);
  border-radius: 3px;
  padding: 10px 0 0;
  display: inline-block;
}
.field {
  margin-bottom: 15px;
  text-align-last: center;
  justify-content: center;
}
.field label {
  color: #555;
  display: block;
  margin-bottom: 5px;
  align-self: center;
  margin-right: 5px;
}
.field input {
  color: #777;
  padding: 5px 10px;
  border: 1px solid #c7d0d2;
  border-radius: 2px;
  box-shadow: inset 0 1.5px 3px rgb(190 190 190 / 40%), 0 0 0 5px #f5f7f8;
  outline: none;
}
.field select {
  padding: 5px 0;
  width: 70%;
  color: #777;
  border: 1px solid #c7d0d2;
  border-radius: 2px;
  box-shadow: inset 0 1.5px 3px rgb(190 190 190 / 40%), 0 0 0 5px #f5f7f8;
  outline: none;
}
input[type="text"] {
  font-size: 16px;
}
</style>