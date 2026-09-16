<div align="center">

<img src="https://smsadda.vercel.app/favicon/favicon.svg" width="74" alt="SMS Adda">

# SMS Adda

**A security research playground for Nepal's SMS infrastructure.**

<br>

<a href="https://smsadda.vercel.app/">
<img src="https://img.shields.io/badge/LIVE-smsadda.vercel.app-111111?style=flat-square&logo=vercel&logoColor=white" />
</a>
&nbsp;
<a href="https://github.com/iamlaxman/sms">
<img src="https://img.shields.io/badge/SOURCE-GitHub-111111?style=flat-square&logo=github&logoColor=white" />
</a>
&nbsp;
<img src="https://img.shields.io/github/last-commit/iamlaxman/sms?style=flat-square&color=ff4d00" />

<br><br>

<img src="https://readme-typing-svg.demolab.com?font=IBM+Plex+Mono&size=16&duration=2800&pause=1000&color=FF4D00&center=true&vCenter=true&width=760&height=30&lines=security+research;SMS+%2F+OTP+infrastructure;gateway+experimentation;responsible+testing;built+in+Nepal." />

</div>

---

## `/ about`

**SMS Adda** is a web-first security research project built around Nepal's SMS and OTP ecosystem.

The project explores how automated messaging systems behave, where weaknesses can appear in SMS delivery pipelines, and how those weaknesses can be understood from a defensive perspective.

The project's own documentation describes the goal as understanding vulnerabilities and documenting the **pattern rather than weaponising the exploit**.

```text
research
   ↓
observe
   ↓
understand
   ↓
document
   ↓
improve defensive awareness
```

---

## `/ live`

**Web**

https://smsadda.vercel.app/

**Repository**

https://github.com/iamlaxman/sms

**Author**

Laxman Poudel

---

## `/ what-it-is`

```text
SMS Adda
├── security research playground
├── Nepal-focused SMS / OTP workflow
├── browser-based interface
├── gateway experimentation
├── live request trace
├── bulk input support
└── installable PWA
```

The landing page presents the project as a security-research playground built in Nepal, while the application itself provides the SMS sending workflow.

---

## `/ research`

The project documents several classes of weaknesses observed in SMS systems, including:

```text
rate-limit gaps
session-handling flaws
unauthenticated OTP triggers
automated request exposure
gateway-level failure handling
```

The public site explicitly frames these as research subjects rather than targets for abuse.

---

## `/ workflow`

The application models a request flow built around:

```text
01  client.submit()
02  worker request
03  phone validation
04  gateway selection
05  gateway attempts
06  delivery
```

The interface exposes this process through a terminal-style live trace, including request metadata, validation, gateway selection and delivery states.

---

## `/ sending`

The application currently supports two input modes:

```text
single
bulk
```

Single mode accepts a Nepal phone number, while bulk mode allows multiple numbers to be added manually or through file input. The code currently limits bulk input to 50 numbers, with separate message-count limits for single and bulk modes.

Nepal numbers are handled with the `+977` prefix and the interface validates the expected local mobile-number format.

---

## `/ gateways`

The current frontend configuration contains six gateway definitions:

```text
GW-01  Clamphook
GW-02  Ambition
GW-03  MeroDoctor
GW-04  CollegeInfo
GW-05  Pariksha
GW-06  QuickConnect
```

The application supports both automatic gateway selection and manual gateway selection. In automatic mode, the candidates are shuffled before the request flow; in manual mode, selected candidates are used directly.

The landing page also documents the research categories associated with the mapped services rather than presenting them simply as a list of targets.

---

## `/ terminal`

One of the defining parts of the project is the terminal-style trace.

```text
SMS ADDA ~/send — live trace

[01/06] client.submit()
[02/06] worker.fetch(request, env)
[03/06] validatePhone(phone)
[04/06] selectGateways(mode)
[05/06] tryGateways(phone, candidates)
[06/06] delivery
```

The browser UI renders each step progressively, including request state, validation output, gateway attempts and final status.

---

## `/ implementation`

The repository is intentionally lightweight.

```text
HTML
CSS
JavaScript
Cloudflare Worker endpoint
PWA manifest / install flow
Vercel deployment
```

The project does not use a conventional Node/Express application structure in the repository. The primary application is implemented directly in the HTML/CSS/JavaScript pages, with the sending interface configured to communicate with a Cloudflare Worker endpoint.

---

## `/ limits`

The current client-side configuration defines:

```text
MAX_BULK          = 50
MAX_COUNT_SINGLE  = 10
MAX_COUNT_BULK    = 5
```

The interface also disables controls while a send flow is running and includes a terms/privacy acceptance step before submission.

---

## `/ privacy`

The project documentation states that submitted phone numbers are intended to remain in memory for the session rather than being written to disk or retained as logs.

The repository also includes dedicated:

```text
privacy.html
terms.html
```

pages alongside the main application.

---

## `/ install`

SMS Adda is designed as a **web-first PWA**.

The project supports:

```text
Desktop browsers
Mobile browsers
PWA installation
```

The get-started page explicitly provides separate paths for continuing in the browser or installing the app, and documents installation behavior for Android, iOS and desktop browsers.

---

## `/ pages`

```text
sms/
│
├── index.html
├── app.html
├── get-started.html
├── about.html
├── login.html
├── admin.html
│
├── send-sms-np.html
├── privacy.html
├── terms.html
├── offline.html
├── 404.html
│
├── favicon/
├── og-image.png
├── robots.txt
└── sitemap.xml
```

The repository currently contains the public landing page, application interface, onboarding/install page, about page, authentication/admin-related pages, legal pages and PWA/static assets.

---

## `/ design`

SMS Adda has a deliberate editorial / brutalist visual direction rather than a conventional SaaS dashboard.

```text
F4F1E8   warm paper background
111111   primary ink
FF4D00   orange accent
DFFF00   signal highlight
```

The site uses **Space Grotesk** for display typography and **IBM Plex Mono** for technical/interface text. The homepage includes animated grid movement, reveal transitions, ticker motion, terminal panels and responsive fullscreen navigation.

---

## `/ security`

This project is published for **security research and responsible experimentation**.

The intent is to study weaknesses in automated SMS systems, understand how they can be detected, and communicate defensive lessons.

```text
Do research.
Test responsibly.
Respect providers.
Respect users.
Don't weaponise vulnerabilities.
```

The public project explicitly states that it publishes research patterns rather than exploit instructions.

---

## `/ stack`

<div align="center">

<img src="https://skillicons.dev/icons?i=html,css,js,cloudflare,vercel" />

</div>

```text
HTML5
CSS3
JavaScript
Cloudflare Workers
Vercel
PWA
```

---

## `/ philosophy`

> **Understand the system before trying to break it.**

SMS Adda is less about building another messaging interface and more about making the underlying request pipeline visible:

```text
input
  ↓
validation
  ↓
routing
  ↓
gateway
  ↓
response
  ↓
delivery
```

The interface turns that normally invisible chain into something observable.

---

## `/ author`

Built by **Laxman Poudel** in Nepal.

```yaml
name: Laxman Poudel
project: SMS Adda
website: https://laxman-poudel.com.np
github: https://github.com/iamlaxman
location: Nepal
```

---

<div align="center">

<br>

<img src="https://readme-typing-svg.demolab.com?font=IBM+Plex+Mono&size=14&duration=3000&pause=1200&color=6B665C&center=true&vCenter=true&width=620&height=28&lines=observe.;understand.;document.;secure." />

<br><br>

<sub>SMS Adda · Security research · Responsible experimentation · Built in Nepal</sub>

<br><br>

<img src="https://capsule-render.vercel.app/api?type=waving&section=footer&height=90&color=0:F4F1E8,100:FF4D00" width="100%" />

</div>
