<script setup>

</script>

<template>
    <section class="welcome">
        <div class="container">
            <div class="welcome-header">
                <h1 class="welcome-header__title">Напиши в меня, что нибудь ^_^</h1>
                <p class="welcome-header__subtitle">Чеклист создан в ознакомительных целях.<a href="https://youtu.be/dQw4w9WgXcQ" target="_blank">Узнать больше</a></p>
            </div>
        </div>
    </section>
</template>

<style lang="scss">
@use '../../sass/common/vars';
@use '../../sass/common/font';

.welcome {
    margin-bottom: 3rem;
}

.welcome-header {
    display: flex;
    flex-direction: column;

    gap: 1.2rem;

    text-align: center;

        &__title {
            color: vars.$white-color;

            @extend %font-h1;
        }

        &__subtitle {
            display: flex;
            justify-content: center;

            gap: 0.5rem;

            color: vars.$text-secondary;

            @extend %subtitle;

            & > a {
                display: flex;
                align-items: center;

                color: vars.$secondary-color;

                &::after {
                display: block;
                content: "";
                background: url('../../img/svg/arrow.svg');
                width: 12px;
                height: 13px;

                padding-right: 3px;
            }

            }
        }
}

</style>