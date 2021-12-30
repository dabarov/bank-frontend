<script>
    let iin = ''
    let login = ''
    let password = ''
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
            />
            <input
                type="password"
                name="password"
                id="signin-password"
                placeholder="Пароль"
                class="last-input"
            />
            <button type="submit">Войти</button>
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
            />
            <input
                type="password"
                name="password"
                id="signup-password"
                placeholder="Пароль"
            />
            <input type="number" name="iin" id="signup-iin" placeholder="ИИН" class="last-input"/>
            <button type="submit">Зарегистрироваться</button>
        </div>
    </div>
</div>

<style>
    @import url('https://fonts.googleapis.com/css2?family=Roboto:wght@100;300;400&display=swap');
    :global(body) {
        background-color: rgb(240, 240, 240);
        font-family: 'Roboto', sans-serif;
        font-size: 14px;
    }
    .container {
        display: flex;
        justify-content: center;
        align-items: center;
        width: 100%;
        height: 100vh;
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
        transition: all .2s ease-in-out;
    }
    button:hover {
        background: #006aa0;
    }
</style>
