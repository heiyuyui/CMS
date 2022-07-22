<template>
  <div class="modal fade" id="productModal" tabindex="-1" role="dialog"
       aria-labelledby="exampleModalLabel" aria-hidden="true" ref="modal">
    <div class="modal-dialog modal-xl" role="document">
      <div class="modal-content border-0">
        <div class="modal-header text-black">
          <h5 class="modal-title" id="exampleModalLabel">
            <span>LINE Pay QRCode</span>
          </h5>
          <button type="button" class="btn-close btn-outline-secondary"
                  data-bs-dismiss="modal" aria-label="Close"></button>
        </div>
        <div>
          <img src="/img/logo.82b9c7a5.png" class="rounded mx-auto d-block" />
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-outline-secondary"
                  @click="$emit('update-order', tempOrder)">取消</button>
          <button type="button" class="btn btn-primary"
                  data-bs-dismiss="modal" @click="$emit('update-checkout')">確認
          </button>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import modalMixin from '@/mixins/modalMixin';

export default {
  name: 'LinePayModal',
  props: {
    order: {
      type: Object,
      default() { return {}; },
    },
  },
  data() {
    return {
      status: {},
      modal: '',
      tempOrder: {},
      isPaid: false,
    };
  },
  methods: {
  },
  emits: ['update-checkout'],
  mixins: [modalMixin],
  inject: ['emitter'],
  watch: {
    order() {
      this.tempOrder = this.order;
      this.isPaid = this.tempOrder.is_paid;
    },
  },
};
</script>
