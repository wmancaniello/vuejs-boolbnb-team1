<script>
export default {
    props: {
        services: {
            type: Array,
        }
    },
    data() {
        return {
            showServices: false,
            baseUrl: "http://127.0.0.1:8000/storage/services",
        }
    },
    methods: {
        serviceModal() {
            this.showServices = !this.showServices;
            console.log(this.services);
        },
        closeModal(event) {
            if (event.target.classList.contains('ms_service-modal')) {
                this.showServices = false;
            }
        },
    }
}
</script>

<template>
    <!-- Modale servizi -->
    <button @click="serviceModal" class="btn ms_brown_btn mt-2 mb-2 me-2">Mostra tutti i servizi</button>

    <div class="modal ms_service-modal" :class="showServices ? 'd-block' : ''" tabindex="-1" aria-hidden="true" @click="closeModal">
        <div class="modal-dialog">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title">Tutti i servizi</h5>
                    <button type="button" class="btn-close" aria-label="Close" @click="serviceModal"></button>
                </div>
                <div class="modal-body">
                    <ul>
                        <li v-for="(service, index) in services" :key="index" class="d-flex align-items-center">
                            <img :src="`${baseUrl}/${service.icon}`" alt="Icona" />
                            <span class="ms-2">{{ service.name }}</span>
                        </li>
                    </ul>
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn ms_brown_btn" @click="serviceModal">Chiudi</button>
                </div>
            </div>
        </div>
    </div>
</template>


<style lang="scss" scoped>
.ms_service-modal {
    background: rgba(0, 0, 0, 0.5)
}

.ms_brown_btn {
    background-color: #705D3F;
    border: 1px solid #705D3F;
    color: white;

    &:hover {
        background-color: #F8F2EB;
        transition: all 0.7s;
        color: var(--primary-color);
        border: 1px solid #705D3F;
    }
}

ul {
    list-style: none;

    li {
        border: 1px solid #705D3F;
        color: #705D3F;
        border-radius: 5px;
        padding: 5px;
        margin: 5px;

        img {
            width: 20px;
            filter: invert(24%) sepia(25%) saturate(356%) hue-rotate(7deg) brightness(89%) contrast(85%);
        }
    }
}

</style>