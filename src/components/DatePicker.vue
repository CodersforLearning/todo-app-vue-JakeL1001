<template>
    <Datepicker v-model="date"></Datepicker>
</template>

<script>
    import Datepicker from 'vue3-date-time-picker';
    import 'vue3-date-time-picker/dist/main.css'
    import 'vue3-date-time-picker/src/Vue3DatePicker/style/main.scss';
    
    export default {
        components: { Datepicker },
        data() {
            return {
                date: '',
            };
        }
    }
</script>

<style scoped>
.dp__theme_dark {
    --dp-background-color: #212121;
    --dp-text-color: #ffffff;
    --dp-hover-color: #484848;
    --dp-hover-text-color: #ffffff;
    --dp-hover-icon-color: #959595;
    --dp-primary-color: #005cb2;
    --dp-primary-text-color: #ffffff;
    --dp-secondary-color: #a9a9a9;
    --dp-border-color: #2d2d2d;
    --dp-border-color-hover: #aaaeb7;
    --dp-disabled-color: #737373;
    --dp-scroll-bar-background: #212121;
    --dp-scroll-bar-color: #484848;
    --dp-success-color: #00701a;
    --dp-icon-color: #959595;
    --dp-danger-color: #e53935;
}
</style>