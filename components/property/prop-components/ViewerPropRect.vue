<script setup lang="ts">
import { ElCol, ElInputNumber, ElRow } from 'element-plus';
import { reactive, Ref, watch } from 'vue';
import { ClientBridge, trackersMap } from '../../../CreatorViewerMiddleware';

const props = defineProps<{ modelValue: cvType.Rect , uuid : string, propName : string  }>();
const tracker = trackersMap.get(props.uuid + props.propName) as Ref<cvType.Rect>;

watch(tracker,()=>{
    internalValue.x = tracker.value.x;
    internalValue.y = tracker.value.y;
    internalValue.width = tracker.value.width;
    internalValue.height = tracker.value.height;
})

const internalValue = reactive({
    x: props.modelValue.x,
    y: props.modelValue.y,
    width: props.modelValue.width,
    height: props.modelValue.height,
})

watch(
    () => internalValue,
    (newVal) => {
        if(newVal.width == tracker.value.width && newVal.height == tracker.value.height && newVal.x == tracker.value.x && newVal.y == tracker.value.y) return;
        tracker.value.height = newVal.height;
        tracker.value.width = newVal.width;
        tracker.value.x = newVal.x;
        tracker.value.y = newVal.y;
        ClientBridge.modifyTargetProp(props.uuid, props.propName, newVal);
    },
    { deep: true }
)

</script>

<template>
        <ElRow :gutter="10">
        <ElCol :span="12">
            <div class="vec-field">
                <ElInputNumber size="small" controls-position="right" v-model="internalValue.x">
                    <template #prefix>
                        <span>X</span>
                    </template>
                </ElInputNumber>
            </div>
        </ElCol>
        <ElCol :span="12">
            <div class="vec-field">
                <ElInputNumber size="small" controls-position="right" v-model="internalValue.y">
                    <template #prefix>
                        <span>Y</span>
                    </template>
                </ElInputNumber>
                <!-- <CoordinateNumInput v-model="internalValue.height" color="#67a900"></CoordinateNumInput> -->
            </div>
        </ElCol>
    </ElRow>
    <ElRow :gutter="10" style="margin-top: 4px;">
        <ElCol :span="12">
            <div class="vec-field">
                <ElInputNumber size="small" controls-position="right" v-model="internalValue.width">
                    <template #prefix>
                        <span>W</span>
                    </template>
                </ElInputNumber>
            </div>
        </ElCol>
        <ElCol :span="12">
            <div class="vec-field">
                <ElInputNumber size="small" controls-position="right" v-model="internalValue.height">
                    <template #prefix>
                        <span>H</span>
                    </template>
                </ElInputNumber>
                <!-- <CoordinateNumInput v-model="internalValue.height" color="#67a900"></CoordinateNumInput> -->
            </div>
        </ElCol>

    </ElRow>
</template>

<style lang="css">
.vec-field {
    display: flex;
    align-items: center;
    gap: 4px;
    white-space: nowrap;
}

.vec-field .el-input-number {
    flex: 1;
    min-width: 0;
    width: 100%;
}

.vec-field .el-input-number .el-input-number__increase {
    width: 16px;
}

.vec-field .el-input-number .el-input-number__decrease {
    width: 16px;
}

/* 外部容器用于布局 */
.color-bar-wrapper {
    position: relative;
    display: inline-block;
}

/* 竖线条 */
.color-bar {
    position: absolute;
    top: 6px;
    bottom: 6px;
    left: 5px;
    width: 4px;
    background-color: #f56c6c;
    /* 只有这条竖线有颜色 */
    border-radius: 4px;
    z-index: 2;
    pointer-events: none;
    /* 让它不影响点击 */
}
</style>