<template>
  <div class="backdrop" @click.self="closeModal">
    <div class="modal" :class="{ sale: theme === 'sale' }">
      <slot>default content</slot>
      <div class="actions">
        <slot name="links"></slot>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'Modal',

    props: {
      theme: {
        type: String,
        default: ''
      }
    },

    methods: {
      closeModal() {
        this.$emit('close')
      }
    },
  }
</script>

<style lang="scss" scoped>
.backdrop {
  top: 0;
  position: fixed;
  background: rgba(0, 0, 0, 0.5);
  height: 100%;
  width: 100%;
}
.modal {
  width: 400px;
  padding: 20px;
  margin: 100px auto;
  background: white;
  border-radius: 10px;

  &.sale {
    background: crimson;
    color: white;

    h1 {
      color: white;
    }

    .actions {
      &::v-deep a {
        color: white;
      }
    }
  }

  .actions {
    text-align: center;
    margin: 30px 0 10px;

    &::v-deep a {
      color: #333;
      padding: 8px;
      border: 1px solid #eee;
      border-radius: 4px;
      text-decoration: none;
      margin: 10px;
    }
  }
}

h1 {
  color: #03cfb4;
}

p {
  font-style: normal;
}
</style>