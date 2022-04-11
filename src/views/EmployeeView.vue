<template>
    <div class="container">
        <Employees />
    </div>
</template>

<script>
// @ is an alias to /src
import Employees from "@/components/company/Employees-List.vue";

export default {
    name: "EmployeeView",
    components: {
        Employees,
    },
};
</script>
