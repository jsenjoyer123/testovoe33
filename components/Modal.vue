<template>
  <div class="modal-overlay" @click.self="close">
    <div class="modal">
      <button class="modal__close" @click="close">&times;</button>
      <div class="modal__content">
        <h2 class="modal__title">Осталось совсем немного!</h2>
        <p>{{ message }}</p>
        <form @submit.prevent="submitForm">
          <div class="modal__row">
          <div class="modal__field">
            <input v-model="name" type="text" required placeholder="Имя" />
          </div>
          <div class="modal__field">
            <input v-model="phone" type="tel" required placeholder="Телефон" />
           </div>
           </div>
          <button type="submit" class="modal__submit">Оставить заявку</button>
          <div class="modal__policy">
            <label>
              <input type="checkbox" v-model="accepted" required />
              Нажимая кнопку, я соглашаюсь с политикой конфиденциальности и даю разрешение на обработку моих персональных данных.
            </label>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { defineProps, defineEmits, ref } from 'vue';

const props = defineProps<{ message: string }>();
const emit = defineEmits(['close', 'submit']);
const close = () => emit('close');

const name = ref('');
const phone = ref('');
const accepted = ref(false);

const submitForm = () => {
  emit('submit', { name: name.value, phone: phone.value, accepted: accepted.value });
  close();
};
</script>

<style scoped>
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  backdrop-filter: blur(8px);
  -webkit-backdrop-filter: blur(8px);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
}

.modal {
  background: #fff;
  position: relative;
  max-width: 600px;
  width: 90%;
  padding: 2rem;
  border-radius: 12px;
  box-shadow: 0 4px 16px rgba(0, 0, 0, 0.1);
}

.modal__close {
  position: absolute;
  top: 0.5rem;
  right: 0.5rem;
  background: none;
  border: none;
  font-size: 1.5rem;
  cursor: pointer;
}

.modal__content {
  margin-top: 1rem;
}

.modal__row {
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
  margin-bottom: 1rem;
}

.modal__field {
  flex: 1;
  min-width: 0;
}
  .modal__title {
    font-size: 1.75rem;
    font-weight: 700;
    margin-bottom: 0.5rem;
    color: #111;
  }
  .modal__content {
    margin-top: 1rem;
    text-align: center;
  }
  .modal__content p {
    font-size: 1rem;
    color: #555;
    margin-bottom: 1.5rem;
  }
  .modal__row {
    display: flex;
    gap: 1rem;
    flex-wrap: wrap;
    margin-bottom: 1.5rem;
  }
  .modal__field input {
    /* width: 100%; */
    padding: 0.75rem 1rem;
    background: #f2f4f9;
    border: none;
    border-radius: 8px;
    font-size: 1rem;
    color: #333;
  }
  .modal__submit {
    width: 100%;
    padding: 0.75rem;
    font-size: 1rem;
    background: linear-gradient(90deg, #6e56cf 0%, #8b71f7 100%);
    border: none;
    border-radius: 24px;
    color: #fff;
    cursor: pointer;
    transition: background 0.3s;
    margin-bottom: 1rem;
  }
  .modal__submit:hover {
    background: linear-gradient(90deg, #5b46b7 0%, #7960dd 100%);
  }
  .modal__policy {
    display: flex;
    align-items: flex-start;
    font-size: 0.75rem;
    color: #777;
  }
  .modal__policy input {
    margin-right: 0.5rem;
    margin-top: 0.25rem;
  }

@media (max-width: 768px) {
  .modal__row {
    flex-direction: column;
    gap: 0.5rem;
  }
  .modal__field {
    width: 100%;
    flex: none;
  }
  .modal__field input {
    width: 100%;
    box-sizing: border-box;
  }
  .modal {
    width: auto;
    max-width: 320px;
    margin: 0 20px;
    padding: 2rem 20px;
  }
}
</style>
