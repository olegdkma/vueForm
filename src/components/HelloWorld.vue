<template>
  <div class="main">
  <div class="yelowBl">
    <div class="content">
  <h1>Попробуйте БЕСПЛАТНО</h1>
    <div class="prevText">
      <p class="linedText">
        <b>2000</b> <br>Бизнесов
      </p>
      <div class="normalText">
        <span>уже попробовали JoinChat.</span>
        <p>Присоединяйтесь к ним - создайте аккаунт прямо сейчас. Первые <b>15 дней</b> бесплатно.</p>
      </div>
    </div>
  <form @submit.prevent="someAction()">


    <div class="formFields">
      <div class="field">
        <input
                id="name"
                type="text"
                v-model="name"
                placeholder="Название компании"
                @blur="$v.name.$touch()"
        >
        <div class="error" v-if="$v.name.$error">
          <template v-if="!$v.name.maxLength">
            Длина названия не должна превышать {{ $v.name.$params.maxLength.max }} символов
          </template>
         <!-- <template v-else-if="!$v.name.alpha">
            Название должно быть на кирилице
          </template>-->
          <template v-else>
            Название обязательно для заполнения
          </template>
        </div>
      </div>
      <div class="field">

        <input id="passport_data" type="text"
               @blur="$v.email.$touch()"
               v-model="email"
               placeholder="Email"
        >
        <div class="error" v-if="$v.email.$error">
          Неверный формат почты
        </div>
      </div>
      <div class="field">
        <input
                id="passport_date"
                type="text"
                placeholder="Телефон"
                v-model="phone"
                @blur="$v.phone.$touch()"
        >
        <div class="error" v-if="$v.phone.$error">
          Ошибка в номере
        </div>
      </div>
    </div>


    <button type="submit" >
      Попробовать бесплатно
    </button>
  </form>
  </div>
  </div>
    <div class="white">
      <img class="iphone" src="../assets/Iphone.png" alt="">
      <img class="ipad" src="../assets/iPad-Pro.png" alt="">
    </div>
  </div>
</template>

<script>
  import { required, maxLength } from "vuelidate/lib/validators";


  export default {
    data() {
      return {
        email: null,
        name: null,
        phone: null,
      };
    },

    validations: {
      email: {
        required,
        validFormat: val => /^[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,4}$/i.test(val),
      },
      phone: {
        required,
        validFormat: val => /^\+?3?8?(0\d{9})$/i.test(val),
      },
      name: {
        required,
        maxLength: maxLength(10),
        /*alpha: val => /^[а-яё]*$/i.test(val),*/
      },
    },

    methods: {
      someAction() {

        this.$v.$touch()
        if (this.$v.$invalid) {
          console.log('invalid data')
        } else {
          // do your submit logic here
          alert(`email:${this.email},name:${this.name},phone:${this.phone}`)

        }
      }
    }
  }

</script>

<style scoped lang="scss">
  /*@import url('https://db.onlinewebfonts.com/c/0be7748549934c0e481bdb7b8ba5270f?family=Gotham+Pro+Black');
  @import url('https://db.onlinewebfonts.com/c/059288033e0f23aa4c5b19f0965ccc0d?family=Gotham+Pro+Medium');
  @import url('https://db.onlinewebfonts.com/c/1064f0ad1cb65fdab43bb592ddd8aa91?family=Gilroy-Bold');*/
  @font-face {
    font-family: "Gotham Pro Black";
    src: url('./../fonts/Gotham Pro Black Regular.ttf');
  }
  @font-face {
    font-family: "Gotham Pro Medium";
    src: url('./../fonts/Gotham Pro Medium Regular.ttf');
  }
  @font-face {
    font-family: "Gilroy-Bold";
    src: url('./../fonts/Gilroy-Bold.ttf');
  }
  .main{
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    max-width: 1920px;
    overflow: hidden;
  }
  .white{
    width: 38%;

    .iphone{

      transform: translateX(-35%);
    }
    .ipad{
      position: absolute;
      right: 0;
      transform: translate(64%, -39%);
      top: 50%;
    }
    img{

      /*display: inline-block;
      width: 40%;*/
    }
  }
.yelowBl{
  background: #fdde00;
  height: 100%;
  width: 62%;
  display: flex;
  align-items: center;
  justify-content: flex-end;
}
  .content{
    max-width: 900px;
    margin-right: 70px;


  }
  h1{
    font-family: 'Gotham Pro Black', sans-serif;
    font-size: 63px;
    margin-bottom: 39px;
  }
  .prevText{
    display: flex;

    .linedText{
      padding-right: 18px;
      color: black;
      border-right: 3px solid black;
      font-family: 'Gotham Pro Black', sans-serif;
      font-size: 36px;
      b{
        font-size: 75px;
      }
    }
    .normalText{
      span{
        font-family: 'Gotham Pro Black', sans-serif;
        font-size: 33px;
        color: black;
        display: inline-block;
        margin-bottom: 25px;
      }
      p{
        font-family: 'Gotham Pro Medium', sans-serif;
        font-size: 20px;
      }
     padding: 0 20px;
      max-width: 525px;
    }
  }
  .formFields{
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    align-items: center;
    margin-top: 55px;
    margin-bottom: 50px;
  }
  form{
    input{
      width: 260px;
      padding: 15px 0 15px 9px;
      border: none;
      outline: none;
      border-radius: 4px;
    font-family: 'Gilroy-Bold', sans-serif;
      font-size: 16px;
    }
    button{
      width: 326px;
      text-align: center;
      border: none;
      outline: none;
      padding: 20px 0;
      background: #001515;
      border-radius: 4px;
      color: #ffffff;
      cursor: pointer;
      font-size: 18px;
    font-family: 'Gilroy-Bold', sans-serif;
    }
    ::-webkit-input-placeholder, :-ms-input-placeholder,::placeholder  { /* Edge */
      color: #7f7f7f;
      font-size: 16px;
    }


  }
  .field{
    margin-right: 25px;
    margin-bottom: 20px;
    position: relative;
  }

  .error{
    color: red;
    position: absolute;
    left: 0;
    bottom: -20px;
    font-size: 12px;
  }

  @media (max-width: 1666px){
    html{
      overflow: auto;
    }
    .yelowBl{
      padding: 30px;
      width: 100%;
    }
    .ipad{
      display: none;
    }
    .white{
      width: auto;
    }
    @media (max-width: 1230px){
      .formFields{
        flex-direction: column;
        margin-bottom: 0;
        .field{
          margin-right: 0;
        }
      }
      form{
        text-align: center;
      }
      .content{
        margin-right: 0;
      }
      h1{
        text-align: center;
      }
    }
    @media (max-width: 1100px){
      .white{
        display: none;
      }
      .content{
        margin: auto;
      }
      .main{
        height: auto;
        min-height: 100vh;
      }
      .prevText{
        flex-wrap: wrap;
        justify-content: center;
      }
    }
    @media (max-width: 700px){
      h1{
        font-size: 40px;
      }
      .prevText{
        text-align: center;
      .linedText{
        border: none;
      }

}
      form {
        button{
          width: 80%;
        }
      }
    }
  }

</style>