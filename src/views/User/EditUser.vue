<template>
    <a-table :columns="columns" :data-source="dataSource" bordered>
        <template #bodyCell="{ column, text, record }">
            <template v-if="['name', 'age', 'address'].includes(column.dataIndex)">
                <div>
                    <a-input v-if="editableData[record.key]" v-model:value="editableData[record.key][column.dataIndex]"
                        style="margin: -5px 0" />
                    <template v-else>
                        {{ text }}
                    </template>
                </div>
            </template>
            <template v-else-if="column.dataIndex === 'operation'">
                <div class="editable-row-operations">
                    <span v-if="editableData[record.key]">
                        <a-typography-link @click="save(record.key)">Save</a-typography-link>
                        <a-popconfirm title="Sure to cancel?" @confirm="cancel(record.key)">
                            <a>Cancel</a>
                        </a-popconfirm>
                    </span>
                    <span v-else>
                        <a @click="edit(record.key)">Edit</a>
                    </span>
                </div>
            </template>
        </template>
    </a-table>
</template>
<script>
import { cloneDeep } from 'lodash-es';
import { defineComponent, reactive, ref } from 'vue';
import axios from 'axios';

const columns = [
    {
        title: 'name',
        dataIndex: 'name',
        width: '25%',
    },
    {
        title: 'age',
        dataIndex: 'age',
        width: '15%',
    },
    {
        title: 'address',
        dataIndex: 'address',
        width: '40%',
    },
    {
        title: 'operation',
        dataIndex: 'operation',
    },
];

export default defineComponent({
    setup() {
        const dataSource = ref([]);
        const editableData = reactive({});
        const edit = (key) => {
            editableData[key] = cloneDeep(
                dataSource.value.filter((item) => key === item.key)[0]
            );
        };
        const save = (key) => {
            Object.assign(
                dataSource.value.filter((item) => key === item.key)[0],
                editableData[key]
            );
            delete editableData[key];
        };
        const cancel = (key) => {
            delete editableData[key];
        };

        axios.get('/api/users').then((response) => {
            dataSource.value = response.data;
        });

        return {
            dataSource,
            columns,
            editingKey: '',
            editableData,
            edit,
            save,
            cancel,
        };
    },
});
</script>
<style scoped>
.editable-row-operations a {
    margin-right: 8px;
}
</style>