<template >
  <div class="w-full h-full m-auto items-center">
    <button class="p-[50px] m-10 text-[#111] bg-[blue]" @click="onToggleModal">
      clickMe
    </button>
  </div>
  <!-- nhớ thêm : lấy động -->
  <teleport to="body">
    <BaseModal v-if="isShowModal" @closeModal="onToggleModal">
      <template v-slot:title>
        <div
          class="
            flex
            justify-between
            items-start
            p-4
            rounded-t
            border-b
            dark:border-gray-100
          "
        >
          <h3
            class="text-xl font-semibold text-gray-900 dark:text-gray break-all"
          >
            <!-- {{ $t("reservation_calendar.modal.modal_label") }} -->
            reservation_calendar.modal.modal_lab
          </h3>
          <button
            @click="onToggleModal"
            class="
              text-gray-900
              bg-transparent
              hover:bg-gray-200 hover:text-gray-900
              rounded-lg
              text-sm
              p-1.5
              items-center
              dark:hover:bg-gray-600 dark:hover:text-white
            "
          >
            <span>X</span>
          </button>
        </div>
      </template>
      <template v-slot:content>
        <div class="p-6 space-y-6">
          <p class="text-base leading-relaxed break-all">
            <!-- {{ $t("`reservation_calendar.modal.close_reservation") }} -->
            reservation_calendar.modal.close_reservation
          </p>
        </div>
      </template>
      <template v-slot:foot>
        <div class="flex items-center p-6 space-x-2 rounded-b break-all">
          <button
            @click="onModalConfirm"
            class="
              text-white
              bg-blue-600
              font-medium
              rounded-lg
              text-sm
              inline-flex
              items-center
              px-5
              py-2.5
              text-center
              mr-2
              break-all
            "
          >
            <!-- {{ $t("`reservation_calendar.modal.close_reservation") }} -->
            reservation_calendar.modal.close_reservation
          </button>
          <button
            @click="onToggleModal"
            class="
              text-white
              bg-blue-600
              font-medium
              rounded-lg
              text-sm
              inline-flex
              items-center
              px-5
              py-2.5
              text-center
              mr-2
              break-all
            "
          >
            <!-- {{ reservation_calendar.modal.set_unavailable }} -->
            reservation_calendar.modal.set_unavailable
          </button>
        </div>
      </template>
    </BaseModal>
  </teleport>
  <teleport to="body">
    <BaseModal v-if="isShowModalConfirm" @closeModal=onModalConfirm>
      <template v-slot:content>
        <div class="p-6 space-y-6">
          <p class="text-base leading-relaxed break-all">
            reservation_calendar.modal.close_reservation
          </p>
        </div>
      </template>
      <template v-slot:foot>
        <div class="flex items-center p-6 space-x-2 rounded-b break-all">
          <button
            @click="onConfirmFinal"
            class="
              text-white
              bg-blue-600
              font-medium
              rounded-lg
              text-sm
              inline-flex
              items-center
              px-5
              py-2.5
              text-center
              mr-2
              break-all
            "
          >
            reservation_calendar.modal.close_reservation
          </button>
          <button
            @click="onModalConfirm"
            class="
              text-white
              bg-blue-600
              font-medium
              rounded-lg
              text-sm
              inline-flex
              items-center
              px-5
              py-2.5
              text-center
              mr-2
              break-all
            "
          >
            reservation_calendar.modal.set_unavailable
          </button>
        </div>
      </template>
    </BaseModal>
  </teleport>
  <teleport to="body">
    <BaseModal v-if="isConfirmFinal"  @closeModal=onConfirmFinal>
      <template v-slot:content>
        <div class="p-6 space-y-6">
          <p class="text-base leading-relaxed break-all">
            reservation_calendar.modal.close_reservation
          </p>
        </div>
      </template>
      <template v-slot:foot>
        <div class="flex items-center p-6 space-x-2 rounded-b break-all">
          <button
            @click="onConfirmFinal"
            class="
              text-white
              bg-blue-600
              font-medium
              rounded-lg
              text-sm
              inline-flex
              items-center
              px-5
              py-2.5
              text-center
              mr-2
              break-all
            "
          >
            OK
          </button>
        </div>
      </template>
    </BaseModal>
  </teleport>
</template>

<script>
import { ref } from "vue";
import Modal from "./components/Modal.vue";
export default {
  components: { BaseModal: Modal },
  name: "App",
  setup() {
    const isShowModal = ref(false);
    const isShowModalConfirm = ref(false);
    const isConfirmFinal = ref(false);
    const onToggleModal = () => {
      isShowModal.value = !isShowModal.value;
    };
    const onModalConfirm = () => {
      isShowModal.value = false;
      isShowModalConfirm.value = !isShowModalConfirm.value;
    };
    const onConfirmFinal = () => {
      isShowModalConfirm.value = false;
      isConfirmFinal.value = !isConfirmFinal.value;
    };
    return {
      isShowModal,
      isShowModalConfirm,
      isConfirmFinal,
      onToggleModal,
      onModalConfirm,
      onConfirmFinal,
    };
  },
};
</script>

<style>
</style>
