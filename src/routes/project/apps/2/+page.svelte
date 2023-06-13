<h1>Учет расходов</h1>

<label>
    <h2>Название</h2>
    <input bind:value={newName} type="text">
</label>
<label>
    <h2>Сумма</h2>
    <input bind:value={newAmount} type="number">
    <button on:click={() => addExpense()}>Добавить</button>
</label>

<table>
    <thead>
        <tr>
            <th>Название</th>
            <th>Сумма</th>
            <th>Действия</th>
        </tr>
    </thead>
    <tbody>
        {#each expenses as expense, i}
            <tr>
                <td><div>{expense.name}</div></td>
                <td><div>{expense.amount}</div></td>
                <td><button on:click={() => deleteExpense(i)}>Удалить</button></td>
            </tr>
        {/each}
    </tbody>
</table>

<script>
    let expenses = [];

    let newName = '';
    let newAmount = '';

    function addExpense(){
        const obj = {
            name: newName,
            amount: parseInt(newAmount),
        };
        expenses.push(obj);
        expenses = expenses;
        newName = '';
        newAmount = '';
    }

    function deleteExpense(index){
        expenses.splice(index, 1);
        expenses = expenses;
    }
</script>

<style>
    label{
        display: block;
        margin-bottom: 10px;
    }

    input{
        padding: 5px;
        margin-right: 10px;
        border: 1px solid #ccc;
        border-radius: 5px;
        width: 150px;
    }

    table{
        margin-top: 20px;
        width: 100%;
        border-collapse: collapse;
    }

    td{
        padding: 8px;
        border: 1px solid #ccc;
        text-align: left;
    }

    th{
        padding: 8px;
        border: 1px solid #ccc;
        background-color: #eee;
        text-align: left;
    }

    button{
        padding: 5px 10px;
        background-color: green;
        color: #eee;
        border: none;
        border-radius: 5px;
        cursor: pointer;
    }

    h1{
        font-size: 32px;
        margin-bottom: 20px;
    }

    h2{
        font-weight: 300;
    }
</style>