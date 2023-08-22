<template>
    <div class="backdrop" @click.self="hideMyModal">
        <div class="modal" :class="{success: type === 'success'}" ref="myModal">
        <div class="cancel-container">
            <button class="cancel" v-on:click="hideMyModal">
                <span>x</span>
            </button>
        </div>
        <div class="modal-body">
            <slot>default content</slot>
            <slot name="links"></slot>
        </div>
    </div>
    </div>
    
</template>


<script>
export default {
    name: "MyModal",
    props: {
        header: String,
        msg: String,
        type: String
    },
    methods: {
        hideMyModal(){
            this.$emit("close-modal");
        }
    }
}
</script>


<style scoped>

.backdrop{
    top: 0;
    position: absolute;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.2);
}
.modal {
    background-color: #fff;
    width: 800px;
    height: 600px;
    margin: 0 auto;
    border-radius: 8px;
}
.modal.error {
    background: rgba(151, 44, 44, 1);
    color: white;
}
.modal.success{
    background: rgb(9, 175, 9);
    color: white;
}
.modal .cancel-container{
    display: flex;
    flex-direction: row-reverse;
}
.modal .cancel-container button {
    color: red;
    font-size: 22px;
    width: 40px;
    height: 40px;
}

</style>
