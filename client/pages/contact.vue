<template>
    <main>
        <h1 class="text-4xl font-extrabold my-4 dark:text-white">Контакты</h1>
        <div class="flex gap-32 items-center mt-16 mb-20">
            <div>
                <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d762.5071661811821!2d39.725774475768695!3d43.59295583265837!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x40f5cba53a28206d%3A0x15959bb73136c25d!2z0JrQvtC80L_RjNGO0YLQtdGA0L3QsNGPINCw0LrQsNC00LXQvNC40Y8gVE9Q!5e1!3m2!1sru!2sru!4v1734019274060!5m2!1sru!2sru" width="600" height="450" style="border:0;" loading="lazy" referrerpolicy="no-referrer-when-downgrade" class="rounded-lg"></iframe>
            </div>
            <div>
                <h3 class="text-2xl my-4">Вы можете связаться с нами:</h3>
                <ul class="flex flex-col gap-3 mx-4">
                    <li id="gh" class="flex items-center hover:text-blue-700"><a href="https://github.com/WhyUcry">GitHub</a></li>
                    <li id="tg" class="flex items-center hover:text-blue-700"><a href="https://t.me/kylonil">Telegram</a></li>
                    <li id="tg" class="flex items-center hover:text-blue-700"><a href="https://t.me/kylonilprod">Наш Telegram канал</a></li>
                    <li id="vk" class="flex items-center hover:text-blue-700"><a href="https://vk.com/kylonil">VKontakte</a></li>
                    <li id="em" class="flex items-center hover:text-blue-700"><a href="https://mail.google.com/">ivane6749@gmail.com</a></li>
                    <li id="em" class="flex items-center hover:text-blue-700"><a href="https://mail.google.com/">iemelvan67@gmail.com</a></li>
                    <li id="em" class="flex items-center hover:text-blue-700"><a href="https://mail.google.com/">babykylonil@gmail.com</a></li>
                    <li id="pn" class="flex items-center hover:text-blue-700"><a href="#">+7 (988) 141-74-48</a></li>
                    <li id="pn" class="flex items-center hover:text-blue-700"><a href="#">+7 (989) 166-95-12</a></li>
                </ul>
            </div>
        </div>
    </main>
</template>

<style scoped>
    #gh::before {
        content: url("../assets/img/icons/github.svg");
        margin-right: 10px;
    }

    #tg::before {
        content: url("../assets/img/icons/tg.svg");
        margin-right: 10px;
    }

    #vk::before {
        content: url("../assets/img/icons/vk.svg");
        margin-right: 10px;
    }

    #em::before {
        content: url("../assets/img/icons/email.svg");
        margin-right: 10px;
    }

    #pn::before {
        content: url("../assets/img/icons/phone.svg");
        margin-right: 10px;
    }
</style>