<template>
    <Preloader v-if="isLoading" />
    <router-view v-slot="{ Component }">
        <transition 
            enter-active-class="animated fadeIn" 
            leave-active-class="animated fadeOut" 
            mode="out-in" 
            :duration="600" 
            @after-leave="$root.$emit('triggerScroll')"
        >
            <component :is="Component" />
        </transition>
    </router-view>
    <SidebarModal />
    <BackToTop />
</template>

<script>
import Preloader from './components/Layouts/Preloader'
import SidebarModal from './components/Layouts/SidebarModal'
import BackToTop from './components/Layouts/BackToTop'

export default {
    name: 'App',
    components: {
        Preloader,
        SidebarModal,
        BackToTop,
    },
    data() {
        return {
            isLoading: true
        }
    },
    mounted() {
        setTimeout(() => {
            this.isLoading = false
        }, 2000)
    }
}
</script>