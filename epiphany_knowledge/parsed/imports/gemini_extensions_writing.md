# gemini_extensions_writing.md [DISTILLED]

**Source:** https://geminicli.com/docs/extensions/writing-extensions/

**Summary:** Guide on writing Gemini CLI extensions, explaining features like MCP servers, custom commands, hooks, and Agent Skills, along with structure and linking. Included in [Skill Packaging and Distribution](../topics/skill-packaging-and-distribution.md) and [Extension Architectures](../topics/extension-architectures.md).

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
.astro-3ef6ksr2}](https://github.com/google-gemini/gemini-cli/issues/new?template=website_issue.yml&url=https%3A%2F%2Fgeminicli.com%2Fdocs%2Fextensions%2Fwriting-extensions%2F){.feedback-link
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
            aria-current="false"}
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
                aria-current="page"}
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
        aria-current="false"}
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
            aria-current="page"}
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
-   [[Prerequisites]{.astro-g2bywc46
    style="--depth: 0;"}](#prerequisites){.astro-g2bywc46
    style="--depth: 0;"}
-   [[Extension features]{.astro-g2bywc46
    style="--depth: 0;"}](#extension-features){.astro-g2bywc46
    style="--depth: 0;"}
-   [[Step 1: Create a new extension]{.astro-g2bywc46
    style="--depth: 0;"}](#step-1-create-a-new-extension){.astro-g2bywc46
    style="--depth: 0;"}
-   [[Step 2: Understand the extension files]{.astro-g2bywc46
    style="--depth: 0;"}](#step-2-understand-the-extension-files){.astro-g2bywc46
    style="--depth: 0;"}
    -   [[gemini-extension.json]{.astro-g2bywc46
        style="--depth: 1;"}](#gemini-extensionjson){.astro-g2bywc46
        style="--depth: 1;"}
    -   [[example.js]{.astro-g2bywc46
        style="--depth: 1;"}](#examplejs){.astro-g2bywc46
        style="--depth: 1;"}
    -   [[package.json]{.astro-g2bywc46
        style="--depth: 1;"}](#packagejson){.astro-g2bywc46
        style="--depth: 1;"}
-   [[Step 3: Add extension settings]{.astro-g2bywc46
    style="--depth: 0;"}](#step-3-add-extension-settings){.astro-g2bywc46
    style="--depth: 0;"}
-   [[Step 4: Link your extension]{.astro-g2bywc46
    style="--depth: 0;"}](#step-4-link-your-extension){.astro-g2bywc46
    style="--depth: 0;"}
-   [[Step 5: Add a custom command]{.astro-g2bywc46
    style="--depth: 0;"}](#step-5-add-a-custom-command){.astro-g2bywc46
    style="--depth: 0;"}
-   [[Step 6: Add a custom GEMINI.md]{.astro-g2bywc46
    style="--depth: 0;"}](#step-6-add-a-custom-geminimd){.astro-g2bywc46
    style="--depth: 0;"}
-   [[(Optional) Step 7: Add an Agent Skill]{.astro-g2bywc46
    style="--depth: 0;"}](#optional-step-7-add-an-agent-skill){.astro-g2bywc46
    style="--depth: 0;"}
-   [[Step 8: Release your extension]{.astro-g2bywc46
    style="--depth: 0;"}](#step-8-release-your-extension){.astro-g2bywc46
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
-   [[Prerequisites]{.astro-g2bywc46
    style="--depth: 0;"}](#prerequisites){.astro-g2bywc46
    style="--depth: 0;"}
-   [[Extension features]{.astro-g2bywc46
    style="--depth: 0;"}](#extension-features){.astro-g2bywc46
    style="--depth: 0;"}
-   [[Step 1: Create a new extension]{.astro-g2bywc46
    style="--depth: 0;"}](#step-1-create-a-new-extension){.astro-g2bywc46
    style="--depth: 0;"}
-   [[Step 2: Understand the extension files]{.astro-g2bywc46
    style="--depth: 0;"}](#step-2-understand-the-extension-files){.astro-g2bywc46
    style="--depth: 0;"}
    -   [[gemini-extension.json]{.astro-g2bywc46
        style="--depth: 1;"}](#gemini-extensionjson){.astro-g2bywc46
        style="--depth: 1;"}
    -   [[example.js]{.astro-g2bywc46
        style="--depth: 1;"}](#examplejs){.astro-g2bywc46
        style="--depth: 1;"}
    -   [[package.json]{.astro-g2bywc46
        style="--depth: 1;"}](#packagejson){.astro-g2bywc46
        style="--depth: 1;"}
-   [[Step 3: Add extension settings]{.astro-g2bywc46
    style="--depth: 0;"}](#step-3-add-extension-settings){.astro-g2bywc46
    style="--depth: 0;"}
-   [[Step 4: Link your extension]{.astro-g2bywc46
    style="--depth: 0;"}](#step-4-link-your-extension){.astro-g2bywc46
    style="--depth: 0;"}
-   [[Step 5: Add a custom command]{.astro-g2bywc46
    style="--depth: 0;"}](#step-5-add-a-custom-command){.astro-g2bywc46
    style="--depth: 0;"}
-   [[Step 6: Add a custom GEMINI.md]{.astro-g2bywc46
    style="--depth: 0;"}](#step-6-add-a-custom-geminimd){.astro-g2bywc46
    style="--depth: 0;"}
-   [[(Optional) Step 7: Add an Agent Skill]{.astro-g2bywc46
    style="--depth: 0;"}](#optional-step-7-add-an-agent-skill){.astro-g2bywc46
    style="--depth: 0;"}
-   [[Step 8: Release your extension]{.astro-g2bywc46
    style="--depth: 0;"}](#step-8-release-your-extension){.astro-g2bywc46
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
# Build Gemini CLI extensions {#_top .flex-1 .astro-guvttfii}

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
Gemini CLI extensions let you expand the capabilities of Gemini CLI by
adding custom tools, commands, and context. This guide walks you through
creating your first extension, from setting up a template to adding
custom functionality and linking it for local development.

::: {.sl-heading-wrapper .level-h2}
## Prerequisites

[[![](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iY3VycmVudGNvbG9yIiBkPSJtMTIuMTEgMTUuMzktMy44OCAzLjg4YTIuNTIgMi41MiAwIDAgMS0zLjUgMCAyLjQ3IDIuNDcgMCAwIDEgMC0zLjVsMy44OC0zLjg4YTEgMSAwIDAgMC0xLjQyLTEuNDJsLTMuODggMy44OWE0LjQ4IDQuNDggMCAwIDAgNi4zMyA2LjMzbDMuODktMy44OGExIDEgMCAxIDAtMS40Mi0xLjQyWm04LjU4LTEyLjA4YTQuNDkgNC40OSAwIDAgMC02LjMzIDBsLTMuODkgMy44OGExIDEgMCAwIDAgMS40MiAxLjQybDMuODgtMy44OGEyLjUyIDIuNTIgMCAwIDEgMy41IDAgMi40NyAyLjQ3IDAgMCAxIDAgMy41bC0zLjg4IDMuODhhMSAxIDAgMSAwIDEuNDIgMS40MmwzLjg4LTMuODlhNC40OSA0LjQ5IDAgMCAwIDAtNi4zM1pNOC44MyAxNS4xN2ExIDEgMCAwIDAgMS4xLjIyIDEgMSAwIDAgMCAuMzItLjIybDQuOTItNC45MmExIDEgMCAwIDAtMS40Mi0xLjQybC00LjkyIDQuOTJhMSAxIDAgMCAwIDAgMS40MloiPjwvcGF0aD48L3N2Zz4=)]{.sl-anchor-icon
aria-hidden="true"}[Section titled
"Prerequisites"]{.sr-only}](#prerequisites){.sl-anchor-link}
:::

Before you start, ensure you have Gemini CLI installed and a basic
understanding of Node.js.

::: {.sl-heading-wrapper .level-h2}
## Extension features

[[![](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iY3VycmVudGNvbG9yIiBkPSJtMTIuMTEgMTUuMzktMy44OCAzLjg4YTIuNTIgMi41MiAwIDAgMS0zLjUgMCAyLjQ3IDIuNDcgMCAwIDEgMC0zLjVsMy44OC0zLjg4YTEgMSAwIDAgMC0xLjQyLTEuNDJsLTMuODggMy44OWE0LjQ4IDQuNDggMCAwIDAgNi4zMyA2LjMzbDMuODktMy44OGExIDEgMCAxIDAtMS40Mi0xLjQyWm04LjU4LTEyLjA4YTQuNDkgNC40OSAwIDAgMC02LjMzIDBsLTMuODkgMy44OGExIDEgMCAwIDAgMS40MiAxLjQybDMuODgtMy44OGEyLjUyIDIuNTIgMCAwIDEgMy41IDAgMi40NyAyLjQ3IDAgMCAxIDAgMy41bC0zLjg4IDMuODhhMSAxIDAgMSAwIDEuNDIgMS40MmwzLjg4LTMuODlhNC40OSA0LjQ5IDAgMCAwIDAtNi4zM1pNOC44MyAxNS4xN2ExIDEgMCAwIDAgMS4xLjIyIDEgMSAwIDAgMCAuMzItLjIybDQuOTItNC45MmExIDEgMCAwIDAtMS40Mi0xLjQybC00LjkyIDQuOTJhMSAxIDAgMCAwIDAgMS40MloiPjwvcGF0aD48L3N2Zz4=)]{.sl-anchor-icon
aria-hidden="true"}[Section titled "Extension
features"]{.sr-only}](#extension-features){.sl-anchor-link}
:::

Extensions offer several ways to customize Gemini CLI. Use this table to
decide which features your extension needs.

  Feature                                                                                    What it is                                                                                                                  When to use it                                                                                                                                                                                                                                                                                   Invoked by
  ------------------------------------------------------------------------------------------ --------------------------------------------------------------------------------------------------------------------------- ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ -----------------------
  **[MCP server](/docs/extensions/reference#mcp-servers)**                                   A standard way to expose new tools and data sources to the model.                                                           Use this when you want the model to be able to *do* new things, like fetching data from an internal API, querying a database, or controlling a local application. We also support MCP resources (which can replace custom commands) and system instructions (which can replace custom context)   Model
  **[Custom commands](/docs/cli/custom-commands)**                                           A shortcut (like `/my-cmd`{dir="auto"}) that executes a pre-defined prompt or shell command.                                Use this for repetitive tasks or to save long, complex prompts that you use frequently. Great for automation.                                                                                                                                                                                    User
  **[Context file (`GEMINI.md`{dir="auto"})](/docs/extensions/reference#contextfilename)**   A markdown file containing instructions that are loaded into the model's context at the start of every session.             Use this to define the "personality" of your extension, set coding standards, or provide essential knowledge that the model should always have.                                                                                                                                                  CLI provides to model
  **[Agent skills](/docs/cli/skills)**                                                       A specialized set of instructions and workflows that the model activates only when needed.                                  Use this for complex, occasional tasks (like "create a PR" or "audit security") to avoid cluttering the main context window when the skill isn't being used.                                                                                                                                     Model
  **[Hooks](/docs/hooks)**                                                                   A way to intercept and customize the CLI's behavior at specific lifecycle events (for example, before/after a tool call).   Use this when you want to automate actions based on what the model is doing, like validating tool arguments, logging activity, or modifying the model's input/output.                                                                                                                            CLI
  **[Custom themes](/docs/extensions/reference#themes)**                                     A set of color definitions to personalize the CLI UI.                                                                       Use this to provide a unique visual identity for your extension or to offer specialized high-contrast or thematic color schemes.                                                                                                                                                                 User (via /theme)

::: {.sl-heading-wrapper .level-h2}
## Step 1: Create a new extension

[[![](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iY3VycmVudGNvbG9yIiBkPSJtMTIuMTEgMTUuMzktMy44OCAzLjg4YTIuNTIgMi41MiAwIDAgMS0zLjUgMCAyLjQ3IDIuNDcgMCAwIDEgMC0zLjVsMy44OC0zLjg4YTEgMSAwIDAgMC0xLjQyLTEuNDJsLTMuODggMy44OWE0LjQ4IDQuNDggMCAwIDAgNi4zMyA2LjMzbDMuODktMy44OGExIDEgMCAxIDAtMS40Mi0xLjQyWm04LjU4LTEyLjA4YTQuNDkgNC40OSAwIDAgMC02LjMzIDBsLTMuODkgMy44OGExIDEgMCAwIDAgMS40MiAxLjQybDMuODgtMy44OGEyLjUyIDIuNTIgMCAwIDEgMy41IDAgMi40NyAyLjQ3IDAgMCAxIDAgMy41bC0zLjg4IDMuODhhMSAxIDAgMSAwIDEuNDIgMS40MmwzLjg4LTMuODlhNC40OSA0LjQ5IDAgMCAwIDAtNi4zM1pNOC44MyAxNS4xN2ExIDEgMCAwIDAgMS4xLjIyIDEgMSAwIDAgMCAuMzItLjIybDQuOTItNC45MmExIDEgMCAwIDAtMS40Mi0xLjQybC00LjkyIDQuOTJhMSAxIDAgMCAwIDAgMS40MloiPjwvcGF0aD48L3N2Zz4=)]{.sl-anchor-icon
aria-hidden="true"}[Section titled "Step 1: Create a new
extension"]{.sr-only}](#step-1-create-a-new-extension){.sl-anchor-link}
:::

The easiest way to start is by using a built-in template. We'll use the
`mcp-server`{dir="auto"} example as our foundation.

Run the following command to create a new directory called
`my-first-extension`{dir="auto"} with the template files:

::: expressive-code
<figure class="frame is-terminal not-content">
<pre data-language="bash"><code>gemini extensions new my-first-extension mcp-server</code></pre>
<div class="copy">
<div>

</div>
</div>
<figcaption><span class="title"></span><span class="sr-only">Terminal
window</span></figcaption>
</figure>
:::

This creates a directory with the following structure:

::: expressive-code
<figure class="frame not-content">
<pre data-language="plaintext"><code>my-first-extension/├── example.js├── gemini-extension.json└── package.json</code></pre>
<div class="copy">
<div>

</div>
</div>
</figure>
:::

::: {.sl-heading-wrapper .level-h2}
## Step 2: Understand the extension files

[[![](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iY3VycmVudGNvbG9yIiBkPSJtMTIuMTEgMTUuMzktMy44OCAzLjg4YTIuNTIgMi41MiAwIDAgMS0zLjUgMCAyLjQ3IDIuNDcgMCAwIDEgMC0zLjVsMy44OC0zLjg4YTEgMSAwIDAgMC0xLjQyLTEuNDJsLTMuODggMy44OWE0LjQ4IDQuNDggMCAwIDAgNi4zMyA2LjMzbDMuODktMy44OGExIDEgMCAxIDAtMS40Mi0xLjQyWm04LjU4LTEyLjA4YTQuNDkgNC40OSAwIDAgMC02LjMzIDBsLTMuODkgMy44OGExIDEgMCAwIDAgMS40MiAxLjQybDMuODgtMy44OGEyLjUyIDIuNTIgMCAwIDEgMy41IDAgMi40NyAyLjQ3IDAgMCAxIDAgMy41bC0zLjg4IDMuODhhMSAxIDAgMSAwIDEuNDIgMS40MmwzLjg4LTMuODlhNC40OSA0LjQ5IDAgMCAwIDAtNi4zM1pNOC44MyAxNS4xN2ExIDEgMCAwIDAgMS4xLjIyIDEgMSAwIDAgMCAuMzItLjIybDQuOTItNC45MmExIDEgMCAwIDAtMS40Mi0xLjQybC00LjkyIDQuOTJhMSAxIDAgMCAwIDAgMS40MloiPjwvcGF0aD48L3N2Zz4=)]{.sl-anchor-icon
aria-hidden="true"}[Section titled "Step 2: Understand the extension
files"]{.sr-only}](#step-2-understand-the-extension-files){.sl-anchor-link}
:::

Your new extension contains several key files that define its behavior.

::: {.sl-heading-wrapper .level-h3}
### `gemini-extension.json`{dir="auto"} {#gemini-extensionjson}

[[![](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iY3VycmVudGNvbG9yIiBkPSJtMTIuMTEgMTUuMzktMy44OCAzLjg4YTIuNTIgMi41MiAwIDAgMS0zLjUgMCAyLjQ3IDIuNDcgMCAwIDEgMC0zLjVsMy44OC0zLjg4YTEgMSAwIDAgMC0xLjQyLTEuNDJsLTMuODggMy44OWE0LjQ4IDQuNDggMCAwIDAgNi4zMyA2LjMzbDMuODktMy44OGExIDEgMCAxIDAtMS40Mi0xLjQyWm04LjU4LTEyLjA4YTQuNDkgNC40OSAwIDAgMC02LjMzIDBsLTMuODkgMy44OGExIDEgMCAwIDAgMS40MiAxLjQybDMuODgtMy44OGEyLjUyIDIuNTIgMCAwIDEgMy41IDAgMi40NyAyLjQ3IDAgMCAxIDAgMy41bC0zLjg4IDMuODhhMSAxIDAgMSAwIDEuNDIgMS40MmwzLjg4LTMuODlhNC40OSA0LjQ5IDAgMCAwIDAtNi4zM1pNOC44MyAxNS4xN2ExIDEgMCAwIDAgMS4xLjIyIDEgMSAwIDAgMCAuMzItLjIybDQuOTItNC45MmExIDEgMCAwIDAtMS40Mi0xLjQybC00LjkyIDQuOTJhMSAxIDAgMCAwIDAgMS40MloiPjwvcGF0aD48L3N2Zz4=)]{.sl-anchor-icon
aria-hidden="true"}[Section titled
"gemini-extension.json"]{.sr-only}](#gemini-extensionjson){.sl-anchor-link}
:::

The manifest file tells Gemini CLI how to load and use your extension.

::: expressive-code
<figure class="frame not-content">
<pre data-language="json"><code>{  &quot;name&quot;: &quot;mcp-server-example&quot;,  &quot;version&quot;: &quot;1.0.0&quot;,  &quot;mcpServers&quot;: {    &quot;nodeServer&quot;: {      &quot;command&quot;: &quot;node&quot;,      &quot;args&quot;: [&quot;${extensionPath}${/}example.js&quot;],      &quot;cwd&quot;: &quot;${extensionPath}&quot;    }  }}</code></pre>
<div class="copy">
<div>

</div>
</div>
</figure>
:::

-   `name`{dir="auto"}: The unique name for your extension.
-   `version`{dir="auto"}: The version of your extension.
-   `mcpServers`{dir="auto"}: Defines Model Context Protocol (MCP)
    servers to add new tools.
    -   `command`{dir="auto"}, `args`{dir="auto"}, `cwd`{dir="auto"}:
        Specify how to start your server. The
        `${extensionPath}`{dir="auto"} variable is replaced with the
        absolute path to your extension's directory.

::: {.sl-heading-wrapper .level-h3}
### `example.js`{dir="auto"} {#examplejs}

[[![](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iY3VycmVudGNvbG9yIiBkPSJtMTIuMTEgMTUuMzktMy44OCAzLjg4YTIuNTIgMi41MiAwIDAgMS0zLjUgMCAyLjQ3IDIuNDcgMCAwIDEgMC0zLjVsMy44OC0zLjg4YTEgMSAwIDAgMC0xLjQyLTEuNDJsLTMuODggMy44OWE0LjQ4IDQuNDggMCAwIDAgNi4zMyA2LjMzbDMuODktMy44OGExIDEgMCAxIDAtMS40Mi0xLjQyWm04LjU4LTEyLjA4YTQuNDkgNC40OSAwIDAgMC02LjMzIDBsLTMuODkgMy44OGExIDEgMCAwIDAgMS40MiAxLjQybDMuODgtMy44OGEyLjUyIDIuNTIgMCAwIDEgMy41IDAgMi40NyAyLjQ3IDAgMCAxIDAgMy41bC0zLjg4IDMuODhhMSAxIDAgMSAwIDEuNDIgMS40MmwzLjg4LTMuODlhNC40OSA0LjQ5IDAgMCAwIDAtNi4zM1pNOC44MyAxNS4xN2ExIDEgMCAwIDAgMS4xLjIyIDEgMSAwIDAgMCAuMzItLjIybDQuOTItNC45MmExIDEgMCAwIDAtMS40Mi0xLjQybC00LjkyIDQuOTJhMSAxIDAgMCAwIDAgMS40MloiPjwvcGF0aD48L3N2Zz4=)]{.sl-anchor-icon
aria-hidden="true"}[Section titled
"example.js"]{.sr-only}](#examplejs){.sl-anchor-link}
:::

This file contains the source code for your MCP server. It uses the
`@modelcontextprotocol/sdk`{dir="auto"} to define tools.

::: expressive-code
<figure class="frame not-content">
<pre data-language="javascript"><code>/** * @license * Copyright 2025 Google LLC * SPDX-License-Identifier: Apache-2.0 */
import { McpServer } from &#39;@modelcontextprotocol/sdk/server/mcp.js&#39;;import { StdioServerTransport } from &#39;@modelcontextprotocol/sdk/server/stdio.js&#39;;import { z } from &#39;zod&#39;;
const server = new McpServer({  name: &#39;prompt-server&#39;,  version: &#39;1.0.0&#39;,});
// Registers a new tool named &#39;fetch_posts&#39;server.registerTool(  &#39;fetch_posts&#39;,  {    description: &#39;Fetches a list of posts from a public API.&#39;,    inputSchema: z.object({}).shape,  },  async () =&gt; {    const apiResponse = await fetch(      &#39;https://jsonplaceholder.typicode.com/posts&#39;,    );    const posts = await apiResponse.json();    const response = { posts: posts.slice(0, 5) };    return {      content: [        {          type: &#39;text&#39;,          text: JSON.stringify(response),        },      ],    };  },);
const transport = new StdioServerTransport();await server.connect(transport);</code></pre>
<div class="copy">
<div>

</div>
</div>
</figure>
:::

::: {.sl-heading-wrapper .level-h3}
### `package.json`{dir="auto"} {#packagejson}

[[![](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iY3VycmVudGNvbG9yIiBkPSJtMTIuMTEgMTUuMzktMy44OCAzLjg4YTIuNTIgMi41MiAwIDAgMS0zLjUgMCAyLjQ3IDIuNDcgMCAwIDEgMC0zLjVsMy44OC0zLjg4YTEgMSAwIDAgMC0xLjQyLTEuNDJsLTMuODggMy44OWE0LjQ4IDQuNDggMCAwIDAgNi4zMyA2LjMzbDMuODktMy44OGExIDEgMCAxIDAtMS40Mi0xLjQyWm04LjU4LTEyLjA4YTQuNDkgNC40OSAwIDAgMC02LjMzIDBsLTMuODkgMy44OGExIDEgMCAwIDAgMS40MiAxLjQybDMuODgtMy44OGEyLjUyIDIuNTIgMCAwIDEgMy41IDAgMi40NyAyLjQ3IDAgMCAxIDAgMy41bC0zLjg4IDMuODhhMSAxIDAgMSAwIDEuNDIgMS40MmwzLjg4LTMuODlhNC40OSA0LjQ5IDAgMCAwIDAtNi4zM1pNOC44MyAxNS4xN2ExIDEgMCAwIDAgMS4xLjIyIDEgMSAwIDAgMCAuMzItLjIybDQuOTItNC45MmExIDEgMCAwIDAtMS40Mi0xLjQybC00LjkyIDQuOTJhMSAxIDAgMCAwIDAgMS40MloiPjwvcGF0aD48L3N2Zz4=)]{.sl-anchor-icon
aria-hidden="true"}[Section titled
"package.json"]{.sr-only}](#packagejson){.sl-anchor-link}
:::

The standard configuration file for a Node.js project. It defines
dependencies and scripts for your extension.

::: {.sl-heading-wrapper .level-h2}
## Step 3: Add extension settings

[[![](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iY3VycmVudGNvbG9yIiBkPSJtMTIuMTEgMTUuMzktMy44OCAzLjg4YTIuNTIgMi41MiAwIDAgMS0zLjUgMCAyLjQ3IDIuNDcgMCAwIDEgMC0zLjVsMy44OC0zLjg4YTEgMSAwIDAgMC0xLjQyLTEuNDJsLTMuODggMy44OWE0LjQ4IDQuNDggMCAwIDAgNi4zMyA2LjMzbDMuODktMy44OGExIDEgMCAxIDAtMS40Mi0xLjQyWm04LjU4LTEyLjA4YTQuNDkgNC40OSAwIDAgMC02LjMzIDBsLTMuODkgMy44OGExIDEgMCAwIDAgMS40MiAxLjQybDMuODgtMy44OGEyLjUyIDIuNTIgMCAwIDEgMy41IDAgMi40NyAyLjQ3IDAgMCAxIDAgMy41bC0zLjg4IDMuODhhMSAxIDAgMSAwIDEuNDIgMS40MmwzLjg4LTMuODlhNC40OSA0LjQ5IDAgMCAwIDAtNi4zM1pNOC44MyAxNS4xN2ExIDEgMCAwIDAgMS4xLjIyIDEgMSAwIDAgMCAuMzItLjIybDQuOTItNC45MmExIDEgMCAwIDAtMS40Mi0xLjQybC00LjkyIDQuOTJhMSAxIDAgMCAwIDAgMS40MloiPjwvcGF0aD48L3N2Zz4=)]{.sl-anchor-icon
aria-hidden="true"}[Section titled "Step 3: Add extension
settings"]{.sr-only}](#step-3-add-extension-settings){.sl-anchor-link}
:::

Some extensions need configuration, such as API keys or user
preferences. Let's add a setting for an API key.

1.  Open `gemini-extension.json`{dir="auto"}.

2.  Add a `settings`{dir="auto"} array to the configuration:

    ::: expressive-code
    <figure class="frame not-content">
    <pre data-language="json"><code>{  &quot;name&quot;: &quot;mcp-server-example&quot;,  &quot;version&quot;: &quot;1.0.0&quot;,  &quot;settings&quot;: [    {      &quot;name&quot;: &quot;API Key&quot;,      &quot;description&quot;: &quot;The API key for the service.&quot;,      &quot;envVar&quot;: &quot;MY_SERVICE_API_KEY&quot;,      &quot;sensitive&quot;: true    }  ],  &quot;mcpServers&quot;: {    // ...  }}</code></pre>
    <div class="copy">
    <div>

    </div>
    </div>
    </figure>
    :::

When a user installs this extension, Gemini CLI will prompt them to
enter the "API Key". The value will be stored securely in the system
keychain (because `sensitive`{dir="auto"} is true) and injected into the
MCP server's process as the `MY_SERVICE_API_KEY`{dir="auto"} environment
variable.

::: {.sl-heading-wrapper .level-h2}
## Step 4: Link your extension

[[![](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iY3VycmVudGNvbG9yIiBkPSJtMTIuMTEgMTUuMzktMy44OCAzLjg4YTIuNTIgMi41MiAwIDAgMS0zLjUgMCAyLjQ3IDIuNDcgMCAwIDEgMC0zLjVsMy44OC0zLjg4YTEgMSAwIDAgMC0xLjQyLTEuNDJsLTMuODggMy44OWE0LjQ4IDQuNDggMCAwIDAgNi4zMyA2LjMzbDMuODktMy44OGExIDEgMCAxIDAtMS40Mi0xLjQyWm04LjU4LTEyLjA4YTQuNDkgNC40OSAwIDAgMC02LjMzIDBsLTMuODkgMy44OGExIDEgMCAwIDAgMS40MiAxLjQybDMuODgtMy44OGEyLjUyIDIuNTIgMCAwIDEgMy41IDAgMi40NyAyLjQ3IDAgMCAxIDAgMy41bC0zLjg4IDMuODhhMSAxIDAgMSAwIDEuNDIgMS40MmwzLjg4LTMuODlhNC40OSA0LjQ5IDAgMCAwIDAtNi4zM1pNOC44MyAxNS4xN2ExIDEgMCAwIDAgMS4xLjIyIDEgMSAwIDAgMCAuMzItLjIybDQuOTItNC45MmExIDEgMCAwIDAtMS40Mi0xLjQybC00LjkyIDQuOTJhMSAxIDAgMCAwIDAgMS40MloiPjwvcGF0aD48L3N2Zz4=)]{.sl-anchor-icon
aria-hidden="true"}[Section titled "Step 4: Link your
extension"]{.sr-only}](#step-4-link-your-extension){.sl-anchor-link}
:::

Link your extension to your Gemini CLI installation for local
development.

1.  **Install dependencies:**

    ::: expressive-code
    <figure class="frame is-terminal not-content">
    <pre data-language="bash"><code>cd my-first-extensionnpm install</code></pre>
    <div class="copy">
    <div>

    </div>
    </div>
    <figcaption><span class="title"></span><span class="sr-only">Terminal
    window</span></figcaption>
    </figure>
    :::

2.  **Link the extension:**

    The `link`{dir="auto"} command creates a symbolic link from Gemini
    CLI extensions directory to your development directory. Changes you
    make are reflected immediately.

    ::: expressive-code
    <figure class="frame is-terminal not-content">
    <pre data-language="bash"><code>gemini extensions link .</code></pre>
    <div class="copy">
    <div>

    </div>
    </div>
    <figcaption><span class="title"></span><span class="sr-only">Terminal
    window</span></figcaption>
    </figure>
    :::

Restart your Gemini CLI session to use the new `fetch_posts`{dir="auto"}
tool. Test it by asking: "fetch posts".

::: {.sl-heading-wrapper .level-h2}
## Step 5: Add a custom command

[[![](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iY3VycmVudGNvbG9yIiBkPSJtMTIuMTEgMTUuMzktMy44OCAzLjg4YTIuNTIgMi41MiAwIDAgMS0zLjUgMCAyLjQ3IDIuNDcgMCAwIDEgMC0zLjVsMy44OC0zLjg4YTEgMSAwIDAgMC0xLjQyLTEuNDJsLTMuODggMy44OWE0LjQ4IDQuNDggMCAwIDAgNi4zMyA2LjMzbDMuODktMy44OGExIDEgMCAxIDAtMS40Mi0xLjQyWm04LjU4LTEyLjA4YTQuNDkgNC40OSAwIDAgMC02LjMzIDBsLTMuODkgMy44OGExIDEgMCAwIDAgMS40MiAxLjQybDMuODgtMy44OGEyLjUyIDIuNTIgMCAwIDEgMy41IDAgMi40NyAyLjQ3IDAgMCAxIDAgMy41bC0zLjg4IDMuODhhMSAxIDAgMSAwIDEuNDIgMS40MmwzLjg4LTMuODlhNC40OSA0LjQ5IDAgMCAwIDAtNi4zM1pNOC44MyAxNS4xN2ExIDEgMCAwIDAgMS4xLjIyIDEgMSAwIDAgMCAuMzItLjIybDQuOTItNC45MmExIDEgMCAwIDAtMS40Mi0xLjQybC00LjkyIDQuOTJhMSAxIDAgMCAwIDAgMS40MloiPjwvcGF0aD48L3N2Zz4=)]{.sl-anchor-icon
aria-hidden="true"}[Section titled "Step 5: Add a custom
command"]{.sr-only}](#step-5-add-a-custom-command){.sl-anchor-link}
:::

Custom commands create shortcuts for complex prompts.

1.  Create a `commands`{dir="auto"} directory and a subdirectory for
    your command group:

    **macOS/Linux**

    ::: expressive-code
    <figure class="frame is-terminal not-content">
    <pre data-language="bash"><code>mkdir -p commands/fs</code></pre>
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
    <pre data-language="powershell"><code>New-Item -ItemType Directory -Force -Path &quot;commands\fs&quot;</code></pre>
    <div class="copy">
    <div>

    </div>
    </div>
    <figcaption><span class="title"></span><span class="sr-only">Terminal
    window</span></figcaption>
    </figure>
    :::

2.  Create a file named `commands/fs/grep-code.toml`{dir="auto"}:

    ::: expressive-code
    <figure class="frame not-content">
    <pre data-language="toml"><code>prompt = &quot;&quot;&quot;Please summarize the findings for the pattern `{{args}}`.
    Search Results:!{grep -r {{args}} .}&quot;&quot;&quot;</code></pre>
    <div class="copy">
    <div>

    </div>
    </div>
    </figure>
    :::

    This command, `/fs:grep-code`{dir="auto"}, takes an argument, runs
    the `grep`{dir="auto"} shell command, and pipes the results into a
    prompt for summarization.

After saving the file, restart Gemini CLI. Run
`/fs:grep-code "some pattern"`{dir="auto"} to use your new command.

::: {.sl-heading-wrapper .level-h2}
## Step 6: Add a custom `GEMINI.md`{dir="auto"} {#step-6-add-a-custom-geminimd}

[[![](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iY3VycmVudGNvbG9yIiBkPSJtMTIuMTEgMTUuMzktMy44OCAzLjg4YTIuNTIgMi41MiAwIDAgMS0zLjUgMCAyLjQ3IDIuNDcgMCAwIDEgMC0zLjVsMy44OC0zLjg4YTEgMSAwIDAgMC0xLjQyLTEuNDJsLTMuODggMy44OWE0LjQ4IDQuNDggMCAwIDAgNi4zMyA2LjMzbDMuODktMy44OGExIDEgMCAxIDAtMS40Mi0xLjQyWm04LjU4LTEyLjA4YTQuNDkgNC40OSAwIDAgMC02LjMzIDBsLTMuODkgMy44OGExIDEgMCAwIDAgMS40MiAxLjQybDMuODgtMy44OGEyLjUyIDIuNTIgMCAwIDEgMy41IDAgMi40NyAyLjQ3IDAgMCAxIDAgMy41bC0zLjg4IDMuODhhMSAxIDAgMSAwIDEuNDIgMS40MmwzLjg4LTMuODlhNC40OSA0LjQ5IDAgMCAwIDAtNi4zM1pNOC44MyAxNS4xN2ExIDEgMCAwIDAgMS4xLjIyIDEgMSAwIDAgMCAuMzItLjIybDQuOTItNC45MmExIDEgMCAwIDAtMS40Mi0xLjQybC00LjkyIDQuOTJhMSAxIDAgMCAwIDAgMS40MloiPjwvcGF0aD48L3N2Zz4=)]{.sl-anchor-icon
aria-hidden="true"}[Section titled "Step 6: Add a custom
GEMINI.md"]{.sr-only}](#step-6-add-a-custom-geminimd){.sl-anchor-link}
:::

Provide persistent context to the model by adding a
`GEMINI.md`{dir="auto"} file to your extension. This is useful for
setting behavior or providing essential tool information.

1.  Create a file named `GEMINI.md`{dir="auto"} in the root of your
    extension directory:

    ::: expressive-code
    <figure class="frame not-content">
    <pre data-language="markdown"><code># My First Extension Instructions
    You are an expert developer assistant. When the user asks you to fetchposts, use the `fetch_posts` tool. Be concise in your responses.</code></pre>
    <div class="copy">
    <div>

    </div>
    </div>
    </figure>
    :::

2.  Update your `gemini-extension.json`{dir="auto"} to load this file:

    ::: expressive-code
    <figure class="frame not-content">
    <pre data-language="json"><code>{  &quot;name&quot;: &quot;my-first-extension&quot;,  &quot;version&quot;: &quot;1.0.0&quot;,  &quot;contextFileName&quot;: &quot;GEMINI.md&quot;,  &quot;mcpServers&quot;: {    &quot;nodeServer&quot;: {      &quot;command&quot;: &quot;node&quot;,      &quot;args&quot;: [&quot;${extensionPath}${/}example.js&quot;],      &quot;cwd&quot;: &quot;${extensionPath}&quot;    }  }}</code></pre>
    <div class="copy">
    <div>

    </div>
    </div>
    </figure>
    :::

Restart Gemini CLI. The model now has the context from your
`GEMINI.md`{dir="auto"} file in every session where the extension is
active.

::: {.sl-heading-wrapper .level-h2}
## (Optional) Step 7: Add an Agent Skill

[[![](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iY3VycmVudGNvbG9yIiBkPSJtMTIuMTEgMTUuMzktMy44OCAzLjg4YTIuNTIgMi41MiAwIDAgMS0zLjUgMCAyLjQ3IDIuNDcgMCAwIDEgMC0zLjVsMy44OC0zLjg4YTEgMSAwIDAgMC0xLjQyLTEuNDJsLTMuODggMy44OWE0LjQ4IDQuNDggMCAwIDAgNi4zMyA2LjMzbDMuODktMy44OGExIDEgMCAxIDAtMS40Mi0xLjQyWm04LjU4LTEyLjA4YTQuNDkgNC40OSAwIDAgMC02LjMzIDBsLTMuODkgMy44OGExIDEgMCAwIDAgMS40MiAxLjQybDMuODgtMy44OGEyLjUyIDIuNTIgMCAwIDEgMy41IDAgMi40NyAyLjQ3IDAgMCAxIDAgMy41bC0zLjg4IDMuODhhMSAxIDAgMSAwIDEuNDIgMS40MmwzLjg4LTMuODlhNC40OSA0LjQ5IDAgMCAwIDAtNi4zM1pNOC44MyAxNS4xN2ExIDEgMCAwIDAgMS4xLjIyIDEgMSAwIDAgMCAuMzItLjIybDQuOTItNC45MmExIDEgMCAwIDAtMS40Mi0xLjQybC00LjkyIDQuOTJhMSAxIDAgMCAwIDAgMS40MloiPjwvcGF0aD48L3N2Zz4=)]{.sl-anchor-icon
aria-hidden="true"}[Section titled "(Optional) Step 7: Add an Agent
Skill"]{.sr-only}](#optional-step-7-add-an-agent-skill){.sl-anchor-link}
:::

[Agent Skills](/docs/cli/skills) bundle specialized expertise and
workflows. Skills are activated only when needed, which saves context
tokens.

1.  Create a `skills`{dir="auto"} directory and a subdirectory for your
    skill:

    **macOS/Linux**

    ::: expressive-code
    <figure class="frame is-terminal not-content">
    <pre data-language="bash"><code>mkdir -p skills/security-audit</code></pre>
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
    <pre data-language="powershell"><code>New-Item -ItemType Directory -Force -Path &quot;skills\security-audit&quot;</code></pre>
    <div class="copy">
    <div>

    </div>
    </div>
    <figcaption><span class="title"></span><span class="sr-only">Terminal
    window</span></figcaption>
    </figure>
    :::

2.  Create a `skills/security-audit/SKILL.md`{dir="auto"} file:

    ::: expressive-code
    <figure class="frame not-content">
    <pre data-language="markdown"><code>---name: security-auditdescription:  Expertise in auditing code for security vulnerabilities. Use when the user  asks to &quot;check for security issues&quot; or &quot;audit&quot; their changes.---
    # Security Auditor
    You are an expert security researcher. When auditing code:
    1. Look for common vulnerabilities (OWASP Top 10).2. Check for hardcoded secrets or API keys.3. Suggest remediation steps for any findings.</code></pre>
    <div class="copy">
    <div>

    </div>
    </div>
    </figure>
    :::

Gemini CLI automatically discovers skills bundled with your extension.
The model activates them when it identifies a relevant task.

::: {.sl-heading-wrapper .level-h2}
## Step 8: Release your extension

[[![](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iY3VycmVudGNvbG9yIiBkPSJtMTIuMTEgMTUuMzktMy44OCAzLjg4YTIuNTIgMi41MiAwIDAgMS0zLjUgMCAyLjQ3IDIuNDcgMCAwIDEgMC0zLjVsMy44OC0zLjg4YTEgMSAwIDAgMC0xLjQyLTEuNDJsLTMuODggMy44OWE0LjQ4IDQuNDggMCAwIDAgNi4zMyA2LjMzbDMuODktMy44OGExIDEgMCAxIDAtMS40Mi0xLjQyWm04LjU4LTEyLjA4YTQuNDkgNC40OSAwIDAgMC02LjMzIDBsLTMuODkgMy44OGExIDEgMCAwIDAgMS40MiAxLjQybDMuODgtMy44OGEyLjUyIDIuNTIgMCAwIDEgMy41IDAgMi40NyAyLjQ3IDAgMCAxIDAgMy41bC0zLjg4IDMuODhhMSAxIDAgMSAwIDEuNDIgMS40MmwzLjg4LTMuODlhNC40OSA0LjQ5IDAgMCAwIDAtNi4zM1pNOC44MyAxNS4xN2ExIDEgMCAwIDAgMS4xLjIyIDEgMSAwIDAgMCAuMzItLjIybDQuOTItNC45MmExIDEgMCAwIDAtMS40Mi0xLjQybC00LjkyIDQuOTJhMSAxIDAgMCAwIDAgMS40MloiPjwvcGF0aD48L3N2Zz4=)]{.sl-anchor-icon
aria-hidden="true"}[Section titled "Step 8: Release your
extension"]{.sr-only}](#step-8-release-your-extension){.sl-anchor-link}
:::

When your extension is ready, share it with others via a Git repository
or GitHub Releases. Refer to the [Extension Releasing
Guide](/docs/extensions/releasing) for detailed instructions and learn
how to list your extension in the gallery.

::: {.sl-heading-wrapper .level-h2}
## Next steps

[[![](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iY3VycmVudGNvbG9yIiBkPSJtMTIuMTEgMTUuMzktMy44OCAzLjg4YTIuNTIgMi41MiAwIDAgMS0zLjUgMCAyLjQ3IDIuNDcgMCAwIDEgMC0zLjVsMy44OC0zLjg4YTEgMSAwIDAgMC0xLjQyLTEuNDJsLTMuODggMy44OWE0LjQ4IDQuNDggMCAwIDAgNi4zMyA2LjMzbDMuODktMy44OGExIDEgMCAxIDAtMS40Mi0xLjQyWm04LjU4LTEyLjA4YTQuNDkgNC40OSAwIDAgMC02LjMzIDBsLTMuODkgMy44OGExIDEgMCAwIDAgMS40MiAxLjQybDMuODgtMy44OGEyLjUyIDIuNTIgMCAwIDEgMy41IDAgMi40NyAyLjQ3IDAgMCAxIDAgMy41bC0zLjg4IDMuODhhMSAxIDAgMSAwIDEuNDIgMS40MmwzLjg4LTMuODlhNC40OSA0LjQ5IDAgMCAwIDAtNi4zM1pNOC44MyAxNS4xN2ExIDEgMCAwIDAgMS4xLjIyIDEgMSAwIDAgMCAuMzItLjIybDQuOTItNC45MmExIDEgMCAwIDAtMS40Mi0xLjQybC00LjkyIDQuOTJhMSAxIDAgMCAwIDAgMS40MloiPjwvcGF0aD48L3N2Zz4=)]{.sl-anchor-icon
aria-hidden="true"}[Section titled "Next
steps"]{.sr-only}](#next-steps){.sl-anchor-link}
:::

-   [Extension reference](/docs/extensions/reference): Deeply understand
    the extension format, commands, and configuration.
-   [Best practices](/docs/extensions/best-practices): Learn strategies
    for building great extensions.
:::

::: {.starlight-footer .astro-nixdnp5i}
::: {.last-updated .astro-asuirehi}
![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgd2lkdGg9IjE2IiBoZWlnaHQ9IjE2IiB2aWV3Ym94PSIwIDAgMjQgMjQiIGZpbGw9ImN1cnJlbnRDb2xvciIgY2xhc3M9ImNhbGVuZGFyLWljb24gYXN0cm8tYXN1aXJlaGkiPjxwYXRoIGQ9Ik0xOSA0aC0xVjJoLTJ2Mkg4VjJINnYySDVjLTEuMTEgMC0xLjk5LjktMS45OSAyTDMgMjBhMiAyIDAgMCAwIDIgMmgxNGMxLjEgMCAyLS45IDItMlY2YzAtMS4xLS45LTItMi0yem0wIDE2SDVWMTBoMTR2MTB6bTAtMTJINVY2aDE0djJ6bS03IDVoNXY1aC01di01eiIgY2xhc3M9ImFzdHJvLWFzdWlyZWhpIj48L3BhdGg+PC9zdmc+){.calendar-icon
.astro-asuirehi}[Last updated: Apr 10, 2026]{.astro-asuirehi}
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
