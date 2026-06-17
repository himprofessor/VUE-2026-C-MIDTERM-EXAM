<template>

    <div class="card-parent">
        <div class="card">
            <slot></slot>
        </div>
    </div>



</template>



<style>
.card-parent {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: row;
    width: 800px;
}

.card {
    display: flex;
    flex-direction: column;
    width: 500px;
    border: 1px solid gray;
    padding: 30px;
    margin: 10px;
    border-radius: 10px;

}

.btn {
    display: flex;
    justify-content: flex-end;
    gap: 20px;
}

button {
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}

.btn-pending {
    background-color: #f39c12;
    /* Orange for pending */
    color: white;
}

.btn-complete {
    background-color: #27ae60;
    /* Green for complete */
    color: white;
}

#del {
    background-color: red;
    color: white;
}

#com {
    background-color: #27ae60;
    color: #fcfdfc;
}
#not{
    margin-top: 200px;
    text-align: center;
    font-size: 20px;
}
</style>
