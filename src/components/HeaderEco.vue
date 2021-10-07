<template>
    <div class = "header">
    <header class="header">
            <img class="header__img" src="" alt="">
            <div class="header__menu">
                <nav class="navbar navbar-inverse box-shadow navbar-light justify-content-end" id="headerCustom">
                    <ul class="nav   lista">
                        <li class="nav-item">
                            <a class="nav-link" aria-current="page" href="Index.html">Inicio</a>
                        </li>
                        <li class="nav-item">
                            <a class="nav-link" href="ZUInformacion.html">Información</a>
                        </li>
                        <li class="nav-item">
                            <a class="nav-link" href="#">Datos de Perfil</a>
                        </li>
                        <li class="nav-item">
                            <a class="nav-link" href="chat_y_anuncios.html">Chat y Anuncios</a>
                        </li>
                        <li class="nav-item profile">
                            <a href="">
                                <i class="bi bi-person-circle"></i>
                                <p class="display-7 login">Iniciar Sesión</p>
                            </a>
                        </li>
                    </ul>
                </nav>
            </div>
        </header>
    </div>
</template>

<script>
export default {

}
</script>

<style>
.header{
    box-shadow:  0 4px 6px 0 rgb(0 0 0 / 9%), 0 6px 20px 0 rgb(0 0 0 / 10%);
    width: 100%;
    height: 80px;
    display: flex;
    justify-content: space-between;
    align-items: center;

}
.header__img{
    width: 100px;
    margin-top: -7px;
    margin-left: 86px;;
}

.header__menu {
    margin-right: 30px;
}

.header__menu li {
    margin: auto;
}

.header__menu li a {
    text-decoration: none;

}

</style>