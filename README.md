# vue-simple-datatable

&#x20;

A lightweight, reusable, and customizable Vue 3 table component with sorting, searching, and pagination. Built with Tailwind CSS for styling, this component is easy to integrate into any project and supports dynamic columns, custom slots, and actions.

## Features

- **Sorting**: Click on column headers to sort table data.
- **Searching**: Search across specified columns to filter rows dynamically.
- **Pagination**: Navigate through paginated data with customizable page sizes.
- **Custom Slots**: Use scoped slots to render custom content (e.g., images, buttons).
- **Dynamic Columns**: Define columns dynamically with options for sorting, searching, and custom rendering.
- **Tailwind CSS**: Styled with Tailwind CSS for a clean and modern look.

## Usage

### Basic Example

```vue
<script setup>
import TableComponent from 'vue-simple-datatable';

const categories = [
    { id: 1, name: 'Electronics', image: 'image-url' },
    { id: 2, name: 'Books', image: 'image-url' },
    { id: 3, name: 'Clothing', image: 'image-url' },
];

const columns = [
    { key: 'name', label: 'Name', searchable: true, sortable: true },
    { key: 'image', label: 'Image', slot: 'image-slot' },
];
</script>

<template>
    <div>
        <h1 class="text-2xl font-bold mb-4">Categories</h1>
        <TableComponent :data="categories" :columns="columns" :page-size="5">
            <template #image-slot="{ row }">
                <img :src="row.image" :alt="`Image for ${row.name}`" class="w-10 h-10 rounded-full" />
            </template>
        </TableComponent>
    </div>
</template>
```

### Example with Actions Column

```vue
<script setup>
import TableComponent from 'vue-simple-datatable';

const categories = [
    { id: 1, name: 'Electronics', image: 'https://via.placeholder.com/50' },
    { id: 2, name: 'Books', image: 'https://via.placeholder.com/60' },
    { id: 3, name: 'Clothing', image: 'https://via.placeholder.com/70' },
];

const columns = [
    { key: 'name', label: 'Name', searchable: true, sortable: true },
    { key: 'image', label: 'Image', slot: 'image-slot' },
    { key: 'actions', label: 'Actions', slot: 'actions-slot' },
];
</script>

<template>
    <div>
        <h1 class="text-2xl font-bold mb-4">Categories</h1>
        <TableComponent :data="categories" :columns="columns" :page-size="5">
            <template #image-slot="{ row }">
                <img :src="row.image" :alt="`Image for ${row.name}`" class="w-10 h-10 rounded-full" />
            </template>
            <template #actions-slot="{ row }">
                <div class="space-x-2">
                    <button class="bg-yellow-500 text-white px-2 py-1 rounded-md">Edit</button>
                    <button class="bg-red-500 text-white px-2 py-1 rounded-md">Delete</button>
                </div>
            </template>
        </TableComponent>
    </div>
</template>
```

## Column Definition

Each column object can have the following properties:

| Property     | Type    | Default | Description                                                          |
| ------------ | ------- | ------- | -------------------------------------------------------------------- |
| `key`        | String  | -       | The property name in the data object to display in the column.       |
| `label`      | String  | -       | The column header label.                                             |
| `sortable`   | Boolean | `false` | Whether the column is sortable.                                      |
| `searchable` | Boolean | `false` | Whether the column is included in the search query.                  |
| `slot`       | String  | -       | The name of the custom slot to use for rendering the column content. |

## Props

| Prop       | Type   | Default | Description                                                                    |
| ---------- | ------ | ------- | ------------------------------------------------------------------------------ |
| `data`     | Array  | `[]`    | The array of objects representing the table data.                              |
| `columns`  | Array  | `[]`    | An array of column definitions with keys like `key`, `label`, `sortable`, etc. |
| `pageSize` | Number | `5`     | The number of rows displayed per page.                                         |

## License

This project is licensed under the MIT License.

