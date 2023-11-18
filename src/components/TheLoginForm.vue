<template>
  <Form class="form" @submit="handleSubmit" :validation-schema="validationSchema">
    <div class="fields">
      <div class="wrapper">
        <LabelInput required name="email" label="E-mail">
          <div>
            <Field class="input" :validateOnInput="true" placeholder="mail@simmmple.com" :name="'email'" />
            <ErrorMessage class="error-message" :name="'email'" />
          </div>
          <button type="submit">Submit</button>
        </LabelInput>
      </div>
    </div>

  </Form>


</template>

<script setup>
import LabelInput from "./LabelInput.vue";
import { ref, computed } from 'vue';
import { Form, Field, ErrorMessage, configure } from 'vee-validate';
import * as Yup from 'yup';

const formFields = ref({
  email: '',
  // другие поля формы...
});


const validationSchema = computed(() =>
    Yup.object().shape({
      email: Yup.string().required('Email is required').email('Invalid email'),
    })
);

const handleSubmit = () => {
  // логика обработки отправки формы
  // например, вызов API для отправки данных
};
</script>

<style lang="scss" scoped>
  .form {
    margin-top: 28px;
  }
  .fields {
    display: flex;
    flex-direction: column;
    row-gap: 24px;
  }
  .wrapper {
    display: flex;
    flex-direction: column;
    row-gap: 12px;
  }
  .error-message {
    font-size: 12px;
    color: #c73f3f;
    font-weight: 400;
    margin-bottom: 0;
    margin-top: 4px;
    display: block;
  }
  .input {
    width: 100%;
    height: 50px;
    padding-left: 24px;
    padding-right: 24px;
    background: #FFF;
    border: 1px solid #E0E5F2;
    outline: none;
    transition: 0.2s all;
    color: var(--input);
    font-size: 14px;
    font-weight: 400;
    border-radius: 16px;
    &::placeholder {
      font-size: 14px;
      font-weight: 400;
      line-height: 100%;
      color: #A3AED0;
    }
    &:active, &:focus {
      border: 1px solid var(--interface);
    }
  }
</style>