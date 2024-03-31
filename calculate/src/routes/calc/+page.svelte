<script>
    import{createEventDispatcher} from 'svelte';
    const dispatcher = createEventDispatcher();

    let num1 = 0;
    let num2 = 0;
    let action = '+';
    let result = 0;
    
    function calculate() {
        switch(action){
            case '+':
                result = num1 + num2;
                break;
                case '-':
                    result = num1 - num2;
                    break;
                    case '*':
                        result = num1 * num2;
                        break;
                        case '/':
                            result = num1 / num2;
                            break;
        }
        dispatcher('calculation', {result});
    }
</script>

<main>
<h1>Простой калькулятор</h1>

<input type="number" bind:value={num1} placeholder="Введите первое число" />
<select bind:value={action}>
    <option value="+">+</option>
    <option value="-">-</option>
    <option value="*">*</option>
    <option value="/">/</option>
</select>
<input type="number" bind:value={num2} placeholder="Введите второе число" />
<button on:click={calculate}>Посчитать</button>
{#if result !==0}
<p>Результат: {result}</p>
{/if}
</main>
<style>
    main{
        display: flex;
        flex-direction: column;
        align-items: center;
    }
    input, select, button {
        margin: 10px;
        padding: 5px;
        border: 1 px solid #ccc;
        border-radius: 3px;
    }
    button {
        background-color: blue;
        color: black;
    }
</style>