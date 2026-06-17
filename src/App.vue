<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'
import {
  ArrowUpRight,
  BookOpen,
  BriefcaseBusiness,
  CheckCircle2,
  Database,
  Download,
  ExternalLink,
  FolderKanban,
  GitBranch,
  GraduationCap,
  Languages,
  Mail,
  MapPin,
  Phone,
  ShieldCheck,
  Sparkles,
  Terminal,
} from '@lucide/vue'

const activeSection = ref('')
let observer

onMounted(() => {
  observer = new IntersectionObserver(
    entries => {
      for (const entry of entries) {
        if (entry.isIntersecting) activeSection.value = entry.target.id
      }
    },
    { rootMargin: '-40% 0px -55% 0px' }
  )
  for (const id of ['projects', 'experience', 'publications', 'skills', 'contact']) {
    const el = document.getElementById(id)
    if (el) observer.observe(el)
  }
})

onBeforeUnmount(() => observer?.disconnect())

const contactLinks = [
  {
    label: 'Email',
    value: 'ebenco94@gmail.com',
    href: 'mailto:ebenco94@gmail.com',
    icon: Mail,
    external: false,
  },
  {
    label: 'Phone',
    value: '+49 176 88432408',
    href: 'tel:+4917688432408',
    icon: Phone,
    external: false,
  },
  {
    label: 'LinkedIn',
    value: 'linkedin.com/in/ebenezer-awotoro',
    href: 'https://linkedin.com/in/ebenezer-awotoro',
    icon: ExternalLink,
    external: true,
  },
  {
    label: 'GitHub',
    value: 'github.com/Ebenco36',
    href: 'https://github.com/Ebenco36',
    icon: GitBranch,
    external: true,
  },
]

const proofPoints = [
  '5+ years building backend, web, and data-driven systems',
  'Current PhD candidate at Freie Universitat Berlin',
  'Backend technical lead experience across HR, fintech, real estate, and public health',
  'Machine learning, AMR surveillance, API, Laravel, Python, Vue, and database depth',
]

const focusAreas = [
  {
    title: 'Public Health AI',
    icon: Sparkles,
    body:
      'Researching machine learning and high-dimensional data workflows for antimicrobial resistance surveillance, rare pathogen trends, and co-detection analysis.',
  },
  {
    title: 'Backend Platforms',
    icon: Terminal,
    body:
      'Designing APIs, microservices, Laravel/PHP systems, Python services, CI/CD workflows, and production-ready technical documentation.',
  },
  {
    title: 'Data Systems',
    icon: Database,
    body:
      'Cleaning, structuring, analyzing, and visualizing large datasets with attention to reproducibility, maintainability, and stakeholder communication.',
  },
]

const experience = [
  {
    role: 'Doctoral Researcher',
    company: 'Robert Koch Institute',
    period: 'Oct 2024 - Present',
    location: 'Berlin, Germany',
    summary:
      'PhD candidate enrolled at Freie Universitat Berlin, conducting doctoral research with Robert Koch Institute on machine learning and visualization methods for antimicrobial resistance surveillance.',
    bullets: [
      'Analyze AMR trends and pathogen co-detection patterns using surveillance data.',
      'Develop AI-driven visualization workflows for anomaly and trend detection.',
      'Apply unsupervised learning, categorical coding, and tensor-completion methods to complex data.',
    ],
  },
  {
    role: 'Research Assistant',
    company: 'Robert Koch Institute',
    period: 'Apr 2023 - Sep 2024',
    location: 'Berlin, Germany',
    summary:
      'Supported machine learning research through literature review, data preparation, model evaluation, research tooling, and stakeholder communication.',
    bullets: [
      'Collected, cleaned, and analyzed large datasets for machine learning experiments.',
      'Designed, implemented, and evaluated machine learning algorithms and systems.',
      'Served as teaching assistant at Freie Universitat Berlin and supported junior researchers.',
    ],
  },
  {
    role: 'Back End Engineer, Technical Lead',
    company: 'SeamlessHR',
    period: 'Nov 2021 - Mar 2023',
    location: 'Lagos, Nigeria',
    summary:
      'Owned backend technical leadership for HRIS and Leave modules, aligning engineering execution with product priorities, architecture decisions, defect resolution, and release planning.',
    bullets: [
      'Led a cross-functional delivery group of four engineers, partnering closely with UI/UX, QA, product, and stakeholder teams to move complex HR workflows from planning to production.',
      'Translated product requirements into technical specifications, architecture models, sprint-ready tasks, and implementation guidance using Structurizr for clearer system design decisions.',
      'Drove backend execution across product improvements, defect investigations, sprint delivery, and release readiness while maintaining engineering quality and delivery accountability.',
    ],
  },
  {
    role: 'Back End Developer',
    company: 'Casafina Development Company',
    period: 'Mar 2019 - Sep 2021',
    location: 'Lagos, Nigeria',
    summary:
      'Led backend development for financial workflow platforms and internal operational tools, combining API delivery, documentation, automation, and product collaboration.',
    bullets: [
      'Coordinated a two-engineer backend team to deliver loan and savings platforms, balancing feature delivery, technical quality, and day-to-day engineering execution.',
      'Designed internal tools and technical documentation that improved customer-interaction workflows, reduced implementation ambiguity, and supported smoother onboarding for team members.',
      'Implemented CI/CD pipelines and worked with product and QA partners to strengthen release discipline, improve testing flow, and resolve technical issues before production impact.',
    ],
  },
  {
    role: 'Back End Developer, Contract',
    company: 'Patricia',
    period: 'Mar 2021 - Aug 2021',
    location: 'Lagos, Nigeria',
    summary:
      'Delivered responsive WordPress and PHP solutions, custom themes, plugin work, third-party API integrations, testing, and technical support.',
    bullets: [
      'Customized themes and plugins to meet project requirements.',
      'Integrated external services and tested cross-browser, cross-device compatibility.',
      'Documented technical specifications and supported project milestones.',
    ],
  },
  {
    role: 'Back-End Developer, Contract',
    company: 'Menaget Inc',
    period: 'Jul 2019 - Jul 2020',
    location: 'Lagos, Nigeria',
    summary:
      'Developed Laravel backend components, RESTful APIs, database schemas, migrations, performance improvements, and security-focused fixes.',
    bullets: [
      'Built maintainable backend components with Laravel and PHPUnit practices.',
      'Designed database schemas, migrations, queries, and API integrations.',
      'Provided code reviews and technical guidance to junior developers.',
    ],
  },
]

const skillGroups = [
  {
    label: 'Core Engineering',
    skills: ['Python', 'PHP', 'Laravel', 'Laravel Lumen', 'JavaScript', 'Vue.js', 'Node.js', 'Django', 'Flask'],
  },
  {
    label: 'Data & Research',
    skills: ['Machine Learning', 'Deep Learning', 'Bioinformatics', 'AMR Surveillance', 'Proteomics', 'Data Visualization'],
  },
  {
    label: 'Systems & Delivery',
    skills: ['REST APIs', 'Microservices', 'Docker', 'Git', 'CI/CD', 'Scrum', 'Technical Specs', 'TDD'],
  },
  {
    label: 'Databases',
    skills: ['MySQL', 'PostgreSQL', 'MongoDB', 'Oracle Database'],
  },
]

const education = [
  {
    degree: 'PhD Candidate',
    school: 'Freie Universitat Berlin',
    period: 'Current',
    detail:
      'Doctoral research focused on machine learning, high-dimensional data analysis, and visualization workflows for antimicrobial resistance surveillance.',
  },
  {
    degree: "Master's Degree, Bioinformatics",
    school: 'University of Ibadan',
    period: '2019 - 2022',
    detail:
      'Applied machine learning to ischemic stroke RNA-Seq data to identify differential gene expression.',
  },
  {
    degree: 'Bachelor of Computer Application',
    school: 'Bangalore University',
    period: '2012 - 2015',
    detail: 'Computer software technology and application development foundation.',
  },
]

const certifications = [
  'PHP: Design Patterns',
  'Django Essential Training',
  'Learning Node.js',
  'Python Data Structures: Linked Lists',
  'Critical Thinking',
  'Oracle: Java, Oracle',
]

const projects = [
  {
    title: 'MetaMP Server',
    meta: 'Robert Koch Institute · Research software',
    body:
      'Backend research software for membrane-protein metadata enrichment, data integration, AI-assisted analysis, and visualization workflows.',
    tags: ['Python', 'Research Software', 'Bioinformatics', 'API'],
    links: [
      {
        label: 'GitHub repo',
        href: 'https://github.com/Ebenco36/MetaMP-Server',
      },
    ],
  },
  {
    title: 'AMR Surveillance Workflows',
    meta: 'Robert Koch Institute · Doctoral research',
    body:
      'Develops machine-learning and visualization workflows for antimicrobial resistance surveillance, rare pathogen trends, co-detection analysis, and anomaly-oriented exploration.',
    tags: ['AMR', 'Unsupervised Learning', 'High-Dimensional Data'],
  },
  {
    title: 'SeamlessHR Platform Modules',
    meta: 'SeamlessHR · HR software',
    body:
      'Led backend execution for HRIS and Leave modules, translating roadmap needs into technical specifications, architecture planning, delivery coordination, and production fixes.',
    tags: ['Laravel', 'Vue.js', 'REST APIs', 'Technical Leadership'],
    links: [
      {
        label: 'Company site',
        href: 'https://seamlesshr.com/',
      },
    ],
  },
  {
    title: 'Menaget Client Platforms',
    meta: 'Menaget Inc · Contract engineering',
    body:
      'Built and maintained Laravel backend components, REST APIs, database schemas, integrations, and performance-focused fixes for client-facing products.',
    tags: ['Laravel', 'REST APIs', 'Database Design', 'PHP'],
    links: [
      {
        label: 'eSarcar',
        href: 'https://www.esarcar.com/en/',
      },
      {
        label: 'e-ticket',
        href: 'https://e-ticket.app/',
      },
    ],
  },
]

const publications = [
  {
    title: 'MetaMP: Seamless Metadata Enrichment and AI Application Framework for Enhanced Membrane Protein Visualization and Analysis',
    venue: 'Manuscript under review',
    authors: 'Ebenezer Awotoro et al.',
  },
  {
    title: 'Network-based characterisation of latent co-testing patterns in antimicrobial susceptibility testing',
    venue: 'Manuscript under review',
    authors: 'Ebenezer Awotoro et al.',
  },
  {
    title: 'Cascade analysis paper',
    venue: 'In progress',
    authors: 'Ebenezer Awotoro et al.',
  },
]

const languages = [
  {
    name: 'English',
    level: 'Proficient',
  },
  {
    name: 'Yoruba',
    level: 'Native',
  },
  {
    name: 'German',
    level: 'Beginner · A1',
  },
]
</script>

<template>
  <div class="site-shell">
    <header class="topbar" aria-label="Primary navigation">
      <a class="brand" href="#top" aria-label="Awotoro Ebenezer home">AE</a>
      <nav>
        <a href="#projects" :class="{ active: activeSection === 'projects' }">Projects</a>
        <a href="#experience" :class="{ active: activeSection === 'experience' }">Experience</a>
        <a href="#publications" :class="{ active: activeSection === 'publications' }">Publications</a>
        <a href="#skills" :class="{ active: activeSection === 'skills' }">Skills</a>
        <a href="#contact" :class="{ active: activeSection === 'contact' }">Contact</a>
      </nav>
    </header>

    <main id="top">
      <section class="hero">
        <img
          class="hero-image"
          src="/hero-research-software.png"
          alt="Abstract public health data visualization and software engineering workspace"
        />
        <div class="hero-overlay"></div>
        <div class="hero-content">
          <div class="hero-text">
            <p class="eyebrow"><MapPin :size="16" /> Berlin, Germany</p>
            <h1>Awotoro Ebenezer Oladimeji</h1>
            <p class="hero-title">Researcher & Software Engineer</p>
            <p class="hero-copy">
              I build reliable backend platforms and research software for data-intensive problems,
              combining production engineering experience with machine learning work in public health
              and antimicrobial resistance surveillance.
            </p>
            <div class="hero-actions" aria-label="Primary actions">
              <a class="button button-primary" href="mailto:ebenco94@gmail.com">
                <Mail :size="18" />
                Contact me
              </a>
              <a class="button button-secondary" href="/resume-awotoro-ebenezer-oladimeji.pdf" download>
                <Download :size="18" />
                Download CV
              </a>
            </div>
          </div>
          <figure class="hero-portrait">
            <div class="portrait-frame">
              <img
                src="/DSC00811_Awotoro_hockant.jpg"
                alt="Professional portrait of Awotoro Ebenezer Oladimeji"
                width="1024"
                height="1536"
              />
            </div>
          </figure>
        </div>
      </section>

      <section class="proof-band" aria-label="Profile proof points">
        <div v-for="point in proofPoints" :key="point" class="proof-item">
          <CheckCircle2 :size="18" />
          <span>{{ point }}</span>
        </div>
      </section>

      <section class="section intro-section">
        <div class="section-heading">
          <p class="eyebrow">Recruiter Summary</p>
          <h2>Backend depth with research-grade analytical discipline.</h2>
        </div>
        <div class="intro-copy">
          <p>
            My strongest profile is not generic full-stack breadth. It is the intersection of backend
            engineering, machine learning, data workflows, and technical leadership. I have delivered
            APIs and web platforms in production, led engineering teams, written technical
            specifications, and now apply that engineering base to public-health research systems.
          </p>
          <p>
            I am best matched to roles that need a software engineer who can reason about systems,
            data, stakeholders, and scientific uncertainty without treating implementation quality as
            an afterthought.
          </p>
        </div>
      </section>

      <section class="section focus-section" aria-label="Focus areas">
        <article v-for="area in focusAreas" :key="area.title" class="focus-card">
          <component :is="area.icon" :size="24" />
          <h3>{{ area.title }}</h3>
          <p>{{ area.body }}</p>
        </article>
      </section>

      <section id="projects" class="section projects-section">
        <div class="section-heading">
          <p class="eyebrow"><FolderKanban :size="16" /> Selected Projects</p>
          <h2>Selected systems, research tools, and product work.</h2>
        </div>
        <div class="project-grid">
          <article v-for="project in projects" :key="project.title" class="project-card">
            <p class="timeline-date">{{ project.meta }}</p>
            <h3>{{ project.title }}</h3>
            <p>{{ project.body }}</p>
            <div class="chips">
              <span v-for="tag in project.tags" :key="`${project.title}-${tag}`">{{ tag }}</span>
            </div>
            <div v-if="project.links" class="project-links">
              <a
                v-for="link in project.links"
                :key="`${project.title}-${link.href}`"
                :href="link.href"
                class="text-link"
                target="_blank"
                rel="noreferrer"
              >
                {{ link.label }}
                <ArrowUpRight :size="16" />
              </a>
            </div>
          </article>
        </div>
      </section>

      <section id="experience" class="section timeline-section">
        <div class="section-heading">
          <p class="eyebrow"><BriefcaseBusiness :size="16" /> Experience</p>
          <h2>Evidence of delivery across research and production systems.</h2>
        </div>
        <div class="timeline">
          <article v-for="item in experience" :key="`${item.company}-${item.period}`" class="timeline-item">
            <div class="timeline-date">{{ item.period }}</div>
            <div class="timeline-card">
              <div class="role-line">
                <div>
                  <h3>{{ item.role }}</h3>
                  <p>{{ item.company }} · {{ item.location }}</p>
                </div>
                <ShieldCheck :size="22" />
              </div>
              <p class="summary">{{ item.summary }}</p>
              <ul>
                <li v-for="bullet in item.bullets" :key="bullet">{{ bullet }}</li>
              </ul>
            </div>
          </article>
        </div>
      </section>

      <section id="publications" class="section publications-section">
        <div class="section-heading">
          <p class="eyebrow"><BookOpen :size="16" /> Publications</p>
          <h2>Research output that supports the software and public-health positioning.</h2>
        </div>
        <div class="publication-list">
          <article v-for="publication in publications" :key="publication.title" class="publication-card">
            <p class="timeline-date">{{ publication.venue }}</p>
            <h3>{{ publication.title }}</h3>
            <p>{{ publication.authors }}</p>
          </article>
        </div>
      </section>

      <section id="skills" class="section skills-section">
        <div class="section-heading">
          <p class="eyebrow">Technical Range</p>
          <h2>Skills grouped by how recruiters evaluate fit.</h2>
        </div>
        <div class="skill-grid">
          <article v-for="group in skillGroups" :key="group.label" class="skill-card">
            <h3>{{ group.label }}</h3>
            <div class="chips">
              <span v-for="skill in group.skills" :key="skill">{{ skill }}</span>
            </div>
          </article>
        </div>
      </section>

      <section class="section languages-section">
        <div class="section-heading">
          <p class="eyebrow"><Languages :size="16" /> Languages</p>
          <h2>Communication range for international engineering and research teams.</h2>
        </div>
        <div class="language-grid">
          <article v-for="language in languages" :key="language.name" class="language-card">
            <h3>{{ language.name }}</h3>
            <p v-if="language.level">{{ language.level }}</p>
          </article>
        </div>
      </section>

      <section id="education" class="section education-section">
        <div class="section-heading">
          <p class="eyebrow"><GraduationCap :size="16" /> Education & Credentials</p>
          <h2>Academic base for computational biology and software systems.</h2>
        </div>
        <div class="education-layout">
          <div class="education-list">
            <article v-for="item in education" :key="item.degree" class="education-card">
              <p class="timeline-date">{{ item.period }}</p>
              <h3>{{ item.degree }}</h3>
              <p class="school">{{ item.school }}</p>
              <p>{{ item.detail }}</p>
            </article>
          </div>
          <div class="certification-panel">
            <h3>Selected Certifications</h3>
            <div class="cert-list">
              <span v-for="cert in certifications" :key="cert">{{ cert }}</span>
            </div>
          </div>
        </div>
      </section>

      <section id="contact" class="contact-section">
        <div>
          <p class="eyebrow">Available For</p>
          <h2>Backend engineering, research software, data platforms, and ML-enabled health technology roles.</h2>
        </div>
        <div class="contact-grid">
          <a
            v-for="link in contactLinks"
            :key="link.label"
            :href="link.href"
            class="contact-card"
            :target="link.external ? '_blank' : undefined"
            :rel="link.external ? 'noopener noreferrer' : undefined"
          >
            <component :is="link.icon" :size="22" />
            <span>{{ link.label }}</span>
            <strong>{{ link.value }}</strong>
            <ArrowUpRight :size="18" class="contact-arrow" />
          </a>
        </div>
      </section>
    </main>
    <footer class="site-footer">
      <div>
        <strong>Awotoro Ebenezer Oladimeji</strong>
        <span>Researcher & Software Engineer · Berlin, Germany</span>
      </div>
      <div class="footer-links">
        <a href="mailto:ebenco94@gmail.com">Email</a>
        <a href="https://linkedin.com/in/ebenezer-awotoro" target="_blank" rel="noreferrer">LinkedIn</a>
        <a href="https://github.com/Ebenco36" target="_blank" rel="noreferrer">GitHub</a>
        <a href="/resume-awotoro-ebenezer-oladimeji.pdf" download>CV</a>
      </div>
    </footer>
  </div>
</template>
