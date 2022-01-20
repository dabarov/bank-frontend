<script>
    let login = ''
    let role = ''
    let iin = ''
    let created_at = ''

    fetch('http://localhost:8080/user', {
        credentials: 'include',
    })
        .then((response) => response.json())
        .then((result) => {
            login = result.login
            role = result.role
            iin = result.iin
            created_at = result.created_at
        })
        .catch((error) => console.log('error', error))

    let wallets = []
    let myHeaders = new Headers()

    fetch('http://localhost:8081/wallet', {
        credentials: 'include',
    })
        .then((response) => response.json())
        .then((result) => {
            wallets = result
        })
        .catch((error) => console.log('error', error))

    async function create() {
        let myHeaders = new Headers()

        fetch(`http://localhost:8081/wallet/create/${iin}`, {
            method: 'POST',
            credentials: 'include',
            headers: myHeaders,
        })
            .then((response) => response.status)
            .then((result) => console.log(result))
            .catch((error) => console.log('error', error))
    }

    let walletDepositID = ''
    let depositAmount = ''
    async function deposit() {
        let myHeaders = new Headers()

        let formdata = new FormData()
        formdata.append('walletID', walletDepositID)
        formdata.append('amount', depositAmount)

        let requestOptions = {
            method: 'POST',
            credentials: 'include',
            headers: myHeaders,
            body: formdata,
        }

        fetch('http://localhost:8081/wallet/deposit', requestOptions)
            .then((response) => response.status)
            .then((result) => console.log(result))
            .catch((error) => console.log('error', error))
    }

    let walletFromID = ''
    let walletToID = ''
    let transferAmount = ''
    async function transfer() {
        let myHeaders = new Headers()

        let formdata = new FormData()
        formdata.append('walletFromID', walletFromID)
        formdata.append('walletToID', walletToID)
        formdata.append('amount', transferAmount)

        let requestOptions = {
            method: 'POST',
            credentials: 'include',
            headers: myHeaders,
            body: formdata,
        }

        fetch('http://localhost:8081/wallet/transfer', requestOptions)
            .then((response) => response.status)
            .then((result) => console.log(result))
            .catch((error) => console.log('error', error))
    }
</script>

<div class="container">
    <h1>{login}</h1>
    <ul>
        <li><strong>ROLE:</strong> {role}</li>
        <li><strong>IIN:</strong> {iin}</li>
    </ul>

    <h2>Ваши кошельки:</h2>
    {#each wallets as wallet}
        <hr />
        <ul>
            <li><strong>ID:</strong> {wallet.id}</li>
            <li><strong>BALANCE:</strong> {wallet.balance}</li>
        </ul>
    {/each}

    <button on:click={create}>Создать новый кошелек</button>

    <h2>Пополнить кошелек:</h2>
    <input
        type="text"
        name="walletDepositID"
        id="walletDepositID"
        placeholder="ID кошелька"
        bind:value={walletDepositID}
    />
    <input
        type="number"
        name="amount"
        id="depositAmount"
        placeholder="Количество"
        class="last-input"
        bind:value={depositAmount}
    />
    <button type="submit" on:click={deposit}>Пополнить</button>

    <h2>Сделать перевод:</h2>
    <input
        type="text"
        name="walletFromID"
        id="walletFromID"
        placeholder="ID кошелька откуда"
        bind:value={walletFromID}
    />
    <input
        type="text"
        name="walletToID"
        id="walletToID"
        placeholder="ID кошелька куда"
        bind:value={walletToID}
    />
    <input
        type="number"
        name="amount"
        id="transferAmount"
        placeholder="Количество"
        class="last-input"
        bind:value={transferAmount}
    />
    <button type="submit" on:click={transfer}>Перевести</button>
</div>

<style>
    .container {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        margin: auto auto;
        width: 100%;
        background-color: white;
        padding: 50px 0;
    }
    ul {
        list-style-type: none;
    }
    li {
        font-family: Roboto-Regular, 'Roboto-Regular', Helvetica, Arial,
            sans-serif;
        font-size: 17px;
        line-height: 1.2;
        letter-spacing: normal;
        color: inherit;
        display: block;
        width: 100%;
    }
    h1 {
        font-family: Roboto-Bold, 'Roboto-Bold', Helvetica, Arial, sans-serif;
        text-align: center;
        font-size: 50px;
        margin: 0;
        line-height: 1.2;
        letter-spacing: normal;
        width: 100%;
        color: #4a4a4a;
        font-weight: normal;
        padding: 0;
        overflow: hidden;
        white-space: nowrap;
    }
    h2 {
        font-family: Roboto-Bold, 'Roboto-Bold', Helvetica, Arial, sans-serif;
        text-align: center;
        margin-bottom: 10px;
        font-size: 30px;
        line-height: 1;
        letter-spacing: normal;
        width: 100%;
        color: #4a4a4a;
        font-weight: normal;
        padding: 0;
        overflow: hidden;
        white-space: nowrap;
    }
    input {
        height: 19px;
        width: 335px;
        font-size: 17px;
        background-color: white;
        border: 1px solid #ddd;
        border-bottom: none;
        color: #4a4a4a;
        padding: 23px 15px;
        line-height: 1.2;
    }
    .last-input {
        border-bottom: 1px solid #ddd;
    }
    button {
        cursor: pointer;
        display: block;
        width: 50%;
        height: 60px;
        padding: 0 15px;
        background-color: #0089d0;
        color: #fff;
        border: none;
        position: relative;
        font-size: 17px;
        border-radius: 2px;
        margin: 10px auto 8px;
        transition: all 0.2s ease-in-out;
    }
    button:hover {
        background: #006aa0;
    }
</style>
