<template>
    <div class="employee">
        <h1>List Of Employees</h1>

        <button type="button" class="btn btn-primary">Add New Employee</button>
        <table class="table">
            <tr class="head">
                <th>Id</th>
                <th>Name</th>
                <th>Department</th>
                <th>Salary</th>
                <th>Manager</th>
                <th>Action</th>
            </tr>
            <tr>
                <td>emp.id</td>
                <td>emp.name</td>
                <td>emp.deptId</td>
                <td>emp.salary</td>
                <td>emp.employeeManagerId</td>
                <td>
                    <button>Edit</button>
                    <button>Delete</button>
                </td>
            </tr>
            <tr class="tail" v-for="emp in Employees" v-bind:key="emp.id">
                <td>{{ emp.id }}</td>
                <td>{{ emp.name }}</td>
                <td>{{ emp.deptId }}</td>
                <td>{{ emp.salary }}</td>
                <td>{{ emp.employeeManagerId }}</td>
                <td>
                    <button>Edit</button>
                    <button>Delete</button>
                </td>
            </tr>
        </table>
    </div>
</template>
<script>
import axios from "axios";
import swal from "sweetalert2";
let employees = [
    {
        id: 1,
        name: "Ahmed Khalifa",
        salary: 20000,
        employeeManagerId: null,
        deptId: 1,
        dept: {
            id: 1,
            name: "IT",
            deptManagerId: 1,
            deptManager: null,
            employees: [],
        },
        employeeManager: null,
        departments: [],
        inverseEmployeeManager: [],
    },
    {
        id: 2,
        name: "Zain Ahmed ",
        salary: 15000,
        employeeManagerId: null,
        deptId: 2,
        dept: {
            id: 2,
            name: "CS",
            deptManagerId: 2,
            deptManager: null,
            employees: [],
        },
        employeeManager: null,
        departments: [],
        inverseEmployeeManager: [],
    },
    {
        id: 3,
        name: "Farida",
        salary: 25000,
        employeeManagerId: 1,
        deptId: 1,
        dept: {
            id: 1,
            name: "IT",
            deptManagerId: 1,
            deptManager: null,
            employees: [],
        },
        employeeManager: {
            id: 1,
            name: "Ahmed Khalifa",
            salary: 20000,
            employeeManagerId: null,
            deptId: 1,
            dept: null,
            employeeManager: null,
            departments: [],
            inverseEmployeeManager: [],
        },
        departments: [],
        inverseEmployeeManager: [],
    },
    {
        id: 4,
        name: "Shaker",
        salary: 15000,
        employeeManagerId: 1,
        deptId: 1,
        dept: {
            id: 1,
            name: "IT",
            deptManagerId: 1,
            deptManager: null,
            employees: [],
        },
        employeeManager: {
            id: 1,
            name: "Ahmed Khalifa",
            salary: 20000,
            employeeManagerId: null,
            deptId: 1,
            dept: null,
            employeeManager: null,
            departments: [],
            inverseEmployeeManager: [],
        },
        departments: [],
        inverseEmployeeManager: [],
    },
    {
        id: 5,
        name: "Darin",
        salary: 20000,
        employeeManagerId: 2,
        deptId: 2,
        dept: {
            id: 2,
            name: "CS",
            deptManagerId: 2,
            deptManager: null,
            employees: [],
        },
        employeeManager: {
            id: 2,
            name: "Zain Ahmed ",
            salary: 15000,
            employeeManagerId: null,
            deptId: 2,
            dept: null,
            employeeManager: null,
            departments: [],
            inverseEmployeeManager: [],
        },
        departments: [],
        inverseEmployeeManager: [],
    },
    {
        id: 6,
        name: "RMG",
        salary: 15000,
        employeeManagerId: 2,
        deptId: 2,
        dept: {
            id: 2,
            name: "CS",
            deptManagerId: 2,
            deptManager: null,
            employees: [],
        },
        employeeManager: {
            id: 2,
            name: "Zain Ahmed ",
            salary: 15000,
            employeeManagerId: null,
            deptId: 2,
            dept: null,
            employeeManager: null,
            departments: [],
            inverseEmployeeManager: [],
        },
        departments: [],
        inverseEmployeeManager: [],
    },
];
export default {
    name: "Employees-List",
    datat() {
        return {
            Employees: employees,
        };
    },
    setup() {},

    methods: {
        async getEmployees() {
            await axios
                .get("http://localhost:41630/api/Employees")
                .then((Response) => {
                    this.Employees = Response.data;
                    //console.log(this.Employees);
                    return this.Employees;
                })
                .catch((err) => {
                    if (err.Response) swal.fire(err.Response.data);
                });
        },
    },
    mounted: async function () {
        await axios
            .get("http://localhost:41630/api/Employees")
            .then((Response) => {
                this.Employees = Response.data;
                console.log(this.Employees);
            })
            .catch((err) => {
                if (err.Response) swal.fire(err.Response.data);
            });
    },
};
</script>
