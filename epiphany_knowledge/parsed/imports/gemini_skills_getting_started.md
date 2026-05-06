# gemini_skills_getting_started.md [DISTILLED]

**Summary:** This document provides a getting-started tutorial for creating, discovering, and managing Agent Skills in Gemini CLI. It covers the creation of `SKILL.md` and script files, explains how to verify and troubleshoot skill discovery (e.g., trust, case-sensitivity, path layout), describes the activation flow, and lists CLI commands for skill management. [See: ## Create your first skill], [See: ## Verify discovery], [See: ## Manage skills].

**Source:** https://geminicli.com/docs/cli/tutorials/skills-getting-started/

[Skip to content](#_top){.astro-7q3lir66}

::: {.page .sl-flex .astro-yriad4ts}
::: {.header .astro-yriad4ts}
::: {#page-header .header .astro-3ef6ksr2}
::: {.title-wrapper .sl-flex .items-center .gap-4 .astro-3ef6ksr2}
::: {.mobile-only .mobile-menu-wrapper .astro-3ef6ksr2}
![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9Im9wZW4tbWVudSBhc3Ryby1qaWY3M3l6dyBhc3Ryby1jNnZzb3FhcyIgd2lkdGg9IjE2IiBoZWlnaHQ9IjE2IiB2aWV3Ym94PSIwIDAgMjQgMjQiIGZpbGw9ImN1cnJlbnRDb2xvciIgc3R5bGU9Ii0tc2wtaWNvbi1zaXplOiAxZW07Ij48cGF0aCBkPSJNMyA4aDE4YTEgMSAwIDEgMCAwLTJIM2ExIDEgMCAwIDAgMCAyWm0xOCA4SDNhMSAxIDAgMCAwIDAgMmgxOGExIDEgMCAwIDAgMC0yWm0wLTVIM2ExIDEgMCAwIDAgMCAyaDE4YTEgMSAwIDAgMCAwLTJaIj48L3BhdGg+PC9zdmc+){.open-menu
.astro-jif73yzw .astro-c6vsoqas}
![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9ImNsb3NlLW1lbnUgYXN0cm8tamlmNzN5encgYXN0cm8tYzZ2c29xYXMiIHdpZHRoPSIxNiIgaGVpZ2h0PSIxNiIgdmlld2JveD0iMCAwIDI0IDI0IiBmaWxsPSJjdXJyZW50Q29sb3IiIHN0eWxlPSItLXNsLWljb24tc2l6ZTogMWVtOyI+PHBhdGggZD0ibTEzLjQxIDEyIDYuMy02LjI5YTEuMDA0IDEuMDA0IDAgMSAwLTEuNDItMS40MkwxMiAxMC41OWwtNi4yOS02LjNhMS4wMDQgMS4wMDQgMCAwIDAtMS40MiAxLjQybDYuMyA2LjI5LTYuMyA2LjI5YTEgMSAwIDAgMCAwIDEuNDIuOTk4Ljk5OCAwIDAgMCAxLjQyIDBsNi4yOS02LjMgNi4yOSA2LjNhLjk5OS45OTkgMCAwIDAgMS40MiAwIDEgMSAwIDAgMCAwLTEuNDJMMTMuNDEgMTJaIj48L3BhdGg+PC9zdmc+){.close-menu
.astro-jif73yzw .astro-c6vsoqas}
:::

[![Gemini CLI Icon](/_astro/icon.Bo4M5sF3.png){.astro-m46x6ez3
width="1645" height="1645"} [ Gemini CLI ]{.astro-m46x6ez3
translate="no"}](/){.site-title .sl-flex .astro-m46x6ez3}

::: {.mobile-hide .astro-3ef6ksr2}
-   [[Home]{.astro-jvd4jwbq}](/){.no-underline .astro-jvd4jwbq}
-   [[Plans]{.astro-jvd4jwbq}](/plans/){.no-underline .astro-jvd4jwbq}
-   [Extensions]{.astro-jvd4jwbq}
    ![](data:image/svg+xml;base64,PHN2ZyB2aWV3Ym94PSIwIDAgMjQgMjQiIHdpZHRoPSIyMCIgaGVpZ2h0PSIyMCIgY2xhc3M9ImNhcmV0IGFzdHJvLWp2ZDRqd2JxIiBmaWxsPSJjdXJyZW50Q29sb3IiPiA8cGF0aCBkPSJtMTQuODMgMTEuMjktNC4yNC00LjI0YTEgMSAwIDEgMC0xLjQyIDEuNDFMMTIuNzEgMTJsLTMuNTQgMy41NGExIDEgMCAwIDAgMCAxLjQxIDEgMSAwIDAgMCAuNzEuMjkgMSAxIDAgMCAwIC43MS0uMjlsNC4yNC00LjI0YTEuMDAyIDEuMDAyIDAgMCAwIDAtMS40MloiIGNsYXNzPSJhc3Ryby1qdmQ0andicSI+PC9wYXRoPiA8L3N2Zz4=){.caret
    .astro-jvd4jwbq}
    -   [[Browse
        extensions]{.astro-jvd4jwbq}](/extensions/){.no-underline
        .astro-jvd4jwbq}
    -   [[About
        Extensions]{.astro-jvd4jwbq}](/extensions/about){.no-underline
        .astro-jvd4jwbq}
-   [[Docs]{.astro-jvd4jwbq}](/docs/){.no-underline .is-active
    .astro-jvd4jwbq}
-   [[Reference]{.astro-jvd4jwbq}](/docs/reference/commands){.no-underline
    .astro-jvd4jwbq}
-   [[Resources]{.astro-jvd4jwbq}](/docs/resources/quota-and-pricing){.no-underline
    .astro-jvd4jwbq}
-   [[Changelog]{.astro-jvd4jwbq}](/docs/changelogs/){.no-underline
    .astro-jvd4jwbq}
:::
:::

::: {.sl-flex .items-center .gap-4 .search-and-icons .astro-3ef6ksr2}
::: {.sl-flex .justify-end .print:hidden .search .astro-3ef6ksr2}
![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9ImFzdHJvLXYzN21ua256IGFzdHJvLWM2dnNvcWFzIiB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCIgZmlsbD0iY3VycmVudENvbG9yIiBzdHlsZT0iLS1zbC1pY29uLXNpemU6IDFlbTsiPjxwYXRoIGQ9Ik0yMS43MSAyMC4yOSAxOCAxNi42MUE5IDkgMCAxIDAgMTYuNjEgMThsMy42OCAzLjY4YS45OTkuOTk5IDAgMCAwIDEuNDIgMCAxIDEgMCAwIDAgMC0xLjM5Wk0xMSAxOGE3IDcgMCAxIDEgMC0xNCA3IDcgMCAwIDEgMCAxNFoiPjwvcGF0aD48L3N2Zz4=){.astro-v37mnknz
.astro-c6vsoqas} [Search]{.sl-hidden .md:sl-block .astro-v37mnknz
aria-hidden="true"} [ [Ctrl]{.kbd .astro-v37mnknz}[K]{.kbd
.astro-v37mnknz} ]{.kbd .sl-hidden .md:sl-flex .astro-v37mnknz
style="display: none;"}

::: {.dialog-frame .sl-flex .astro-v37mnknz}
Cancel

::: {.search-container .astro-v37mnknz}
::: {#starlight__search .astro-v37mnknz}
:::
:::
:::
:::

::: {.sl-flex .print:hidden .right-group .astro-3ef6ksr2}
::: {.sl-flex .social-icons .links .astro-3ef6ksr2}
[![](data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIGhlaWdodD0iMjRweCIgdmlld2JveD0iMCAwIDI0IDI0IiB3aWR0aD0iMjRweCIgZmlsbD0iY3VycmVudENvbG9yIiBjbGFzcz0iZmVlZGJhY2staWNvbiBhc3Ryby0zZWY2a3NyMiIgYXJpYS1oaWRkZW49InRydWUiPiA8cGF0aCBkPSJNMCAwaDI0djI0SDBWMHoiIGZpbGw9Im5vbmUiIGNsYXNzPSJhc3Ryby0zZWY2a3NyMiI+PC9wYXRoPiA8cGF0aCBkPSJNMjAgMkg0Yy0xLjEgMC0yIC45LTIgMnYxOGw0LTRoMTRjMS4xIDAgMi0uOSAyLTJWNGMwLTEuMS0uOS0yLTItMnptMCAxNEg2bC0yIDJWNGgxNnYxMnoiIGNsYXNzPSJhc3Ryby0zZWY2a3NyMiI+PC9wYXRoPiA8cGF0aCBkPSJNMTEgNWgydjZoLTJ6bTAgOGgydjJoLTJ6IiBjbGFzcz0iYXN0cm8tM2VmNmtzcjIiPjwvcGF0aD4gPC9zdmc+){.feedback-icon
.astro-3ef6ksr2} [Feedback]{.feedback-label
.astro-3ef6ksr2}](https://github.com/google-gemini/gemini-cli/issues/new?template=website_issue.yml&url=https%3A%2F%2Fgeminicli.com%2Fdocs%2Fcli%2Ftutorials%2Fskills-getting-started%2F){.feedback-link
.astro-3ef6ksr2 target="_blank" rel="noopener noreferrer"}
[[GitHub]{.sr-only .astro-3ef6ksr2}
![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgd2lkdGg9IjE2IiBoZWlnaHQ9IjE2IiB2aWV3Ym94PSIwIDAgMjQgMjQiIGZpbGw9ImN1cnJlbnRDb2xvciIgY2xhc3M9ImFzdHJvLTNlZjZrc3IyIj4gPHBhdGggZD0iTTEyIC4zYTEyIDEyIDAgMCAwLTMuOCAyMy4zOGMuNi4xMi44My0uMjYuODMtLjU3TDkgMjEuMDdjLTMuMzQuNzItNC4wNC0xLjYxLTQuMDQtMS42MS0uNTUtMS4zOS0xLjM0LTEuNzYtMS4zNC0xLjc2LTEuMDgtLjc0LjA5LS43My4wOS0uNzMgMS4yLjA5IDEuODMgMS4yNCAxLjgzIDEuMjQgMS4wOCAxLjgzIDIuODEgMS4zIDMuNSAxIC4xLS43OC40Mi0xLjMxLjc2LTEuNjEtMi42Ny0uMy01LjQ3LTEuMzMtNS40Ny01LjkzIDAtMS4zMS40Ny0yLjM4IDEuMjQtMy4yMi0uMTQtLjMtLjU0LTEuNTIuMS0zLjE4IDAgMCAxLS4zMiAzLjMgMS4yM2ExMS41IDExLjUgMCAwIDEgNiAwYzIuMjgtMS41NSAzLjI5LTEuMjMgMy4yOS0xLjIzLjY0IDEuNjYuMjQgMi44OC4xMiAzLjE4YTQuNjUgNC42NSAwIDAgMSAxLjIzIDMuMjJjMCA0LjYxLTIuOCA1LjYzLTUuNDggNS45Mi40Mi4zNi44MSAxLjEuODEgMi4yMmwtLjAxIDMuMjljMCAuMzEuMi42OS44Mi41N0ExMiAxMiAwIDAgMCAxMiAuM1oiIGNsYXNzPSJhc3Ryby0zZWY2a3NyMiI+PC9wYXRoPiA8L3N2Zz4=){.astro-3ef6ksr2}
[GitHub]{.github-label
.astro-3ef6ksr2}](https://github.com/google-gemini/gemini-cli){.github-link
.astro-3ef6ksr2 target="_blank" rel="noopener noreferrer"}
:::

::: {.select-group .astro-3ef6ksr2}
[Select theme]{.sr-only .astro-4yphtoen}
![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9Imljb24gbGFiZWwtaWNvbiBhc3Ryby00eXBodG9lbiBhc3Ryby1jNnZzb3FhcyIgd2lkdGg9IjE2IiBoZWlnaHQ9IjE2IiB2aWV3Ym94PSIwIDAgMjQgMjQiIGZpbGw9ImN1cnJlbnRDb2xvciIgc3R5bGU9Ii0tc2wtaWNvbi1zaXplOiAxZW07Ij48cGF0aCBkPSJNMjEgMTRoLTFWN2EzIDMgMCAwIDAtMy0zSDdhMyAzIDAgMCAwLTMgM3Y3SDNhMSAxIDAgMCAwLTEgMXYyYTMgMyAwIDAgMCAzIDNoMTRhMyAzIDAgMCAwIDMtM3YtMmExIDEgMCAwIDAtMS0xWk02IDdhMSAxIDAgMCAxIDEtMWgxMGExIDEgMCAwIDEgMSAxdjdINlY3Wm0xNCAxMGExIDEgMCAwIDEtMSAxSDVhMSAxIDAgMCAxLTEtMXYtMWgxNnYxWiI+PC9wYXRoPjwvc3ZnPg==){.icon
.label-icon .astro-4yphtoen .astro-c6vsoqas} DarkLightAuto
![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9Imljb24gY2FyZXQgYXN0cm8tNHlwaHRvZW4gYXN0cm8tYzZ2c29xYXMiIHdpZHRoPSIxNiIgaGVpZ2h0PSIxNiIgdmlld2JveD0iMCAwIDI0IDI0IiBmaWxsPSJjdXJyZW50Q29sb3IiIHN0eWxlPSItLXNsLWljb24tc2l6ZTogMWVtOyI+PHBhdGggZD0iTTE3IDkuMTdhMSAxIDAgMCAwLTEuNDEgMEwxMiAxMi43MSA4LjQ2IDkuMTdhMSAxIDAgMSAwLTEuNDEgMS40Mmw0LjI0IDQuMjRhMS4wMDIgMS4wMDIgMCAwIDAgMS40MiAwTDE3IDEwLjU5YTEuMDAyIDEuMDAyIDAgMCAwIDAtMS40MloiPjwvcGF0aD48L3N2Zz4=){.icon
.caret .astro-4yphtoen .astro-c6vsoqas}
:::
:::
:::
:::
:::

::: {#starlight__sidebar .sidebar-pane .astro-yriad4ts}
::: {.sidebar-content .sl-flex .astro-yriad4ts}
::: {.mobile-only .w-full .astro-yriad4ts}
-   [[Home]{.astro-3ii7xxms}](/){.large .astro-3ii7xxms
    aria-current="false"}
-   [[Plans]{.astro-3ii7xxms}](/plans/){.large .astro-3ii7xxms
    aria-current="false"}
-   [ [Extensions]{.large .astro-3ii7xxms} ]{.group-label
    .astro-3ii7xxms}
    ![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9ImNhcmV0IGFzdHJvLTNpaTd4eG1zIGFzdHJvLWM2dnNvcWFzIiB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCIgZmlsbD0iY3VycmVudENvbG9yIiBzdHlsZT0iLS1zbC1pY29uLXNpemU6IDEuMjVyZW07Ij48cGF0aCBkPSJtMTQuODMgMTEuMjktNC4yNC00LjI0YTEgMSAwIDEgMC0xLjQyIDEuNDFMMTIuNzEgMTJsLTMuNTQgMy41NGExIDEgMCAwIDAgMCAxLjQxIDEgMSAwIDAgMCAuNzEuMjkgMSAxIDAgMCAwIC43MS0uMjlsNC4yNC00LjI0YTEuMDAyIDEuMDAyIDAgMCAwIDAtMS40MloiPjwvcGF0aD48L3N2Zz4=){.caret
    .astro-3ii7xxms .astro-c6vsoqas}
    -   [[Browse
        extensions]{.astro-3ii7xxms}](/extensions/){.astro-3ii7xxms
        aria-current="false"}
    -   [[About
        Extensions]{.astro-3ii7xxms}](/extensions/about){.astro-3ii7xxms
        aria-current="false"}
-   [ [Docs]{.large .astro-3ii7xxms} ]{.group-label .astro-3ii7xxms}
    ![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9ImNhcmV0IGFzdHJvLTNpaTd4eG1zIGFzdHJvLWM2dnNvcWFzIiB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCIgZmlsbD0iY3VycmVudENvbG9yIiBzdHlsZT0iLS1zbC1pY29uLXNpemU6IDEuMjVyZW07Ij48cGF0aCBkPSJtMTQuODMgMTEuMjktNC4yNC00LjI0YTEgMSAwIDEgMC0xLjQyIDEuNDFMMTIuNzEgMTJsLTMuNTQgMy41NGExIDEgMCAwIDAgMCAxLjQxIDEgMSAwIDAgMCAuNzEuMjkgMSAxIDAgMCAwIC43MS0uMjlsNC4yNC00LjI0YTEuMDAyIDEuMDAyIDAgMCAwIDAtMS40MloiPjwvcGF0aD48L3N2Zz4=){.caret
    .astro-3ii7xxms .astro-c6vsoqas}
    -   [ [Get started]{.large .astro-3ii7xxms} ]{.group-label
        .astro-3ii7xxms}
        ![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9ImNhcmV0IGFzdHJvLTNpaTd4eG1zIGFzdHJvLWM2dnNvcWFzIiB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCIgZmlsbD0iY3VycmVudENvbG9yIiBzdHlsZT0iLS1zbC1pY29uLXNpemU6IDEuMjVyZW07Ij48cGF0aCBkPSJtMTQuODMgMTEuMjktNC4yNC00LjI0YTEgMSAwIDEgMC0xLjQyIDEuNDFMMTIuNzEgMTJsLTMuNTQgMy41NGExIDEgMCAwIDAgMCAxLjQxIDEgMSAwIDAgMCAuNzEuMjkgMSAxIDAgMCAwIC43MS0uMjlsNC4yNC00LjI0YTEuMDAyIDEuMDAyIDAgMCAwIDAtMS40MloiPjwvcGF0aD48L3N2Zz4=){.caret
        .astro-3ii7xxms .astro-c6vsoqas}
        -   [[Overview]{.astro-3ii7xxms}](/docs/){.astro-3ii7xxms
            aria-current="false"}
        -   [[Quickstart]{.astro-3ii7xxms}](/docs/get-started/){.astro-3ii7xxms
            aria-current="false"}
        -   [[Installation]{.astro-3ii7xxms}](/docs/get-started/installation/){.astro-3ii7xxms
            aria-current="false"}
        -   [[Authentication]{.astro-3ii7xxms}](/docs/get-started/authentication/){.astro-3ii7xxms
            aria-current="false"}
        -   [[CLI
            cheatsheet]{.astro-3ii7xxms}](/docs/cli/cli-reference/){.astro-3ii7xxms
            aria-current="false"}
        -   [[Gemini 3 on Gemini
            CLI]{.astro-3ii7xxms}](/docs/get-started/gemini-3/){.astro-3ii7xxms
            aria-current="false"}
    -   [ [Use Gemini CLI]{.large .astro-3ii7xxms} ]{.group-label
        .astro-3ii7xxms}
        ![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9ImNhcmV0IGFzdHJvLTNpaTd4eG1zIGFzdHJvLWM2dnNvcWFzIiB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCIgZmlsbD0iY3VycmVudENvbG9yIiBzdHlsZT0iLS1zbC1pY29uLXNpemU6IDEuMjVyZW07Ij48cGF0aCBkPSJtMTQuODMgMTEuMjktNC4yNC00LjI0YTEgMSAwIDEgMC0xLjQyIDEuNDFMMTIuNzEgMTJsLTMuNTQgMy41NGExIDEgMCAwIDAgMCAxLjQxIDEgMSAwIDAgMCAuNzEuMjkgMSAxIDAgMCAwIC43MS0uMjlsNC4yNC00LjI0YTEuMDAyIDEuMDAyIDAgMCAwIDAtMS40MloiPjwvcGF0aD48L3N2Zz4=){.caret
        .astro-3ii7xxms .astro-c6vsoqas}
        -   [[File
            management]{.astro-3ii7xxms}](/docs/cli/tutorials/file-management/){.astro-3ii7xxms
            aria-current="false"}
        -   [[Get started with Agent
            Skills]{.astro-3ii7xxms}](/docs/cli/tutorials/skills-getting-started/){.astro-3ii7xxms
            aria-current="page"}
        -   [[Manage context and
            memory]{.astro-3ii7xxms}](/docs/cli/tutorials/memory-management/){.astro-3ii7xxms
            aria-current="false"}
        -   [[Execute shell
            commands]{.astro-3ii7xxms}](/docs/cli/tutorials/shell-commands/){.astro-3ii7xxms
            aria-current="false"}
        -   [[Manage sessions and
            history]{.astro-3ii7xxms}](/docs/cli/tutorials/session-management/){.astro-3ii7xxms
            aria-current="false"}
        -   [[Plan tasks with
            todos]{.astro-3ii7xxms}](/docs/cli/tutorials/task-planning/){.astro-3ii7xxms
            aria-current="false"}
        -   [[Use Plan Mode with model steering]{.astro-3ii7xxms}
            [🔬]{.sl-badge .default .small .astro-3ii7xxms
            .astro-avdet4wd}](/docs/cli/tutorials/plan-mode-steering/){.astro-3ii7xxms
            aria-current="false"}
        -   [[Web search and
            fetch]{.astro-3ii7xxms}](/docs/cli/tutorials/web-tools/){.astro-3ii7xxms
            aria-current="false"}
        -   [[Set up an MCP
            server]{.astro-3ii7xxms}](/docs/cli/tutorials/mcp-setup/){.astro-3ii7xxms
            aria-current="false"}
        -   [[Automate
            tasks]{.astro-3ii7xxms}](/docs/cli/tutorials/automation/){.astro-3ii7xxms
            aria-current="false"}
    -   [ [Features]{.large .astro-3ii7xxms} ]{.group-label
        .astro-3ii7xxms}
        ![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9ImNhcmV0IGFzdHJvLTNpaTd4eG1zIGFzdHJvLWM2dnNvcWFzIiB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCIgZmlsbD0iY3VycmVudENvbG9yIiBzdHlsZT0iLS1zbC1pY29uLXNpemU6IDEuMjVyZW07Ij48cGF0aCBkPSJtMTQuODMgMTEuMjktNC4yNC00LjI0YTEgMSAwIDEgMC0xLjQyIDEuNDFMMTIuNzEgMTJsLTMuNTQgMy41NGExIDEgMCAwIDAgMCAxLjQxIDEgMSAwIDAgMCAuNzEuMjkgMSAxIDAgMCAwIC43MS0uMjlsNC4yNC00LjI0YTEuMDAyIDEuMDAyIDAgMCAwIDAtMS40MloiPjwvcGF0aD48L3N2Zz4=){.caret
        .astro-3ii7xxms .astro-c6vsoqas}
        -   [ [Extensions]{.large .astro-3ii7xxms} ]{.group-label
            .astro-3ii7xxms}
            ![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9ImNhcmV0IGFzdHJvLTNpaTd4eG1zIGFzdHJvLWM2dnNvcWFzIiB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCIgZmlsbD0iY3VycmVudENvbG9yIiBzdHlsZT0iLS1zbC1pY29uLXNpemU6IDEuMjVyZW07Ij48cGF0aCBkPSJtMTQuODMgMTEuMjktNC4yNC00LjI0YTEgMSAwIDEgMC0xLjQyIDEuNDFMMTIuNzEgMTJsLTMuNTQgMy41NGExIDEgMCAwIDAgMCAxLjQxIDEgMSAwIDAgMCAuNzEuMjkgMSAxIDAgMCAwIC43MS0uMjlsNC4yNC00LjI0YTEuMDAyIDEuMDAyIDAgMCAwIDAtMS40MloiPjwvcGF0aD48L3N2Zz4=){.caret
            .astro-3ii7xxms .astro-c6vsoqas}
            -   [[Overview]{.astro-3ii7xxms}](/docs/extensions/){.astro-3ii7xxms
                aria-current="false"}
            -   [[User guide: Install and
                manage]{.astro-3ii7xxms}](/docs/extensions/#manage-extensions){.astro-3ii7xxms
                aria-current="false"}
            -   [[Developer guide: Build
                extensions]{.astro-3ii7xxms}](/docs/extensions/writing-extensions/){.astro-3ii7xxms
                aria-current="false"}
            -   [[Developer guide: Best
                practices]{.astro-3ii7xxms}](/docs/extensions/best-practices/){.astro-3ii7xxms
                aria-current="false"}
            -   [[Developer guide:
                Releasing]{.astro-3ii7xxms}](/docs/extensions/releasing/){.astro-3ii7xxms
                aria-current="false"}
            -   [[Developer guide:
                Reference]{.astro-3ii7xxms}](/docs/extensions/reference/){.astro-3ii7xxms
                aria-current="false"}
        -   [ [Agent Skills]{.large .astro-3ii7xxms} ]{.group-label
            .astro-3ii7xxms}
            ![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9ImNhcmV0IGFzdHJvLTNpaTd4eG1zIGFzdHJvLWM2dnNvcWFzIiB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCIgZmlsbD0iY3VycmVudENvbG9yIiBzdHlsZT0iLS1zbC1pY29uLXNpemU6IDEuMjVyZW07Ij48cGF0aCBkPSJtMTQuODMgMTEuMjktNC4yNC00LjI0YTEgMSAwIDEgMC0xLjQyIDEuNDFMMTIuNzEgMTJsLTMuNTQgMy41NGExIDEgMCAwIDAgMCAxLjQxIDEgMSAwIDAgMCAuNzEuMjkgMSAxIDAgMCAwIC43MS0uMjlsNC4yNC00LjI0YTEuMDAyIDEuMDAyIDAgMCAwIDAtMS40MloiPjwvcGF0aD48L3N2Zz4=){.caret
            .astro-3ii7xxms .astro-c6vsoqas}
            -   [[Overview]{.astro-3ii7xxms}](/docs/cli/skills/){.astro-3ii7xxms
                aria-current="false"}
            -   [[Get started with Agent
                Skills]{.astro-3ii7xxms}](/docs/cli/tutorials/skills-getting-started/){.astro-3ii7xxms
                aria-current="false"}
            -   [[Creating Agent
                Skills]{.astro-3ii7xxms}](/docs/cli/creating-skills/){.astro-3ii7xxms
                aria-current="false"}
            -   [[Using Agent
                Skills]{.astro-3ii7xxms}](/docs/cli/using-agent-skills/){.astro-3ii7xxms
                aria-current="false"}
            -   [[Developer guide: Best
                practices]{.astro-3ii7xxms}](/docs/cli/skills-best-practices/){.astro-3ii7xxms
                aria-current="false"}
        -   [[Auto Memory]{.astro-3ii7xxms} [🔬]{.sl-badge .default
            .small .astro-3ii7xxms
            .astro-avdet4wd}](/docs/cli/auto-memory/){.astro-3ii7xxms
            aria-current="false"}
        -   [[Checkpointing]{.astro-3ii7xxms}](/docs/cli/checkpointing/){.astro-3ii7xxms
            aria-current="false"}
        -   [[Headless
            mode]{.astro-3ii7xxms}](/docs/cli/headless/){.astro-3ii7xxms
            aria-current="false"}
        -   [[Git worktrees]{.astro-3ii7xxms} [🔬]{.sl-badge .default
            .small .astro-3ii7xxms
            .astro-avdet4wd}](/docs/cli/git-worktrees/){.astro-3ii7xxms
            aria-current="false"}
        -   [ [Hooks]{.large .astro-3ii7xxms} ]{.group-label
            .astro-3ii7xxms}
            ![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9ImNhcmV0IGFzdHJvLTNpaTd4eG1zIGFzdHJvLWM2dnNvcWFzIiB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCIgZmlsbD0iY3VycmVudENvbG9yIiBzdHlsZT0iLS1zbC1pY29uLXNpemU6IDEuMjVyZW07Ij48cGF0aCBkPSJtMTQuODMgMTEuMjktNC4yNC00LjI0YTEgMSAwIDEgMC0xLjQyIDEuNDFMMTIuNzEgMTJsLTMuNTQgMy41NGExIDEgMCAwIDAgMCAxLjQxIDEgMSAwIDAgMCAuNzEuMjkgMSAxIDAgMCAwIC43MS0uMjlsNC4yNC00LjI0YTEuMDAyIDEuMDAyIDAgMCAwIDAtMS40MloiPjwvcGF0aD48L3N2Zz4=){.caret
            .astro-3ii7xxms .astro-c6vsoqas}
            -   [[Overview]{.astro-3ii7xxms}](/docs/hooks/){.astro-3ii7xxms
                aria-current="false"}
            -   [[Reference]{.astro-3ii7xxms}](/docs/hooks/reference/){.astro-3ii7xxms
                aria-current="false"}
        -   [ [IDE integration]{.large .astro-3ii7xxms} ]{.group-label
            .astro-3ii7xxms}
            ![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9ImNhcmV0IGFzdHJvLTNpaTd4eG1zIGFzdHJvLWM2dnNvcWFzIiB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCIgZmlsbD0iY3VycmVudENvbG9yIiBzdHlsZT0iLS1zbC1pY29uLXNpemU6IDEuMjVyZW07Ij48cGF0aCBkPSJtMTQuODMgMTEuMjktNC4yNC00LjI0YTEgMSAwIDEgMC0xLjQyIDEuNDFMMTIuNzEgMTJsLTMuNTQgMy41NGExIDEgMCAwIDAgMCAxLjQxIDEgMSAwIDAgMCAuNzEuMjkgMSAxIDAgMCAwIC43MS0uMjlsNC4yNC00LjI0YTEuMDAyIDEuMDAyIDAgMCAwIDAtMS40MloiPjwvcGF0aD48L3N2Zz4=){.caret
            .astro-3ii7xxms .astro-c6vsoqas}
            -   [[Overview]{.astro-3ii7xxms}](/docs/ide-integration/){.astro-3ii7xxms
                aria-current="false"}
            -   [[Developer guide: ACP
                mode]{.astro-3ii7xxms}](/docs/cli/acp-mode/){.astro-3ii7xxms
                aria-current="false"}
        -   [ [MCP servers]{.large .astro-3ii7xxms} ]{.group-label
            .astro-3ii7xxms}
            ![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9ImNhcmV0IGFzdHJvLTNpaTd4eG1zIGFzdHJvLWM2dnNvcWFzIiB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCIgZmlsbD0iY3VycmVudENvbG9yIiBzdHlsZT0iLS1zbC1pY29uLXNpemU6IDEuMjVyZW07Ij48cGF0aCBkPSJtMTQuODMgMTEuMjktNC4yNC00LjI0YTEgMSAwIDEgMC0xLjQyIDEuNDFMMTIuNzEgMTJsLTMuNTQgMy41NGExIDEgMCAwIDAgMCAxLjQxIDEgMSAwIDAgMCAuNzEuMjkgMSAxIDAgMCAwIC43MS0uMjlsNC4yNC00LjI0YTEuMDAyIDEuMDAyIDAgMCAwIDAtMS40MloiPjwvcGF0aD48L3N2Zz4=){.caret
            .astro-3ii7xxms .astro-c6vsoqas}
            -   [[Overview]{.astro-3ii7xxms}](/docs/tools/mcp-server/){.astro-3ii7xxms
                aria-current="false"}
            -   [[Resource
                tools]{.astro-3ii7xxms}](/docs/tools/mcp-resources/){.astro-3ii7xxms
                aria-current="false"}
        -   [[Model
            routing]{.astro-3ii7xxms}](/docs/cli/model-routing/){.astro-3ii7xxms
            aria-current="false"}
        -   [[Model
            selection]{.astro-3ii7xxms}](/docs/cli/model/){.astro-3ii7xxms
            aria-current="false"}
        -   [[Model steering]{.astro-3ii7xxms} [🔬]{.sl-badge .default
            .small .astro-3ii7xxms
            .astro-avdet4wd}](/docs/cli/model-steering/){.astro-3ii7xxms
            aria-current="false"}
        -   [[Notifications]{.astro-3ii7xxms} [🔬]{.sl-badge .default
            .small .astro-3ii7xxms
            .astro-avdet4wd}](/docs/cli/notifications/){.astro-3ii7xxms
            aria-current="false"}
        -   [[Plan
            mode]{.astro-3ii7xxms}](/docs/cli/plan-mode/){.astro-3ii7xxms
            aria-current="false"}
        -   [[Subagents]{.astro-3ii7xxms}](/docs/core/subagents/){.astro-3ii7xxms
            aria-current="false"}
        -   [[Remote
            subagents]{.astro-3ii7xxms}](/docs/core/remote-agents/){.astro-3ii7xxms
            aria-current="false"}
        -   [[Rewind]{.astro-3ii7xxms}](/docs/cli/rewind/){.astro-3ii7xxms
            aria-current="false"}
        -   [[Sandboxing]{.astro-3ii7xxms}](/docs/cli/sandbox/){.astro-3ii7xxms
            aria-current="false"}
        -   [[Settings]{.astro-3ii7xxms}](/docs/cli/settings/){.astro-3ii7xxms
            aria-current="false"}
        -   [[Telemetry]{.astro-3ii7xxms}](/docs/cli/telemetry/){.astro-3ii7xxms
            aria-current="false"}
        -   [[Token
            caching]{.astro-3ii7xxms}](/docs/cli/token-caching/){.astro-3ii7xxms
            aria-current="false"}
    -   [ [Configuration]{.large .astro-3ii7xxms} ]{.group-label
        .astro-3ii7xxms}
        ![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9ImNhcmV0IGFzdHJvLTNpaTd4eG1zIGFzdHJvLWM2dnNvcWFzIiB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCIgZmlsbD0iY3VycmVudENvbG9yIiBzdHlsZT0iLS1zbC1pY29uLXNpemU6IDEuMjVyZW07Ij48cGF0aCBkPSJtMTQuODMgMTEuMjktNC4yNC00LjI0YTEgMSAwIDEgMC0xLjQyIDEuNDFMMTIuNzEgMTJsLTMuNTQgMy41NGExIDEgMCAwIDAgMCAxLjQxIDEgMSAwIDAgMCAuNzEuMjkgMSAxIDAgMCAwIC43MS0uMjlsNC4yNC00LjI0YTEuMDAyIDEuMDAyIDAgMCAwIDAtMS40MloiPjwvcGF0aD48L3N2Zz4=){.caret
        .astro-3ii7xxms .astro-c6vsoqas}
        -   [[Custom
            commands]{.astro-3ii7xxms}](/docs/cli/custom-commands/){.astro-3ii7xxms
            aria-current="false"}
        -   [[Enterprise
            configuration]{.astro-3ii7xxms}](/docs/cli/enterprise/){.astro-3ii7xxms
            aria-current="false"}
        -   [[Ignore files
            (.geminiignore)]{.astro-3ii7xxms}](/docs/cli/gemini-ignore/){.astro-3ii7xxms
            aria-current="false"}
        -   [[Model
            configuration]{.astro-3ii7xxms}](/docs/cli/generation-settings/){.astro-3ii7xxms
            aria-current="false"}
        -   [[Project context
            (GEMINI.md)]{.astro-3ii7xxms}](/docs/cli/gemini-md/){.astro-3ii7xxms
            aria-current="false"}
        -   [[Settings]{.astro-3ii7xxms}](/docs/cli/settings/){.astro-3ii7xxms
            aria-current="false"}
        -   [[System prompt
            override]{.astro-3ii7xxms}](/docs/cli/system-prompt/){.astro-3ii7xxms
            aria-current="false"}
        -   [[Themes]{.astro-3ii7xxms}](/docs/cli/themes/){.astro-3ii7xxms
            aria-current="false"}
        -   [[Trusted
            folders]{.astro-3ii7xxms}](/docs/cli/trusted-folders/){.astro-3ii7xxms
            aria-current="false"}
    -   [ [Development]{.large .astro-3ii7xxms} ]{.group-label
        .astro-3ii7xxms}
        ![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9ImNhcmV0IGFzdHJvLTNpaTd4eG1zIGFzdHJvLWM2dnNvcWFzIiB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCIgZmlsbD0iY3VycmVudENvbG9yIiBzdHlsZT0iLS1zbC1pY29uLXNpemU6IDEuMjVyZW07Ij48cGF0aCBkPSJtMTQuODMgMTEuMjktNC4yNC00LjI0YTEgMSAwIDEgMC0xLjQyIDEuNDFMMTIuNzEgMTJsLTMuNTQgMy41NGExIDEgMCAwIDAgMCAxLjQxIDEgMSAwIDAgMCAuNzEuMjkgMSAxIDAgMCAwIC43MS0uMjlsNC4yNC00LjI0YTEuMDAyIDEuMDAyIDAgMCAwIDAtMS40MloiPjwvcGF0aD48L3N2Zz4=){.caret
        .astro-3ii7xxms .astro-c6vsoqas}
        -   [[Contribution
            guide]{.astro-3ii7xxms}](/docs/contributing/){.astro-3ii7xxms
            aria-current="false"}
        -   [[Integration
            testing]{.astro-3ii7xxms}](/docs/integration-tests/){.astro-3ii7xxms
            aria-current="false"}
        -   [[Issue and PR
            automation]{.astro-3ii7xxms}](/docs/issue-and-pr-automation/){.astro-3ii7xxms
            aria-current="false"}
        -   [[Local
            development]{.astro-3ii7xxms}](/docs/local-development/){.astro-3ii7xxms
            aria-current="false"}
        -   [[NPM package
            structure]{.astro-3ii7xxms}](/docs/npm/){.astro-3ii7xxms
            aria-current="false"}
-   [ [Reference]{.large .astro-3ii7xxms} ]{.group-label
    .astro-3ii7xxms}
    ![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9ImNhcmV0IGFzdHJvLTNpaTd4eG1zIGFzdHJvLWM2dnNvcWFzIiB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCIgZmlsbD0iY3VycmVudENvbG9yIiBzdHlsZT0iLS1zbC1pY29uLXNpemU6IDEuMjVyZW07Ij48cGF0aCBkPSJtMTQuODMgMTEuMjktNC4yNC00LjI0YTEgMSAwIDEgMC0xLjQyIDEuNDFMMTIuNzEgMTJsLTMuNTQgMy41NGExIDEgMCAwIDAgMCAxLjQxIDEgMSAwIDAgMCAuNzEuMjkgMSAxIDAgMCAwIC43MS0uMjlsNC4yNC00LjI0YTEuMDAyIDEuMDAyIDAgMCAwIDAtMS40MloiPjwvcGF0aD48L3N2Zz4=){.caret
    .astro-3ii7xxms .astro-c6vsoqas}
    -   [[Command
        reference]{.astro-3ii7xxms}](/docs/reference/commands/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Configuration
        reference]{.astro-3ii7xxms}](/docs/reference/configuration/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Keyboard
        shortcuts]{.astro-3ii7xxms}](/docs/reference/keyboard-shortcuts/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Memory import
        processor]{.astro-3ii7xxms}](/docs/reference/memport/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Policy
        engine]{.astro-3ii7xxms}](/docs/reference/policy-engine/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Tools
        reference]{.astro-3ii7xxms}](/docs/reference/tools/){.astro-3ii7xxms
        aria-current="false"}
-   [ [Resources]{.large .astro-3ii7xxms} ]{.group-label
    .astro-3ii7xxms}
    ![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9ImNhcmV0IGFzdHJvLTNpaTd4eG1zIGFzdHJvLWM2dnNvcWFzIiB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCIgZmlsbD0iY3VycmVudENvbG9yIiBzdHlsZT0iLS1zbC1pY29uLXNpemU6IDEuMjVyZW07Ij48cGF0aCBkPSJtMTQuODMgMTEuMjktNC4yNC00LjI0YTEgMSAwIDEgMC0xLjQyIDEuNDFMMTIuNzEgMTJsLTMuNTQgMy41NGExIDEgMCAwIDAgMCAxLjQxIDEgMSAwIDAgMCAuNzEuMjkgMSAxIDAgMCAwIC43MS0uMjlsNC4yNC00LjI0YTEuMDAyIDEuMDAyIDAgMCAwIDAtMS40MloiPjwvcGF0aD48L3N2Zz4=){.caret
    .astro-3ii7xxms .astro-c6vsoqas}
    -   [[FAQ]{.astro-3ii7xxms}](/docs/resources/faq/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Quota and
        pricing]{.astro-3ii7xxms}](/docs/resources/quota-and-pricing/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Terms and
        privacy]{.astro-3ii7xxms}](/docs/resources/tos-privacy/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Troubleshooting]{.astro-3ii7xxms}](/docs/resources/troubleshooting/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Uninstall]{.astro-3ii7xxms}](/docs/resources/uninstall/){.astro-3ii7xxms
        aria-current="false"}
-   [ [Changelog]{.large .astro-3ii7xxms} ]{.group-label
    .astro-3ii7xxms}
    ![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9ImNhcmV0IGFzdHJvLTNpaTd4eG1zIGFzdHJvLWM2dnNvcWFzIiB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCIgZmlsbD0iY3VycmVudENvbG9yIiBzdHlsZT0iLS1zbC1pY29uLXNpemU6IDEuMjVyZW07Ij48cGF0aCBkPSJtMTQuODMgMTEuMjktNC4yNC00LjI0YTEgMSAwIDEgMC0xLjQyIDEuNDFMMTIuNzEgMTJsLTMuNTQgMy41NGExIDEgMCAwIDAgMCAxLjQxIDEgMSAwIDAgMCAuNzEuMjkgMSAxIDAgMCAwIC43MS0uMjlsNC4yNC00LjI0YTEuMDAyIDEuMDAyIDAgMCAwIDAtMS40MloiPjwvcGF0aD48L3N2Zz4=){.caret
    .astro-3ii7xxms .astro-c6vsoqas}
    -   [[Release
        notes]{.astro-3ii7xxms}](/docs/changelogs/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Stable
        release]{.astro-3ii7xxms}](/docs/changelogs/latest/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Preview
        release]{.astro-3ii7xxms}](/docs/changelogs/preview/){.astro-3ii7xxms
        aria-current="false"}
:::

::: {.w-full .hide-native-sidebar-on-mobile .astro-yriad4ts}
::: {starlight-multi-sidebar-label="docs_tab"}
-   [ [Get started]{.large .astro-3ii7xxms} ]{.group-label
    .astro-3ii7xxms}
    ![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9ImNhcmV0IGFzdHJvLTNpaTd4eG1zIGFzdHJvLWM2dnNvcWFzIiB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCIgZmlsbD0iY3VycmVudENvbG9yIiBzdHlsZT0iLS1zbC1pY29uLXNpemU6IDEuMjVyZW07Ij48cGF0aCBkPSJtMTQuODMgMTEuMjktNC4yNC00LjI0YTEgMSAwIDEgMC0xLjQyIDEuNDFMMTIuNzEgMTJsLTMuNTQgMy41NGExIDEgMCAwIDAgMCAxLjQxIDEgMSAwIDAgMCAuNzEuMjkgMSAxIDAgMCAwIC43MS0uMjlsNC4yNC00LjI0YTEuMDAyIDEuMDAyIDAgMCAwIDAtMS40MloiPjwvcGF0aD48L3N2Zz4=){.caret
    .astro-3ii7xxms .astro-c6vsoqas}
    -   [[Overview]{.astro-3ii7xxms}](/docs/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Quickstart]{.astro-3ii7xxms}](/docs/get-started/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Installation]{.astro-3ii7xxms}](/docs/get-started/installation/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Authentication]{.astro-3ii7xxms}](/docs/get-started/authentication/){.astro-3ii7xxms
        aria-current="false"}
    -   [[CLI
        cheatsheet]{.astro-3ii7xxms}](/docs/cli/cli-reference/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Gemini 3 on Gemini
        CLI]{.astro-3ii7xxms}](/docs/get-started/gemini-3/){.astro-3ii7xxms
        aria-current="false"}
-   [ [Use Gemini CLI]{.large .astro-3ii7xxms} ]{.group-label
    .astro-3ii7xxms}
    ![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9ImNhcmV0IGFzdHJvLTNpaTd4eG1zIGFzdHJvLWM2dnNvcWFzIiB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCIgZmlsbD0iY3VycmVudENvbG9yIiBzdHlsZT0iLS1zbC1pY29uLXNpemU6IDEuMjVyZW07Ij48cGF0aCBkPSJtMTQuODMgMTEuMjktNC4yNC00LjI0YTEgMSAwIDEgMC0xLjQyIDEuNDFMMTIuNzEgMTJsLTMuNTQgMy41NGExIDEgMCAwIDAgMCAxLjQxIDEgMSAwIDAgMCAuNzEuMjkgMSAxIDAgMCAwIC43MS0uMjlsNC4yNC00LjI0YTEuMDAyIDEuMDAyIDAgMCAwIDAtMS40MloiPjwvcGF0aD48L3N2Zz4=){.caret
    .astro-3ii7xxms .astro-c6vsoqas}
    -   [[File
        management]{.astro-3ii7xxms}](/docs/cli/tutorials/file-management/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Get started with Agent
        Skills]{.astro-3ii7xxms}](/docs/cli/tutorials/skills-getting-started/){.astro-3ii7xxms
        aria-current="page"}
    -   [[Manage context and
        memory]{.astro-3ii7xxms}](/docs/cli/tutorials/memory-management/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Execute shell
        commands]{.astro-3ii7xxms}](/docs/cli/tutorials/shell-commands/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Manage sessions and
        history]{.astro-3ii7xxms}](/docs/cli/tutorials/session-management/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Plan tasks with
        todos]{.astro-3ii7xxms}](/docs/cli/tutorials/task-planning/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Use Plan Mode with model steering]{.astro-3ii7xxms}
        [🔬]{.sl-badge .default .small .astro-3ii7xxms
        .astro-avdet4wd}](/docs/cli/tutorials/plan-mode-steering/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Web search and
        fetch]{.astro-3ii7xxms}](/docs/cli/tutorials/web-tools/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Set up an MCP
        server]{.astro-3ii7xxms}](/docs/cli/tutorials/mcp-setup/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Automate
        tasks]{.astro-3ii7xxms}](/docs/cli/tutorials/automation/){.astro-3ii7xxms
        aria-current="false"}
-   [ [Features]{.large .astro-3ii7xxms} ]{.group-label .astro-3ii7xxms}
    ![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9ImNhcmV0IGFzdHJvLTNpaTd4eG1zIGFzdHJvLWM2dnNvcWFzIiB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCIgZmlsbD0iY3VycmVudENvbG9yIiBzdHlsZT0iLS1zbC1pY29uLXNpemU6IDEuMjVyZW07Ij48cGF0aCBkPSJtMTQuODMgMTEuMjktNC4yNC00LjI0YTEgMSAwIDEgMC0xLjQyIDEuNDFMMTIuNzEgMTJsLTMuNTQgMy41NGExIDEgMCAwIDAgMCAxLjQxIDEgMSAwIDAgMCAuNzEuMjkgMSAxIDAgMCAwIC43MS0uMjlsNC4yNC00LjI0YTEuMDAyIDEuMDAyIDAgMCAwIDAtMS40MloiPjwvcGF0aD48L3N2Zz4=){.caret
    .astro-3ii7xxms .astro-c6vsoqas}
    -   [ [Extensions]{.large .astro-3ii7xxms} ]{.group-label
        .astro-3ii7xxms}
        ![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9ImNhcmV0IGFzdHJvLTNpaTd4eG1zIGFzdHJvLWM2dnNvcWFzIiB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCIgZmlsbD0iY3VycmVudENvbG9yIiBzdHlsZT0iLS1zbC1pY29uLXNpemU6IDEuMjVyZW07Ij48cGF0aCBkPSJtMTQuODMgMTEuMjktNC4yNC00LjI0YTEgMSAwIDEgMC0xLjQyIDEuNDFMMTIuNzEgMTJsLTMuNTQgMy41NGExIDEgMCAwIDAgMCAxLjQxIDEgMSAwIDAgMCAuNzEuMjkgMSAxIDAgMCAwIC43MS0uMjlsNC4yNC00LjI0YTEuMDAyIDEuMDAyIDAgMCAwIDAtMS40MloiPjwvcGF0aD48L3N2Zz4=){.caret
        .astro-3ii7xxms .astro-c6vsoqas}
        -   [[Overview]{.astro-3ii7xxms}](/docs/extensions/){.astro-3ii7xxms
            aria-current="false"}
        -   [[User guide: Install and
            manage]{.astro-3ii7xxms}](/docs/extensions/#manage-extensions){.astro-3ii7xxms
            aria-current="false"}
        -   [[Developer guide: Build
            extensions]{.astro-3ii7xxms}](/docs/extensions/writing-extensions/){.astro-3ii7xxms
            aria-current="false"}
        -   [[Developer guide: Best
            practices]{.astro-3ii7xxms}](/docs/extensions/best-practices/){.astro-3ii7xxms
            aria-current="false"}
        -   [[Developer guide:
            Releasing]{.astro-3ii7xxms}](/docs/extensions/releasing/){.astro-3ii7xxms
            aria-current="false"}
        -   [[Developer guide:
            Reference]{.astro-3ii7xxms}](/docs/extensions/reference/){.astro-3ii7xxms
            aria-current="false"}
    -   [ [Agent Skills]{.large .astro-3ii7xxms} ]{.group-label
        .astro-3ii7xxms}
        ![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9ImNhcmV0IGFzdHJvLTNpaTd4eG1zIGFzdHJvLWM2dnNvcWFzIiB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCIgZmlsbD0iY3VycmVudENvbG9yIiBzdHlsZT0iLS1zbC1pY29uLXNpemU6IDEuMjVyZW07Ij48cGF0aCBkPSJtMTQuODMgMTEuMjktNC4yNC00LjI0YTEgMSAwIDEgMC0xLjQyIDEuNDFMMTIuNzEgMTJsLTMuNTQgMy41NGExIDEgMCAwIDAgMCAxLjQxIDEgMSAwIDAgMCAuNzEuMjkgMSAxIDAgMCAwIC43MS0uMjlsNC4yNC00LjI0YTEuMDAyIDEuMDAyIDAgMCAwIDAtMS40MloiPjwvcGF0aD48L3N2Zz4=){.caret
        .astro-3ii7xxms .astro-c6vsoqas}
        -   [[Overview]{.astro-3ii7xxms}](/docs/cli/skills/){.astro-3ii7xxms
            aria-current="false"}
        -   [[Get started with Agent
            Skills]{.astro-3ii7xxms}](/docs/cli/tutorials/skills-getting-started/){.astro-3ii7xxms
            aria-current="false"}
        -   [[Creating Agent
            Skills]{.astro-3ii7xxms}](/docs/cli/creating-skills/){.astro-3ii7xxms
            aria-current="false"}
        -   [[Using Agent
            Skills]{.astro-3ii7xxms}](/docs/cli/using-agent-skills/){.astro-3ii7xxms
            aria-current="false"}
        -   [[Developer guide: Best
            practices]{.astro-3ii7xxms}](/docs/cli/skills-best-practices/){.astro-3ii7xxms
            aria-current="false"}
    -   [[Auto Memory]{.astro-3ii7xxms} [🔬]{.sl-badge .default .small
        .astro-3ii7xxms
        .astro-avdet4wd}](/docs/cli/auto-memory/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Checkpointing]{.astro-3ii7xxms}](/docs/cli/checkpointing/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Headless
        mode]{.astro-3ii7xxms}](/docs/cli/headless/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Git worktrees]{.astro-3ii7xxms} [🔬]{.sl-badge .default .small
        .astro-3ii7xxms
        .astro-avdet4wd}](/docs/cli/git-worktrees/){.astro-3ii7xxms
        aria-current="false"}
    -   [ [Hooks]{.large .astro-3ii7xxms} ]{.group-label
        .astro-3ii7xxms}
        ![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9ImNhcmV0IGFzdHJvLTNpaTd4eG1zIGFzdHJvLWM2dnNvcWFzIiB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCIgZmlsbD0iY3VycmVudENvbG9yIiBzdHlsZT0iLS1zbC1pY29uLXNpemU6IDEuMjVyZW07Ij48cGF0aCBkPSJtMTQuODMgMTEuMjktNC4yNC00LjI0YTEgMSAwIDEgMC0xLjQyIDEuNDFMMTIuNzEgMTJsLTMuNTQgMy41NGExIDEgMCAwIDAgMCAxLjQxIDEgMSAwIDAgMCAuNzEuMjkgMSAxIDAgMCAwIC43MS0uMjlsNC4yNC00LjI0YTEuMDAyIDEuMDAyIDAgMCAwIDAtMS40MloiPjwvcGF0aD48L3N2Zz4=){.caret
        .astro-3ii7xxms .astro-c6vsoqas}
        -   [[Overview]{.astro-3ii7xxms}](/docs/hooks/){.astro-3ii7xxms
            aria-current="false"}
        -   [[Reference]{.astro-3ii7xxms}](/docs/hooks/reference/){.astro-3ii7xxms
            aria-current="false"}
    -   [ [IDE integration]{.large .astro-3ii7xxms} ]{.group-label
        .astro-3ii7xxms}
        ![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9ImNhcmV0IGFzdHJvLTNpaTd4eG1zIGFzdHJvLWM2dnNvcWFzIiB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCIgZmlsbD0iY3VycmVudENvbG9yIiBzdHlsZT0iLS1zbC1pY29uLXNpemU6IDEuMjVyZW07Ij48cGF0aCBkPSJtMTQuODMgMTEuMjktNC4yNC00LjI0YTEgMSAwIDEgMC0xLjQyIDEuNDFMMTIuNzEgMTJsLTMuNTQgMy41NGExIDEgMCAwIDAgMCAxLjQxIDEgMSAwIDAgMCAuNzEuMjkgMSAxIDAgMCAwIC43MS0uMjlsNC4yNC00LjI0YTEuMDAyIDEuMDAyIDAgMCAwIDAtMS40MloiPjwvcGF0aD48L3N2Zz4=){.caret
        .astro-3ii7xxms .astro-c6vsoqas}
        -   [[Overview]{.astro-3ii7xxms}](/docs/ide-integration/){.astro-3ii7xxms
            aria-current="false"}
        -   [[Developer guide: ACP
            mode]{.astro-3ii7xxms}](/docs/cli/acp-mode/){.astro-3ii7xxms
            aria-current="false"}
    -   [ [MCP servers]{.large .astro-3ii7xxms} ]{.group-label
        .astro-3ii7xxms}
        ![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9ImNhcmV0IGFzdHJvLTNpaTd4eG1zIGFzdHJvLWM2dnNvcWFzIiB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCIgZmlsbD0iY3VycmVudENvbG9yIiBzdHlsZT0iLS1zbC1pY29uLXNpemU6IDEuMjVyZW07Ij48cGF0aCBkPSJtMTQuODMgMTEuMjktNC4yNC00LjI0YTEgMSAwIDEgMC0xLjQyIDEuNDFMMTIuNzEgMTJsLTMuNTQgMy41NGExIDEgMCAwIDAgMCAxLjQxIDEgMSAwIDAgMCAuNzEuMjkgMSAxIDAgMCAwIC43MS0uMjlsNC4yNC00LjI0YTEuMDAyIDEuMDAyIDAgMCAwIDAtMS40MloiPjwvcGF0aD48L3N2Zz4=){.caret
        .astro-3ii7xxms .astro-c6vsoqas}
        -   [[Overview]{.astro-3ii7xxms}](/docs/tools/mcp-server/){.astro-3ii7xxms
            aria-current="false"}
        -   [[Resource
            tools]{.astro-3ii7xxms}](/docs/tools/mcp-resources/){.astro-3ii7xxms
            aria-current="false"}
    -   [[Model
        routing]{.astro-3ii7xxms}](/docs/cli/model-routing/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Model
        selection]{.astro-3ii7xxms}](/docs/cli/model/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Model steering]{.astro-3ii7xxms} [🔬]{.sl-badge .default
        .small .astro-3ii7xxms
        .astro-avdet4wd}](/docs/cli/model-steering/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Notifications]{.astro-3ii7xxms} [🔬]{.sl-badge .default .small
        .astro-3ii7xxms
        .astro-avdet4wd}](/docs/cli/notifications/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Plan
        mode]{.astro-3ii7xxms}](/docs/cli/plan-mode/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Subagents]{.astro-3ii7xxms}](/docs/core/subagents/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Remote
        subagents]{.astro-3ii7xxms}](/docs/core/remote-agents/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Rewind]{.astro-3ii7xxms}](/docs/cli/rewind/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Sandboxing]{.astro-3ii7xxms}](/docs/cli/sandbox/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Settings]{.astro-3ii7xxms}](/docs/cli/settings/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Telemetry]{.astro-3ii7xxms}](/docs/cli/telemetry/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Token
        caching]{.astro-3ii7xxms}](/docs/cli/token-caching/){.astro-3ii7xxms
        aria-current="false"}
-   [ [Configuration]{.large .astro-3ii7xxms} ]{.group-label
    .astro-3ii7xxms}
    ![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9ImNhcmV0IGFzdHJvLTNpaTd4eG1zIGFzdHJvLWM2dnNvcWFzIiB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCIgZmlsbD0iY3VycmVudENvbG9yIiBzdHlsZT0iLS1zbC1pY29uLXNpemU6IDEuMjVyZW07Ij48cGF0aCBkPSJtMTQuODMgMTEuMjktNC4yNC00LjI0YTEgMSAwIDEgMC0xLjQyIDEuNDFMMTIuNzEgMTJsLTMuNTQgMy41NGExIDEgMCAwIDAgMCAxLjQxIDEgMSAwIDAgMCAuNzEuMjkgMSAxIDAgMCAwIC43MS0uMjlsNC4yNC00LjI0YTEuMDAyIDEuMDAyIDAgMCAwIDAtMS40MloiPjwvcGF0aD48L3N2Zz4=){.caret
    .astro-3ii7xxms .astro-c6vsoqas}
    -   [[Custom
        commands]{.astro-3ii7xxms}](/docs/cli/custom-commands/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Enterprise
        configuration]{.astro-3ii7xxms}](/docs/cli/enterprise/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Ignore files
        (.geminiignore)]{.astro-3ii7xxms}](/docs/cli/gemini-ignore/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Model
        configuration]{.astro-3ii7xxms}](/docs/cli/generation-settings/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Project context
        (GEMINI.md)]{.astro-3ii7xxms}](/docs/cli/gemini-md/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Settings]{.astro-3ii7xxms}](/docs/cli/settings/){.astro-3ii7xxms
        aria-current="false"}
    -   [[System prompt
        override]{.astro-3ii7xxms}](/docs/cli/system-prompt/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Themes]{.astro-3ii7xxms}](/docs/cli/themes/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Trusted
        folders]{.astro-3ii7xxms}](/docs/cli/trusted-folders/){.astro-3ii7xxms
        aria-current="false"}
-   [ [Development]{.large .astro-3ii7xxms} ]{.group-label
    .astro-3ii7xxms}
    ![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9ImNhcmV0IGFzdHJvLTNpaTd4eG1zIGFzdHJvLWM2dnNvcWFzIiB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCIgZmlsbD0iY3VycmVudENvbG9yIiBzdHlsZT0iLS1zbC1pY29uLXNpemU6IDEuMjVyZW07Ij48cGF0aCBkPSJtMTQuODMgMTEuMjktNC4yNC00LjI0YTEgMSAwIDEgMC0xLjQyIDEuNDFMMTIuNzEgMTJsLTMuNTQgMy41NGExIDEgMCAwIDAgMCAxLjQxIDEgMSAwIDAgMCAuNzEuMjkgMSAxIDAgMCAwIC43MS0uMjlsNC4yNC00LjI0YTEuMDAyIDEuMDAyIDAgMCAwIDAtMS40MloiPjwvcGF0aD48L3N2Zz4=){.caret
    .astro-3ii7xxms .astro-c6vsoqas}
    -   [[Contribution
        guide]{.astro-3ii7xxms}](/docs/contributing/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Integration
        testing]{.astro-3ii7xxms}](/docs/integration-tests/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Issue and PR
        automation]{.astro-3ii7xxms}](/docs/issue-and-pr-automation/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Local
        development]{.astro-3ii7xxms}](/docs/local-development/){.astro-3ii7xxms
        aria-current="false"}
    -   [[NPM package
        structure]{.astro-3ii7xxms}](/docs/npm/){.astro-3ii7xxms
        aria-current="false"}

::: md:sl-hidden
::: {.mobile-preferences .sl-flex .astro-wu23bvmt}
::: {.social-icons .astro-wu23bvmt}
[[GitHub]{.sr-only
.astro-wy4te6ga}![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9ImFzdHJvLXd5NHRlNmdhIGFzdHJvLWM2dnNvcWFzIiB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCIgZmlsbD0iY3VycmVudENvbG9yIiBzdHlsZT0iLS1zbC1pY29uLXNpemU6IDFlbTsiPjxwYXRoIGQ9Ik0xMiAuM2ExMiAxMiAwIDAgMC0zLjggMjMuMzhjLjYuMTIuODMtLjI2LjgzLS41N0w5IDIxLjA3Yy0zLjM0LjcyLTQuMDQtMS42MS00LjA0LTEuNjEtLjU1LTEuMzktMS4zNC0xLjc2LTEuMzQtMS43Ni0xLjA4LS43NC4wOS0uNzMuMDktLjczIDEuMi4wOSAxLjgzIDEuMjQgMS44MyAxLjI0IDEuMDggMS44MyAyLjgxIDEuMyAzLjUgMSAuMS0uNzguNDItMS4zMS43Ni0xLjYxLTIuNjctLjMtNS40Ny0xLjMzLTUuNDctNS45MyAwLTEuMzEuNDctMi4zOCAxLjI0LTMuMjItLjE0LS4zLS41NC0xLjUyLjEtMy4xOCAwIDAgMS0uMzIgMy4zIDEuMjNhMTEuNSAxMS41IDAgMCAxIDYgMGMyLjI4LTEuNTUgMy4yOS0xLjIzIDMuMjktMS4yMy42NCAxLjY2LjI0IDIuODguMTIgMy4xOGE0LjY1IDQuNjUgMCAwIDEgMS4yMyAzLjIyYzAgNC42MS0yLjggNS42My01LjQ4IDUuOTIuNDIuMzYuODEgMS4xLjgxIDIuMjJsLS4wMSAzLjI5YzAgLjMxLjIuNjkuODIuNTdBMTIgMTIgMCAwIDAgMTIgLjNaIj48L3BhdGg+PC9zdmc+){.astro-wy4te6ga
.astro-c6vsoqas}](https://github.com/google-gemini/gemini-cli){.sl-flex
.astro-wy4te6ga rel="me"}
:::

[Select theme]{.sr-only .astro-4yphtoen}
![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9Imljb24gbGFiZWwtaWNvbiBhc3Ryby00eXBodG9lbiBhc3Ryby1jNnZzb3FhcyIgd2lkdGg9IjE2IiBoZWlnaHQ9IjE2IiB2aWV3Ym94PSIwIDAgMjQgMjQiIGZpbGw9ImN1cnJlbnRDb2xvciIgc3R5bGU9Ii0tc2wtaWNvbi1zaXplOiAxZW07Ij48cGF0aCBkPSJNMjEgMTRoLTFWN2EzIDMgMCAwIDAtMy0zSDdhMyAzIDAgMCAwLTMgM3Y3SDNhMSAxIDAgMCAwLTEgMXYyYTMgMyAwIDAgMCAzIDNoMTRhMyAzIDAgMCAwIDMtM3YtMmExIDEgMCAwIDAtMS0xWk02IDdhMSAxIDAgMCAxIDEtMWgxMGExIDEgMCAwIDEgMSAxdjdINlY3Wm0xNCAxMGExIDEgMCAwIDEtMSAxSDVhMSAxIDAgMCAxLTEtMXYtMWgxNnYxWiI+PC9wYXRoPjwvc3ZnPg==){.icon
.label-icon .astro-4yphtoen .astro-c6vsoqas} DarkLightAuto
![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9Imljb24gY2FyZXQgYXN0cm8tNHlwaHRvZW4gYXN0cm8tYzZ2c29xYXMiIHdpZHRoPSIxNiIgaGVpZ2h0PSIxNiIgdmlld2JveD0iMCAwIDI0IDI0IiBmaWxsPSJjdXJyZW50Q29sb3IiIHN0eWxlPSItLXNsLWljb24tc2l6ZTogMWVtOyI+PHBhdGggZD0iTTE3IDkuMTdhMSAxIDAgMCAwLTEuNDEgMEwxMiAxMi43MSA4LjQ2IDkuMTdhMSAxIDAgMSAwLTEuNDEgMS40Mmw0LjI0IDQuMjRhMS4wMDIgMS4wMDIgMCAwIDAgMS40MiAwTDE3IDEwLjU5YTEuMDAyIDEuMDAyIDAgMCAwIDAtMS40MloiPjwvcGF0aD48L3N2Zz4=){.icon
.caret .astro-4yphtoen .astro-c6vsoqas}
:::
:::
:::

::: {hidden="" starlight-multi-sidebar-label="reference_tab"}
-   [ [Reference]{.large .astro-3ii7xxms} ]{.group-label
    .astro-3ii7xxms}
    ![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9ImNhcmV0IGFzdHJvLTNpaTd4eG1zIGFzdHJvLWM2dnNvcWFzIiB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCIgZmlsbD0iY3VycmVudENvbG9yIiBzdHlsZT0iLS1zbC1pY29uLXNpemU6IDEuMjVyZW07Ij48cGF0aCBkPSJtMTQuODMgMTEuMjktNC4yNC00LjI0YTEgMSAwIDEgMC0xLjQyIDEuNDFMMTIuNzEgMTJsLTMuNTQgMy41NGExIDEgMCAwIDAgMCAxLjQxIDEgMSAwIDAgMCAuNzEuMjkgMSAxIDAgMCAwIC43MS0uMjlsNC4yNC00LjI0YTEuMDAyIDEuMDAyIDAgMCAwIDAtMS40MloiPjwvcGF0aD48L3N2Zz4=){.caret
    .astro-3ii7xxms .astro-c6vsoqas}
    -   [[Command
        reference]{.astro-3ii7xxms}](/docs/reference/commands/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Configuration
        reference]{.astro-3ii7xxms}](/docs/reference/configuration/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Keyboard
        shortcuts]{.astro-3ii7xxms}](/docs/reference/keyboard-shortcuts/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Memory import
        processor]{.astro-3ii7xxms}](/docs/reference/memport/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Policy
        engine]{.astro-3ii7xxms}](/docs/reference/policy-engine/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Tools
        reference]{.astro-3ii7xxms}](/docs/reference/tools/){.astro-3ii7xxms
        aria-current="false"}

::: md:sl-hidden
::: {.mobile-preferences .sl-flex .astro-wu23bvmt}
::: {.social-icons .astro-wu23bvmt}
[[GitHub]{.sr-only
.astro-wy4te6ga}![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9ImFzdHJvLXd5NHRlNmdhIGFzdHJvLWM2dnNvcWFzIiB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCIgZmlsbD0iY3VycmVudENvbG9yIiBzdHlsZT0iLS1zbC1pY29uLXNpemU6IDFlbTsiPjxwYXRoIGQ9Ik0xMiAuM2ExMiAxMiAwIDAgMC0zLjggMjMuMzhjLjYuMTIuODMtLjI2LjgzLS41N0w5IDIxLjA3Yy0zLjM0LjcyLTQuMDQtMS42MS00LjA0LTEuNjEtLjU1LTEuMzktMS4zNC0xLjc2LTEuMzQtMS43Ni0xLjA4LS43NC4wOS0uNzMuMDktLjczIDEuMi4wOSAxLjgzIDEuMjQgMS44MyAxLjI0IDEuMDggMS44MyAyLjgxIDEuMyAzLjUgMSAuMS0uNzguNDItMS4zMS43Ni0xLjYxLTIuNjctLjMtNS40Ny0xLjMzLTUuNDctNS45MyAwLTEuMzEuNDctMi4zOCAxLjI0LTMuMjItLjE0LS4zLS41NC0xLjUyLjEtMy4xOCAwIDAgMS0uMzIgMy4zIDEuMjNhMTEuNSAxMS41IDAgMCAxIDYgMGMyLjI4LTEuNTUgMy4yOS0xLjIzIDMuMjktMS4yMy42NCAxLjY2LjI0IDIuODguMTIgMy4xOGE0LjY1IDQuNjUgMCAwIDEgMS4yMyAzLjIyYzAgNC42MS0yLjggNS42My01LjQ4IDUuOTIuNDIuMzYuODEgMS4xLjgxIDIuMjJsLS4wMSAzLjI5YzAgLjMxLjIuNjkuODIuNTdBMTIgMTIgMCAwIDAgMTIgLjNaIj48L3BhdGg+PC9zdmc+){.astro-wy4te6ga
.astro-c6vsoqas}](https://github.com/google-gemini/gemini-cli){.sl-flex
.astro-wy4te6ga rel="me"}
:::

[Select theme]{.sr-only .astro-4yphtoen}
![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9Imljb24gbGFiZWwtaWNvbiBhc3Ryby00eXBodG9lbiBhc3Ryby1jNnZzb3FhcyIgd2lkdGg9IjE2IiBoZWlnaHQ9IjE2IiB2aWV3Ym94PSIwIDAgMjQgMjQiIGZpbGw9ImN1cnJlbnRDb2xvciIgc3R5bGU9Ii0tc2wtaWNvbi1zaXplOiAxZW07Ij48cGF0aCBkPSJNMjEgMTRoLTFWN2EzIDMgMCAwIDAtMy0zSDdhMyAzIDAgMCAwLTMgM3Y3SDNhMSAxIDAgMCAwLTEgMXYyYTMgMyAwIDAgMCAzIDNoMTRhMyAzIDAgMCAwIDMtM3YtMmExIDEgMCAwIDAtMS0xWk02IDdhMSAxIDAgMCAxIDEtMWgxMGExIDEgMCAwIDEgMSAxdjdINlY3Wm0xNCAxMGExIDEgMCAwIDEtMSAxSDVhMSAxIDAgMCAxLTEtMXYtMWgxNnYxWiI+PC9wYXRoPjwvc3ZnPg==){.icon
.label-icon .astro-4yphtoen .astro-c6vsoqas} DarkLightAuto
![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9Imljb24gY2FyZXQgYXN0cm8tNHlwaHRvZW4gYXN0cm8tYzZ2c29xYXMiIHdpZHRoPSIxNiIgaGVpZ2h0PSIxNiIgdmlld2JveD0iMCAwIDI0IDI0IiBmaWxsPSJjdXJyZW50Q29sb3IiIHN0eWxlPSItLXNsLWljb24tc2l6ZTogMWVtOyI+PHBhdGggZD0iTTE3IDkuMTdhMSAxIDAgMCAwLTEuNDEgMEwxMiAxMi43MSA4LjQ2IDkuMTdhMSAxIDAgMSAwLTEuNDEgMS40Mmw0LjI0IDQuMjRhMS4wMDIgMS4wMDIgMCAwIDAgMS40MiAwTDE3IDEwLjU5YTEuMDAyIDEuMDAyIDAgMCAwIDAtMS40MloiPjwvcGF0aD48L3N2Zz4=){.icon
.caret .astro-4yphtoen .astro-c6vsoqas}
:::
:::
:::

::: {hidden="" starlight-multi-sidebar-label="resources_tab"}
-   [ [Resources]{.large .astro-3ii7xxms} ]{.group-label
    .astro-3ii7xxms}
    ![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9ImNhcmV0IGFzdHJvLTNpaTd4eG1zIGFzdHJvLWM2dnNvcWFzIiB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCIgZmlsbD0iY3VycmVudENvbG9yIiBzdHlsZT0iLS1zbC1pY29uLXNpemU6IDEuMjVyZW07Ij48cGF0aCBkPSJtMTQuODMgMTEuMjktNC4yNC00LjI0YTEgMSAwIDEgMC0xLjQyIDEuNDFMMTIuNzEgMTJsLTMuNTQgMy41NGExIDEgMCAwIDAgMCAxLjQxIDEgMSAwIDAgMCAuNzEuMjkgMSAxIDAgMCAwIC43MS0uMjlsNC4yNC00LjI0YTEuMDAyIDEuMDAyIDAgMCAwIDAtMS40MloiPjwvcGF0aD48L3N2Zz4=){.caret
    .astro-3ii7xxms .astro-c6vsoqas}
    -   [[FAQ]{.astro-3ii7xxms}](/docs/resources/faq/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Quota and
        pricing]{.astro-3ii7xxms}](/docs/resources/quota-and-pricing/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Terms and
        privacy]{.astro-3ii7xxms}](/docs/resources/tos-privacy/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Troubleshooting]{.astro-3ii7xxms}](/docs/resources/troubleshooting/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Uninstall]{.astro-3ii7xxms}](/docs/resources/uninstall/){.astro-3ii7xxms
        aria-current="false"}

::: md:sl-hidden
::: {.mobile-preferences .sl-flex .astro-wu23bvmt}
::: {.social-icons .astro-wu23bvmt}
[[GitHub]{.sr-only
.astro-wy4te6ga}![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9ImFzdHJvLXd5NHRlNmdhIGFzdHJvLWM2dnNvcWFzIiB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCIgZmlsbD0iY3VycmVudENvbG9yIiBzdHlsZT0iLS1zbC1pY29uLXNpemU6IDFlbTsiPjxwYXRoIGQ9Ik0xMiAuM2ExMiAxMiAwIDAgMC0zLjggMjMuMzhjLjYuMTIuODMtLjI2LjgzLS41N0w5IDIxLjA3Yy0zLjM0LjcyLTQuMDQtMS42MS00LjA0LTEuNjEtLjU1LTEuMzktMS4zNC0xLjc2LTEuMzQtMS43Ni0xLjA4LS43NC4wOS0uNzMuMDktLjczIDEuMi4wOSAxLjgzIDEuMjQgMS44MyAxLjI0IDEuMDggMS44MyAyLjgxIDEuMyAzLjUgMSAuMS0uNzguNDItMS4zMS43Ni0xLjYxLTIuNjctLjMtNS40Ny0xLjMzLTUuNDctNS45MyAwLTEuMzEuNDctMi4zOCAxLjI0LTMuMjItLjE0LS4zLS41NC0xLjUyLjEtMy4xOCAwIDAgMS0uMzIgMy4zIDEuMjNhMTEuNSAxMS41IDAgMCAxIDYgMGMyLjI4LTEuNTUgMy4yOS0xLjIzIDMuMjktMS4yMy42NCAxLjY2LjI0IDIuODguMTIgMy4xOGE0LjY1IDQuNjUgMCAwIDEgMS4yMyAzLjIyYzAgNC42MS0yLjggNS42My01LjQ4IDUuOTIuNDIuMzYuODEgMS4xLjgxIDIuMjJsLS4wMSAzLjI5YzAgLjMxLjIuNjkuODIuNTdBMTIgMTIgMCAwIDAgMTIgLjNaIj48L3BhdGg+PC9zdmc+){.astro-wy4te6ga
.astro-c6vsoqas}](https://github.com/google-gemini/gemini-cli){.sl-flex
.astro-wy4te6ga rel="me"}
:::

[Select theme]{.sr-only .astro-4yphtoen}
![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9Imljb24gbGFiZWwtaWNvbiBhc3Ryby00eXBodG9lbiBhc3Ryby1jNnZzb3FhcyIgd2lkdGg9IjE2IiBoZWlnaHQ9IjE2IiB2aWV3Ym94PSIwIDAgMjQgMjQiIGZpbGw9ImN1cnJlbnRDb2xvciIgc3R5bGU9Ii0tc2wtaWNvbi1zaXplOiAxZW07Ij48cGF0aCBkPSJNMjEgMTRoLTFWN2EzIDMgMCAwIDAtMy0zSDdhMyAzIDAgMCAwLTMgM3Y3SDNhMSAxIDAgMCAwLTEgMXYyYTMgMyAwIDAgMCAzIDNoMTRhMyAzIDAgMCAwIDMtM3YtMmExIDEgMCAwIDAtMS0xWk02IDdhMSAxIDAgMCAxIDEtMWgxMGExIDEgMCAwIDEgMSAxdjdINlY3Wm0xNCAxMGExIDEgMCAwIDEtMSAxSDVhMSAxIDAgMCAxLTEtMXYtMWgxNnYxWiI+PC9wYXRoPjwvc3ZnPg==){.icon
.label-icon .astro-4yphtoen .astro-c6vsoqas} DarkLightAuto
![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9Imljb24gY2FyZXQgYXN0cm8tNHlwaHRvZW4gYXN0cm8tYzZ2c29xYXMiIHdpZHRoPSIxNiIgaGVpZ2h0PSIxNiIgdmlld2JveD0iMCAwIDI0IDI0IiBmaWxsPSJjdXJyZW50Q29sb3IiIHN0eWxlPSItLXNsLWljb24tc2l6ZTogMWVtOyI+PHBhdGggZD0iTTE3IDkuMTdhMSAxIDAgMCAwLTEuNDEgMEwxMiAxMi43MSA4LjQ2IDkuMTdhMSAxIDAgMSAwLTEuNDEgMS40Mmw0LjI0IDQuMjRhMS4wMDIgMS4wMDIgMCAwIDAgMS40MiAwTDE3IDEwLjU5YTEuMDAyIDEuMDAyIDAgMCAwIDAtMS40MloiPjwvcGF0aD48L3N2Zz4=){.icon
.caret .astro-4yphtoen .astro-c6vsoqas}
:::
:::
:::

::: {hidden="" starlight-multi-sidebar-label="releases_tab"}
-   [ [Releases]{.large .astro-3ii7xxms} ]{.group-label .astro-3ii7xxms}
    ![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9ImNhcmV0IGFzdHJvLTNpaTd4eG1zIGFzdHJvLWM2dnNvcWFzIiB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCIgZmlsbD0iY3VycmVudENvbG9yIiBzdHlsZT0iLS1zbC1pY29uLXNpemU6IDEuMjVyZW07Ij48cGF0aCBkPSJtMTQuODMgMTEuMjktNC4yNC00LjI0YTEgMSAwIDEgMC0xLjQyIDEuNDFMMTIuNzEgMTJsLTMuNTQgMy41NGExIDEgMCAwIDAgMCAxLjQxIDEgMSAwIDAgMCAuNzEuMjkgMSAxIDAgMCAwIC43MS0uMjlsNC4yNC00LjI0YTEuMDAyIDEuMDAyIDAgMCAwIDAtMS40MloiPjwvcGF0aD48L3N2Zz4=){.caret
    .astro-3ii7xxms .astro-c6vsoqas}
    -   [[Release
        notes]{.astro-3ii7xxms}](/docs/changelogs/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Stable
        release]{.astro-3ii7xxms}](/docs/changelogs/latest/){.astro-3ii7xxms
        aria-current="false"}
    -   [[Preview
        release]{.astro-3ii7xxms}](/docs/changelogs/preview/){.astro-3ii7xxms
        aria-current="false"}

::: md:sl-hidden
::: {.mobile-preferences .sl-flex .astro-wu23bvmt}
::: {.social-icons .astro-wu23bvmt}
[[GitHub]{.sr-only
.astro-wy4te6ga}![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9ImFzdHJvLXd5NHRlNmdhIGFzdHJvLWM2dnNvcWFzIiB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCIgZmlsbD0iY3VycmVudENvbG9yIiBzdHlsZT0iLS1zbC1pY29uLXNpemU6IDFlbTsiPjxwYXRoIGQ9Ik0xMiAuM2ExMiAxMiAwIDAgMC0zLjggMjMuMzhjLjYuMTIuODMtLjI2LjgzLS41N0w5IDIxLjA3Yy0zLjM0LjcyLTQuMDQtMS42MS00LjA0LTEuNjEtLjU1LTEuMzktMS4zNC0xLjc2LTEuMzQtMS43Ni0xLjA4LS43NC4wOS0uNzMuMDktLjczIDEuMi4wOSAxLjgzIDEuMjQgMS44MyAxLjI0IDEuMDggMS44MyAyLjgxIDEuMyAzLjUgMSAuMS0uNzguNDItMS4zMS43Ni0xLjYxLTIuNjctLjMtNS40Ny0xLjMzLTUuNDctNS45MyAwLTEuMzEuNDctMi4zOCAxLjI0LTMuMjItLjE0LS4zLS41NC0xLjUyLjEtMy4xOCAwIDAgMS0uMzIgMy4zIDEuMjNhMTEuNSAxMS41IDAgMCAxIDYgMGMyLjI4LTEuNTUgMy4yOS0xLjIzIDMuMjktMS4yMy42NCAxLjY2LjI0IDIuODguMTIgMy4xOGE0LjY1IDQuNjUgMCAwIDEgMS4yMyAzLjIyYzAgNC42MS0yLjggNS42My01LjQ4IDUuOTIuNDIuMzYuODEgMS4xLjgxIDIuMjJsLS4wMSAzLjI5YzAgLjMxLjIuNjkuODIuNTdBMTIgMTIgMCAwIDAgMTIgLjNaIj48L3BhdGg+PC9zdmc+){.astro-wy4te6ga
.astro-c6vsoqas}](https://github.com/google-gemini/gemini-cli){.sl-flex
.astro-wy4te6ga rel="me"}
:::

[Select theme]{.sr-only .astro-4yphtoen}
![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9Imljb24gbGFiZWwtaWNvbiBhc3Ryby00eXBodG9lbiBhc3Ryby1jNnZzb3FhcyIgd2lkdGg9IjE2IiBoZWlnaHQ9IjE2IiB2aWV3Ym94PSIwIDAgMjQgMjQiIGZpbGw9ImN1cnJlbnRDb2xvciIgc3R5bGU9Ii0tc2wtaWNvbi1zaXplOiAxZW07Ij48cGF0aCBkPSJNMjEgMTRoLTFWN2EzIDMgMCAwIDAtMy0zSDdhMyAzIDAgMCAwLTMgM3Y3SDNhMSAxIDAgMCAwLTEgMXYyYTMgMyAwIDAgMCAzIDNoMTRhMyAzIDAgMCAwIDMtM3YtMmExIDEgMCAwIDAtMS0xWk02IDdhMSAxIDAgMCAxIDEtMWgxMGExIDEgMCAwIDEgMSAxdjdINlY3Wm0xNCAxMGExIDEgMCAwIDEtMSAxSDVhMSAxIDAgMCAxLTEtMXYtMWgxNnYxWiI+PC9wYXRoPjwvc3ZnPg==){.icon
.label-icon .astro-4yphtoen .astro-c6vsoqas} DarkLightAuto
![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9Imljb24gY2FyZXQgYXN0cm8tNHlwaHRvZW4gYXN0cm8tYzZ2c29xYXMiIHdpZHRoPSIxNiIgaGVpZ2h0PSIxNiIgdmlld2JveD0iMCAwIDI0IDI0IiBmaWxsPSJjdXJyZW50Q29sb3IiIHN0eWxlPSItLXNsLWljb24tc2l6ZTogMWVtOyI+PHBhdGggZD0iTTE3IDkuMTdhMSAxIDAgMCAwLTEuNDEgMEwxMiAxMi43MSA4LjQ2IDkuMTdhMSAxIDAgMSAwLTEuNDEgMS40Mmw0LjI0IDQuMjRhMS4wMDIgMS4wMDIgMCAwIDAgMS40MiAwTDE3IDEwLjU5YTEuMDAyIDEuMDAyIDAgMCAwIDAtMS40MloiPjwvcGF0aD48L3N2Zz4=){.icon
.caret .astro-4yphtoen .astro-c6vsoqas}
:::
:::
:::
:::
:::
:::

::: {.main-frame .astro-yriad4ts}
::: {.lg:sl-flex .astro-67yu43on}
::: {.right-sidebar .astro-67yu43on}
::: {.lg:sl-hidden .astro-pb3aqygn}
[On this
page![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9ImNhcmV0IGFzdHJvLWRveW5rNXRsIGFzdHJvLWM2dnNvcWFzIiB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCIgZmlsbD0iY3VycmVudENvbG9yIiBzdHlsZT0iLS1zbC1pY29uLXNpemU6IDFyZW07Ij48cGF0aCBkPSJtMTQuODMgMTEuMjktNC4yNC00LjI0YTEgMSAwIDEgMC0xLjQyIDEuNDFMMTIuNzEgMTJsLTMuNTQgMy41NGExIDEgMCAwIDAgMCAxLjQxIDEgMSAwIDAgMCAuNzEuMjkgMSAxIDAgMCAwIC43MS0uMjlsNC4yNC00LjI0YTEuMDAyIDEuMDAyIDAgMCAwIDAtMS40MloiPjwvcGF0aD48L3N2Zz4=){.caret
.astro-doynk5tl .astro-c6vsoqas}]{.toggle .sl-flex
.astro-doynk5tl}[]{.display-current .astro-doynk5tl}

::: {.dropdown .astro-doynk5tl}
-   [[Introduction]{.astro-g2bywc46
    style="--depth: 0;"}](#_top){.astro-g2bywc46 style="--depth: 0;"}
-   [[Create your first skill]{.astro-g2bywc46
    style="--depth: 0;"}](#create-your-first-skill){.astro-g2bywc46
    style="--depth: 0;"}
    -   [[1. Create the directory structure]{.astro-g2bywc46
        style="--depth: 1;"}](#1-create-the-directory-structure){.astro-g2bywc46
        style="--depth: 1;"}
    -   [[2. Create the definition (SKILL.md)]{.astro-g2bywc46
        style="--depth: 1;"}](#2-create-the-definition-skillmd){.astro-g2bywc46
        style="--depth: 1;"}
    -   [[3. Add the tool logic]{.astro-g2bywc46
        style="--depth: 1;"}](#3-add-the-tool-logic){.astro-g2bywc46
        style="--depth: 1;"}
-   [[Verify discovery]{.astro-g2bywc46
    style="--depth: 0;"}](#verify-discovery){.astro-g2bywc46
    style="--depth: 0;"}
    -   [[If your skill doesn't appear]{.astro-g2bywc46
        style="--depth: 1;"}](#if-your-skill-doesnt-appear){.astro-g2bywc46
        style="--depth: 1;"}
-   [[How to use the skill]{.astro-g2bywc46
    style="--depth: 0;"}](#how-to-use-the-skill){.astro-g2bywc46
    style="--depth: 0;"}
-   [[Pro tip: Use the skill-creator]{.astro-g2bywc46
    style="--depth: 0;"}](#pro-tip-use-the-skill-creator){.astro-g2bywc46
    style="--depth: 0;"}
-   [[Manage skills]{.astro-g2bywc46
    style="--depth: 0;"}](#manage-skills){.astro-g2bywc46
    style="--depth: 0;"}
-   [[Next steps]{.astro-g2bywc46
    style="--depth: 0;"}](#next-steps){.astro-g2bywc46
    style="--depth: 0;"}
:::
:::

::: {.right-sidebar-panel .sl-hidden .lg:sl-block .astro-pb3aqygn}
::: {.sl-container .astro-pb3aqygn}
## On this page {#starlight__on-this-page}

-   [[Introduction]{.astro-g2bywc46
    style="--depth: 0;"}](#_top){.astro-g2bywc46 style="--depth: 0;"}
-   [[Create your first skill]{.astro-g2bywc46
    style="--depth: 0;"}](#create-your-first-skill){.astro-g2bywc46
    style="--depth: 0;"}
    -   [[1. Create the directory structure]{.astro-g2bywc46
        style="--depth: 1;"}](#1-create-the-directory-structure){.astro-g2bywc46
        style="--depth: 1;"}
    -   [[2. Create the definition (SKILL.md)]{.astro-g2bywc46
        style="--depth: 1;"}](#2-create-the-definition-skillmd){.astro-g2bywc46
        style="--depth: 1;"}
    -   [[3. Add the tool logic]{.astro-g2bywc46
        style="--depth: 1;"}](#3-add-the-tool-logic){.astro-g2bywc46
        style="--depth: 1;"}
-   [[Verify discovery]{.astro-g2bywc46
    style="--depth: 0;"}](#verify-discovery){.astro-g2bywc46
    style="--depth: 0;"}
    -   [[If your skill doesn't appear]{.astro-g2bywc46
        style="--depth: 1;"}](#if-your-skill-doesnt-appear){.astro-g2bywc46
        style="--depth: 1;"}
-   [[How to use the skill]{.astro-g2bywc46
    style="--depth: 0;"}](#how-to-use-the-skill){.astro-g2bywc46
    style="--depth: 0;"}
-   [[Pro tip: Use the skill-creator]{.astro-g2bywc46
    style="--depth: 0;"}](#pro-tip-use-the-skill-creator){.astro-g2bywc46
    style="--depth: 0;"}
-   [[Manage skills]{.astro-g2bywc46
    style="--depth: 0;"}](#manage-skills){.astro-g2bywc46
    style="--depth: 0;"}
-   [[Next steps]{.astro-g2bywc46
    style="--depth: 0;"}](#next-steps){.astro-g2bywc46
    style="--depth: 0;"}
:::
:::
:::

::: {.main-pane .astro-67yu43on}
::: {.astro-bguv2lll role="main" pagefind-body="" lang="en" dir="ltr"}
::: {.content-panel .astro-7nkwcw3z}
::: {.sl-container .astro-7nkwcw3z}
::: {.flex .items-center .page-title .astro-guvttfii}
# Get started with Agent Skills {#_top .flex-1 .astro-guvttfii}

::: {.mt-4 .astro-guvttfii}
![](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSJjdXJyZW50Q29sb3IiIHN0cm9rZS13aWR0aD0iMiIgc3Ryb2tlLWxpbmVjYXA9InJvdW5kIiBzdHJva2UtbGluZWpvaW49InJvdW5kIiBjbGFzcz0iYXN0cm8teW0yY2J5ZHkiPiA8cmVjdCB3aWR0aD0iMTQiIGhlaWdodD0iMTQiIHg9IjgiIHk9IjgiIHJ4PSIyIiByeT0iMiIgY2xhc3M9ImFzdHJvLXltMmNieWR5Ij48L3JlY3Q+IDxwYXRoIGQ9Im00IDE2Yy0xLjEgMC0yLS45LTItMlY0YzAtMS4xLjktMiAyLTJoMTBjMS4xIDAgMiAuOSAyIDIiIGNsYXNzPSJhc3Ryby15bTJjYnlkeSI+PC9wYXRoPiA8L3N2Zz4=){.astro-ym2cbydy}
[Copy as Markdown]{.button-text .astro-ym2cbydy} [Copied!]{.success-text
.astro-ym2cbydy style="display: none;"}
:::
:::
:::
:::

::: {.content-panel .astro-7nkwcw3z}
::: {.sl-container .astro-7nkwcw3z}
::: sl-markdown-content
Agent Skills extend Gemini CLI with specialized expertise. In this
tutorial, you'll learn how to create your first skill, bundle custom
logic, and activate it during a session.

::: {.sl-heading-wrapper .level-h2}
## Create your first skill

[[![](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iY3VycmVudGNvbG9yIiBkPSJtMTIuMTEgMTUuMzktMy44OCAzLjg4YTIuNTIgMi41MiAwIDAgMS0zLjUgMCAyLjQ3IDIuNDcgMCAwIDEgMC0zLjVsMy44OC0zLjg4YTEgMSAwIDAgMC0xLjQyLTEuNDJsLTMuODggMy44OWE0LjQ4IDQuNDggMCAwIDAgNi4zMyA2LjMzbDMuODktMy44OGExIDEgMCAxIDAtMS40Mi0xLjQyWm04LjU4LTEyLjA4YTQuNDkgNC40OSAwIDAgMC02LjMzIDBsLTMuODkgMy44OGExIDEgMCAwIDAgMS40MiAxLjQybDMuODgtMy44OGEyLjUyIDIuNTIgMCAwIDEgMy41IDAgMi40NyAyLjQ3IDAgMCAxIDAgMy41bC0zLjg4IDMuODhhMSAxIDAgMSAwIDEuNDIgMS40MmwzLjg4LTMuODlhNC40OSA0LjQ5IDAgMCAwIDAtNi4zM1pNOC44MyAxNS4xN2ExIDEgMCAwIDAgMS4xLjIyIDEgMSAwIDAgMCAuMzItLjIybDQuOTItNC45MmExIDEgMCAwIDAtMS40Mi0xLjQybC00LjkyIDQuOTJhMSAxIDAgMCAwIDAgMS40MloiPjwvcGF0aD48L3N2Zz4=)]{.sl-anchor-icon
aria-hidden="true"}[Section titled "Create your first
skill"]{.sr-only}](#create-your-first-skill){.sl-anchor-link}
:::

A skill is defined by a directory containing a `SKILL.md`{dir="auto"}
file and subdirectories containing reference materials or scripts used
by the skill. Let's create an **API Auditor** skill that runs a script
to help you verify if local or remote endpoints are responding
correctly.

::: {.sl-heading-wrapper .level-h3}
### 1. Create the directory structure {#1-create-the-directory-structure}

[[![](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iY3VycmVudGNvbG9yIiBkPSJtMTIuMTEgMTUuMzktMy44OCAzLjg4YTIuNTIgMi41MiAwIDAgMS0zLjUgMCAyLjQ3IDIuNDcgMCAwIDEgMC0zLjVsMy44OC0zLjg4YTEgMSAwIDAgMC0xLjQyLTEuNDJsLTMuODggMy44OWE0LjQ4IDQuNDggMCAwIDAgNi4zMyA2LjMzbDMuODktMy44OGExIDEgMCAxIDAtMS40Mi0xLjQyWm04LjU4LTEyLjA4YTQuNDkgNC40OSAwIDAgMC02LjMzIDBsLTMuODkgMy44OGExIDEgMCAwIDAgMS40MiAxLjQybDMuODgtMy44OGEyLjUyIDIuNTIgMCAwIDEgMy41IDAgMi40NyAyLjQ3IDAgMCAxIDAgMy41bC0zLjg4IDMuODhhMSAxIDAgMSAwIDEuNDIgMS40MmwzLjg4LTMuODlhNC40OSA0LjQ5IDAgMCAwIDAtNi4zM1pNOC44MyAxNS4xN2ExIDEgMCAwIDAgMS4xLjIyIDEgMSAwIDAgMCAuMzItLjIybDQuOTItNC45MmExIDEgMCAwIDAtMS40Mi0xLjQybC00LjkyIDQuOTJhMSAxIDAgMCAwIDAgMS40MloiPjwvcGF0aD48L3N2Zz4=)]{.sl-anchor-icon
aria-hidden="true"}[Section titled "1. Create the directory
structure"]{.sr-only}](#1-create-the-directory-structure){.sl-anchor-link}
:::

The first step is to create the necessary folders for your skill and its
scripts.

**macOS/Linux**

::: expressive-code
<figure class="frame is-terminal not-content">
<pre data-language="bash"><code>mkdir -p .gemini/skills/api-auditor/scripts</code></pre>
<div class="copy">
<div>

</div>
</div>
<figcaption><span class="title"></span><span class="sr-only">Terminal
window</span></figcaption>
</figure>
:::

**Windows (PowerShell)**

::: expressive-code
<figure class="frame is-terminal not-content">
<pre data-language="powershell"><code>New-Item -ItemType Directory -Force -Path &quot;.gemini\skills\api-auditor\scripts&quot;</code></pre>
<div class="copy">
<div>

</div>
</div>
<figcaption><span class="title"></span><span class="sr-only">Terminal
window</span></figcaption>
</figure>
:::

::: {.sl-heading-wrapper .level-h3}
### 2. Create the definition (`SKILL.md`{dir="auto"}) {#2-create-the-definition-skillmd}

[[![](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iY3VycmVudGNvbG9yIiBkPSJtMTIuMTEgMTUuMzktMy44OCAzLjg4YTIuNTIgMi41MiAwIDAgMS0zLjUgMCAyLjQ3IDIuNDcgMCAwIDEgMC0zLjVsMy44OC0zLjg4YTEgMSAwIDAgMC0xLjQyLTEuNDJsLTMuODggMy44OWE0LjQ4IDQuNDggMCAwIDAgNi4zMyA2LjMzbDMuODktMy44OGExIDEgMCAxIDAtMS40Mi0xLjQyWm04LjU4LTEyLjA4YTQuNDkgNC40OSAwIDAgMC02LjMzIDBsLTMuODkgMy44OGExIDEgMCAwIDAgMS40MiAxLjQybDMuODgtMy44OGEyLjUyIDIuNTIgMCAwIDEgMy41IDAgMi40NyAyLjQ3IDAgMCAxIDAgMy41bC0zLjg4IDMuODhhMSAxIDAgMSAwIDEuNDIgMS40MmwzLjg4LTMuODlhNC40OSA0LjQ5IDAgMCAwIDAtNi4zM1pNOC44MyAxNS4xN2ExIDEgMCAwIDAgMS4xLjIyIDEgMSAwIDAgMCAuMzItLjIybDQuOTItNC45MmExIDEgMCAwIDAtMS40Mi0xLjQybC00LjkyIDQuOTJhMSAxIDAgMCAwIDAgMS40MloiPjwvcGF0aD48L3N2Zz4=)]{.sl-anchor-icon
aria-hidden="true"}[Section titled "2. Create the definition
(SKILL.md)"]{.sr-only}](#2-create-the-definition-skillmd){.sl-anchor-link}
:::

The `SKILL.md`{dir="auto"} file defines the skill's purpose and
instructions for the agent. Create a file at
`.gemini/skills/api-auditor/SKILL.md`{dir="auto"}. This tells the agent
*when* to use the skill and *how* to behave.

::: expressive-code
<figure class="frame not-content">
<pre data-language="markdown"><code>---name: api-auditordescription:  Expertise in auditing and testing API endpoints. Use when the user asks to  &quot;check&quot;, &quot;test&quot;, or &quot;audit&quot; a URL or API.---
# API Auditor Instructions
You act as a QA engineer specialized in API reliability. When this skill isactive, you MUST:
1.  **Audit**: Use the bundled `scripts/audit.js` utility to check the status of    the provided URL.2.  **Report**: Analyze the output (status codes, latency) and explain any    failures in plain English.3.  **Secure**: Remind the user if they are testing a sensitive endpoint without    an `https://` protocol.</code></pre>
<div class="copy">
<div>

</div>
</div>
</figure>
:::

::: {.sl-heading-wrapper .level-h3}
### 3. Add the tool logic {#3-add-the-tool-logic}

[[![](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iY3VycmVudGNvbG9yIiBkPSJtMTIuMTEgMTUuMzktMy44OCAzLjg4YTIuNTIgMi41MiAwIDAgMS0zLjUgMCAyLjQ3IDIuNDcgMCAwIDEgMC0zLjVsMy44OC0zLjg4YTEgMSAwIDAgMC0xLjQyLTEuNDJsLTMuODggMy44OWE0LjQ4IDQuNDggMCAwIDAgNi4zMyA2LjMzbDMuODktMy44OGExIDEgMCAxIDAtMS40Mi0xLjQyWm04LjU4LTEyLjA4YTQuNDkgNC40OSAwIDAgMC02LjMzIDBsLTMuODkgMy44OGExIDEgMCAwIDAgMS40MiAxLjQybDMuODgtMy44OGEyLjUyIDIuNTIgMCAwIDEgMy41IDAgMi40NyAyLjQ3IDAgMCAxIDAgMy41bC0zLjg4IDMuODhhMSAxIDAgMSAwIDEuNDIgMS40MmwzLjg4LTMuODlhNC40OSA0LjQ5IDAgMCAwIDAtNi4zM1pNOC44MyAxNS4xN2ExIDEgMCAwIDAgMS4xLjIyIDEgMSAwIDAgMCAuMzItLjIybDQuOTItNC45MmExIDEgMCAwIDAtMS40Mi0xLjQybC00LjkyIDQuOTJhMSAxIDAgMCAwIDAgMS40MloiPjwvcGF0aD48L3N2Zz4=)]{.sl-anchor-icon
aria-hidden="true"}[Section titled "3. Add the tool
logic"]{.sr-only}](#3-add-the-tool-logic){.sl-anchor-link}
:::

Skills can bundle resources like scripts to perform deterministic tasks.
Create a file at
`.gemini/skills/api-auditor/scripts/audit.js`{dir="auto"}. This is the
code the agent will run.

::: expressive-code
<figure class="frame has-title not-content">
<pre data-language="javascript"><code>const url = process.argv[2];
if (!url) {  console.error(&#39;Usage: node audit.js &lt;url&gt;&#39;);  process.exit(1);}
console.log(`Auditing ${url}...`);fetch(url, { method: &#39;HEAD&#39; })  .then((r) =&gt; console.log(`Result: Success (Status ${r.status})`))  .catch((e) =&gt; console.error(`Result: Failed (${e.message})`));</code></pre>
<div class="copy">
<div>

</div>
</div>
<figcaption><span
class="title">.gemini/skills/api-auditor/scripts/audit.js</span></figcaption>
</figure>
:::

::: {.sl-heading-wrapper .level-h2}
## Verify discovery

[[![](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iY3VycmVudGNvbG9yIiBkPSJtMTIuMTEgMTUuMzktMy44OCAzLjg4YTIuNTIgMi41MiAwIDAgMS0zLjUgMCAyLjQ3IDIuNDcgMCAwIDEgMC0zLjVsMy44OC0zLjg4YTEgMSAwIDAgMC0xLjQyLTEuNDJsLTMuODggMy44OWE0LjQ4IDQuNDggMCAwIDAgNi4zMyA2LjMzbDMuODktMy44OGExIDEgMCAxIDAtMS40Mi0xLjQyWm04LjU4LTEyLjA4YTQuNDkgNC40OSAwIDAgMC02LjMzIDBsLTMuODkgMy44OGExIDEgMCAwIDAgMS40MiAxLjQybDMuODgtMy44OGEyLjUyIDIuNTIgMCAwIDEgMy41IDAgMi40NyAyLjQ3IDAgMCAxIDAgMy41bC0zLjg4IDMuODhhMSAxIDAgMSAwIDEuNDIgMS40MmwzLjg4LTMuODlhNC40OSA0LjQ5IDAgMCAwIDAtNi4zM1pNOC44MyAxNS4xN2ExIDEgMCAwIDAgMS4xLjIyIDEgMSAwIDAgMCAuMzItLjIybDQuOTItNC45MmExIDEgMCAwIDAtMS40Mi0xLjQybC00LjkyIDQuOTJhMSAxIDAgMCAwIDAgMS40MloiPjwvcGF0aD48L3N2Zz4=)]{.sl-anchor-icon
aria-hidden="true"}[Section titled "Verify
discovery"]{.sr-only}](#verify-discovery){.sl-anchor-link}
:::

Gemini CLI automatically discovers skills in the
`.gemini/skills`{dir="auto"} directory (as well as the
`.agents/skills`{dir="auto"} alias).

To check if Gemini CLI found your new skill, use the
`/skills list`{dir="auto"} command within an interactive session:

::: expressive-code
<figure class="frame is-terminal not-content">
<pre data-language="bash"><code>/skills list</code></pre>
<div class="copy">
<div>

</div>
</div>
<figcaption><span class="title"></span><span class="sr-only">Terminal
window</span></figcaption>
</figure>
:::

You should see `api-auditor`{dir="auto"} in the list of available
skills. If you just added the files, you can run
`/skills reload`{dir="auto"} to refresh the list without restarting the
session.

::: {.sl-heading-wrapper .level-h3}
### If your skill doesn't appear

[[![](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iY3VycmVudGNvbG9yIiBkPSJtMTIuMTEgMTUuMzktMy44OCAzLjg4YTIuNTIgMi41MiAwIDAgMS0zLjUgMCAyLjQ3IDIuNDcgMCAwIDEgMC0zLjVsMy44OC0zLjg4YTEgMSAwIDAgMC0xLjQyLTEuNDJsLTMuODggMy44OWE0LjQ4IDQuNDggMCAwIDAgNi4zMyA2LjMzbDMuODktMy44OGExIDEgMCAxIDAtMS40Mi0xLjQyWm04LjU4LTEyLjA4YTQuNDkgNC40OSAwIDAgMC02LjMzIDBsLTMuODkgMy44OGExIDEgMCAwIDAgMS40MiAxLjQybDMuODgtMy44OGEyLjUyIDIuNTIgMCAwIDEgMy41IDAgMi40NyAyLjQ3IDAgMCAxIDAgMy41bC0zLjg4IDMuODhhMSAxIDAgMSAwIDEuNDIgMS40MmwzLjg4LTMuODlhNC40OSA0LjQ5IDAgMCAwIDAtNi4zM1pNOC44MyAxNS4xN2ExIDEgMCAwIDAgMS4xLjIyIDEgMSAwIDAgMCAuMzItLjIybDQuOTItNC45MmExIDEgMCAwIDAtMS40Mi0xLjQybC00LjkyIDQuOTJhMSAxIDAgMCAwIDAgMS40MloiPjwvcGF0aD48L3N2Zz4=)]{.sl-anchor-icon
aria-hidden="true"}[Section titled "If your skill doesn't
appear"]{.sr-only}](#if-your-skill-doesnt-appear){.sl-anchor-link}
:::

If `/skills list`{dir="auto"} doesn't show your skill, check the
following:

1.  **The folder must be trusted (workspace skills only).** Skills under
    `<workspace>/.gemini/skills/`{dir="auto"} are only loaded when the
    workspace folder is marked as trusted. Run `/trust`{dir="auto"} and
    restart the session if needed. Skills under
    `~/.gemini/skills/`{dir="auto"} (user scope) are not affected by
    trust.
2.  **Check the path layout.** `SKILL.md`{dir="auto"} is discovered
    either at the root of the skills directory
    (`.gemini/skills/SKILL.md`{dir="auto"}) or one directory deep
    (`.gemini/skills/<skill-name>/SKILL.md`{dir="auto"}). The
    recommended layout uses a subdirectory per skill so you can bundle
    scripts and other resources alongside it. Files nested more than one
    directory deep are not discovered.
3.  **The filename must be exactly `SKILL.md`{dir="auto"}.**
    Capitalization matters on case-sensitive filesystems (Linux, and
    macOS when configured as such): `skill.md`{dir="auto"} or
    `Skill.md`{dir="auto"} will be ignored.
4.  **Frontmatter must include both `name:`{dir="auto"} and
    `description:`{dir="auto"}, and must be the first thing in the
    file.** A `SKILL.md`{dir="auto"} is silently skipped if either field
    is missing, if the delimiters (`---`{dir="auto"} on their own lines)
    are absent, or if any text (an H1 title, a comment, even a blank
    line) appears before the opening `---`{dir="auto"}.
5.  **The skill name comes from the `name:`{dir="auto"} field, not the
    directory name.** If your frontmatter says `name: foo`{dir="auto"},
    the skill appears as `foo`{dir="auto"} in `/skills list`{dir="auto"}
    regardless of what its parent directory is called. The characters
    `: \ / < > * ? " |`{dir="auto"} in the name are replaced with
    `-`{dir="auto"}.

::: {.sl-heading-wrapper .level-h2}
## How to use the skill

[[![](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iY3VycmVudGNvbG9yIiBkPSJtMTIuMTEgMTUuMzktMy44OCAzLjg4YTIuNTIgMi41MiAwIDAgMS0zLjUgMCAyLjQ3IDIuNDcgMCAwIDEgMC0zLjVsMy44OC0zLjg4YTEgMSAwIDAgMC0xLjQyLTEuNDJsLTMuODggMy44OWE0LjQ4IDQuNDggMCAwIDAgNi4zMyA2LjMzbDMuODktMy44OGExIDEgMCAxIDAtMS40Mi0xLjQyWm04LjU4LTEyLjA4YTQuNDkgNC40OSAwIDAgMC02LjMzIDBsLTMuODkgMy44OGExIDEgMCAwIDAgMS40MiAxLjQybDMuODgtMy44OGEyLjUyIDIuNTIgMCAwIDEgMy41IDAgMi40NyAyLjQ3IDAgMCAxIDAgMy41bC0zLjg4IDMuODhhMSAxIDAgMSAwIDEuNDIgMS40MmwzLjg4LTMuODlhNC40OSA0LjQ5IDAgMCAwIDAtNi4zM1pNOC44MyAxNS4xN2ExIDEgMCAwIDAgMS4xLjIyIDEgMSAwIDAgMCAuMzItLjIybDQuOTItNC45MmExIDEgMCAwIDAtMS40Mi0xLjQybC00LjkyIDQuOTJhMSAxIDAgMCAwIDAgMS40MloiPjwvcGF0aD48L3N2Zz4=)]{.sl-anchor-icon
aria-hidden="true"}[Section titled "How to use the
skill"]{.sr-only}](#how-to-use-the-skill){.sl-anchor-link}
:::

Now that the skill is discovered, you can trigger its activation by
asking a relevant question.

1.  **Trigger**: Start a new session and ask: "Can you audit
    <https://google.com>"
2.  **Activation**: Gemini identifies that the request matches the
    `api-auditor`{dir="auto"} description and calls the
    `activate_skill`{dir="auto"} tool.
3.  **Consent**: You will see a confirmation prompt. Type **y** to
    approve.
4.  **Execution**: Once activated, Gemini uses the
    `run_shell_command`{dir="auto"} tool to execute your bundled script:
    `node .gemini/skills/api-auditor/scripts/audit.js https://google.com`{dir="auto"}

::: {.sl-heading-wrapper .level-h2}
## Pro tip: Use the skill-creator

[[![](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iY3VycmVudGNvbG9yIiBkPSJtMTIuMTEgMTUuMzktMy44OCAzLjg4YTIuNTIgMi41MiAwIDAgMS0zLjUgMCAyLjQ3IDIuNDcgMCAwIDEgMC0zLjVsMy44OC0zLjg4YTEgMSAwIDAgMC0xLjQyLTEuNDJsLTMuODggMy44OWE0LjQ4IDQuNDggMCAwIDAgNi4zMyA2LjMzbDMuODktMy44OGExIDEgMCAxIDAtMS40Mi0xLjQyWm04LjU4LTEyLjA4YTQuNDkgNC40OSAwIDAgMC02LjMzIDBsLTMuODkgMy44OGExIDEgMCAwIDAgMS40MiAxLjQybDMuODgtMy44OGEyLjUyIDIuNTIgMCAwIDEgMy41IDAgMi40NyAyLjQ3IDAgMCAxIDAgMy41bC0zLjg4IDMuODhhMSAxIDAgMSAwIDEuNDIgMS40MmwzLjg4LTMuODlhNC40OSA0LjQ5IDAgMCAwIDAtNi4zM1pNOC44MyAxNS4xN2ExIDEgMCAwIDAgMS4xLjIyIDEgMSAwIDAgMCAuMzItLjIybDQuOTItNC45MmExIDEgMCAwIDAtMS40Mi0xLjQybC00LjkyIDQuOTJhMSAxIDAgMCAwIDAgMS40MloiPjwvcGF0aD48L3N2Zz4=)]{.sl-anchor-icon
aria-hidden="true"}[Section titled "Pro tip: Use the
skill-creator"]{.sr-only}](#pro-tip-use-the-skill-creator){.sl-anchor-link}
:::

If you don't want to create the files manually, you can use the built-in
`skill-creator`{dir="auto"} skill. Simply ask Gemini:

> "Create a new skill called 'api-auditor' that tests if URLs are
> responding."

The `skill-creator`{dir="auto"} will handle the directory structure and
boilerplate for you.

::: {.sl-heading-wrapper .level-h2}
## Manage skills

[[![](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iY3VycmVudGNvbG9yIiBkPSJtMTIuMTEgMTUuMzktMy44OCAzLjg4YTIuNTIgMi41MiAwIDAgMS0zLjUgMCAyLjQ3IDIuNDcgMCAwIDEgMC0zLjVsMy44OC0zLjg4YTEgMSAwIDAgMC0xLjQyLTEuNDJsLTMuODggMy44OWE0LjQ4IDQuNDggMCAwIDAgNi4zMyA2LjMzbDMuODktMy44OGExIDEgMCAxIDAtMS40Mi0xLjQyWm04LjU4LTEyLjA4YTQuNDkgNC40OSAwIDAgMC02LjMzIDBsLTMuODkgMy44OGExIDEgMCAwIDAgMS40MiAxLjQybDMuODgtMy44OGEyLjUyIDIuNTIgMCAwIDEgMy41IDAgMi40NyAyLjQ3IDAgMCAxIDAgMy41bC0zLjg4IDMuODhhMSAxIDAgMSAwIDEuNDIgMS40MmwzLjg4LTMuODlhNC40OSA0LjQ5IDAgMCAwIDAtNi4zM1pNOC44MyAxNS4xN2ExIDEgMCAwIDAgMS4xLjIyIDEgMSAwIDAgMCAuMzItLjIybDQuOTItNC45MmExIDEgMCAwIDAtMS40Mi0xLjQybC00LjkyIDQuOTJhMSAxIDAgMCAwIDAgMS40MloiPjwvcGF0aD48L3N2Zz4=)]{.sl-anchor-icon
aria-hidden="true"}[Section titled "Manage
skills"]{.sr-only}](#manage-skills){.sl-anchor-link}
:::

You can also manage skills using the `gemini skills`{dir="auto"} command
from your terminal:

-   **Install**: `gemini skills install <url-or-path>`{dir="auto"}
-   **Link**: `gemini skills link <path>`{dir="auto"} (useful for local
    development)
-   **Uninstall**: `gemini skills uninstall <name>`{dir="auto"}

::: {.sl-heading-wrapper .level-h2}
## Next steps

[[![](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iY3VycmVudGNvbG9yIiBkPSJtMTIuMTEgMTUuMzktMy44OCAzLjg4YTIuNTIgMi41MiAwIDAgMS0zLjUgMCAyLjQ3IDIuNDcgMCAwIDEgMC0zLjVsMy44OC0zLjg4YTEgMSAwIDAgMC0xLjQyLTEuNDJsLTMuODggMy44OWE0LjQ4IDQuNDggMCAwIDAgNi4zMyA2LjMzbDMuODktMy44OGExIDEgMCAxIDAtMS40Mi0xLjQyWm04LjU4LTEyLjA4YTQuNDkgNC40OSAwIDAgMC02LjMzIDBsLTMuODkgMy44OGExIDEgMCAwIDAgMS40MiAxLjQybDMuODgtMy44OGEyLjUyIDIuNTIgMCAwIDEgMy41IDAgMi40NyAyLjQ3IDAgMCAxIDAgMy41bC0zLjg4IDMuODhhMSAxIDAgMSAwIDEuNDIgMS40MmwzLjg4LTMuODlhNC40OSA0LjQ5IDAgMCAwIDAtNi4zM1pNOC44MyAxNS4xN2ExIDEgMCAwIDAgMS4xLjIyIDEgMSAwIDAgMCAuMzItLjIybDQuOTItNC45MmExIDEgMCAwIDAtMS40Mi0xLjQybC00LjkyIDQuOTJhMSAxIDAgMCAwIDAgMS40MloiPjwvcGF0aD48L3N2Zz4=)]{.sl-anchor-icon
aria-hidden="true"}[Section titled "Next
steps"]{.sr-only}](#next-steps){.sl-anchor-link}
:::

-   [Creating Agent Skills](/docs/cli/creating-skills): Detailed guide
    on advanced skill features and metadata.
-   [Using Agent Skills](/docs/cli/using-agent-skills): More ways to
    discover and manage your skill library.
-   [Skill best practices](/docs/cli/skills-best-practices): Learn how
    to design reliable and effective expertise.
:::

::: {.starlight-footer .astro-nixdnp5i}
::: {.last-updated .astro-asuirehi}
![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgd2lkdGg9IjE2IiBoZWlnaHQ9IjE2IiB2aWV3Ym94PSIwIDAgMjQgMjQiIGZpbGw9ImN1cnJlbnRDb2xvciIgY2xhc3M9ImNhbGVuZGFyLWljb24gYXN0cm8tYXN1aXJlaGkiPjxwYXRoIGQ9Ik0xOSA0aC0xVjJoLTJ2Mkg4VjJINnYySDVjLTEuMTEgMC0xLjk5LjktMS45OSAyTDMgMjBhMiAyIDAgMCAwIDIgMmgxNGMxLjEgMCAyLS45IDItMlY2YzAtMS4xLS45LTItMi0yem0wIDE2SDVWMTBoMTR2MTB6bTAtMTJINVY2aDE0djJ6bS03IDVoNXY1aC01di01eiIgY2xhc3M9ImFzdHJvLWFzdWlyZWhpIj48L3BhdGg+PC9zdmc+){.calendar-icon
.astro-asuirehi}[Last updated: Apr 30, 2026]{.astro-asuirehi}
:::
:::
:::
:::
:::
:::
:::
:::

::: {#cookie-notice-wrapper .hidden .astro-uz2wdcl7}
::: {.cookie-notice-container .fixed .bottom-0 .left-0 .right-0 .flex .justify-center .z-50 .astro-uz2wdcl7}
::: {.cookie-notice .text-sm .bg-[var(--sl-color-bg)]/50 .backdrop-blur-sm .m-2 .p-3 .rounded-lg .flex .max-sm:flex-col .items-center .border .border-[var(--sl-color-white)]/20 .astro-uz2wdcl7}
::: {.mr-2 .astro-uz2wdcl7}
This website uses
[cookies](https://policies.google.com/technologies/cookies){.underline
.text-[var(--sl-color-white)]/70 .astro-uz2wdcl7 target="_blank"} from
Google to deliver and enhance the quality of its services and to analyze
traffic.
:::

I understand.
:::
:::
:::

::: {.footer-content .astro-sz7xmlte}
::: {.logos .astro-sz7xmlte}
![Google logo](/assets/Google.svg){.logo-light .astro-sz7xmlte
width="64.216" height="21"} ![Google
logo](/assets/Google-dark.svg){.logo-dark .astro-sz7xmlte width="64.216"
height="21"} ![For Developers
logo](/assets/fordevelopers.svg){.logo-light .fordev-logo
.astro-sz7xmlte width="122.678" height="17.583"} ![For Developers
logo](/assets/fordevelopers-dark.svg){.logo-dark .fordev-logo
.astro-sz7xmlte width="122.678" height="17.583"}
:::

::: {.footer-links .astro-sz7xmlte}
[Terms](/terms){.tos-link .astro-sz7xmlte target="_blank"
rel="noopener noreferrer"} [\|]{.divider .astro-sz7xmlte}
[Privacy](https://policies.google.com/privacy){.tos-link .astro-sz7xmlte
target="_blank" rel="noopener noreferrer"}
:::
:::
:::
