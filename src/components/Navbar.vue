<script>

export default {
    name: "Navbar",
    data() {
        return {
            burgerVisibility: false
        };
    },
    methods: {
        changeVisibility() {
            this.burgerVisibility = !this.burgerVisibility;
        }
    }
};

</script>

<template>
    <div id="app">
        <header class="header">
            <a class="header__logo" href="#">Kaban</a>
            <div class="ham-menu" @click="changeVisibility()" :class="{ 'active': burgerVisibility }">
                <span class="ham-menu__item"></span>
                <span class="ham-menu__item"></span>
                <span class="ham-menu__item"></span>
            </div>
            
        </header>
    </div>
</template>

<style scoped>
    .header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 1rem;
        background-color: #e3dac9;
        color: #fff;
    }

    .header__logo {
        font-size: 1.5rem;
        text-decoration: none;
        color: #fff;
    }

    .ham-menu {
        display: none;
        flex-direction: column;
        justify-content: space-between;
        width: 30px;
        height: 20px;
        cursor: pointer;
    }

    .ham-menu__item {
        width: 100%;
        height: 3px;
        background-color: #fff;
    }

    .header__nav-wrap {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    .header__nav-list {
        display: flex;
        list-style: none;
    }

    .header__nav-item {
        margin-right: 1rem;
    }

    .header__nav-link {
        text-decoration: none;
        color: #fff;
    }

    @media (max-width: 768px) {
        .ham-menu {
            display: flex;
        }

        .header__nav-wrap {
            display: none;
            position: absolute;
            top: 100%;
            left: 0;
            width: 100%;
            background-color: #e3dac9;
        }

        .header__nav-wrap.open {
            display: flex;
            flex-direction: column;
        }

        .header__nav-item {
            margin: 0;
            padding: 1rem;
            border-bottom: 1px solid #fff;
        }
    }
</style>