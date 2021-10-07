<template>
    <div class="carousel">
    <slot :currentSlide="currentSlide" />
        
    <!-- Navegacion -->
    <div v-if="navEnabled" class="navegar">
        <div class="toggle-page left">
            <i @click="prevSlide" class="fas fa-chevron-left"></i>
        </div>
        <div class="toggle-page right">
            <i @click="nextSlide" class="fas fa-chevron-right"></i>
        </div>
    </div>

    <!-- Paginacion -->
    <div v-if="paginacionEnabled" class="paginacion">
        <span
            @click="goToSlide(index)"
            v-for="(slide, index) in getSlideCount"
            :key="index"
            :class="{ active: index + 1 === currentSlide }">
        </span>
    </div>
    </div>
</template>

<script>
import { ref, onMounted } from "vue";
export default {
    props: ["startAutoPlay", "timeout", "navegacion", "paginacion"],
    setup(props) {
    const currentSlide = ref(1);
    const getSlideCount = ref(null);
    const autoPlayEnabled = ref(
        props.startAutoPlay === undefined ? true : props.startAutoPlay
    );
    const timeoutDuration = ref(props.timeout === undefined ? 5000 : props.timeout);
    const paginacionEnabled = ref(
        props.paginacion === undefined ? true : props.paginacion
    );
    const navEnabled = ref(props.navegacion === undefined ? true : props.navegacion);
    // next slide
    const nextSlide = () => {
        if (currentSlide.value === getSlideCount.value) {
        currentSlide.value = 1;
        return;
    }
    currentSlide.value += 1;
    };
    // previsualizacion slide
    const prevSlide = () => {
        if (currentSlide.value === 1) {
            currentSlide.value = 1;
        return;
    }
    currentSlide.value -= 1;
    };
    const goToSlide = (index) => {
    currentSlide.value = index + 1;
    };
    // autoplay
    const autoPlay = () => {
        setInterval(() => {
        nextSlide();
    }, timeoutDuration.value);
    };
    if (autoPlayEnabled.value) {
        autoPlay();
    }
    onMounted(() => {
        getSlideCount.value = document.querySelectorAll(".slide").length;
    });
    return {
        currentSlide,
        nextSlide,
        prevSlide,
        getSlideCount,
        goToSlide,
        paginacionEnabled,
        navEnabled,
    };
},
};
</script>

<style lang="scss">
.navegar {
    padding: 0 16px;
    height: 80%;
    width: 100%;
    position: absolute;
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 1;
.toggle-page {
    display: flex;
    flex: 1;
}
.right {
    justify-content: flex-end;
}
i {
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 50%;
    width: 40px;
    height: 40px;
    background-color: #2D46B9;
    color: #fff;
}
}.paginacion {
    position: absolute;
    bottom: 126px;
    width: 100%;
    display: flex;
    gap: 16px;
    justify-content: center;
    align-items: center;
    span {
    cursor: pointer;
    width: 20px;
    height: 20px;
    border-radius: 50%;
    background-color: #fff;
    box-shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.1), 0 1px 2px 0 rgba(0, 0, 0, 0.06);
  }
  .active {
    background-color: #2D46B9;
  }
  .absolute-div {
    position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
}

.carousel-caption h3 {
    display:table-cell;
    vertical-align: middle;
    text-align:center;
}

.item {
    position:relative;
}
}
</style>
