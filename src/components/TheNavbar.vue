<template>
    <nav>
        <div class="branding">
            <img src="../assets/logo.png" alt="Logo">
            <h1>Vite todos</h1>
        </div>
        <ul class="nav-routes">
            <RouterLink to="/">Главная</RouterLink>
            <RouterLink to="/about">О нас</RouterLink>
        </ul>
    </nav>
</template>

<script setup>

</script>

<style lang="scss" scoped>
nav {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 20px 16px;
    background-color: #f1f1f1;

    .branding {
        display: flex;
        align-items: center;
        gap: 12px;

        img {
            max-width: 50px;
        }

        h1 {
            font-size: 24px;
            color: #926dfe;
        }
    }

    .nav-routes {
        display: flex;
        align-items: center;
        gap: 12px;

        a {
            position: relative;
            text-decoration: none;

            &::after {
                content: '';
                position: absolute;
                bottom: 0;
                left: 50%;
                display: block;
                width: 0;
                height: 2px;
                background-color: #000000;
                transform: translateX(-50%);
                transition: 0.25s ease-in-out;
            }

            &:hover::after,
            &:focus::after {
                width: 100%;
            }
        }
    }
}
</style>