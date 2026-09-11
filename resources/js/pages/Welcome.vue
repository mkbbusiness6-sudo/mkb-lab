<script setup lang="ts">
import { Head, Link } from '@inertiajs/vue3';
import {
    ArrowRight,
    ArrowUpRight,
    BookOpen,
    Cpu,
    Menu,
    MonitorPlay,
    Play,
    Sparkles,
    Terminal,
    X,
} from '@lucide/vue';
import { ref } from 'vue';
import LabMark from '@/components/LabMark.vue';
import { dashboard, login } from '@/routes';

const youtubeUrl = 'https://www.youtube.com/@MKBLab';
const menuOpen = ref(false);

const pillars = [
    {
        icon: Sparkles,
        index: '01',
        title: 'Snippets concrets',
        text: 'Des gestes testés avant le push. Tu dois pouvoir les reproduire le jour même.',
    },
    {
        icon: BookOpen,
        index: '02',
        title: 'Logs de session',
        text: 'Ce qui compile, ce qui casse, ce que je garde. Le chemin compte autant que le résultat.',
    },
    {
        icon: MonitorPlay,
        index: '03',
        title: 'Walkthrough vidéo',
        text: 'L’article pour le détail. La vidéo pour le geste. Même spec, deux runtimes.',
    },
];

const experiments = [
    {
        code: 'EXP-001',
        category: 'outils',
        title: 'Premiers protocoles en WIP',
        note: 'Les astuces en cours de test atterriront ici, commit par commit.',
    },
    {
        code: 'EXP-002',
        category: 'prod',
        title: 'Moins de friction',
        note: 'Des méthodes courtes, éprouvées au quotidien — pas un awesome-list de 47 outils.',
    },
    {
        code: 'EXP-003',
        category: 'media',
        title: 'Du lab à YouTube',
        note: 'Chaque note peut devenir une démo. Lire, puis watch.',
    },
];

function closeMenu(): void {
    menuOpen.value = false;
}
</script>

<template>
    <Head title="Un lab d'astuces">
        <meta
            name="description"
            content="MKB Lab est un lab perso : astuces testées, notes versionnées, et une chaîne YouTube pour le walkthrough."
        />
        <link rel="preconnect" href="https://fonts.bunny.net" />
        <link
            href="https://fonts.bunny.net/css?family=jetbrains-mono:400,500,600|space-grotesk:400,500,600,700"
            rel="stylesheet"
        />
    </Head>

    <div
        class="lab-grid lab-mesh relative min-h-screen bg-[#f4f7fb] text-[#0b1220] dark:bg-[#070b14] dark:text-[#e8eef8]"
    >
        <a
            href="#contenu"
            class="bg-background text-foreground sr-only focus:not-sr-only focus:absolute focus:top-3 focus:left-3 focus:z-50 focus:rounded-md focus:px-3 focus:py-2"
        >
            Aller au contenu
        </a>

        <header
            class="sticky top-0 z-40 border-b border-[#0b1220]/8 bg-[#f4f7fb]/75 backdrop-blur-xl dark:border-cyan-400/10 dark:bg-[#070b14]/75"
        >
            <div
                class="pointer-events-none absolute inset-0 overflow-hidden"
                aria-hidden="true"
            >
                <div
                    class="absolute -top-16 left-8 size-40 rounded-full bg-cyan-400/20 blur-3xl dark:bg-cyan-400/15"
                />
                <div
                    class="absolute -top-12 right-16 size-36 rounded-full bg-violet-500/15 blur-3xl dark:bg-violet-500/20"
                />
            </div>

            <div
                class="relative mx-auto flex h-17 max-w-6xl items-center justify-between px-5 sm:px-8"
            >
                <a
                    href="#contenu"
                    class="group flex items-center gap-3 rounded-md focus-visible:ring-2 focus-visible:ring-cyan-400 focus-visible:outline-none"
                    @click="closeMenu"
                >
                    <span
                        class="relative flex size-10 items-center justify-center rounded-lg bg-linear-to-br from-cyan-400 to-violet-500 p-px shadow-[0_0_20px_-4px_rgba(34,211,238,0.7)]"
                    >
                        <span
                            class="flex size-full items-center justify-center rounded-[7px] bg-[#0b1220] text-cyan-300"
                        >
                            <LabMark class="size-6" />
                        </span>
                    </span>
                    <span class="leading-tight">
                        <span
                            class="block text-sm font-semibold tracking-tight"
                        >
                            MKB Lab
                        </span>
                        <span
                            class="font-mono text-[10px] tracking-[0.18em] text-[#5b6578] uppercase dark:text-cyan-400/70"
                            >~/dev · neural lab</span
                        >
                    </span>
                </a>

                <nav
                    class="hidden items-center gap-1 font-mono text-[12px] md:flex"
                    aria-label="Navigation principale"
                >
                    <a
                        href="#astuces"
                        class="rounded-md px-3 py-1.5 text-[#5b6578] transition-colors hover:bg-cyan-400/8 hover:text-[#0b1220] dark:text-slate-400 dark:hover:text-cyan-300"
                        >/astuces</a
                    >
                    <a
                        href="#youtube"
                        class="rounded-md px-3 py-1.5 text-[#5b6578] transition-colors hover:bg-cyan-400/8 hover:text-[#0b1220] dark:text-slate-400 dark:hover:text-cyan-300"
                        >/youtube</a
                    >
                    <a
                        href="#manifeste"
                        class="rounded-md px-3 py-1.5 text-[#5b6578] transition-colors hover:bg-cyan-400/8 hover:text-[#0b1220] dark:text-slate-400 dark:hover:text-cyan-300"
                        >/lab</a
                    >
                </nav>

                <div class="flex items-center gap-2">
                    <span
                        class="hidden items-center gap-1.5 rounded-md border border-cyan-400/25 bg-cyan-400/8 px-2.5 py-1 font-mono text-[10px] tracking-wider text-cyan-700 uppercase sm:inline-flex dark:text-cyan-300"
                    >
                        <span
                            class="size-1.5 rounded-full bg-cyan-400 motion-safe:animate-[lab-pulse_2s_ease-in-out_infinite]"
                            aria-hidden="true"
                        />
                        online
                    </span>
                    <a
                        :href="youtubeUrl"
                        target="_blank"
                        rel="noopener noreferrer"
                        class="hidden items-center gap-1.5 rounded-md border border-[#0b1220]/10 px-3 py-1.5 font-mono text-[11px] text-[#5b6578] transition-colors hover:border-cyan-400/40 hover:text-[#0b1220] sm:inline-flex dark:border-white/10 dark:text-slate-400 dark:hover:text-cyan-300"
                    >
                        <MonitorPlay class="size-3.5" />
                        chaîne
                    </a>
                    <Link
                        v-if="$page.props.auth.user"
                        :href="dashboard()"
                        class="hidden rounded-md bg-linear-to-r from-cyan-400 to-violet-500 px-3.5 py-1.5 font-mono text-[11px] font-medium text-[#070b14] sm:inline-flex"
                    >
                        dashboard
                    </Link>
                    <Link
                        v-else
                        :href="login()"
                        class="hidden rounded-md px-3 py-1.5 font-mono text-[11px] text-[#5b6578] transition-colors hover:text-[#0b1220] sm:inline-flex dark:text-slate-400 dark:hover:text-cyan-300"
                    >
                        login
                    </Link>
                    <button
                        type="button"
                        class="inline-flex size-9 items-center justify-center rounded-md text-[#0b1220] md:hidden dark:text-[#e8eef8]"
                        :aria-expanded="menuOpen"
                        aria-controls="menu-mobile"
                        :aria-label="
                            menuOpen ? 'Fermer le menu' : 'Ouvrir le menu'
                        "
                        @click="menuOpen = !menuOpen"
                    >
                        <X v-if="menuOpen" class="size-5" />
                        <Menu v-else class="size-5" />
                    </button>
                </div>
            </div>

            <div class="overflow-hidden" aria-hidden="true">
                <div
                    class="lab-header-beam h-px motion-safe:animate-[lab-beam_7s_ease-in-out_infinite]"
                />
            </div>

            <div
                v-if="menuOpen"
                id="menu-mobile"
                class="border-t border-[#0b1220]/8 bg-[#f4f7fb]/95 px-5 py-4 md:hidden dark:border-cyan-400/10 dark:bg-[#070b14]/95"
            >
                <nav
                    class="flex flex-col gap-1 font-mono text-sm"
                    aria-label="Navigation mobile"
                >
                    <a
                        href="#astuces"
                        class="rounded-md px-2 py-2.5"
                        @click="closeMenu"
                        >/astuces</a
                    >
                    <a
                        href="#youtube"
                        class="rounded-md px-2 py-2.5"
                        @click="closeMenu"
                        >/youtube</a
                    >
                    <a
                        href="#manifeste"
                        class="rounded-md px-2 py-2.5"
                        @click="closeMenu"
                        >/lab</a
                    >
                    <a
                        :href="youtubeUrl"
                        target="_blank"
                        rel="noopener noreferrer"
                        class="rounded-md px-2 py-2.5"
                        @click="closeMenu"
                        >/youtube/chaîne</a
                    >
                    <Link
                        v-if="$page.props.auth.user"
                        :href="dashboard()"
                        class="rounded-md px-2 py-2.5"
                        @click="closeMenu"
                    >
                        /dashboard
                    </Link>
                    <Link
                        v-else
                        :href="login()"
                        class="rounded-md px-2 py-2.5"
                        @click="closeMenu"
                    >
                        /login
                    </Link>
                </nav>
            </div>
        </header>

        <main id="contenu" class="relative z-10">
            <section class="relative overflow-hidden">
                <div
                    class="pointer-events-none absolute -top-24 left-1/3 h-80 w-2xl -translate-x-1/2 rounded-full bg-cyan-400/20 blur-3xl motion-safe:animate-[lab-glow_8s_ease-in-out_infinite] dark:bg-cyan-400/12"
                    aria-hidden="true"
                />
                <div
                    class="pointer-events-none absolute top-10 right-0 h-64 w-96 rounded-full bg-violet-500/15 blur-3xl dark:bg-violet-500/12"
                    aria-hidden="true"
                />

                <div
                    class="relative mx-auto grid max-w-6xl items-center gap-12 px-5 py-16 sm:px-8 lg:grid-cols-[1.1fr_0.9fr] lg:gap-16 lg:py-24"
                >
                    <div
                        class="opacity-100 transition-all duration-700 starting:translate-y-3 starting:opacity-0"
                    >
                        <p
                            class="mb-6 inline-flex items-center gap-2 font-mono text-[11px] tracking-[0.18em] text-[#5b6578] uppercase dark:text-cyan-400/80"
                        >
                            <Cpu class="size-3.5 text-cyan-500" />
                            mkb@lab — session ouverte
                        </p>

                        <h1
                            class="text-[2.45rem] leading-[1.08] font-semibold tracking-tight text-balance sm:text-6xl lg:text-[4.1rem]"
                        >
                            Un lab d’astuces,
                            <span
                                class="bg-linear-to-r from-cyan-500 to-violet-500 bg-clip-text text-transparent dark:from-cyan-300 dark:to-violet-400"
                                >versionné comme du code.</span
                            >
                        </h1>

                        <p
                            class="mt-6 max-w-lg text-base leading-relaxed text-[#5b6578] sm:text-lg dark:text-slate-400"
                        >
                            MKB Lab, c’est mon lab perso. J’y pousse les astuces
                            que je teste — en notes, en articles, et bientôt en
                            walkthrough YouTube.
                        </p>

                        <div class="mt-9 flex flex-wrap items-center gap-3">
                            <a
                                href="#astuces"
                                class="inline-flex items-center gap-2 rounded-md bg-linear-to-r from-cyan-400 to-violet-500 px-5 py-2.5 text-sm font-semibold text-[#070b14] shadow-[0_0_28px_-6px_rgba(34,211,238,0.7)] transition-transform hover:scale-[1.02]"
                            >
                                cd /astuces
                                <ArrowRight class="size-4" />
                            </a>
                            <a
                                href="#youtube"
                                class="inline-flex items-center gap-2 rounded-md border border-[#0b1220]/12 px-5 py-2.5 font-mono text-sm text-[#0b1220] transition-colors hover:border-cyan-400/40 hover:bg-cyan-400/5 dark:border-white/12 dark:text-[#e8eef8] dark:hover:border-cyan-400/30"
                            >
                                <MonitorPlay class="size-4" />
                                watch --later
                            </a>
                        </div>
                    </div>

                    <div
                        class="relative mx-auto w-full max-w-md px-1 pb-10 motion-safe:animate-[lab-float_7s_ease-in-out_infinite] lg:max-w-none"
                    >
                        <article
                            class="relative overflow-hidden rounded-xl border border-cyan-400/20 bg-[#0b1220] text-[#d7e2f0] shadow-[0_24px_80px_-28px_rgba(34,211,238,0.35)]"
                        >
                            <div
                                class="flex items-center gap-2 border-b border-white/8 px-4 py-2.5 font-mono text-[10px] tracking-wider text-slate-400 uppercase"
                            >
                                <span
                                    class="size-2 rounded-full bg-[#ff5f56]"
                                    aria-hidden="true"
                                />
                                <span
                                    class="size-2 rounded-full bg-[#ffbd2e]"
                                    aria-hidden="true"
                                />
                                <span
                                    class="size-2 rounded-full bg-[#27c93f]"
                                    aria-hidden="true"
                                />
                                <span class="ml-2 flex items-center gap-1.5">
                                    <Terminal class="size-3" />
                                    protocol.md
                                </span>
                                <span
                                    class="ml-auto rounded-md border border-cyan-400/30 px-2 py-0.5 text-cyan-300"
                                    >wip</span
                                >
                            </div>
                            <div class="space-y-1.5 p-5 font-mono text-[13px]">
                                <p>
                                    <span class="text-violet-400">const</span>
                                    <span class="text-cyan-300"> lab</span>
                                    <span class="text-slate-500"> = </span>
                                    <span class="text-emerald-300"
                                        >'MKB Lab'</span
                                    >
                                </p>
                                <p>
                                    <span class="text-violet-400">status</span>
                                    <span class="text-slate-500">: </span>
                                    <span class="text-cyan-300">online</span>
                                </p>
                                <p class="text-slate-500">
                                    // reproductible, testé, versionné
                                </p>
                                <p>
                                    <span class="text-violet-400">export</span>
                                    <span class="text-cyan-300">
                                        format</span
                                    >
                                    <span class="text-slate-500"> = </span>
                                    <span class="text-emerald-300"
                                        >'article + youtube'</span
                                    >
                                </p>
                            </div>
                            <div
                                class="mx-5 mb-5 flex items-center gap-3 rounded-lg border border-white/8 bg-white/4 p-3"
                            >
                                <span
                                    class="flex size-10 items-center justify-center rounded-md bg-linear-to-br from-cyan-400 to-violet-500 text-[#070b14]"
                                >
                                    <Play class="size-4 fill-current" />
                                </span>
                                <div>
                                    <p class="text-sm font-medium text-white">
                                        Preview YouTube
                                    </p>
                                    <p
                                        class="font-mono text-[11px] text-slate-400"
                                    >
                                        readme.md → demo.mp4
                                    </p>
                                </div>
                            </div>
                        </article>

                        <div
                            class="absolute -right-3 -bottom-5 hidden rounded-lg border border-cyan-400/25 bg-[#0b1220] px-3 py-2 text-cyan-100 shadow-[0_12px_40px_-16px_rgba(34,211,238,0.6)] sm:block"
                        >
                            <p
                                class="font-mono text-[10px] tracking-[0.16em] text-cyan-400/70 uppercase"
                            >
                                output
                            </p>
                            <p class="font-mono text-sm">article + vidéo</p>
                        </div>
                    </div>
                </div>
            </section>

            <section
                class="border-y border-[#0b1220]/8 dark:border-cyan-400/10"
                aria-label="Ce que tu trouveras ici"
            >
                <div
                    class="mx-auto grid max-w-6xl gap-px bg-[#0b1220]/8 sm:grid-cols-3 dark:bg-cyan-400/10"
                >
                    <article
                        v-for="pillar in pillars"
                        :key="pillar.index"
                        class="bg-[#f4f7fb] px-5 py-10 sm:px-8 dark:bg-[#070b14]"
                    >
                        <div class="flex items-center justify-between">
                            <span
                                class="flex size-10 items-center justify-center rounded-md border border-cyan-400/25 text-cyan-600 dark:text-cyan-300"
                            >
                                <component :is="pillar.icon" class="size-5" />
                            </span>
                            <span
                                class="font-mono text-[11px] tracking-[0.18em] text-[#8b95a7] dark:text-slate-500"
                                >{{ pillar.index }}</span
                            >
                        </div>
                        <h2
                            class="mt-6 font-mono text-base font-semibold tracking-tight"
                        >
                            {{ pillar.title }}
                        </h2>
                        <p
                            class="mt-2 text-sm leading-relaxed text-[#5b6578] dark:text-slate-400"
                        >
                            {{ pillar.text }}
                        </p>
                    </article>
                </div>
            </section>

            <section id="astuces" class="scroll-mt-24 py-20 sm:py-24">
                <div class="mx-auto max-w-6xl px-5 sm:px-8">
                    <div
                        class="flex flex-col justify-between gap-6 sm:flex-row sm:items-end"
                    >
                        <div class="max-w-xl">
                            <p
                                class="font-mono text-[11px] tracking-[0.2em] text-[#5b6578] uppercase dark:text-cyan-400/80"
                            >
                                // changelog
                            </p>
                            <h2
                                class="mt-3 text-3xl font-semibold tracking-tight sm:text-4xl"
                            >
                                Les premières astuces se compilent.
                            </h2>
                            <p class="mt-3 text-[#5b6578] dark:text-slate-400">
                                Rien de fictif ici : le lab s’ouvre. Les
                                protocoles arrivent au fur et à mesure, dès
                                qu’ils ont vraiment été testés.
                            </p>
                        </div>
                        <p
                            class="shrink-0 font-mono text-[11px] tracking-[0.16em] whitespace-nowrap text-[#8b95a7] uppercase dark:text-slate-500"
                        >
                            0 / ∞ shipped
                        </p>
                    </div>

                    <div class="mt-12 grid gap-4 sm:grid-cols-2 lg:grid-cols-3">
                        <article
                            v-for="experiment in experiments"
                            :key="experiment.code"
                            class="group rounded-xl border border-[#0b1220]/10 bg-white p-5 dark:border-cyan-400/12 dark:bg-[#0e1522]"
                        >
                            <div
                                class="flex items-center justify-between font-mono text-[10px] tracking-[0.16em] uppercase"
                            >
                                <span
                                    class="text-[#8b95a7] dark:text-slate-500"
                                    >{{ experiment.code }}</span
                                >
                                <span
                                    class="rounded-md bg-cyan-400/12 px-2 py-0.5 text-cyan-700 dark:text-cyan-300"
                                    >{{ experiment.category }}</span
                                >
                            </div>
                            <h3
                                class="mt-5 text-lg font-semibold tracking-tight"
                            >
                                {{ experiment.title }}
                            </h3>
                            <p
                                class="mt-2 text-sm leading-relaxed text-[#5b6578] dark:text-slate-400"
                            >
                                {{ experiment.note }}
                            </p>
                            <p
                                class="mt-6 font-mono text-[11px] tracking-[0.14em] text-[#8b95a7] uppercase dark:text-slate-500"
                            >
                                queued
                            </p>
                        </article>
                    </div>
                </div>
            </section>

            <section
                id="youtube"
                class="scroll-mt-24 border-y border-[#0b1220]/8 bg-[#0b1220] py-20 text-[#e8eef8] sm:py-24 dark:border-cyan-400/10 dark:bg-[#0e1522]"
            >
                <div
                    class="mx-auto grid max-w-6xl items-center gap-12 px-5 sm:px-8 lg:grid-cols-2"
                >
                    <div>
                        <p
                            class="font-mono text-[11px] tracking-[0.2em] text-cyan-400 uppercase"
                        >
                            dual output
                        </p>
                        <h2
                            class="mt-3 text-3xl font-semibold tracking-tight sm:text-5xl"
                        >
                            Même spec.<br />
                            Deux runtimes.
                        </h2>
                        <p class="mt-5 max-w-md text-slate-400">
                            L’écrit pour garder une trace nette. La vidéo pour
                            le walkthrough. MKB Lab et YouTube racontent la
                            même expérience, chacun dans son format.
                        </p>
                        <a
                            :href="youtubeUrl"
                            target="_blank"
                            rel="noopener noreferrer"
                            class="mt-8 inline-flex items-center gap-2 rounded-md bg-linear-to-r from-cyan-400 to-violet-500 px-5 py-2.5 text-sm font-semibold text-[#070b14] transition-transform hover:scale-[1.02]"
                        >
                            git clone la chaîne
                            <ArrowUpRight class="size-4" />
                        </a>
                    </div>

                    <div
                        class="relative aspect-video overflow-hidden rounded-xl border border-cyan-400/20 bg-[#070b14]"
                    >
                        <div
                            class="lab-grid absolute inset-0 opacity-70"
                            aria-hidden="true"
                        />
                        <div
                            class="absolute inset-0 flex flex-col items-center justify-center gap-3"
                        >
                            <span
                                class="flex size-16 items-center justify-center rounded-xl border border-cyan-400/40 bg-cyan-400/10 text-cyan-300 shadow-[0_0_40px_-8px_rgba(34,211,238,0.8)]"
                            >
                                <Play class="size-6 fill-current" />
                            </span>
                            <p
                                class="font-mono text-[11px] tracking-[0.18em] text-slate-400 uppercase"
                            >
                                preview en build
                            </p>
                        </div>
                    </div>
                </div>
            </section>

            <section id="manifeste" class="scroll-mt-24 py-20 sm:py-28">
                <div class="mx-auto max-w-3xl px-5 text-center sm:px-8">
                    <Cpu
                        class="mx-auto size-8 text-cyan-500 dark:text-cyan-300"
                    />
                    <h2
                        class="mt-6 text-3xl font-semibold tracking-tight sm:text-4xl"
                    >
                        Pas un média.<br />
                        Un repo d’astuces ouvert.
                    </h2>
                    <p
                        class="mt-6 text-base leading-relaxed text-[#5b6578] sm:text-lg dark:text-slate-400"
                    >
                        Chaque astuce publiée ici a été essayée, parfois cassée,
                        puis réécrite pour que tu puisses la reproduire. Pas de
                        bruit, pas de listicles vides : seulement ce qui mérite
                        un commit.
                    </p>
                </div>
            </section>
        </main>

        <footer
            class="relative z-10 border-t border-[#0b1220]/8 py-8 dark:border-cyan-400/10"
        >
            <div
                class="mx-auto flex max-w-6xl flex-col items-start justify-between gap-4 px-5 sm:flex-row sm:items-center sm:px-8"
            >
                <div class="flex items-center gap-2.5">
                    <LabMark class="size-5 text-cyan-500" />
                    <p class="font-mono text-sm">
                        <span class="font-semibold">MKB Lab</span>
                        <span class="text-[#8b95a7] dark:text-slate-500">
                            · ~/dev</span
                        >
                    </p>
                </div>
                <p
                    class="font-mono text-[11px] tracking-[0.14em] text-[#8b95a7] uppercase dark:text-slate-500"
                >
                    © {{ new Date().getFullYear() }}
                </p>
            </div>
        </footer>
    </div>
</template>
