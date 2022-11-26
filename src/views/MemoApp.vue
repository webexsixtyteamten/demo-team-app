<template>
  <h1>Vue メモ</h1>
  <div class="memo-list">
    <ul class="memo-list__container">
      <li class="memo" v-for="(memo, index) in memos" :key="index">
        <div class="memo__checkbox">
          <input type="checkbox" />
        </div>
        <div class="memo__text">{{ memo.memo }}</div>
        <button class="memo__delete" v-on:click="deleteButton(index)">
          削除
        </button>
      </li>
    </ul>
  </div>
  <div class="add-memo-field">
    <input class="add-memo-field__input" type="text" v-model="content" />
    <button class="add-memo-field__button" v-on:click="addButton">追加</button>
  </div>
</template>

<script>
// import { functionExpression } from "@babel/types"

export default {
  data() {
    return {
      memos: [],
    }
  },
  mounted() {
    if (localStorage.memos) {
      this.memos = JSON.parse(localStorage.memos)
    }
  },
  methods: {
    addButton: function () {
      if (this.content !== "") {
        const newMemo = {
          memo: this.content,
        }
        this.memos.push(newMemo)
        localStorage.memos = JSON.stringify(this.memos)
        this.content = ""
        console.log(localStorage.memos)
      }
    },
    deleteButton: function (index) {
      this.memos.splice(index, 1)
      localStorage.memos = JSON.stringify(this.memos)
    },
  },
}
</script>

<style scoped>
.memo-list {
  padding-left: 5rem;
  padding-right: 5rem;
  display: flex;
  flex-direction: column;
  align-items: stretch;
  max-width: 512px;
  margin-left: auto;
  margin-right: auto;
}

.memo-list__container {
  padding: 0;
}

.memo {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0.5rem;
  border-radius: 5px;
}

.memo:hover {
  color: white;
  background-color: #b23b61;
}

.memo__text {
  margin-left: 2rem;
  text-align: left;
}

.memo__text--done {
  text-decoration-line: line-through;
}

.memo__delete {
  margin-left: 1rem;
  padding: 0.5rem 0.5rem;
  border: solid 1px black;
  border-radius: 5px;
  background-color: white;
}

.memo__delete:hover {
  background-color: #b2ae3b;
  border-radius: 5px;
}

.add-memo-field {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.add-memo-field__input {
  padding: 10px;
}
.add-memo-field__button {
  padding: 0.5rem 0.5rem;
  border: solid 1px black;
  border-radius: 5px;
  background-color: white;
}

.add-memo-field__button:hover {
  background-color: #b2ae3b;
  border-radius: 5px;
}
</style>
