<header>
    <nav>
        <a href="/">Мой Банк</a>
        <a href="/user">Профиль</a>
        </nav>
</header>

<slot />

<style>
    :global(body) {
        background-color: rgb(240, 240, 240);
        font-family: 'Roboto', sans-serif;
        font-size: 14px;
        padding: 0;
        margin: 0;
    }
    header {
        margin: 0;
        padding: 0;
        width: 100%;
        font-family: Roboto-Regular, Arial, Helvetica, sans-serif;
        font-size: 17px;
        line-height: 1.2;
        background: #4a4a4a;
        letter-spacing: normal;
    }
    nav {
        height: 100%;
        height: 74px;
        margin-left: 40px;
    }
    a {
        cursor: pointer;
        text-decoration: none;
        color: #f2f2f2;
        margin-right: 20px;
        transition: all 0.2s ease-out;
        padding: 25px 0 29px;
        display: block;
        float: left;
    }
    a:hover {
        color: #f14635;
        text-decoration: none;
    }
</style>
