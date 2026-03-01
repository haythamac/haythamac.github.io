<script setup>
import { ExternalLink, Github, Database, Server, Layout, Code2 } from 'lucide-vue-next';
import Button from '@/components/ui/button.vue';
import Badge from '@/components/ui/badge.vue';


// Helper function to get correct image path
const getImagePath = (imagePath) => {
    if (!imagePath) return null;
    return `${import.meta.env.BASE_URL}${imagePath}`;
};


const projects = [
    {
        title: "Mileage Calculator",
        image: "images/mileage-calculator.png",
        description: "A full-stack guild management app built with Laravel, Vue.js, and MySQL. Features member roles and permissions, a raffle system, and item distribution tracking via a REST API.",
        techStack: [
            { name: "Vue.js", icon: Layout },
        ],
        features: [
            "User input for deposits and mileage calculation",
            "Default results based on game mechanics",
            "Can customize mileage rates and days",
            "Simple and intuitive user interface",
            "No backend, purely frontend application",
            "Error handling for invalid inputs",
        ],
        demoLink: "https://ymir-mileage.vercel.app/",
        githubLink: "https://github.com/haythamac/ymir-mileage-calculator",
    },
    {
        title: "Guild Management System",
        image: "images/paragon.png",
        description: "A full-stack guild management app built with Laravel, Vue.js, and MySQL. Features member roles and permissions, a raffle system, and item distribution tracking via a REST API.",
        techStack: [
            { name: "Laravel", icon: Server },
            { name: "Vue.js", icon: Layout },
            { name: "MySQL", icon: Database },
            { name: "REST API", icon: Code2 },
        ],
        features: [
            "Member management with roles and permissions",
            "Raffle system for event participation",
            "Item Distribution tracking and management",
            "Responsive design for mobile and desktop",
        ],
        demoLink: "#",
        githubLink: "https://github.com/haythamac/paragon-fe",
    },
    {
        title: "Folkvang Timer",
        image: "images/folkvang.png",
        description: "A real-time timer app using WebSockets, built with Express.js, Vue.js, and SQLite. Tracks and manages in-game activity across mobile and desktop.",
        techStack: [
            { name: "Express.js", icon: Server },
            { name: "Vue.js", icon: Layout },
            { name: "SQLite", icon: Database },
            { name: "REST API", icon: Code2 },
        ],
        features: [
            "Real-time timer functionality for tracking time spent in the game using websocket",
            "Timer functionality for tracking time spent in the game",
            "User-friendly interface for setting and managing timers",
            "Responsive design for mobile and desktop",
        ],
        demoLink: "https://folkvang-six.vercel.app/?demo=true",
        githubLink: "https://github.com/haythamac/folkvang",
    },
    {
        title: "Website Admin Dashboard for E-commerce App",
        description: "An admin dashboard built with PHP, vanilla JavaScript, and Firebase. Includes full CRUD for products and orders, analytics, role-based access control, and audit logs.",
        techStack: [
            { name: "PHP", icon: Server },
            { name: "Javascript", icon: Layout },
            { name: "Firebase", icon: Database },
        ],
        features: [
            "Product management with CRUD operations",
            "Order tracking and management",
            "Customer information management",
            "Dashboard with analytics, insights, reporting features, RBAC, and audit logs",
        ],
        demoLink: "#",
        githubLink: "#",
    },
    {
        title: "Learning Management System",
        description: "A full-stack LMS built with PHP, JavaScript, and MySQL. Supports course and lesson management, assessments, grading, and student progress tracking.",
        techStack: [
            { name: "PHP", icon: Server },
            { name: "Javascript", icon: Layout },
            { name: "MySQL", icon: Database },
        ],
        features: [
            "Course management with CRUD operations",
            "Create and manage lessons and assessments",
            "Manage grading and student progress",
            "Reporting and analytics",
        ],
        demoLink: "#",
        githubLink: "#",
    },
];
</script>

<template>
    <section id="projects" class="py-20 px-6">
        <div class="max-w-6xl mx-auto">
            <div class="mb-12">
                <p class="text-primary font-mono text-sm mb-2">Featured Work</p>
                <h2 class="text-3xl md:text-4xl font-bold text-foreground">
                    Project Showcase
                </h2>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                <div v-for="(project, index) in projects" :key="project.title"
                    class="group relative bg-card rounded-lg border border-border overflow-hidden shadow-lg flex flex-col min-h-[480px] cursor-pointer">

                    <!-- Default State: Normal card content -->
                    <div class="flex flex-col flex-1 transition-opacity duration-300 group-hover:opacity-0">

                        <!-- Image -->
                        <div class="bg-secondary/10 h-48 flex items-center justify-center overflow-hidden">
                            <img v-if="project.image" :src="getImagePath(project.image)" :alt="project.title"
                                class="w-full h-full object-cover" />
                            <div v-else class="w-full max-w-xs px-4">
                                <div class="bg-card rounded-lg shadow border border-border overflow-hidden">
                                    <div class="h-5 bg-muted flex items-center px-3 gap-1.5">
                                        <div class="w-2 h-2 rounded-full bg-destructive/60"></div>
                                        <div class="w-2 h-2 rounded-full bg-chart-1/60"></div>
                                        <div class="w-2 h-2 rounded-full bg-primary/60"></div>
                                    </div>
                                    <div class="p-3 space-y-2">
                                        <div class="h-3 bg-muted rounded w-3/4"></div>
                                        <div class="h-2 bg-muted/60 rounded w-full"></div>
                                        <div class="grid grid-cols-3 gap-1 mt-2">
                                            <div class="h-10 bg-primary/20 rounded"></div>
                                            <div class="h-10 bg-primary/20 rounded"></div>
                                            <div class="h-10 bg-primary/20 rounded"></div>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>

                        <!-- Text Content -->
                        <div class="p-6 flex flex-col flex-1">
                            <div class="flex flex-wrap gap-2 mb-3">
                                <Badge v-for="tech in project.techStack" :key="tech.name" variant="secondary"
                                    class="gap-1.5">
                                    <component :is="tech.icon" class="h-3 w-3" />
                                    {{ tech.name }}
                                </Badge>
                            </div>

                            <h3 class="text-xl font-bold text-foreground mb-2">
                                {{ project.title }}
                            </h3>

                            <p class="text-muted-foreground text-sm leading-relaxed mb-4">
                                {{ project.description }}
                            </p>

                            <ul class="grid gap-1.5 mb-5 flex-1">
                                <li v-for="(feature, featureIndex) in project.features" :key="featureIndex"
                                    class="flex items-start gap-2 text-sm text-muted-foreground">
                                    <span class="text-primary mt-0.5">▹</span>
                                    {{ feature }}
                                </li>
                            </ul>
                        </div>
                    </div>

                    <!-- Hover State: Full image with overlay, title and buttons only -->
                    <div class="absolute inset-0 opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex flex-col justify-end">

                        <!-- Full background image -->
                        <div class="absolute inset-0">
                            <img v-if="project.image" :src="getImagePath(project.image)" :alt="project.title"
                                class="w-full h-full object-cover" />
                            <div v-else class="w-full h-full bg-secondary/20 flex items-center justify-center">
                                <div class="w-full max-w-xs px-4">
                                    <div class="bg-card rounded-lg shadow border border-border overflow-hidden">
                                        <div class="h-5 bg-muted flex items-center px-3 gap-1.5">
                                            <div class="w-2 h-2 rounded-full bg-destructive/60"></div>
                                            <div class="w-2 h-2 rounded-full bg-chart-1/60"></div>
                                            <div class="w-2 h-2 rounded-full bg-primary/60"></div>
                                        </div>
                                        <div class="p-3 space-y-2">
                                            <div class="h-3 bg-muted rounded w-3/4"></div>
                                            <div class="h-2 bg-muted/60 rounded w-full"></div>
                                            <div class="grid grid-cols-3 gap-1 mt-2">
                                                <div class="h-10 bg-primary/20 rounded"></div>
                                                <div class="h-10 bg-primary/20 rounded"></div>
                                                <div class="h-10 bg-primary/20 rounded"></div>
                                            </div>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>

                        <!-- Dark overlay -->
                        <div class="absolute inset-0 bg-black/60"></div>

                        <!-- Title + Buttons pinned to bottom -->
                        <div class="relative z-10 p-6">
                            <h3 class="text-xl font-bold text-white mb-4">
                                {{ project.title }}
                            </h3>
                            <div class="flex flex-wrap gap-3">
                                <Button as-child :disabled="!project.demoLink || project.demoLink === '#'">
                                    <a v-if="project.demoLink && project.demoLink !== '#'" :href="project.demoLink"
                                        target="_blank" rel="noopener noreferrer" class="flex row">
                                        <ExternalLink class="mr-2 h-4 w-4" />
                                        Live Demo
                                    </a>
                                    <span v-else class="flex row hover:cursor-not-allowed">
                                        <ExternalLink class="mr-2 h-4 w-4" />
                                        Live Demo
                                    </span>
                                </Button>
                                <Button variant="outline" as-child
                                    :disabled="!project.githubLink || project.githubLink === '#'">
                                    <a v-if="project.githubLink && project.githubLink !== '#'"
                                        :href="project.githubLink" target="_blank" rel="noopener noreferrer"
                                        class="flex row">
                                        <Github class="mr-2 h-4 w-4" />
                                        Source Code
                                    </a>
                                    <span v-else class="flex row hover:cursor-not-allowed">
                                        <Github class="mr-2 h-4 w-4" />
                                        Source Code
                                    </span>
                                </Button>
                            </div>
                        </div>
                    </div>

                </div>
            </div>
        </div>
    </section>
</template>