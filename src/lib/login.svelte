<script>
    $: isRegister = false;

    const toggleForm = (evt) => {
        if (evt.code == 'Space' || evt.code == 'Enter' || evt.type == 'click') {
            isRegister = !isRegister;
        }
    }
</script>


<main>
    <form action="">
        <div class="fieldset">
            <label for="email">
                Email
                <input id="email" type="text" required>
            </label>
        </div>

        <div class="fieldset">
            <label for="password">
                Password
                <input id="password" type="password" required>
            </label>
        </div>

        {#if isRegister}
            <div class="fieldset">
                <label for="passwordConfirmation">
                    Confirm Password
                    <input id="passwordConfirmation" type="password" required>
                </label>
            </div>
        {/if}
        
        {#if !isRegister}     
            <div class="fieldset">
                <button>Submit</button>
            </div>
        {:else}
            <div class="fieldset">
                <button>Register</button>
            </div>
        {/if}
    </form>

    <!-- svelte-ignore a11y-no-noninteractive-tabindex -->
    <span tabindex="0" on:click={toggleForm} on:keydown={toggleForm}>
        Click here to
        {#if !isRegister}
            register
        {:else}
            login
        {/if}
    </span>
</main>


<style>

    main {
        max-width: 600px;
        padding: 4rem 4rem 2rem 4rem;
        background-color: var(--google-blue);
        border-radius: 4px;
        color: white;
    }

    form {
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    .fieldset {
        width: 100%;
        margin-bottom: 1rem;
    }

    input {
        width: 100%;
        line-height: 2rem;
        border: none;
        padding-left: 1rem;
    }

    input:focus, input:hover {
        outline: none;
        box-shadow: 0px 0px 5px var(--google-grey);
    }

    span {
        color: white;
        cursor: pointer;
    }
</style>