<script setup lang="ts">
import { ElCol, ElRow } from 'element-plus';
import { reactive, Ref, watch } from 'vue';
import { ClientBridge, trackersMap } from '../../../CreatorViewerMiddleware';
import CoordinateNumInput from '../../CoordinateNumInput.vue';

const props = defineProps<{ modelValue: cvType.Vec3, uuid : string, propName : string  }>();

const tracker = trackersMap.get(props.uuid + props.propName) as Ref<cvType.Vec3>;

watch(tracker,()=>{
    internalValue.x = tracker.value.x;
    internalValue.y = tracker.value.y;
    internalValue.z = tracker.value.z;
})

const internalValue = reactive({
    x: props.modelValue.x,
    y: props.modelValue.y,
    z: props.modelValue.z,
})

watch(
    internalValue,
    (newVal) => {
        console.log(`on ${props.uuid}  ${props.propName}  vec3 changed `, newVal);
        if(newVal.x == tracker.value.x && newVal.y == tracker.value.y && newVal.z == tracker.value.z) return;
        tracker.value.x = newVal.x;
        tracker.value.y = newVal.y;
        tracker.value.z = newVal.z;
        ClientBridge.modifyTargetProp(props.uuid, props.propName, newVal);
    },
    { deep: true }
)

</script>

<template>
    <ElRow :gutter="10">
        <ElCol :span="8">
            <div class="vec-field">
                <CoordinateNumInput v-model="internalValue.x" color="#cb2600"></CoordinateNumInput>
            </div>
        </ElCol>
        <ElCol :span="8">
            <div class="vec-field">
                <CoordinateNumInput v-model="internalValue.y" color="#67a900"></CoordinateNumInput>
            </div>
        </ElCol>
        <ElCol :span="8">
            <div class="vec-field">
                <CoordinateNumInput v-model="internalValue.z" color="#2c7eed"></CoordinateNumInput>
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
}
.vec-field .el-input-number .el-input-number__increase  {
    width: 16px;
}

.vec-field .el-input-number .el-input-number__decrease  {
    width: 16px;
}
</style>


