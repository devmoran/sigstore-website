<template>
    <nav>
        <ul class="flex items-start" :class="[navType == 'social' ? 'justify-start md:justify-end w-full' : 'justify-start flex-wrap']">
            <li>
                <NuxtLink v-if="navType == 'header'" class="mr-36 flex justify-between" :class="[text]" :to="`/`">
                    Overview
                </NuxtLink>
            </li>
            <li v-for="navItem, index in navList" :key="index">
                <NuxtLink v-if="navType == 'header'" class="mr-36 flex justify-between" :class="[text]" :to="`${navItem.menuLink}`">
                    {{ navItem.name }}
                </NuxtLink>
                <NuxtLink v-else-if="navType == 'footer'" class="footer--nav-button mr-36 flex justify-between h text-16 leading-24 text-gray-dark" :to="`${navItem.footerMenuLink}`">
                    {{ navItem.name }}
                </NuxtLink>
                <a v-else class="footer--nav-button md:mr-30 mr-16 flex justify-between h text-16 leading-24 text-gray-dark" target="_blank" :href="`${navItem.url ? navItem.url : navItem.externalLink}`">
                    <span v-if="navType == 'social' && navItem.name == 'GitHub'" class="mr-16">
                        <GitHubLogo :class="['fill-grey']" />
                    </span>
                    <span v-if="navType == 'social' && navItem.name == 'Twitter'" class="mr-16">
                        <TwitterLogo :class="['fill-grey']" />
                    </span>
                    {{ navItem.name }}
                </a>
            </li>
            <li v-if="navType == 'header'">
                <a class="mr-36 flex justify-between" :class="[text]" target="_blank" href="https://medium.com/sigstore">
                    Blog
                </a>
            </li>
            <li v-if="navType == 'header'">
                <a :class="[text]" href="https://github.com/sigstore" target="_blank" title="GitHub profile link"><GitHubLogo :class="[$route.params.slug === 'trust-security' ? 'fill-white' : 'fill-black']" /></a>
            </li>
        </ul>
    </nav>
</template>
<script lang="js" src="./Navigation.js" />
