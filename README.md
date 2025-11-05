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
