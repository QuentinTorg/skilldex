# gemini_extensions_reference.md [DISTILLED]

**Source:** https://geminicli.com/docs/extensions/reference/

**Summary:** Technical reference for the `gemini-extension.json` manifest format and the `gemini extensions` CLI commands. Included in [Skill Packaging and Distribution](../topics/skill-packaging-and-distribution.md) and [Extension Architectures](../topics/extension-architectures.md).

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
.astro-3ef6ksr2}](https://github.com/google-gemini/gemini-cli/issues/new?template=website_issue.yml&url=https%3A%2F%2Fgeminicli.com%2Fdocs%2Fextensions%2Freference%2F){.feedback-link
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
                aria-current="false"}
            -   [[Developer guide: Best
                practices]{.astro-3ii7xxms}](/docs/extensions/best-practices/){.astro-3ii7xxms
                aria-current="false"}
            -   [[Developer guide:
                Releasing]{.astro-3ii7xxms}](/docs/extensions/releasing/){.astro-3ii7xxms
                aria-current="false"}
            -   [[Developer guide:
                Reference]{.astro-3ii7xxms}](/docs/extensions/reference/){.astro-3ii7xxms
                aria-current="page"}
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
            aria-current="false"}
        -   [[Developer guide: Best
            practices]{.astro-3ii7xxms}](/docs/extensions/best-practices/){.astro-3ii7xxms
            aria-current="false"}
        -   [[Developer guide:
            Releasing]{.astro-3ii7xxms}](/docs/extensions/releasing/){.astro-3ii7xxms
            aria-current="false"}
        -   [[Developer guide:
            Reference]{.astro-3ii7xxms}](/docs/extensions/reference/){.astro-3ii7xxms
            aria-current="page"}
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
-   [[Manage extensions]{.astro-g2bywc46
    style="--depth: 0;"}](#manage-extensions){.astro-g2bywc46
    style="--depth: 0;"}
    -   [[Install an extension]{.astro-g2bywc46
        style="--depth: 1;"}](#install-an-extension){.astro-g2bywc46
        style="--depth: 1;"}
    -   [[Uninstall an extension]{.astro-g2bywc46
        style="--depth: 1;"}](#uninstall-an-extension){.astro-g2bywc46
        style="--depth: 1;"}
    -   [[Disable an extension]{.astro-g2bywc46
        style="--depth: 1;"}](#disable-an-extension){.astro-g2bywc46
        style="--depth: 1;"}
    -   [[Enable an extension]{.astro-g2bywc46
        style="--depth: 1;"}](#enable-an-extension){.astro-g2bywc46
        style="--depth: 1;"}
    -   [[Update an extension]{.astro-g2bywc46
        style="--depth: 1;"}](#update-an-extension){.astro-g2bywc46
        style="--depth: 1;"}
    -   [[Create an extension from a template]{.astro-g2bywc46
        style="--depth: 1;"}](#create-an-extension-from-a-template){.astro-g2bywc46
        style="--depth: 1;"}
    -   [[Link a local extension]{.astro-g2bywc46
        style="--depth: 1;"}](#link-a-local-extension){.astro-g2bywc46
        style="--depth: 1;"}
-   [[Extension format]{.astro-g2bywc46
    style="--depth: 0;"}](#extension-format){.astro-g2bywc46
    style="--depth: 0;"}
    -   [[gemini-extension.json]{.astro-g2bywc46
        style="--depth: 1;"}](#gemini-extensionjson){.astro-g2bywc46
        style="--depth: 1;"}
    -   [[Extension settings]{.astro-g2bywc46
        style="--depth: 1;"}](#extension-settings){.astro-g2bywc46
        style="--depth: 1;"}
    -   [[Custom commands]{.astro-g2bywc46
        style="--depth: 1;"}](#custom-commands){.astro-g2bywc46
        style="--depth: 1;"}
    -   [[Hooks]{.astro-g2bywc46
        style="--depth: 1;"}](#hooks){.astro-g2bywc46
        style="--depth: 1;"}
    -   [[Agent skills]{.astro-g2bywc46
        style="--depth: 1;"}](#agent-skills){.astro-g2bywc46
        style="--depth: 1;"}
    -   [[Sub-agents]{.astro-g2bywc46
        style="--depth: 1;"}](#sub-agents){.astro-g2bywc46
        style="--depth: 1;"}
    -   [[Policy Engine]{.astro-g2bywc46
        style="--depth: 1;"}](#policy-engine){.astro-g2bywc46
        style="--depth: 1;"}
    -   [[Themes]{.astro-g2bywc46
        style="--depth: 1;"}](#themes){.astro-g2bywc46
        style="--depth: 1;"}
    -   [[Conflict resolution]{.astro-g2bywc46
        style="--depth: 1;"}](#conflict-resolution){.astro-g2bywc46
        style="--depth: 1;"}
-   [[Variables]{.astro-g2bywc46
    style="--depth: 0;"}](#variables){.astro-g2bywc46
    style="--depth: 0;"}
:::
:::

::: {.right-sidebar-panel .sl-hidden .lg:sl-block .astro-pb3aqygn}
::: {.sl-container .astro-pb3aqygn}
## On this page {#starlight__on-this-page}

-   [[Introduction]{.astro-g2bywc46
    style="--depth: 0;"}](#_top){.astro-g2bywc46 style="--depth: 0;"}
-   [[Manage extensions]{.astro-g2bywc46
    style="--depth: 0;"}](#manage-extensions){.astro-g2bywc46
    style="--depth: 0;"}
    -   [[Install an extension]{.astro-g2bywc46
        style="--depth: 1;"}](#install-an-extension){.astro-g2bywc46
        style="--depth: 1;"}
    -   [[Uninstall an extension]{.astro-g2bywc46
        style="--depth: 1;"}](#uninstall-an-extension){.astro-g2bywc46
        style="--depth: 1;"}
    -   [[Disable an extension]{.astro-g2bywc46
        style="--depth: 1;"}](#disable-an-extension){.astro-g2bywc46
        style="--depth: 1;"}
    -   [[Enable an extension]{.astro-g2bywc46
        style="--depth: 1;"}](#enable-an-extension){.astro-g2bywc46
        style="--depth: 1;"}
    -   [[Update an extension]{.astro-g2bywc46
        style="--depth: 1;"}](#update-an-extension){.astro-g2bywc46
        style="--depth: 1;"}
    -   [[Create an extension from a template]{.astro-g2bywc46
        style="--depth: 1;"}](#create-an-extension-from-a-template){.astro-g2bywc46
        style="--depth: 1;"}
    -   [[Link a local extension]{.astro-g2bywc46
        style="--depth: 1;"}](#link-a-local-extension){.astro-g2bywc46
        style="--depth: 1;"}
-   [[Extension format]{.astro-g2bywc46
    style="--depth: 0;"}](#extension-format){.astro-g2bywc46
    style="--depth: 0;"}
    -   [[gemini-extension.json]{.astro-g2bywc46
        style="--depth: 1;"}](#gemini-extensionjson){.astro-g2bywc46
        style="--depth: 1;"}
    -   [[Extension settings]{.astro-g2bywc46
        style="--depth: 1;"}](#extension-settings){.astro-g2bywc46
        style="--depth: 1;"}
    -   [[Custom commands]{.astro-g2bywc46
        style="--depth: 1;"}](#custom-commands){.astro-g2bywc46
        style="--depth: 1;"}
    -   [[Hooks]{.astro-g2bywc46
        style="--depth: 1;"}](#hooks){.astro-g2bywc46
        style="--depth: 1;"}
    -   [[Agent skills]{.astro-g2bywc46
        style="--depth: 1;"}](#agent-skills){.astro-g2bywc46
        style="--depth: 1;"}
    -   [[Sub-agents]{.astro-g2bywc46
        style="--depth: 1;"}](#sub-agents){.astro-g2bywc46
        style="--depth: 1;"}
    -   [[Policy Engine]{.astro-g2bywc46
        style="--depth: 1;"}](#policy-engine){.astro-g2bywc46
        style="--depth: 1;"}
    -   [[Themes]{.astro-g2bywc46
        style="--depth: 1;"}](#themes){.astro-g2bywc46
        style="--depth: 1;"}
    -   [[Conflict resolution]{.astro-g2bywc46
        style="--depth: 1;"}](#conflict-resolution){.astro-g2bywc46
        style="--depth: 1;"}
-   [[Variables]{.astro-g2bywc46
    style="--depth: 0;"}](#variables){.astro-g2bywc46
    style="--depth: 0;"}
:::
:::
:::

::: {.main-pane .astro-67yu43on}
::: {.astro-bguv2lll role="main" pagefind-body="" lang="en" dir="ltr"}
::: {.content-panel .astro-7nkwcw3z}
::: {.sl-container .astro-7nkwcw3z}
::: {.flex .items-center .page-title .astro-guvttfii}
# Extension reference {#_top .flex-1 .astro-guvttfii}

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
This guide covers the `gemini extensions`{dir="auto"} commands and the
structure of the `gemini-extension.json`{dir="auto"} configuration file.

::: {.sl-heading-wrapper .level-h2}
## Manage extensions

[[![](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iY3VycmVudGNvbG9yIiBkPSJtMTIuMTEgMTUuMzktMy44OCAzLjg4YTIuNTIgMi41MiAwIDAgMS0zLjUgMCAyLjQ3IDIuNDcgMCAwIDEgMC0zLjVsMy44OC0zLjg4YTEgMSAwIDAgMC0xLjQyLTEuNDJsLTMuODggMy44OWE0LjQ4IDQuNDggMCAwIDAgNi4zMyA2LjMzbDMuODktMy44OGExIDEgMCAxIDAtMS40Mi0xLjQyWm04LjU4LTEyLjA4YTQuNDkgNC40OSAwIDAgMC02LjMzIDBsLTMuODkgMy44OGExIDEgMCAwIDAgMS40MiAxLjQybDMuODgtMy44OGEyLjUyIDIuNTIgMCAwIDEgMy41IDAgMi40NyAyLjQ3IDAgMCAxIDAgMy41bC0zLjg4IDMuODhhMSAxIDAgMSAwIDEuNDIgMS40MmwzLjg4LTMuODlhNC40OSA0LjQ5IDAgMCAwIDAtNi4zM1pNOC44MyAxNS4xN2ExIDEgMCAwIDAgMS4xLjIyIDEgMSAwIDAgMCAuMzItLjIybDQuOTItNC45MmExIDEgMCAwIDAtMS40Mi0xLjQybC00LjkyIDQuOTJhMSAxIDAgMCAwIDAgMS40MloiPjwvcGF0aD48L3N2Zz4=)]{.sl-anchor-icon
aria-hidden="true"}[Section titled "Manage
extensions"]{.sr-only}](#manage-extensions){.sl-anchor-link}
:::

Use the `gemini extensions`{dir="auto"} command group to manage your
extensions from the terminal.

Note that commands like `gemini extensions install`{dir="auto"} are not
supported within the CLI's interactive mode. However, you can use the
`/extensions list`{dir="auto"} command to view installed extensions. All
management operations, including updates to slash commands, take effect
only after you restart the CLI session.

::: {.sl-heading-wrapper .level-h3}
### Install an extension

[[![](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iY3VycmVudGNvbG9yIiBkPSJtMTIuMTEgMTUuMzktMy44OCAzLjg4YTIuNTIgMi41MiAwIDAgMS0zLjUgMCAyLjQ3IDIuNDcgMCAwIDEgMC0zLjVsMy44OC0zLjg4YTEgMSAwIDAgMC0xLjQyLTEuNDJsLTMuODggMy44OWE0LjQ4IDQuNDggMCAwIDAgNi4zMyA2LjMzbDMuODktMy44OGExIDEgMCAxIDAtMS40Mi0xLjQyWm04LjU4LTEyLjA4YTQuNDkgNC40OSAwIDAgMC02LjMzIDBsLTMuODkgMy44OGExIDEgMCAwIDAgMS40MiAxLjQybDMuODgtMy44OGEyLjUyIDIuNTIgMCAwIDEgMy41IDAgMi40NyAyLjQ3IDAgMCAxIDAgMy41bC0zLjg4IDMuODhhMSAxIDAgMSAwIDEuNDIgMS40MmwzLjg4LTMuODlhNC40OSA0LjQ5IDAgMCAwIDAtNi4zM1pNOC44MyAxNS4xN2ExIDEgMCAwIDAgMS4xLjIyIDEgMSAwIDAgMCAuMzItLjIybDQuOTItNC45MmExIDEgMCAwIDAtMS40Mi0xLjQybC00LjkyIDQuOTJhMSAxIDAgMCAwIDAgMS40MloiPjwvcGF0aD48L3N2Zz4=)]{.sl-anchor-icon
aria-hidden="true"}[Section titled "Install an
extension"]{.sr-only}](#install-an-extension){.sl-anchor-link}
:::

Install an extension by providing its GitHub repository URL or a local
file path.

Gemini CLI creates a copy of the extension during installation. You must
run `gemini extensions update`{dir="auto"} to pull changes from the
source. To install from GitHub, you must have `git`{dir="auto"}
installed on your machine.

::: expressive-code
<figure class="frame is-terminal not-content">
<pre data-language="bash"><code>gemini extensions install &lt;source&gt; [--ref &lt;ref&gt;] [--auto-update] [--pre-release] [--consent] [--skip-settings]</code></pre>
<div class="copy">
<div>

</div>
</div>
<figcaption><span class="title"></span><span class="sr-only">Terminal
window</span></figcaption>
</figure>
:::

-   `<source>`{dir="auto"}: The GitHub URL or local path of the
    extension.
-   `--ref`{dir="auto"}: The git ref (branch, tag, or commit) to
    install.
-   `--auto-update`{dir="auto"}: Enable automatic updates for this
    extension.
-   `--pre-release`{dir="auto"}: Enable installation of pre-release
    versions.
-   `--consent`{dir="auto"}: Acknowledge security risks and skip the
    confirmation prompt.
-   `--skip-settings`{dir="auto"}: Skip the configuration on install
    process.

::: {.sl-heading-wrapper .level-h3}
### Uninstall an extension

[[![](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iY3VycmVudGNvbG9yIiBkPSJtMTIuMTEgMTUuMzktMy44OCAzLjg4YTIuNTIgMi41MiAwIDAgMS0zLjUgMCAyLjQ3IDIuNDcgMCAwIDEgMC0zLjVsMy44OC0zLjg4YTEgMSAwIDAgMC0xLjQyLTEuNDJsLTMuODggMy44OWE0LjQ4IDQuNDggMCAwIDAgNi4zMyA2LjMzbDMuODktMy44OGExIDEgMCAxIDAtMS40Mi0xLjQyWm04LjU4LTEyLjA4YTQuNDkgNC40OSAwIDAgMC02LjMzIDBsLTMuODkgMy44OGExIDEgMCAwIDAgMS40MiAxLjQybDMuODgtMy44OGEyLjUyIDIuNTIgMCAwIDEgMy41IDAgMi40NyAyLjQ3IDAgMCAxIDAgMy41bC0zLjg4IDMuODhhMSAxIDAgMSAwIDEuNDIgMS40MmwzLjg4LTMuODlhNC40OSA0LjQ5IDAgMCAwIDAtNi4zM1pNOC44MyAxNS4xN2ExIDEgMCAwIDAgMS4xLjIyIDEgMSAwIDAgMCAuMzItLjIybDQuOTItNC45MmExIDEgMCAwIDAtMS40Mi0xLjQybC00LjkyIDQuOTJhMSAxIDAgMCAwIDAgMS40MloiPjwvcGF0aD48L3N2Zz4=)]{.sl-anchor-icon
aria-hidden="true"}[Section titled "Uninstall an
extension"]{.sr-only}](#uninstall-an-extension){.sl-anchor-link}
:::

To uninstall one or more extensions, use the `uninstall`{dir="auto"}
command:

::: expressive-code
<figure class="frame is-terminal not-content">
<pre data-language="bash"><code>gemini extensions uninstall &lt;name...&gt;</code></pre>
<div class="copy">
<div>

</div>
</div>
<figcaption><span class="title"></span><span class="sr-only">Terminal
window</span></figcaption>
</figure>
:::

::: {.sl-heading-wrapper .level-h3}
### Disable an extension

[[![](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iY3VycmVudGNvbG9yIiBkPSJtMTIuMTEgMTUuMzktMy44OCAzLjg4YTIuNTIgMi41MiAwIDAgMS0zLjUgMCAyLjQ3IDIuNDcgMCAwIDEgMC0zLjVsMy44OC0zLjg4YTEgMSAwIDAgMC0xLjQyLTEuNDJsLTMuODggMy44OWE0LjQ4IDQuNDggMCAwIDAgNi4zMyA2LjMzbDMuODktMy44OGExIDEgMCAxIDAtMS40Mi0xLjQyWm04LjU4LTEyLjA4YTQuNDkgNC40OSAwIDAgMC02LjMzIDBsLTMuODkgMy44OGExIDEgMCAwIDAgMS40MiAxLjQybDMuODgtMy44OGEyLjUyIDIuNTIgMCAwIDEgMy41IDAgMi40NyAyLjQ3IDAgMCAxIDAgMy41bC0zLjg4IDMuODhhMSAxIDAgMSAwIDEuNDIgMS40MmwzLjg4LTMuODlhNC40OSA0LjQ5IDAgMCAwIDAtNi4zM1pNOC44MyAxNS4xN2ExIDEgMCAwIDAgMS4xLjIyIDEgMSAwIDAgMCAuMzItLjIybDQuOTItNC45MmExIDEgMCAwIDAtMS40Mi0xLjQybC00LjkyIDQuOTJhMSAxIDAgMCAwIDAgMS40MloiPjwvcGF0aD48L3N2Zz4=)]{.sl-anchor-icon
aria-hidden="true"}[Section titled "Disable an
extension"]{.sr-only}](#disable-an-extension){.sl-anchor-link}
:::

Extensions are enabled globally by default. You can disable an extension
entirely or for a specific workspace.

::: expressive-code
<figure class="frame is-terminal not-content">
<pre data-language="bash"><code>gemini extensions disable &lt;name&gt; [--scope &lt;scope&gt;]</code></pre>
<div class="copy">
<div>

</div>
</div>
<figcaption><span class="title"></span><span class="sr-only">Terminal
window</span></figcaption>
</figure>
:::

-   `<name>`{dir="auto"}: The name of the extension to disable.
-   `--scope`{dir="auto"}: The scope to disable the extension in
    (`user`{dir="auto"} or `workspace`{dir="auto"}).

::: {.sl-heading-wrapper .level-h3}
### Enable an extension

[[![](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iY3VycmVudGNvbG9yIiBkPSJtMTIuMTEgMTUuMzktMy44OCAzLjg4YTIuNTIgMi41MiAwIDAgMS0zLjUgMCAyLjQ3IDIuNDcgMCAwIDEgMC0zLjVsMy44OC0zLjg4YTEgMSAwIDAgMC0xLjQyLTEuNDJsLTMuODggMy44OWE0LjQ4IDQuNDggMCAwIDAgNi4zMyA2LjMzbDMuODktMy44OGExIDEgMCAxIDAtMS40Mi0xLjQyWm04LjU4LTEyLjA4YTQuNDkgNC40OSAwIDAgMC02LjMzIDBsLTMuODkgMy44OGExIDEgMCAwIDAgMS40MiAxLjQybDMuODgtMy44OGEyLjUyIDIuNTIgMCAwIDEgMy41IDAgMi40NyAyLjQ3IDAgMCAxIDAgMy41bC0zLjg4IDMuODhhMSAxIDAgMSAwIDEuNDIgMS40MmwzLjg4LTMuODlhNC40OSA0LjQ5IDAgMCAwIDAtNi4zM1pNOC44MyAxNS4xN2ExIDEgMCAwIDAgMS4xLjIyIDEgMSAwIDAgMCAuMzItLjIybDQuOTItNC45MmExIDEgMCAwIDAtMS40Mi0xLjQybC00LjkyIDQuOTJhMSAxIDAgMCAwIDAgMS40MloiPjwvcGF0aD48L3N2Zz4=)]{.sl-anchor-icon
aria-hidden="true"}[Section titled "Enable an
extension"]{.sr-only}](#enable-an-extension){.sl-anchor-link}
:::

Re-enable a disabled extension using the `enable`{dir="auto"} command:

::: expressive-code
<figure class="frame is-terminal not-content">
<pre data-language="bash"><code>gemini extensions enable &lt;name&gt; [--scope &lt;scope&gt;]</code></pre>
<div class="copy">
<div>

</div>
</div>
<figcaption><span class="title"></span><span class="sr-only">Terminal
window</span></figcaption>
</figure>
:::

-   `<name>`{dir="auto"}: The name of the extension to enable.
-   `--scope`{dir="auto"}: The scope to enable the extension in
    (`user`{dir="auto"} or `workspace`{dir="auto"}).

::: {.sl-heading-wrapper .level-h3}
### Update an extension

[[![](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iY3VycmVudGNvbG9yIiBkPSJtMTIuMTEgMTUuMzktMy44OCAzLjg4YTIuNTIgMi41MiAwIDAgMS0zLjUgMCAyLjQ3IDIuNDcgMCAwIDEgMC0zLjVsMy44OC0zLjg4YTEgMSAwIDAgMC0xLjQyLTEuNDJsLTMuODggMy44OWE0LjQ4IDQuNDggMCAwIDAgNi4zMyA2LjMzbDMuODktMy44OGExIDEgMCAxIDAtMS40Mi0xLjQyWm04LjU4LTEyLjA4YTQuNDkgNC40OSAwIDAgMC02LjMzIDBsLTMuODkgMy44OGExIDEgMCAwIDAgMS40MiAxLjQybDMuODgtMy44OGEyLjUyIDIuNTIgMCAwIDEgMy41IDAgMi40NyAyLjQ3IDAgMCAxIDAgMy41bC0zLjg4IDMuODhhMSAxIDAgMSAwIDEuNDIgMS40MmwzLjg4LTMuODlhNC40OSA0LjQ5IDAgMCAwIDAtNi4zM1pNOC44MyAxNS4xN2ExIDEgMCAwIDAgMS4xLjIyIDEgMSAwIDAgMCAuMzItLjIybDQuOTItNC45MmExIDEgMCAwIDAtMS40Mi0xLjQybC00LjkyIDQuOTJhMSAxIDAgMCAwIDAgMS40MloiPjwvcGF0aD48L3N2Zz4=)]{.sl-anchor-icon
aria-hidden="true"}[Section titled "Update an
extension"]{.sr-only}](#update-an-extension){.sl-anchor-link}
:::

Update an extension to the version specified in its
`gemini-extension.json`{dir="auto"} file.

::: expressive-code
<figure class="frame is-terminal not-content">
<pre data-language="bash"><code>gemini extensions update &lt;name&gt;</code></pre>
<div class="copy">
<div>

</div>
</div>
<figcaption><span class="title"></span><span class="sr-only">Terminal
window</span></figcaption>
</figure>
:::

To update all installed extensions at once:

::: expressive-code
<figure class="frame is-terminal not-content">
<pre data-language="bash"><code>gemini extensions update --all</code></pre>
<div class="copy">
<div>

</div>
</div>
<figcaption><span class="title"></span><span class="sr-only">Terminal
window</span></figcaption>
</figure>
:::

::: {.sl-heading-wrapper .level-h3}
### Create an extension from a template

[[![](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iY3VycmVudGNvbG9yIiBkPSJtMTIuMTEgMTUuMzktMy44OCAzLjg4YTIuNTIgMi41MiAwIDAgMS0zLjUgMCAyLjQ3IDIuNDcgMCAwIDEgMC0zLjVsMy44OC0zLjg4YTEgMSAwIDAgMC0xLjQyLTEuNDJsLTMuODggMy44OWE0LjQ4IDQuNDggMCAwIDAgNi4zMyA2LjMzbDMuODktMy44OGExIDEgMCAxIDAtMS40Mi0xLjQyWm04LjU4LTEyLjA4YTQuNDkgNC40OSAwIDAgMC02LjMzIDBsLTMuODkgMy44OGExIDEgMCAwIDAgMS40MiAxLjQybDMuODgtMy44OGEyLjUyIDIuNTIgMCAwIDEgMy41IDAgMi40NyAyLjQ3IDAgMCAxIDAgMy41bC0zLjg4IDMuODhhMSAxIDAgMSAwIDEuNDIgMS40MmwzLjg4LTMuODlhNC40OSA0LjQ5IDAgMCAwIDAtNi4zM1pNOC44MyAxNS4xN2ExIDEgMCAwIDAgMS4xLjIyIDEgMSAwIDAgMCAuMzItLjIybDQuOTItNC45MmExIDEgMCAwIDAtMS40Mi0xLjQybC00LjkyIDQuOTJhMSAxIDAgMCAwIDAgMS40MloiPjwvcGF0aD48L3N2Zz4=)]{.sl-anchor-icon
aria-hidden="true"}[Section titled "Create an extension from a
template"]{.sr-only}](#create-an-extension-from-a-template){.sl-anchor-link}
:::

Create a new extension directory using a built-in template.

::: expressive-code
<figure class="frame is-terminal not-content">
<pre data-language="bash"><code>gemini extensions new &lt;path&gt; [template]</code></pre>
<div class="copy">
<div>

</div>
</div>
<figcaption><span class="title"></span><span class="sr-only">Terminal
window</span></figcaption>
</figure>
:::

-   `<path>`{dir="auto"}: The directory to create.
-   `[template]`{dir="auto"}: The template to use (for example,
    `mcp-server`{dir="auto"}, `context`{dir="auto"},
    `custom-commands`{dir="auto"}).

::: {.sl-heading-wrapper .level-h3}
### Link a local extension

[[![](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iY3VycmVudGNvbG9yIiBkPSJtMTIuMTEgMTUuMzktMy44OCAzLjg4YTIuNTIgMi41MiAwIDAgMS0zLjUgMCAyLjQ3IDIuNDcgMCAwIDEgMC0zLjVsMy44OC0zLjg4YTEgMSAwIDAgMC0xLjQyLTEuNDJsLTMuODggMy44OWE0LjQ4IDQuNDggMCAwIDAgNi4zMyA2LjMzbDMuODktMy44OGExIDEgMCAxIDAtMS40Mi0xLjQyWm04LjU4LTEyLjA4YTQuNDkgNC40OSAwIDAgMC02LjMzIDBsLTMuODkgMy44OGExIDEgMCAwIDAgMS40MiAxLjQybDMuODgtMy44OGEyLjUyIDIuNTIgMCAwIDEgMy41IDAgMi40NyAyLjQ3IDAgMCAxIDAgMy41bC0zLjg4IDMuODhhMSAxIDAgMSAwIDEuNDIgMS40MmwzLjg4LTMuODlhNC40OSA0LjQ5IDAgMCAwIDAtNi4zM1pNOC44MyAxNS4xN2ExIDEgMCAwIDAgMS4xLjIyIDEgMSAwIDAgMCAuMzItLjIybDQuOTItNC45MmExIDEgMCAwIDAtMS40Mi0xLjQybC00LjkyIDQuOTJhMSAxIDAgMCAwIDAgMS40MloiPjwvcGF0aD48L3N2Zz4=)]{.sl-anchor-icon
aria-hidden="true"}[Section titled "Link a local
extension"]{.sr-only}](#link-a-local-extension){.sl-anchor-link}
:::

Create a symbolic link between your development directory and Gemini CLI
extensions directory. This lets you test changes immediately without
reinstalling.

::: expressive-code
<figure class="frame is-terminal not-content">
<pre data-language="bash"><code>gemini extensions link &lt;path&gt;</code></pre>
<div class="copy">
<div>

</div>
</div>
<figcaption><span class="title"></span><span class="sr-only">Terminal
window</span></figcaption>
</figure>
:::

::: {.sl-heading-wrapper .level-h2}
## Extension format

[[![](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iY3VycmVudGNvbG9yIiBkPSJtMTIuMTEgMTUuMzktMy44OCAzLjg4YTIuNTIgMi41MiAwIDAgMS0zLjUgMCAyLjQ3IDIuNDcgMCAwIDEgMC0zLjVsMy44OC0zLjg4YTEgMSAwIDAgMC0xLjQyLTEuNDJsLTMuODggMy44OWE0LjQ4IDQuNDggMCAwIDAgNi4zMyA2LjMzbDMuODktMy44OGExIDEgMCAxIDAtMS40Mi0xLjQyWm04LjU4LTEyLjA4YTQuNDkgNC40OSAwIDAgMC02LjMzIDBsLTMuODkgMy44OGExIDEgMCAwIDAgMS40MiAxLjQybDMuODgtMy44OGEyLjUyIDIuNTIgMCAwIDEgMy41IDAgMi40NyAyLjQ3IDAgMCAxIDAgMy41bC0zLjg4IDMuODhhMSAxIDAgMSAwIDEuNDIgMS40MmwzLjg4LTMuODlhNC40OSA0LjQ5IDAgMCAwIDAtNi4zM1pNOC44MyAxNS4xN2ExIDEgMCAwIDAgMS4xLjIyIDEgMSAwIDAgMCAuMzItLjIybDQuOTItNC45MmExIDEgMCAwIDAtMS40Mi0xLjQybC00LjkyIDQuOTJhMSAxIDAgMCAwIDAgMS40MloiPjwvcGF0aD48L3N2Zz4=)]{.sl-anchor-icon
aria-hidden="true"}[Section titled "Extension
format"]{.sr-only}](#extension-format){.sl-anchor-link}
:::

Gemini CLI loads extensions from
`<home>/.gemini/extensions`{dir="auto"}. Each extension must have a
`gemini-extension.json`{dir="auto"} file in its root directory.

::: {.sl-heading-wrapper .level-h3}
### `gemini-extension.json`{dir="auto"} {#gemini-extensionjson}

[[![](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iY3VycmVudGNvbG9yIiBkPSJtMTIuMTEgMTUuMzktMy44OCAzLjg4YTIuNTIgMi41MiAwIDAgMS0zLjUgMCAyLjQ3IDIuNDcgMCAwIDEgMC0zLjVsMy44OC0zLjg4YTEgMSAwIDAgMC0xLjQyLTEuNDJsLTMuODggMy44OWE0LjQ4IDQuNDggMCAwIDAgNi4zMyA2LjMzbDMuODktMy44OGExIDEgMCAxIDAtMS40Mi0xLjQyWm04LjU4LTEyLjA4YTQuNDkgNC40OSAwIDAgMC02LjMzIDBsLTMuODkgMy44OGExIDEgMCAwIDAgMS40MiAxLjQybDMuODgtMy44OGEyLjUyIDIuNTIgMCAwIDEgMy41IDAgMi40NyAyLjQ3IDAgMCAxIDAgMy41bC0zLjg4IDMuODhhMSAxIDAgMSAwIDEuNDIgMS40MmwzLjg4LTMuODlhNC40OSA0LjQ5IDAgMCAwIDAtNi4zM1pNOC44MyAxNS4xN2ExIDEgMCAwIDAgMS4xLjIyIDEgMSAwIDAgMCAuMzItLjIybDQuOTItNC45MmExIDEgMCAwIDAtMS40Mi0xLjQybC00LjkyIDQuOTJhMSAxIDAgMCAwIDAgMS40MloiPjwvcGF0aD48L3N2Zz4=)]{.sl-anchor-icon
aria-hidden="true"}[Section titled
"gemini-extension.json"]{.sr-only}](#gemini-extensionjson){.sl-anchor-link}
:::

The manifest file defines the extension's behavior and configuration.

::: expressive-code
<figure class="frame not-content">
<pre data-language="json"><code>{  &quot;name&quot;: &quot;my-extension&quot;,  &quot;version&quot;: &quot;1.0.0&quot;,  &quot;description&quot;: &quot;My awesome extension&quot;,  &quot;mcpServers&quot;: {    &quot;my-server&quot;: {      &quot;command&quot;: &quot;node&quot;,      &quot;args&quot;: [&quot;${extensionPath}/my-server.js&quot;],      &quot;cwd&quot;: &quot;${extensionPath}&quot;    }  },  &quot;contextFileName&quot;: &quot;GEMINI.md&quot;,  &quot;excludeTools&quot;: [&quot;run_shell_command&quot;],  &quot;migratedTo&quot;: &quot;https://github.com/new-owner/new-extension-repo&quot;,  &quot;plan&quot;: {    &quot;directory&quot;: &quot;.gemini/plans&quot;  }}</code></pre>
<div class="copy">
<div>

</div>
</div>
</figure>
:::

-   `name`{dir="auto"}: The name of the extension. This is used to
    uniquely identify the extension and for conflict resolution when
    extension commands have the same name as user or project commands.
    The name should be lowercase or numbers and use dashes instead of
    underscores or spaces. This is how users will refer to your
    extension in the CLI. Note that we expect this name to match the
    extension directory name.
-   `version`{dir="auto"}: The version of the extension.
-   `description`{dir="auto"}: A short description of the extension.
    This will be displayed on
    [geminicli.com/extensions](https://geminicli.com/extensions).
-   `migratedTo`{dir="auto"}: The URL of the new repository source for
    the extension. If this is set, the CLI will automatically check this
    new source for updates and migrate the extension's installation to
    the new source if an update is found.
-   `mcpServers`{dir="auto"}: A map of MCP servers to settings. The key
    is the name of the server, and the value is the server
    configuration. These servers will be loaded on startup just like MCP
    servers defined in a [`settings.json`{dir="auto"}
    file](/docs/reference/configuration). If both an extension and a
    `settings.json`{dir="auto"} file define an MCP server with the same
    name, the server defined in the `settings.json`{dir="auto"} file
    takes precedence.
    -   Note that all MCP server configuration options are supported
        except for `trust`{dir="auto"}.
    -   For portability, you should use `${extensionPath}`{dir="auto"}
        to refer to files within your extension directory.
    -   Separate your executable and its arguments using
        `command`{dir="auto"} and `args`{dir="auto"} instead of putting
        them both in `command`{dir="auto"}.
-   `contextFileName`{dir="auto"}: The name of the file that contains
    the context for the extension. This will be used to load the context
    from the extension directory. If this property is not used but a
    `GEMINI.md`{dir="auto"} file is present in your extension directory,
    then that file will be loaded.
-   `excludeTools`{dir="auto"}: An array of tool names to exclude from
    the model. You can also specify command-specific restrictions for
    tools that support it, like the `run_shell_command`{dir="auto"}
    tool. For example,
    `"excludeTools": ["run_shell_command(rm -rf)"]`{dir="auto"} will
    block the `rm -rf`{dir="auto"} command. Note that this differs from
    the MCP server `excludeTools`{dir="auto"} functionality, which can
    be listed in the MCP server config.
-   `plan`{dir="auto"}: Planning features configuration.
    -   `directory`{dir="auto"}: The directory where planning artifacts
        are stored. This serves as a fallback if the user hasn't
        specified a plan directory in their settings. If not specified
        by either the extension or the user, the default is
        `~/.gemini/tmp/<project>/<session-id>/plans/`{dir="auto"}.

When Gemini CLI starts, it loads all the extensions and merges their
configurations. If there are any conflicts, the workspace configuration
takes precedence.

::: {.sl-heading-wrapper .level-h3}
### Extension settings

[[![](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iY3VycmVudGNvbG9yIiBkPSJtMTIuMTEgMTUuMzktMy44OCAzLjg4YTIuNTIgMi41MiAwIDAgMS0zLjUgMCAyLjQ3IDIuNDcgMCAwIDEgMC0zLjVsMy44OC0zLjg4YTEgMSAwIDAgMC0xLjQyLTEuNDJsLTMuODggMy44OWE0LjQ4IDQuNDggMCAwIDAgNi4zMyA2LjMzbDMuODktMy44OGExIDEgMCAxIDAtMS40Mi0xLjQyWm04LjU4LTEyLjA4YTQuNDkgNC40OSAwIDAgMC02LjMzIDBsLTMuODkgMy44OGExIDEgMCAwIDAgMS40MiAxLjQybDMuODgtMy44OGEyLjUyIDIuNTIgMCAwIDEgMy41IDAgMi40NyAyLjQ3IDAgMCAxIDAgMy41bC0zLjg4IDMuODhhMSAxIDAgMSAwIDEuNDIgMS40MmwzLjg4LTMuODlhNC40OSA0LjQ5IDAgMCAwIDAtNi4zM1pNOC44MyAxNS4xN2ExIDEgMCAwIDAgMS4xLjIyIDEgMSAwIDAgMCAuMzItLjIybDQuOTItNC45MmExIDEgMCAwIDAtMS40Mi0xLjQybC00LjkyIDQuOTJhMSAxIDAgMCAwIDAgMS40MloiPjwvcGF0aD48L3N2Zz4=)]{.sl-anchor-icon
aria-hidden="true"}[Section titled "Extension
settings"]{.sr-only}](#extension-settings){.sl-anchor-link}
:::

Extensions can define settings that users provide during installation,
such as API keys or URLs. These values are stored in a
`.env`{dir="auto"} file within the extension directory.

To define settings, add a `settings`{dir="auto"} array to your manifest:

::: expressive-code
<figure class="frame not-content">
<pre data-language="json"><code>{  &quot;name&quot;: &quot;my-api-extension&quot;,  &quot;version&quot;: &quot;1.0.0&quot;,  &quot;settings&quot;: [    {      &quot;name&quot;: &quot;API Key&quot;,      &quot;description&quot;: &quot;Your API key for the service.&quot;,      &quot;envVar&quot;: &quot;MY_API_KEY&quot;,      &quot;sensitive&quot;: true    }  ]}</code></pre>
<div class="copy">
<div>

</div>
</div>
</figure>
:::

-   `name`{dir="auto"}: The setting's display name.
-   `description`{dir="auto"}: A clear explanation of the setting.
-   `envVar`{dir="auto"}: The environment variable name where the value
    is stored.
-   `sensitive`{dir="auto"}: If `true`{dir="auto"}, the value is stored
    in the system keychain and obfuscated in the UI.

To update an extension's settings:

::: expressive-code
<figure class="frame is-terminal not-content">
<pre data-language="bash"><code>gemini extensions config &lt;name&gt; [setting] [--scope &lt;scope&gt;]</code></pre>
<div class="copy">
<div>

</div>
</div>
<figcaption><span class="title"></span><span class="sr-only">Terminal
window</span></figcaption>
</figure>
:::

::: {.sl-heading-wrapper .level-h3}
### Custom commands

[[![](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iY3VycmVudGNvbG9yIiBkPSJtMTIuMTEgMTUuMzktMy44OCAzLjg4YTIuNTIgMi41MiAwIDAgMS0zLjUgMCAyLjQ3IDIuNDcgMCAwIDEgMC0zLjVsMy44OC0zLjg4YTEgMSAwIDAgMC0xLjQyLTEuNDJsLTMuODggMy44OWE0LjQ4IDQuNDggMCAwIDAgNi4zMyA2LjMzbDMuODktMy44OGExIDEgMCAxIDAtMS40Mi0xLjQyWm04LjU4LTEyLjA4YTQuNDkgNC40OSAwIDAgMC02LjMzIDBsLTMuODkgMy44OGExIDEgMCAwIDAgMS40MiAxLjQybDMuODgtMy44OGEyLjUyIDIuNTIgMCAwIDEgMy41IDAgMi40NyAyLjQ3IDAgMCAxIDAgMy41bC0zLjg4IDMuODhhMSAxIDAgMSAwIDEuNDIgMS40MmwzLjg4LTMuODlhNC40OSA0LjQ5IDAgMCAwIDAtNi4zM1pNOC44MyAxNS4xN2ExIDEgMCAwIDAgMS4xLjIyIDEgMSAwIDAgMCAuMzItLjIybDQuOTItNC45MmExIDEgMCAwIDAtMS40Mi0xLjQybC00LjkyIDQuOTJhMSAxIDAgMCAwIDAgMS40MloiPjwvcGF0aD48L3N2Zz4=)]{.sl-anchor-icon
aria-hidden="true"}[Section titled "Custom
commands"]{.sr-only}](#custom-commands){.sl-anchor-link}
:::

Provide [custom commands](/docs/cli/custom-commands) by placing TOML
files in a `commands/`{dir="auto"} subdirectory. Gemini CLI uses the
directory structure to determine the command name.

For an extension named `gcp`{dir="auto"}:

-   `commands/deploy.toml`{dir="auto"} becomes `/deploy`{dir="auto"}
-   `commands/gcs/sync.toml`{dir="auto"} becomes `/gcs:sync`{dir="auto"}
    (namespaced with a colon)

::: {.sl-heading-wrapper .level-h3}
### Hooks

[[![](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iY3VycmVudGNvbG9yIiBkPSJtMTIuMTEgMTUuMzktMy44OCAzLjg4YTIuNTIgMi41MiAwIDAgMS0zLjUgMCAyLjQ3IDIuNDcgMCAwIDEgMC0zLjVsMy44OC0zLjg4YTEgMSAwIDAgMC0xLjQyLTEuNDJsLTMuODggMy44OWE0LjQ4IDQuNDggMCAwIDAgNi4zMyA2LjMzbDMuODktMy44OGExIDEgMCAxIDAtMS40Mi0xLjQyWm04LjU4LTEyLjA4YTQuNDkgNC40OSAwIDAgMC02LjMzIDBsLTMuODkgMy44OGExIDEgMCAwIDAgMS40MiAxLjQybDMuODgtMy44OGEyLjUyIDIuNTIgMCAwIDEgMy41IDAgMi40NyAyLjQ3IDAgMCAxIDAgMy41bC0zLjg4IDMuODhhMSAxIDAgMSAwIDEuNDIgMS40MmwzLjg4LTMuODlhNC40OSA0LjQ5IDAgMCAwIDAtNi4zM1pNOC44MyAxNS4xN2ExIDEgMCAwIDAgMS4xLjIyIDEgMSAwIDAgMCAuMzItLjIybDQuOTItNC45MmExIDEgMCAwIDAtMS40Mi0xLjQybC00LjkyIDQuOTJhMSAxIDAgMCAwIDAgMS40MloiPjwvcGF0aD48L3N2Zz4=)]{.sl-anchor-icon
aria-hidden="true"}[Section titled
"Hooks"]{.sr-only}](#hooks){.sl-anchor-link}
:::

Intercept and customize CLI behavior using [hooks](/docs/hooks). Define
hooks in a `hooks/hooks.json`{dir="auto"} file within your extension
directory. Note that hooks are not defined in the
`gemini-extension.json`{dir="auto"} manifest.

::: {.sl-heading-wrapper .level-h3}
### Agent skills

[[![](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iY3VycmVudGNvbG9yIiBkPSJtMTIuMTEgMTUuMzktMy44OCAzLjg4YTIuNTIgMi41MiAwIDAgMS0zLjUgMCAyLjQ3IDIuNDcgMCAwIDEgMC0zLjVsMy44OC0zLjg4YTEgMSAwIDAgMC0xLjQyLTEuNDJsLTMuODggMy44OWE0LjQ4IDQuNDggMCAwIDAgNi4zMyA2LjMzbDMuODktMy44OGExIDEgMCAxIDAtMS40Mi0xLjQyWm04LjU4LTEyLjA4YTQuNDkgNC40OSAwIDAgMC02LjMzIDBsLTMuODkgMy44OGExIDEgMCAwIDAgMS40MiAxLjQybDMuODgtMy44OGEyLjUyIDIuNTIgMCAwIDEgMy41IDAgMi40NyAyLjQ3IDAgMCAxIDAgMy41bC0zLjg4IDMuODhhMSAxIDAgMSAwIDEuNDIgMS40MmwzLjg4LTMuODlhNC40OSA0LjQ5IDAgMCAwIDAtNi4zM1pNOC44MyAxNS4xN2ExIDEgMCAwIDAgMS4xLjIyIDEgMSAwIDAgMCAuMzItLjIybDQuOTItNC45MmExIDEgMCAwIDAtMS40Mi0xLjQybC00LjkyIDQuOTJhMSAxIDAgMCAwIDAgMS40MloiPjwvcGF0aD48L3N2Zz4=)]{.sl-anchor-icon
aria-hidden="true"}[Section titled "Agent
skills"]{.sr-only}](#agent-skills){.sl-anchor-link}
:::

Bundle [agent skills](/docs/cli/skills) to provide specialized
workflows. Place skill definitions in a `skills/`{dir="auto"} directory.
For example, `skills/security-audit/SKILL.md`{dir="auto"} exposes a
`security-audit`{dir="auto"} skill.

::: {.sl-heading-wrapper .level-h3}
### Sub-agents

[[![](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iY3VycmVudGNvbG9yIiBkPSJtMTIuMTEgMTUuMzktMy44OCAzLjg4YTIuNTIgMi41MiAwIDAgMS0zLjUgMCAyLjQ3IDIuNDcgMCAwIDEgMC0zLjVsMy44OC0zLjg4YTEgMSAwIDAgMC0xLjQyLTEuNDJsLTMuODggMy44OWE0LjQ4IDQuNDggMCAwIDAgNi4zMyA2LjMzbDMuODktMy44OGExIDEgMCAxIDAtMS40Mi0xLjQyWm04LjU4LTEyLjA4YTQuNDkgNC40OSAwIDAgMC02LjMzIDBsLTMuODkgMy44OGExIDEgMCAwIDAgMS40MiAxLjQybDMuODgtMy44OGEyLjUyIDIuNTIgMCAwIDEgMy41IDAgMi40NyAyLjQ3IDAgMCAxIDAgMy41bC0zLjg4IDMuODhhMSAxIDAgMSAwIDEuNDIgMS40MmwzLjg4LTMuODlhNC40OSA0LjQ5IDAgMCAwIDAtNi4zM1pNOC44MyAxNS4xN2ExIDEgMCAwIDAgMS4xLjIyIDEgMSAwIDAgMCAuMzItLjIybDQuOTItNC45MmExIDEgMCAwIDAtMS40Mi0xLjQybC00LjkyIDQuOTJhMSAxIDAgMCAwIDAgMS40MloiPjwvcGF0aD48L3N2Zz4=)]{.sl-anchor-icon
aria-hidden="true"}[Section titled
"Sub-agents"]{.sr-only}](#sub-agents){.sl-anchor-link}
:::

![](data:image/svg+xml;base64,PHN2ZyB2aWV3Ym94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgaGVpZ2h0PSIxNiIgZmlsbD0iY3VycmVudENvbG9yIiBjbGFzcz0ic3RhcmxpZ2h0LWFzaWRlX19pY29uIj48cGF0aCBkPSJNMTIgMTFDMTEuNzM0OCAxMSAxMS40ODA0IDExLjEwNTQgMTEuMjkyOSAxMS4yOTI5QzExLjEwNTQgMTEuNDgwNCAxMSAxMS43MzQ4IDExIDEyVjE2QzExIDE2LjI2NTIgMTEuMTA1NCAxNi41MTk2IDExLjI5MjkgMTYuNzA3MUMxMS40ODA0IDE2Ljg5NDYgMTEuNzM0OCAxNyAxMiAxN0MxMi4yNjUyIDE3IDEyLjUxOTYgMTYuODk0NiAxMi43MDcxIDE2LjcwNzFDMTIuODk0NiAxNi41MTk2IDEzIDE2LjI2NTIgMTMgMTZWMTJDMTMgMTEuNzM0OCAxMi44OTQ2IDExLjQ4MDQgMTIuNzA3MSAxMS4yOTI5QzEyLjUxOTYgMTEuMTA1NCAxMi4yNjUyIDExIDEyIDExWk0xMi4zOCA3LjA4QzEyLjEzNjUgNi45Nzk5OCAxMS44NjM1IDYuOTc5OTggMTEuNjIgNy4wOEMxMS40OTczIDcuMTI3NTkgMTEuMzg1MSA3LjE5ODk2IDExLjI5IDcuMjlDMTEuMjAxNyA3LjM4NzIgMTEuMTMwNiA3LjQ5ODgyIDExLjA4IDcuNjJDMTEuMDI0IDcuNzM4NjggMTAuOTk2NiA3Ljg2ODgyIDExIDhDMTAuOTk5MiA4LjEzMTYxIDExLjAyNDUgOC4yNjIwNyAxMS4wNzQyIDguMzgzOTFDMTEuMTI0IDguNTA1NzQgMTEuMTk3MyA4LjYxNjU2IDExLjI5IDguNzFDMTEuMzg3MiA4Ljc5ODMzIDExLjQ5ODggOC44NjkzNiAxMS42MiA4LjkyQzExLjc3MTUgOC45ODIyNCAxMS45MzYgOS4wMDYzMiAxMi4wOTkgOC45OTAxMUMxMi4yNjE5IDguOTczOTEgMTIuNDE4NCA4LjkxNzkyIDEyLjU1NDcgOC44MjcwN0MxMi42OTEgOC43MzYyMiAxMi44MDI5IDguNjEzMjggMTIuODgwNSA4LjQ2OTA3QzEyLjk1ODIgOC4zMjQ4NiAxMi45OTkyIDguMTYzNzggMTMgOEMxMi45OTYzIDcuNzM1MjMgMTIuODkyNyA3LjQ4MTYzIDEyLjcxIDcuMjlDMTIuNjE0OSA3LjE5ODk2IDEyLjUwMjggNy4xMjc1OSAxMi4zOCA3LjA4Wk0xMiAyQzEwLjAyMjIgMiA4LjA4ODc5IDIuNTg2NDkgNi40NDQzIDMuNjg1M0M0Ljc5OTgxIDQuNzg0MTIgMy41MTgwOSA2LjM0NTkgMi43NjEyMSA4LjE3MzE3QzIuMDA0MzMgMTAuMDAwNCAxLjgwNjMgMTIuMDExMSAyLjE5MjE1IDEzLjk1MDlDMi41NzggMTUuODkwNyAzLjUzMDQxIDE3LjY3MjUgNC45Mjg5NCAxOS4wNzExQzYuMzI3NDYgMjAuNDY5NiA4LjEwOTI5IDIxLjQyMiAxMC4wNDkxIDIxLjgwNzlDMTEuOTg4OSAyMi4xOTM3IDEzLjk5OTYgMjEuOTk1NyAxNS44MjY4IDIxLjIzODhDMTcuNjU0MSAyMC40ODE5IDE5LjIxNTkgMTkuMjAwMiAyMC4zMTQ3IDE3LjU1NTdDMjEuNDEzNSAxNS45MTEyIDIyIDEzLjk3NzggMjIgMTJDMjIgMTAuNjg2OCAyMS43NDEzIDkuMzg2NDIgMjEuMjM4OCA4LjE3MzE3QzIwLjczNjMgNi45NTk5MSAxOS45OTk3IDUuODU3NTIgMTkuMDcxMSA0LjkyODkzQzE4LjE0MjUgNC4wMDAzNSAxNy4wNDAxIDMuMjYzNzUgMTUuODI2OCAyLjc2MTJDMTQuNjEzNiAyLjI1ODY2IDEzLjMxMzIgMiAxMiAyWk0xMiAyMEMxMC40MTc4IDIwIDguODcxMDQgMTkuNTMwOCA3LjU1NTQ0IDE4LjY1MThDNi4yMzk4NSAxNy43NzI3IDUuMjE0NDcgMTYuNTIzMyA0LjYwODk3IDE1LjA2MTVDNC4wMDM0NyAxMy41OTk3IDMuODQ1MDQgMTEuOTkxMSA0LjE1MzcyIDEwLjQzOTNDNC40NjI0IDguODg3NDMgNS4yMjQzMyA3LjQ2MTk3IDYuMzQzMTUgNi4zNDMxNUM3LjQ2MTk3IDUuMjI0MzMgOC44ODc0MyA0LjQ2MjQgMTAuNDM5MyA0LjE1MzcyQzExLjk5MTEgMy44NDUwNCAxMy41OTk3IDQuMDAzNDYgMTUuMDYxNSA0LjYwODk2QzE2LjUyMzMgNS4yMTQ0NyAxNy43NzI3IDYuMjM5ODQgMTguNjUxOCA3LjU1NTQ0QzE5LjUzMDggOC44NzEwMyAyMCAxMC40MTc3IDIwIDEyQzIwIDE0LjEyMTcgMTkuMTU3MiAxNi4xNTY2IDE3LjY1NjkgMTcuNjU2OUMxNi4xNTY2IDE5LjE1NzEgMTQuMTIxNyAyMCAxMiAyMFoiPjwvcGF0aD48L3N2Zz4=){.starlight-aside__icon}Note

::: starlight-aside__content
Sub-agents are a preview feature currently under active development.
:::

Provide [sub-agents](/docs/core/subagents) that users can delegate tasks
to. Add agent definition files (`.md`{dir="auto"}) to an
`agents/`{dir="auto"} directory in your extension root.

::: {.sl-heading-wrapper .level-h3}
### []{#policy-engine}Policy Engine

[[![](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iY3VycmVudGNvbG9yIiBkPSJtMTIuMTEgMTUuMzktMy44OCAzLjg4YTIuNTIgMi41MiAwIDAgMS0zLjUgMCAyLjQ3IDIuNDcgMCAwIDEgMC0zLjVsMy44OC0zLjg4YTEgMSAwIDAgMC0xLjQyLTEuNDJsLTMuODggMy44OWE0LjQ4IDQuNDggMCAwIDAgNi4zMyA2LjMzbDMuODktMy44OGExIDEgMCAxIDAtMS40Mi0xLjQyWm04LjU4LTEyLjA4YTQuNDkgNC40OSAwIDAgMC02LjMzIDBsLTMuODkgMy44OGExIDEgMCAwIDAgMS40MiAxLjQybDMuODgtMy44OGEyLjUyIDIuNTIgMCAwIDEgMy41IDAgMi40NyAyLjQ3IDAgMCAxIDAgMy41bC0zLjg4IDMuODhhMSAxIDAgMSAwIDEuNDIgMS40MmwzLjg4LTMuODlhNC40OSA0LjQ5IDAgMCAwIDAtNi4zM1pNOC44MyAxNS4xN2ExIDEgMCAwIDAgMS4xLjIyIDEgMSAwIDAgMCAuMzItLjIybDQuOTItNC45MmExIDEgMCAwIDAtMS40Mi0xLjQybC00LjkyIDQuOTJhMSAxIDAgMCAwIDAgMS40MloiPjwvcGF0aD48L3N2Zz4=)]{.sl-anchor-icon
aria-hidden="true"}[Section titled "Policy
Engine"]{.sr-only}](#policy-engine){.sl-anchor-link}
:::

Extensions can contribute policy rules and safety checkers to Gemini CLI
[Policy Engine](/docs/reference/policy-engine). These rules are defined
in `.toml`{dir="auto"} files and take effect when the extension is
activated.

To add policies, create a `policies/`{dir="auto"} directory in your
extension's root and place your `.toml`{dir="auto"} policy files inside
it. Gemini CLI automatically loads all `.toml`{dir="auto"} files from
this directory.

Rules contributed by extensions run in their own tier (tier 2),
alongside workspace-defined policies. This tier has higher priority than
the default rules but lower priority than user or admin policies.

![](data:image/svg+xml;base64,PHN2ZyB2aWV3Ym94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgaGVpZ2h0PSIxNiIgZmlsbD0iY3VycmVudENvbG9yIiBjbGFzcz0ic3RhcmxpZ2h0LWFzaWRlX19pY29uIj48cGF0aCBkPSJNMTIgMTZDMTEuODAyMiAxNiAxMS42MDg5IDE2LjA1ODcgMTEuNDQ0NCAxNi4xNjg2QzExLjI4IDE2LjI3ODQgMTEuMTUxOCAxNi40MzQ2IDExLjA3NjEgMTYuNjE3M0MxMS4wMDA0IDE2LjgwMDEgMTAuOTgwNiAxNy4wMDExIDExLjAxOTIgMTcuMTk1MUMxMS4wNTc4IDE3LjM4OTEgMTEuMTUzIDE3LjU2NzMgMTEuMjkyOSAxNy43MDcxQzExLjQzMjcgMTcuODQ3IDExLjYxMDkgMTcuOTQyMiAxMS44MDQ5IDE3Ljk4MDhDMTEuOTk4OSAxOC4wMTk0IDEyLjIgMTcuOTk5NiAxMi4zODI3IDE3LjkyMzlDMTIuNTY1NCAxNy44NDgyIDEyLjcyMTYgMTcuNzIgMTIuODMxNSAxNy41NTU2QzEyLjk0MTMgMTcuMzkxMSAxMyAxNy4xOTc4IDEzIDE3QzEzIDE2LjczNDggMTIuODk0NiAxNi40ODA1IDEyLjcwNzEgMTYuMjkyOUMxMi41MTk2IDE2LjEwNTQgMTIuMjY1MiAxNiAxMiAxNlpNMjIuNjcgMTcuNDdMMTQuNjIgMy40NzAwM0MxNC4zNTk4IDMuMDAzNTQgMTMuOTc5OCAyLjYxNDk4IDEzLjUxOTIgMi4zNDQ1QzEzLjA1ODYgMi4wNzQwMSAxMi41MzQxIDEuOTMxNCAxMiAxLjkzMTRDMTEuNDY1OSAxLjkzMTQgMTAuOTQxNCAyLjA3NDAxIDEwLjQ4MDggMi4zNDQ1QzEwLjAyMDIgMi42MTQ5OCA5LjY0MDE5IDMuMDAzNTQgOS4zOCAzLjQ3MDAzTDEuMzggMTcuNDdDMS4xMTA3OSAxNy45MjQgMC45NjYxNDEgMTguNDQxIDAuOTYwNjQzIDE4Ljk2ODhDMC45NTUxNDQgMTkuNDk2NiAxLjA4OSAyMC4wMTY2IDEuMzQ4NjggMjAuNDc2MUMxLjYwODM3IDIwLjkzNTYgMS45ODQ3IDIxLjMxODUgMi40Mzk2OCAyMS41ODYxQzIuODk0NjYgMjEuODUzNiAzLjQxMjE4IDIxLjk5NjQgMy45NCAyMkgyMC4wNkMyMC41OTIxIDIyLjAwNTMgMjEuMTE1OSAyMS44Njg5IDIxLjU3NzkgMjEuNjA0OUMyMi4wMzk5IDIxLjM0MSAyMi40MjM0IDIwLjk1ODkgMjIuNjg5IDIwLjQ5NzhDMjIuOTU0NiAyMC4wMzY4IDIzLjA5MjggMTkuNTEzNCAyMy4wODk1IDE4Ljk4MTRDMjMuMDg2MiAxOC40NDkzIDIyLjk0MTQgMTcuOTI3NyAyMi42NyAxNy40N1pNMjAuOTQgMTkuNDdDMjAuODUyMyAxOS42MjYgMjAuNzI0NSAxOS43NTU2IDIwLjU2OTcgMTkuODQ1M0MyMC40MTQ5IDE5LjkzNSAyMC4yMzg5IDE5Ljk4MTUgMjAuMDYgMTkuOThIMy45NEMzLjc2MTExIDE5Ljk4MTUgMy41ODUxIDE5LjkzNSAzLjQzMDMyIDE5Ljg0NTNDMy4yNzU1MyAxOS43NTU2IDMuMTQ3NjUgMTkuNjI2IDMuMDYgMTkuNDdDMi45NzIyMyAxOS4zMTggMi45MjYwMiAxOS4xNDU2IDIuOTI2MDIgMTguOTdDMi45MjYwMiAxOC43OTQ1IDIuOTcyMjMgMTguNjIyIDMuMDYgMTguNDdMMTEuMDYgNC40NzAwM0MxMS4xNDM5IDQuMzA2MjMgMTEuMjcxNCA0LjE2ODc2IDExLjQyODQgNC4wNzI3N0MxMS41ODU1IDMuOTc2NzggMTEuNzY2IDMuOTI1OTkgMTEuOTUgMy45MjU5OUMxMi4xMzQgMy45MjU5OSAxMi4zMTQ1IDMuOTc2NzggMTIuNDcxNiA0LjA3Mjc3QzEyLjYyODYgNC4xNjg3NiAxMi43NTYxIDQuMzA2MjMgMTIuODQgNC40NzAwM0wyMC44OSAxOC40N0MyMC45ODkyIDE4LjYxOTkgMjEuMDQ2MiAxOC43OTM3IDIxLjA1NSAxOC45NzMyQzIxLjA2MzggMTkuMTUyNyAyMS4wMjQxIDE5LjMzMTIgMjAuOTQgMTkuNDlWMTkuNDdaTTEyIDguMDAwMDNDMTEuNzM0OCA4LjAwMDAzIDExLjQ4MDQgOC4xMDUzOCAxMS4yOTI5IDguMjkyOTJDMTEuMTA1NCA4LjQ4MDQ2IDExIDguNzM0ODEgMTEgOS4wMDAwM1YxM0MxMSAxMy4yNjUyIDExLjEwNTQgMTMuNTE5NiAxMS4yOTI5IDEzLjcwNzFDMTEuNDgwNCAxMy44OTQ3IDExLjczNDggMTQgMTIgMTRDMTIuMjY1MiAxNCAxMi41MTk2IDEzLjg5NDcgMTIuNzA3MSAxMy43MDcxQzEyLjg5NDYgMTMuNTE5NiAxMyAxMy4yNjUyIDEzIDEzVjkuMDAwMDNDMTMgOC43MzQ4MSAxMi44OTQ2IDguNDgwNDYgMTIuNzA3MSA4LjI5MjkyQzEyLjUxOTYgOC4xMDUzOCAxMi4yNjUyIDguMDAwMDMgMTIgOC4wMDAwM1oiPjwvcGF0aD48L3N2Zz4=){.starlight-aside__icon}Caution

::: starlight-aside__content
For security, Gemini CLI ignores any `allow`{dir="auto"} decisions or
`yolo`{dir="auto"} mode configurations in extension policies. This
ensures that an extension cannot automatically approve tool calls or
bypass security measures without your confirmation.
:::

**Example `policies.toml`{dir="auto"}**

::: expressive-code
<figure class="frame not-content">
<pre data-language="toml"><code>[[rule]]mcpName = &quot;my_server&quot;toolName = &quot;dangerous_tool&quot;decision = &quot;ask_user&quot;priority = 100
[[safety_checker]]mcpName = &quot;my_server&quot;toolName = &quot;write_data&quot;priority = 200[safety_checker.checker]type = &quot;in-process&quot;name = &quot;allowed-path&quot;required_context = [&quot;environment&quot;]</code></pre>
<div class="copy">
<div>

</div>
</div>
</figure>
:::

::: {.sl-heading-wrapper .level-h3}
### Themes

[[![](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iY3VycmVudGNvbG9yIiBkPSJtMTIuMTEgMTUuMzktMy44OCAzLjg4YTIuNTIgMi41MiAwIDAgMS0zLjUgMCAyLjQ3IDIuNDcgMCAwIDEgMC0zLjVsMy44OC0zLjg4YTEgMSAwIDAgMC0xLjQyLTEuNDJsLTMuODggMy44OWE0LjQ4IDQuNDggMCAwIDAgNi4zMyA2LjMzbDMuODktMy44OGExIDEgMCAxIDAtMS40Mi0xLjQyWm04LjU4LTEyLjA4YTQuNDkgNC40OSAwIDAgMC02LjMzIDBsLTMuODkgMy44OGExIDEgMCAwIDAgMS40MiAxLjQybDMuODgtMy44OGEyLjUyIDIuNTIgMCAwIDEgMy41IDAgMi40NyAyLjQ3IDAgMCAxIDAgMy41bC0zLjg4IDMuODhhMSAxIDAgMSAwIDEuNDIgMS40MmwzLjg4LTMuODlhNC40OSA0LjQ5IDAgMCAwIDAtNi4zM1pNOC44MyAxNS4xN2ExIDEgMCAwIDAgMS4xLjIyIDEgMSAwIDAgMCAuMzItLjIybDQuOTItNC45MmExIDEgMCAwIDAtMS40Mi0xLjQybC00LjkyIDQuOTJhMSAxIDAgMCAwIDAgMS40MloiPjwvcGF0aD48L3N2Zz4=)]{.sl-anchor-icon
aria-hidden="true"}[Section titled
"Themes"]{.sr-only}](#themes){.sl-anchor-link}
:::

Extensions can provide custom themes to personalize the CLI UI. Themes
are defined in the `themes`{dir="auto"} array in
`gemini-extension.json`{dir="auto"}.

**Example**

::: expressive-code
<figure class="frame not-content">
<pre data-language="json"><code>{  &quot;name&quot;: &quot;my-green-extension&quot;,  &quot;version&quot;: &quot;1.0.0&quot;,  &quot;themes&quot;: [    {      &quot;name&quot;: &quot;shades-of-green&quot;,      &quot;type&quot;: &quot;custom&quot;,      &quot;background&quot;: {        &quot;primary&quot;: &quot;#1a362a&quot;      },      &quot;text&quot;: {        &quot;primary&quot;: &quot;#a6e3a1&quot;,        &quot;secondary&quot;: &quot;#6e8e7a&quot;,        &quot;link&quot;: &quot;#89e689&quot;      },      &quot;status&quot;: {        &quot;success&quot;: &quot;#76c076&quot;,        &quot;warning&quot;: &quot;#d9e689&quot;,        &quot;error&quot;: &quot;#b34e4e&quot;      },      &quot;border&quot;: {        &quot;default&quot;: &quot;#4a6c5a&quot;      },      &quot;ui&quot;: {        &quot;comment&quot;: &quot;#6e8e7a&quot;      }    }  ]}</code></pre>
<div class="copy">
<div>

</div>
</div>
</figure>
:::

Custom themes provided by extensions can be selected using the
`/theme`{dir="auto"} command or by setting the `ui.theme`{dir="auto"}
property in your `settings.json`{dir="auto"} file. Note that when
referring to a theme from an extension, the extension name is appended
to the theme name in parentheses, for example,
`shades-of-green (my-green-extension)`{dir="auto"}.

::: {.sl-heading-wrapper .level-h3}
### Conflict resolution

[[![](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iY3VycmVudGNvbG9yIiBkPSJtMTIuMTEgMTUuMzktMy44OCAzLjg4YTIuNTIgMi41MiAwIDAgMS0zLjUgMCAyLjQ3IDIuNDcgMCAwIDEgMC0zLjVsMy44OC0zLjg4YTEgMSAwIDAgMC0xLjQyLTEuNDJsLTMuODggMy44OWE0LjQ4IDQuNDggMCAwIDAgNi4zMyA2LjMzbDMuODktMy44OGExIDEgMCAxIDAtMS40Mi0xLjQyWm04LjU4LTEyLjA4YTQuNDkgNC40OSAwIDAgMC02LjMzIDBsLTMuODkgMy44OGExIDEgMCAwIDAgMS40MiAxLjQybDMuODgtMy44OGEyLjUyIDIuNTIgMCAwIDEgMy41IDAgMi40NyAyLjQ3IDAgMCAxIDAgMy41bC0zLjg4IDMuODhhMSAxIDAgMSAwIDEuNDIgMS40MmwzLjg4LTMuODlhNC40OSA0LjQ5IDAgMCAwIDAtNi4zM1pNOC44MyAxNS4xN2ExIDEgMCAwIDAgMS4xLjIyIDEgMSAwIDAgMCAuMzItLjIybDQuOTItNC45MmExIDEgMCAwIDAtMS40Mi0xLjQybC00LjkyIDQuOTJhMSAxIDAgMCAwIDAgMS40MloiPjwvcGF0aD48L3N2Zz4=)]{.sl-anchor-icon
aria-hidden="true"}[Section titled "Conflict
resolution"]{.sr-only}](#conflict-resolution){.sl-anchor-link}
:::

Extension commands have the lowest precedence. If an extension command
name conflicts with a user or project command, the extension command is
prefixed with the extension name (for example,
`/gcp.deploy`{dir="auto"}) using a dot separator.

::: {.sl-heading-wrapper .level-h2}
## Variables

[[![](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iY3VycmVudGNvbG9yIiBkPSJtMTIuMTEgMTUuMzktMy44OCAzLjg4YTIuNTIgMi41MiAwIDAgMS0zLjUgMCAyLjQ3IDIuNDcgMCAwIDEgMC0zLjVsMy44OC0zLjg4YTEgMSAwIDAgMC0xLjQyLTEuNDJsLTMuODggMy44OWE0LjQ4IDQuNDggMCAwIDAgNi4zMyA2LjMzbDMuODktMy44OGExIDEgMCAxIDAtMS40Mi0xLjQyWm04LjU4LTEyLjA4YTQuNDkgNC40OSAwIDAgMC02LjMzIDBsLTMuODkgMy44OGExIDEgMCAwIDAgMS40MiAxLjQybDMuODgtMy44OGEyLjUyIDIuNTIgMCAwIDEgMy41IDAgMi40NyAyLjQ3IDAgMCAxIDAgMy41bC0zLjg4IDMuODhhMSAxIDAgMSAwIDEuNDIgMS40MmwzLjg4LTMuODlhNC40OSA0LjQ5IDAgMCAwIDAtNi4zM1pNOC44MyAxNS4xN2ExIDEgMCAwIDAgMS4xLjIyIDEgMSAwIDAgMCAuMzItLjIybDQuOTItNC45MmExIDEgMCAwIDAtMS40Mi0xLjQybC00LjkyIDQuOTJhMSAxIDAgMCAwIDAgMS40MloiPjwvcGF0aD48L3N2Zz4=)]{.sl-anchor-icon
aria-hidden="true"}[Section titled
"Variables"]{.sr-only}](#variables){.sl-anchor-link}
:::

Gemini CLI supports variable substitution in
`gemini-extension.json`{dir="auto"} and `hooks/hooks.json`{dir="auto"}.

  Variable                         Description
  -------------------------------- -------------------------------------------------
  `${extensionPath}`{dir="auto"}   The absolute path to the extension's directory.
  `${workspacePath}`{dir="auto"}   The absolute path to the current workspace.
  `${/}`{dir="auto"}               The platform-specific path separator.
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
