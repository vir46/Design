<template id="sidebar">
    <div class="sidebar">
        <div class="sidebar-backdrop" @click="closeSidebarPanel" v-if="isPanelOpen"></div>
        <transition name="slide">
            <div v-if="isPanelOpen"
                 class="sidebar-panel">
                <slot></slot>
            </div>
        </transition>
    </div>
</template>


<script>
export default {
    name: 'Sidebar',
    props: {
        isPanelOpen: {
            type: Boolean,
            default: false,
        }
    },
    methods: {
        closeSidebarPanel() {
            this.$emit('closeSidebarPanel');
        }
    }
}
</script>

<style scoped>

.slide-enter-active,
.slide-leave-active
{
  transition: transform 0.2s ease;
}

.slide-enter,
.slide-leave-to {
  transform: translateX(-100%);
  transition: all 150ms ease-in 0s
}

.sidebar-backdrop {
  background-color: rgba(19, 15, 64, .4);
  width: 100%;
  height: 100%;
  position: fixed;
  top: 0;
  left: 0;
  cursor: pointer;
}

.sidebar-panel {
  overflow-y: auto;
  background-color: #fff;
  position: fixed;
  left: 0;
  top: 0;
  height: 100%;
  z-index: 999;
  padding: 3rem 20px 2rem 20px;
  width: 300px;
}
</style>