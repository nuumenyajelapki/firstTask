<template>
  <div id="app">
    <form class="form" @submit.prevent="submitHandler">
      <div class="form__input">
        <label>Фамилия
        <input
          type="text"
          name="lastName"
          id="lastName"
          v-model="lastName"
          :class="{invalid: ($v.lastName.$dirty && !$v.lastName.required)}"
        >
        </label>
        <small v-if="$v.lastName.$dirty && !$v.lastName.required" style="color: red">Введите фамилию</small>
        <small v-else>Введите фамилию</small>
      </div>
      <div class="form__input">
        <label>Имя
        <input
          type="text"
          name="firstName"
          id="firstName"
          v-model="firstName"
          :class="{invalid: ($v.firstName.$dirty && !$v.firstName.required)}"
        >
        </label>
        <small v-if="$v.firstName.$dirty && !$v.firstName.required" style="color: red">Введите имя</small>
        <small v-else>Введите имя</small>
      </div>
      <div class="form__input">
        <label>Отчество
        <input
          type="text"
          name="thirdName"
          id="thirdName"
        >
        </label>
        <small>Введите отчество</small>
      </div>
      <div class="form__input">
        <label>Дата рождения
        <input 
          type="date"
          name="birthday"
          id="birthday"
          v-model="birthday"
          :class="{invalid: ($v.birthday.$dirty && !$v.birthday.required)}"
        >
        </label>
        <small v-if="$v.birthday.$dirty && !$v.birthday.required" style="color: red">Введите дату рождения</small>
        <small v-else>Введите дату рождения</small>
      </div>
      <div class="form__input">
        <label>Номер телефона
        <input 
          type="tel"
          name="tel"
          id="tel"
          placeholder="71234567890"
          v-model="tel"
          :class="{invalid: ($v.tel.$dirty && !$v.tel.required) || ($v.tel.$dirty && (!$v.tel.minLength || !$v.tel.maxLength || $v.tel.$model[0]!=7))}"
        >
        </label>
        <small v-if="$v.tel.$dirty && !$v.tel.required" style="color: red">Введите номер телефона</small>
        <small v-else-if="$v.tel.$dirty && (!$v.tel.minLength || !$v.tel.maxLength || $v.tel.$model[0]!=7)" style="color: red">Номер телефона должен начинаться с 7 и быть 11 цифр</small>
        <small v-else>Введите номер телефона</small>
      </div>
      <div class="form__input-radio">
        <div class="i1"> 
          <input name="Pol" type="radio" class="pol" value="Man" checked>
          <label class="pol-lable">Мужчина</label>
        </div>
        <div class="i2"> 
          <input name="Pol" type="radio" class="pol" value="Women">
          <label class="pol-lable">Женщина</label>
        </div>
      </div>
      <div class="form__selector">
        <label>Группа клиентов</label>
        <select 
        multiple name="group" 
        class="select-group" 
        v-model="group" 
        :class="{invalid: ($v.group.$dirty && !$v.group.required)}">
          <option value="Vip">Vip</option>
          <option value="Trouble">Проблемные</option>
          <option value="OMC">ОМС</option>
        </select>
      </div>
      <div class="form__selector">
        <label>Лечащий врач</label>
        <select 
        name="vrach" 
        class="select-vrach"
        >
          <option value="Ivanov" selected="selected">Иванов</option>
          <option value="Zakharov">Захаров</option>
          <option value="Chernisheva">Чернышева</option>
        </select>
      </div>
      <div class="form__checkbox">
        <input type="checkbox" name="sms" class="checkbox">
        <label class="sms-lable">Не отправлять СМС</label>
      </div>
      <div class="form__input">
        <label>Индекс
        <input
          type="number"
          name="index"
          id="index"
        >
        </label>
        <small>Введите индекс</small>
      </div>
      <div class="form__input">
        <label>Страна
        <input
          type="text"
          name="country"
          id="country"
        >
        </label>
        <small>Введите страну</small>
      </div>
      <div class="form__input">
        <label>Область
        <input
          type="text"
          name="region"
          id="region"
        >
        </label>
        <small>Введите область</small>
      </div>
      <div class="form__input">
        <label>Город
        <input
          type="text"
          name="city"
          id="city"
          v-model="city"
          :class="{invalid: ($v.city.$dirty && !$v.city.required)}"
        >
        </label>
        <small v-if="$v.city.$dirty && !$v.city.required" style="color: red">Введите город</small>
        <small v-else>Введите город</small>
      </div>
      <div class="form__input">
        <label>Улица
        <input
          type="text"
          name="street"
          id="street"
        >
        </label>
        <small>Введите улицу</small>
      </div>
      <div class="form__input">
        <label>Дом
        <input
          type="text"
          name="house"
          id="house"
        >
        </label>
        <small>Введите дом</small>
      </div>
      <div class="form__selector">
        <label>Тип документа</label>
        <select 
        name="doc" 
        class="select-doc" 
        v-model="doc"
        :class="{invalid: ($v.doc.$dirty && !$v.doc.required)}"
        >
          <option value="Pass" selected="selected">Паспорт</option>
          <option value="Svid">Свидетельство о рождении</option>
          <option value="Vod">Вод. удостоверение</option>
        </select>
      </div>
      <div class="form__input">
        <label>Серия
        <input 
          type="number"
          name="serial"
          id="serial"
        >
        </label>
        <small>Введите серию</small>
      </div>
      <div class="form__input">
        <label>Номер
        <input 
          type="number"
          name="number"
          id="number"
        >
        </label>
        <small>Введите номер</small>
      </div>
      <div class="form__input">
        <label>Кем выдан
        <input
          type="text"
          name="vidan"
          id="vidan"
        >
        </label>
        <small>Введите кем выдан</small>
      </div>
      <div class="form__input">
        <label>Дата выдачи
        <input 
          type="date"
          name="docDate"
          id="docDate"
          v-model="docDate"
          :class="{invalid: ($v.docDate.$dirty && !$v.docDate.required)}"
        >
        </label>
        <small v-if="$v.docDate.$dirty && !$v.docDate.required" style="color: red">Введите дату выдачи</small>
        <small v-else>Введите дату выдачи</small>
      </div>
      <div class="btn">
      <button type="submit" class="button">ОТПРАВИТЬ</button>
      </div>
    </form>
  </div>
</template>

<script>

import { email, required, minLength, maxLength } from 'vuelidate/lib/validators/'

export default {
  name: 'App',
  data: () => ({
    lastName: '',
    firstName: '',
    birthday: '',
    tel: '',
    group: [],
    city: '',
    doc: '',
    docDate: ''
  }),
  validations: {
    lastName: { required },
    firstName: { required },
    birthday: { required },
    tel: { required, minLength: minLength(11), maxLength: maxLength(11) },
    group: { required },
    city: { required },
    doc: { required },
    docDate: { required }
  },
  methods: {
    submitHandler() {
      if(this.$v.$invalid){
        this.$v.$touch()
        return
      }
      alert("Новый клиент успешно создан!")
    }
  }
}
</script>

<style lang="sass">

body
  background-color: #101319

#app
  max-width: 500px
  padding: 0px 15px
  display: flex
  margin: 0 auto
  background-color: #fff
  border-radius: .25rem
  font-family: Avenir, Helvetica, Arial, sans-serif
  -webkit-font-smoothing: antialiased
  -moz-osx-font-smoothing: grayscale
  // text-align: center;
  color: #2c3e50
  margin-top: 60px
  margin-bottom: 60px


input, label
  display: block


.invalid
  border-color: red
  border-radius: .2rem


form
  width: 100%


input
  width: 100%
  height: 24px
  margin-top: 5px


small
  color: #6c757d


.form__input
  padding: 24px 24px 0px 24px


.form__input-radio
  padding: 24px 24px 0px 24px
  display: flex
  .i1
    display: flex
  
  .i2
    padding: 0 0 0 24px
    display: flex
  
  .pol
    width: auto
  
  .pol-lable
    padding-top: 6px
  


.form__selector
  padding: 24px 24px 0px 24px
  display: block
  select
    width: 100%
    margin-top: 5px
  


.form__checkbox
  padding: 24px 24px 0px 24px
  display: flex
  input
    width: auto
  
  .sms-lable
    padding-top: 6px
  


.select-vrach
  height: 36px


.select-doc
  height: 36px


.btn
  padding: 24px
  display: flex
  button
    margin: 0 auto
    width: 50%
    height: 36px
    border: none
    background-color: #5B32F5
    color: #fff
    border-radius: .25rem
  
  button:hover
    background-color: #7C5BF7
  


</style>
