<script>
export let showModal = false;
</script>

{#if showModal}
<div class="backdrop" on:click|self>
    <div class="modal">
        <slot></slot>
    </div>
</div>
{/if}


<style>
    .backdrop {
        position: fixed;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        z-index: 2;
    }
    .backdrop::after {
        content: "";
        position: absolute;
        height: 10%;
        top: 0;
        width: 100%;
        left: 0;
        height: 100%;
        z-index: 1;
        background-color: rgba(0, 0, 0, 0.8);
        box-shadow: inset 400px 100px 250px #1d2030;
        opacity: 0.9;
        bottom: 15%;
    }
    .modal {
        z-index: 4;
        font-size: x-large;
        position: relative;
        text-align: center;
        border-radius: 10px;
        padding: 10px;
        margin: 10% auto;
        max-width: 400px;
        border: solid 2px gray;
        background:  rgba(0, 0, 0, 0.8);
    }
</style>