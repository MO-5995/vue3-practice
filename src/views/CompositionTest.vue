<template>
  <div>
    CompositionTest
    <p>{{ name }}</p>
    <p>{{ age }}</p>
    <p>ref:{{ nameRef }}</p>
    <p>reactive:{{ book.title }}</p>
    <p>reactive:{{ book.author[0] }}</p>
    <p>reactiveToRefs:{{ titleRef }}</p>
    <p>reactiveToRefs:{{ authorRef[1] }}</p>
    <button @click="btnClick">クリック</button>
  </div>
</template>

<script>
import { ref, reactive, toRefs } from "vue";
export default {
  setup() {
    let name = "鈴木";
    const age = 30;
    const nameRef = ref("田中");

    const book = reactive({
      title: "タイトル",
      author: ["上田", "伊藤"],
    });

    const booktoRefs = reactive({
      titleRef: "タイトル",
      authorRef: ["上田2", "伊藤2"],
    });

    const btnClick = (e) => {
      console.log(book.title);
      console.log(e);
    };
    console.log("setup");
    console.log(nameRef);
    console.log(nameRef.value);
    return {
      name,
      age,
      nameRef,
      book,
      ...toRefs(booktoRefs),
      btnClick,
    };
  },
  data() {
    return {
      number: 1,
      sports: "サッカー",
    };
  },
  created() {
    console.log("created");
    console.log(this);
  },
  mounted() {
    console.log("mounted");
  },
};
</script>
