## Vue 2 → Vue 3 매핑 요약

- 상태 관리: `data()` → `ref` / `reactive`
- 파생 데이터: `computed` 옵션 → `computed()` 함수
- 메서드: `methods` 옵션 → `<script setup>` 내부 함수
- 감시자: `watch` 옵션 → `watch()` 함수
- 라이프사이클 훅: `beforeDestroy/destroyed` → `onBeforeUnmount/onUnmounted`

---

### 상세 매핑 표

| 분류 | Vue 2 | Vue 3 (Composition) |
|---|---|---|
| 상태 | `data()` | `ref()`, `reactive()` |
| 파생 | `computed: { ... }` | `computed(() => ...)` |
| 메서드 | `methods: { fn() {} }` | `function fn() {}` ( `<script setup>` ) |
| 감시 | `watch: { x(n,o){...} }` | `watch(x, (n,o) => { ... })` |
| 훅(생성) | `beforeCreate / created` | (setup 시점) |
| 훅(마운트) | `beforeMount / mounted` | `onBeforeMount / onMounted` |
| 훅(업데이트) | `beforeUpdate / updated` | `onBeforeUpdate / onUpdated` |
| 훅(언마운트) | `beforeDestroy / destroyed` | `onBeforeUnmount / onUnmounted` |
| props | `props: { title: String }` | `defineProps({ title: String })` |
| 자식 등록 | `components: { A }` | `import A from ...` 후 템플릿에서 바로 사용 |

---

### 최소 변환 예

**Vue 2**
```vue
<script>
export default {
  data(){ return { msg: 'Hello' } },
  computed: { upper(){ return this.msg.toUpperCase() } },
  methods: { shout(){ console.log(this.upper) } }
}
</script>
```
---
###t 스크린샷
<img width="1238" height="336" alt="E01-instance" src="https://github.com/user-attachments/assets/504cac02-9018-4d57-9a80-64a1409de960" />
<img width="1236" height="265" alt="E02-reactive" src="https://github.com/user-attachments/assets/cff0b774-fd55-41d9-91ec-da901d70d14e" />
<img width="1238" height="317" alt="E03-binding" src="https://github.com/user-attachments/assets/5859e3dc-24bc-487b-b2b1-6bc03072e12e" />
<img width="1244" height="544" alt="E04-directives" src="https://github.com/user-attachments/assets/92739eb3-0e0e-4f47-8f7d-7cf7b3ae753a" />
<img width="1238" height="317" alt="E05-ParentComponent" src="https://github.com/user-attachments/assets/356e9aaf-cfa1-432a-b86d-a22dd068c3be" />
<img width="452" height="295" alt="E06-ParentComponent" src="https://github.com/user-attachments/assets/8e6c4898-6f86-44d0-a370-096a5f7398c1" />
<img width="790" height="425" alt="E07-OptionsAPI" src="https://github.com/user-attachments/assets/61b41a43-1598-4afe-9e6e-187e112b7211" />
<img width="607" height="352" alt="E08-compositionAPI" src="https://github.com/user-attachments/assets/87b7c453-6ca3-4a3f-82a7-1de55e40de11" />
<img width="681" height="436" alt="E09-compositionAPI2" src="https://github.com/user-attachments/assets/618f14d0-5c54-414f-bc72-08e566b4af74" />
<img width="381" height="226" alt="E10-ref" src="https://github.com/user-attachments/assets/6cbefe66-ae1b-4a12-935c-de991a1848fe" />
<img width="436" height="224" alt="E11-reactive" src="https://github.com/user-attachments/assets/95549571-1960-4dd6-82bc-945ad45d1499" />
<img width="448" height="212" alt="E12-refcomponent" src="https://github.com/user-attachments/assets/b7d355a6-a88b-43c5-a2c5-91d178edd193" />
