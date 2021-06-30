<template>
    <div class="backdrop" @click.self="closeModal">
        <div class="modal" :class="{ sale: theme === 'sale' }">
            <slot></slot>
            <div class="actions">
                <slot name="links" />

            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        theme: {
            type: String,
            default: ''
        }
    },
    methods: {
        closeModal() {
            this.$emit('close', this);
        }
    },
}
</script>

<style>
    .modal {
        width: 400px;
        padding: 20px;
        margin: 100px auto;
        background: #fff;
        border-radius: 10px;
    }

    .backdrop {
        top: 0;
        position: fixed;
        background: rgb(0, 0, 0, 0.5);
        width: 100%;
        height: 100%;
    }

    .modal.sale {
        background: crimson;
        color: white;
    }

    .modal.sale.h1 {
        color: white;
    }

    .modal .actions a {
        color: #333;
        padding: 8px;
        border: 1px solid #eee;
        border-radius: 4px;
        text-decoration: none;
        margin: 10px;
    }

    .modal.sale .actions a {
        color: #eee;
    }   
</style>