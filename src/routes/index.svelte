<script>
    import { goto } from '$app/navigation'
    let iinRegister = ''
    let usernameRegister = ''
    let passwordRegister = ''

    let usernameLogin = ''
    let passwordLogin = ''

    async function doLogin() {
        let myHeaders = new Headers()

        let formdata = new FormData()
        formdata.append('login', usernameLogin)
        formdata.append('password', passwordLogin)

        let requestOptions = {
            method: 'POST',
            credentials: 'include',
            headers: myHeaders,
            body: formdata,
        }
        fetch('http://localhost:8080/signin', requestOptions)
            .then((response) => response.status)
            .then((result) => {
                if (result == 200) goto('/user')
            })
            .catch((error) => console.log('error', error))
    }

    async function doRegistration() {
        let myHeaders = new Headers()

        let formdata = new FormData()
        formdata.append('login', usernameRegister)
        formdata.append('password', passwordRegister)
        formdata.append('iin', iinRegister)

        let requestOptions = {
            method: 'POST',
            credentials: 'include',
            headers: myHeaders,
            body: formdata,
        }

        fetch('http://localhost:8080/signup', requestOptions)
            .then((response) => response.status)
            .then((result) => console.log(result))
            .catch((error) => console.log('error', error))
    }
</script>

<div class="container">
    <div class="form-box">
        <h1>Уже зарегистрированы</h1>
        <div class="form signin-form">
            <input
                type="text"
                name="username"
                id="signin-username"
                placeholder="Имя пользователя"
                bind:value={usernameLogin}
            />
            <input
                type="password"
                name="password"
                id="signin-password"
                placeholder="Пароль"
                class="last-input"
                bind:value={passwordLogin}
            />
            <button type="submit" on:click={doLogin}>Войти</button>
        </div>
    </div>
    <div class="form-box">
        <h1>Впервые на Банк</h1>
        <div class="form signup-form">
            <input
                type="text"
                name="username"
                id="signup-username"
                placeholder="Имя пользователя"
                bind:value={usernameRegister}
            />
            <input
                type="password"
                name="password"
                id="signup-password"
                placeholder="Пароль"
                bind:value={passwordRegister}
            />
            <input
                type="number"
                name="iin"
                id="signup-iin"
                placeholder="ИИН"
                class="last-input"
                bind:value={iinRegister}
            />
            <button type="submit" on:click={doRegistration}
                >Зарегистрироваться</button
            >
        </div>
    </div>
</div>

<style>
    @import url('https://fonts.googleapis.com/css2?family=Roboto:wght@100;300;400&display=swap');

    .container {
        display: flex;
        justify-content: center;
        align-items: center;
        width: 100%;
        height: 80vh;
    }
    h1 {
        font-size: 40px;
        line-height: 1.2;
        color: #4a4a4a;
        margin-bottom: 25px;
    }
    * {
        font-weight: 400;
        outline: none;
        -webkit-tap-highlight-color: transparent;
    }
    .form-box {
        width: 365px;
        height: 400px;
        background-color: white;
        display: flex;
        flex-direction: column;
        padding: 40px 50px;
        margin: 0 5px;
        clear: both;
    }
    .form {
        display: flex;
        flex-direction: column;
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
        width: 100%;
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
