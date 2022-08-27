<template>
  <div class="w-[700px] bg-[#ffffff] rounded items-center m-auto">
    <div
      class="
        w-full
        h-full
        flex
        justify-between
        items-center
        p-[15px]
        text-[18px]
        font-bold
        border-solid border-[#e5e5e5] border-b-2
      "
    >
      <div class="">
        {{ label }}
      </div>
      <button @click="handleDelModal" class="m-[8px]">
        <span>{{ icon }}</span>
      </button>
    </div>
    <div class="p-[15px]">
      <span class="font-normal my-[10px]">{{ subLable }}</span>
      <div class="w-full flex justify-between items-center mt-[15px] gap-2">
        <button
          class="
            w-[50%]
            p-[5px]
            text-[#337ab7] text-[14px] text-center
            border-2 border-solid border-[#337ab7]
            rounded
            font-medium
            break-all
          "
          @click="handleShowWantToBlock"
        >
          {{ contentText1 }}
        </button>
        <button
          class="
            w-[50%]
            p-[5px]
            text-[#337ab7] text-[14px] text-center
            border-2 border-solid border-[#337ab7]
            rounded
            font-medium
            break-all
          "
          @click="handleSetUnavailable"
        >
          {{ contentText2 }}
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Modal",
  props: {
    label: String,
    icon: String,
    subLable: String,
    contentText1: String,
    contentText2: String,
  },
  methods: {
    handleDelModal() {
      this.$emit("handleDelModal");
    },
    handleSetUnavailable() {
      this.$emit("handleSetUnavailable");
    },
    handleShowWantToBlock() {
      this.$emit("handleShowWantToBlock");
    },
  },
};
</script>

<style>
</style>
