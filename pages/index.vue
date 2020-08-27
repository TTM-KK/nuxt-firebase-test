<template>
  <div class="container">
    <!-- {{this.comments.content}}
    {{this.comments.avatar}}-->
  </div>
</template>

<script>
import firebase from "@/plugins/firebase";
import "firebase/firestore";

export default {
  data() {
    return {
      comments: [],
    };
  },
  created() {
    const db = firebase.firestore();

    // const comments = db.collection("comments").doc("DKBT8N3IF6k94CkImz3N");

    // functionにdocを入れる書き方だと怒られてしまう。
    // thenを使用しないで取得しようとすると取得に時間がかかる問題でコードが予期せぬ動作をするので非常に注意！！！！

    // オブジェクトをドキュメントID指定で取得するためのコード
    const comments = db.collection("comments").doc("DKBT8N3IF6k94CkImz3N");
    comments.get().then(function (comments) {
      console.log(comments.data());
    });

    // ドキュメントに登録されているオブジェクトをすべて取得するためのコード
    // const comments = db.collection("comments");
    // comments.get().then(function (comments) {
    //   comments.forEach(function (comment) {
    //     console.log(comment.data());
    //   });
    // });
  },
};
</script>

<style>
</style>
