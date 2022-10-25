<template>
    <div>
        <nav class="navMenu" v-show="showNav">
            <img :src="IconSearch" alt="Search icon" @click="toggleSearch" />

            <p>{{ systemName }}</p>

            <img :src="IconMenu" alt="Menu icon" @click="toggleFullMenu" />
        </nav>
        <transition name="fullMenu">
            <ul class="fullMenu" v-show="openMenu">
                <li>
                    <img class="iconBack" @click="toggleFullMenu" :src="IconArrowBack" alt="Icon Back" />
                    <p>Olá, Gabriel</p>
                    <img class="profileImage" :src="profileImage" alt="Profile Image" />
                </li>
                <li>Home</li>
                <li>Favorites</li>
                <li>Account</li>
            </ul>
        </transition>
    </div>
</template>

<script>

export default {
    data() {
        return {
            systemName: 'Comics Now',
            IconSearch: '../../public/icons/IconSearch.svg',
            IconMenu: '../../public/icons/IconMainMenu.svg',
            IconArrowBack: '../../public/icons/ArrowBack.svg',
            profileImage: '../../public/icons/user.webp',

            openMenu: null,
            showNav: true,
        };
    },

    methods: {
        toggleFullMenu() {
            this.openMenu = !this.openMenu;
            this.showNav = !this.showNav;
        }
    }
}
</script>

<style lang="scss" scoped>
.navMenu {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;

    p {
        font-family: $font__main;
        font-size: 1.2rem;
        text-transform: lowercase;
    }

    img {
        height: 100%;
        padding: 8px 16px;
        transition: 1s ease;
    }

    img:hover {
        filter: brightness(1.4);
        cursor: pointer;
    }

}

.fullMenu {
    margin: 0;
    padding: 0;
    padding-top: 1rem;

    background-color: #2c2c2c;
    color: $color__text-main;

    width: 100vw;
    height: 75vh;

    font-size: 1.5rem;
    line-height: 5rem;

    display: flex;
    flex-direction: column;

    li {
        display: flex;
        justify-content: space-around;
        align-items: center;
        // max-width: 75vw;

        .profileImage {
            max-height: 2.5rem;
            background-color: white;
            padding: 0.45rem;
            border-radius: 50%;
            margin-left: 1rem;
        }

        .iconBack {
            height: 1.5rem;

        }
    }
}
</style>