<template>
  <div class="calculator">
    <h2>Посчитайте стоимость вашего сайта:</h2>
    <div class="fields-grid">
    <div class="field">

      <select id="siteType" v-model="selectedSiteType">
        <option disabled value="" hidden>Тип сайта</option>
        <option v-for="opt in siteTypes" :key="opt.value" :value="opt.value">
          {{ opt.label }}
        </option>
      </select>
    </div>
    <div class="field">

      <select id="cmsType" v-model="selectedCmsType">
        <option disabled value="" hidden>Тип CMS</option>
        <option v-for="opt in cmsTypes" :key="opt.value" :value="opt.value">
          {{ opt.label }}
        </option>
      </select>
    </div>
    <div class="field">

      <select id="topic" v-model="selectedTopic">
        <option disabled value="" hidden>Тематика сайта</option>
        <option v-for="opt in topics" :key="opt.value" :value="opt.value">
          {{ opt.label }}
        </option>
      </select>
    </div>
    <div class="field">

      <select id="design" v-model="selectedDesign">
        <option disabled value="" hidden>Дизайн сайта</option>
        <option v-for="opt in designs" :key="opt.value" :value="opt.value">
          {{ opt.label }}
        </option>
      </select>
    </div>
    <div class="field">

      <select id="extras" v-model="selectedExtras">
        <option disabled value="" hidden>Дополнительные услуги</option>
        <option v-for="opt in extras" :key="opt.value" :value="opt.value">
          {{ opt.label }}
        </option>
      </select>
    </div>
    <div class="field comment-field">

      <textarea id="comments" v-model="comments" rows="4" placeholder="Комментарии к проекту"></textarea>
    </div>
    </div>
    <div class="total">
      <span class="total-label">Стоимость проекта:</span>
      <span class="total-amount">{{ total }} <span class="currency">₽</span></span>
    </div>
    <button :disabled="!policyAgreement" @click="openModal">Связаться с нами</button>
    <div class="field policy">
  <label for="policy" class="custom-checkbox-label">
    <input type="checkbox" id="policy" v-model="policyAgreement" class="custom-checkbox-input" />
    <span class="custom-checkbox"></span>
    <span class="custom-checkbox-text privacy-text">Нажимая кнопку, я соглашаюсь с политикой конфиденциальности и даю разрешение на обработку моих персональных данных.</span>
  </label>
</div>
  </div>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue';

interface Option { label: string; value: string; price: number; }

const siteTypes = ref<Option[]>([
  { label: 'Лендинг', value: 'landing', price: 50000 },
  { label: 'Корпоративный сайт', value: 'corporate', price: 80000 },
  { label: 'Интернет-магазин', value: 'ecommerce', price: 120000 },
]);

const cmsTypes = ref<Option[]>([
  { label: 'Без CMS', value: 'none', price: 0 },
  { label: 'WordPress', value: 'wordpress', price: 20000 },
  { label: 'Drupal', value: 'drupal', price: 25000 },
]);

const topics = ref<Option[]>([
  { label: 'Бизнес', value: 'business', price: 0 },
  { label: 'Блог', value: 'blog', price: 0 },
  { label: 'Портфолио', value: 'portfolio', price: 0 },
]);

const designs = ref<Option[]>([
  { label: 'Шаблонный дизайн', value: 'template', price: 10000 },
  { label: 'Индивидуальный дизайн', value: 'custom', price: 30000 },
]);

const extras = ref<Option[]>([
  { label: 'SEO-оптимизация', value: 'seo', price: 15000 },
  { label: 'Поддержка 1 год', value: 'support', price: 25000 },
  { label: 'Контент-менеджмент', value: 'cms', price: 20000 },
]);

const selectedSiteType = ref('');
const selectedCmsType = ref('');
const selectedTopic = ref('');
const selectedDesign = ref('');
const selectedExtras = ref('');
const comments = ref('');

const total = computed(() => {
  const findPrice = (opts: Option[], val: string) => opts.find(o => o.value === val)?.price || 0;
  return (
    findPrice(siteTypes.value, selectedSiteType.value) +
    findPrice(cmsTypes.value, selectedCmsType.value) +
    findPrice(topics.value, selectedTopic.value) +
    findPrice(designs.value, selectedDesign.value) +
    findPrice(extras.value, selectedExtras.value)
  );
});

const policyAgreement = ref(false);
const emit = defineEmits(['open-modal']);
const openModal = () => emit('open-modal', total.value);
</script>

<style scoped>
.calculator {
  position: relative;
  overflow: hidden;
  background-image: linear-gradient(rgba(30, 30, 30, 0.8), rgba(30, 30, 30, 0.8)), url('~/assets/images/claclback.png');
  background-repeat: no-repeat;
  background-size: cover;
  background-position: 0 0;
  border-radius: 16px;
  padding: 2rem;
  margin-bottom: 1.5rem;
  color: #fff;
}

/* Background decorative image */
.calculator::before {
  content: "";
  position: absolute;
  width: 1131.06px;
  height: 1027.66px;
  top: -350px;
  left: -128px;
  background-image: url('~/assets/images/claclback.png');
  background-repeat: no-repeat;
  background-size: 250% 250%;
  background-position: center;
  
  mask: url('~/assets/images/claclback.png') no-repeat center/cover;
  transform: rotate(24deg);
  z-index: 0;
  pointer-events: none;
}

/* Ensure inner content stays above the decorative background */
.calculator > * {
  position: relative;
  z-index: 1;
}
  .calculator::before { display: none !important; }
.calculator h2 {
  font-size: 1.75rem;
  font-weight: 600;
  margin-bottom: 1.5rem;
}
.fields-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1rem;
}
.field {
  display: flex;
  flex-direction: column;
}
.field label {
  font-size: 0.875rem;
  margin-bottom: 0.5rem;
  color: #fff;
}
.field select,
.field textarea {
  /* width: 100%; */
  padding: 0.75rem 1rem;
  font-size: 0.875rem;
  color: #333;
  background-color: #fff;
  border: none;
  border-radius: 8px;
  box-shadow: 0 2px 6px rgba(0,0,0,0.1);
  outline: none;
}
.calculator select {
  appearance: none;
  background-image: url('@/assets/images/calc-arrow.png');
  background-repeat: no-repeat;
  background-position: right 0.5rem center;
  background-size: 1rem;
  padding-right: 2rem;
}
.field textarea {
  resize: none;
  min-height: 5rem;
}
.total {
  display: flex;
  align-items: baseline;
  margin-top: -3rem;
  position: relative;
  z-index: 1;
}
.total-label {
  font-size: 1rem;
  color: #fff;
  margin-right: 0.5rem;
}
.total-amount {
  font-size: 2rem;
  font-weight: 700;
  color: #fff;
}
.total-amount .currency {
  font-size: 1.5rem;
}
button {
  /* margin-top: 1.5rem; */
  width: 100%;
  padding: 0.75rem;
  font-size: 1rem;
  font-weight: 600;
  color: #fff;
  background: linear-gradient(258.13deg, #0804A1 -68.35%, #9278FA 71.73%);
  border: none;
  border-radius: 24px;
  cursor: pointer;
  transition: background 0.3s;
}
button:disabled {
  cursor: not-allowed;
}
.field.policy {
  display: flex;
  align-items: start;
  gap: 0.5rem;
  margin-top: 0.75rem;
}
.custom-checkbox-label {
  display: flex;
  align-items: flex-start;
  gap: 0.5rem;
}
.custom-checkbox-input {
  position: absolute;
  opacity: 0;
  width: 0;
  height: 0;
}
.custom-checkbox {
  position: relative;
  display: inline-block;
  width: 1.2rem;
  height: 1.2rem;
  aspect-ratio: 1 / 1;
  border: 2px solid #7D6AFE;
  background: #fff;
  border-radius: 0;
  box-sizing: border-box;
  margin-top: 0.1rem;
  transition: border-color 0.2s, background 0.2s;
}
.custom-checkbox-input:checked + .custom-checkbox {
  background: #fff;
  border-color: #7D6AFE;
}

.custom-checkbox::after {
  content: '✓';
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-size: 0.8rem;
  color: #7D6AFE;
  opacity: 0;
  transition: opacity 0.2s;
}

.custom-checkbox-input:checked + .custom-checkbox::after {
  opacity: 1;
}
.custom-checkbox-text {
  color: #CCC;
  font-size: 0.75rem;
  line-height: 1.2rem;
}

.field.policy label {
  color: #CCC;
  font-size: 0.75rem;
  line-height: 1.2rem;
}
.field.comment-field {
  grid-column: 3;
  grid-row: span 2;
}
/* Ensure comment field has the same width as site topic field */
textarea[name="comments"] {
  width: 100%;
}
@media (max-width: 1000px) {
  .fields-grid {
    grid-template-columns: 1fr;
  }
  .field.comment-field {
    grid-column: 1;
    grid-row: auto;
  }
  .total {
    flex-direction: column;
    align-items: flex-start;
    margin-top: 1rem;
  }
}
@media (min-width: 1024px) {
  .calculator h2 {
    font-family: Golos Text;
    font-weight: 600;
    font-size: 44px;
    line-height: 120%;
    letter-spacing: 0%;
    vertical-align: middle;
  }
  .calculator .field label,
  .calculator .field select,
  .calculator .field textarea {
    font-family: Golos Text;
    font-weight: 500;
    font-size: 16px;
    line-height: 120%;
    letter-spacing: 0%;
    vertical-align: middle;
  }
  .calculator .total-label {
    font-family: Golos Text;
    font-weight: 400;
    font-size: 24px;
    line-height: 120%;
    letter-spacing: 0%;
    vertical-align: middle;
  }
  .calculator .total-amount {
    font-family: Golos Text;
    font-weight: 500;
    font-size: 72px;
    line-height: 100%;
    letter-spacing: 0%;
  }
  .calculator .privacy-text {
    font-family: Golos Text;
    font-weight: 400;
    font-size: 16px;
    line-height: 120%;
    letter-spacing: 0%;
    vertical-align: middle;
  }
  button {
    font-family: Golos Text;
    font-weight: 600;
    font-size: 24px;
    line-height: 100%;
    letter-spacing: 0%;
  }
  .calculator .field.comment-field textarea {
    min-height: 10rem;
  }
}
</style>
