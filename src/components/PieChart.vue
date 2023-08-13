<template>
    <div class="chart-container">
        <canvas ref="canvas"></canvas>
    </div>
</template>
  
<script>
import { ref, onMounted, onBeforeUnmount, watch } from 'vue'

export default {
    setup(props) {
        const canvas = ref(null)
        let chart = null
        // Sample data
        const data = ref([
            { value: 10, color: 'red' },
            { value: 20, color: 'blue' },
            { value: 30, color: 'green' },
            { value: 30, color: 'yellow' }

        ])

        onMounted(() => {
            const ctx = canvas.value.getContext('2d')
            let totalValue = data.value.reduce((total, item) => total + item.value, 0)
            let startAngle = 0

            // Draw the pie chart
            data.value.forEach(item => {
                let sliceAngle = 2 * Math.PI * item.value / totalValue

                drawPieSlice(
                    ctx,
                    canvas.value.width / 2,
                    canvas.value.height / 2,
                    Math.min(canvas.value.width / 2, canvas.value.height / 2),
                    startAngle,
                    startAngle + sliceAngle,
                    item.color
                )

                startAngle += sliceAngle
            })
        })

        const drawPieSlice = (ctx, centerX, centerY, radius, startAngle, endAngle, color) => {
            ctx.fillStyle = color
            ctx.beginPath()
            ctx.moveTo(centerX, centerY)
            ctx.arc(centerX, centerY, radius, startAngle, endAngle)
            ctx.closePath()
            ctx.fill()
        }

        onBeforeUnmount(() => {
            if (chart !== null) {
                chart = null;
            }
        })

        return { canvas }
    }
}
</script>

<style scoped>
.chart-container {
    width: 100%;
    max-width: 400px;
    height: 500px;
    padding-bottom: 50%;
    position: relative;
    margin:  auto;
}

canvas {
    position: absolute;
    width: 100%;
    height: 80%;
}
</style>
  