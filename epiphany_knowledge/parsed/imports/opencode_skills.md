# opencode_skills.md [DISTILLED]

**Summary:** Details the implementation of Agent Skills in OpenCode, including directory discovery paths (project-local and global), `SKILL.md` frontmatter constraints, the mechanism of dynamically exposing available skills via the `skill` tool description, and granular permission controls (`allow`, `deny`, `ask`) configured in `opencode.json`.

**Source:** https://opencode.ai/docs/skills/

[Skip to content](#_top){.astro-jk53264c}

::: {.page .sl-flex .astro-na5krsqx}
::: {.header .astro-na5krsqx}
::: {.header .sl-flex .astro-mtc2sj33}
::: {.title-wrapper .sl-flex .astro-mtc2sj33}
[![](/docs/_astro/logo-dark.DOStV66V.svg){.light:sl-hidden .print:hidden
.astro-idrpryed width="234" height="42"}
![](/docs/_astro/logo-light.B0yzR0O5.svg){.dark:sl-hidden .print:block
.astro-idrpryed width="234" height="42"} [ OpenCode ]{.sr-only
.astro-idrpryed translate="no"}](/docs/){.site-title .sl-flex
.astro-idrpryed}
:::

::: {.middle-group .sl-flex .astro-mtc2sj33}
[app.header.home](/){.links
.astro-nrmthvxn}[app.header.docs](/docs/){.links .astro-nrmthvxn}
:::

::: {.sl-hidden .md:sl-flex .right-group .astro-mtc2sj33}
::: {.sl-flex .social-icons .astro-mtc2sj33}
[![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9ImFzdHJvLW10YzJzajMzIGFzdHJvLWRiZ3l3bzJzIiB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCIgZmlsbD0iY3VycmVudENvbG9yIiBzdHlsZT0iLS1zbC1pY29uLXNpemU6IDFyZW07Ij48cGF0aCBkPSJNMTIgLjNhMTIgMTIgMCAwIDAtMy44IDIzLjM4Yy42LjEyLjgzLS4yNi44My0uNTdMOSAyMS4wN2MtMy4zNC43Mi00LjA0LTEuNjEtNC4wNC0xLjYxLS41NS0xLjM5LTEuMzQtMS43Ni0xLjM0LTEuNzYtMS4wOC0uNzQuMDktLjczLjA5LS43MyAxLjIuMDkgMS44MyAxLjI0IDEuODMgMS4yNCAxLjA4IDEuODMgMi44MSAxLjMgMy41IDEgLjEtLjc4LjQyLTEuMzEuNzYtMS42MS0yLjY3LS4zLTUuNDctMS4zMy01LjQ3LTUuOTMgMC0xLjMxLjQ3LTIuMzggMS4yNC0zLjIyLS4xNC0uMy0uNTQtMS41Mi4xLTMuMTggMCAwIDEtLjMyIDMuMyAxLjIzYTExLjUgMTEuNSAwIDAgMSA2IDBjMi4yOC0xLjU1IDMuMjktMS4yMyAzLjI5LTEuMjMuNjQgMS42Ni4yNCAyLjg4LjEyIDMuMThhNC42NSA0LjY1IDAgMCAxIDEuMjMgMy4yMmMwIDQuNjEtMi44IDUuNjMtNS40OCA1LjkyLjQyLjM2LjgxIDEuMS44MSAyLjIybC0uMDEgMy4yOWMwIC4zMS4yLjY5LjgyLjU3QTEyIDEyIDAgMCAwIDEyIC4zWiI+PC9wYXRoPjwvc3ZnPg==){.astro-mtc2sj33
.astro-dbgywo2s}](https://github.com/anomalyco/opencode){.astro-mtc2sj33
rel="me" target="_blank"}
[![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9ImFzdHJvLW10YzJzajMzIGFzdHJvLWRiZ3l3bzJzIiB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCIgZmlsbD0iY3VycmVudENvbG9yIiBzdHlsZT0iLS1zbC1pY29uLXNpemU6IDFyZW07Ij48cGF0aCBkPSJNMjAuMzIgNC4zN2ExOS44IDE5LjggMCAwIDAtNC45My0xLjUxIDEzLjc4IDEzLjc4IDAgMCAwLS42NCAxLjI4IDE4LjI3IDE4LjI3IDAgMCAwLTUuNSAwIDEyLjY0IDEyLjY0IDAgMCAwLS42NC0xLjI4aC0uMDVBMTkuNzQgMTkuNzQgMCAwIDAgMy42NCA0LjQgMjAuMjYgMjAuMjYgMCAwIDAgLjExIDE4LjA5bC4wMi4wMmExOS45IDE5LjkgMCAwIDAgNi4wNCAzLjAzbC4wNC0uMDJhMTQuMjQgMTQuMjQgMCAwIDAgMS4yMy0yLjAzLjA4LjA4IDAgMCAwLS4wNS0uMDcgMTMuMSAxMy4xIDAgMCAxLTEuOS0uOTIuMDguMDggMCAwIDEgLjAyLS4xIDEwLjIgMTAuMiAwIDAgMCAuNDEtLjMxaC4wNGExNC4yIDE0LjIgMCAwIDAgMTIuMSAwbC4wNC4wMWE5LjYzIDkuNjMgMCAwIDAgLjQuMzIuMDguMDggMCAwIDEtLjAzLjEgMTIuMjkgMTIuMjkgMCAwIDEtMS45LjkxLjA4LjA4IDAgMCAwLS4wMi4xIDE1Ljk3IDE1Ljk3IDAgMCAwIDEuMjcgMi4wMWguMDRhMTkuODQgMTkuODQgMCAwIDAgNi4wMy0zLjA1di0uMDNhMjAuMTIgMjAuMTIgMCAwIDAtMy41Ny0xMy42OVpNOC4wMiAxNS4zM2MtMS4xOCAwLTIuMTYtMS4wOC0yLjE2LTIuNDIgMC0xLjMzLjk2LTIuNDIgMi4xNi0yLjQyIDEuMjEgMCAyLjE4IDEuMSAyLjE2IDIuNDIgMCAxLjM0LS45NiAyLjQyLTIuMTYgMi40MlptNy45NyAwYy0xLjE4IDAtMi4xNS0xLjA4LTIuMTUtMi40MiAwLTEuMzMuOTUtMi40MiAyLjE1LTIuNDIgMS4yMiAwIDIuMTggMS4xIDIuMTYgMi40MiAwIDEuMzQtLjk0IDIuNDItMi4xNiAyLjQyWiI+PC9wYXRoPjwvc3ZnPg==){.astro-mtc2sj33
.astro-dbgywo2s}](https://opencode.ai/discord){.astro-mtc2sj33 rel="me"
target="_blank"}
:::

![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9ImFzdHJvLWFtNndhNjZhIGFzdHJvLWRiZ3l3bzJzIiB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCIgZmlsbD0iY3VycmVudENvbG9yIiBzdHlsZT0iLS1zbC1pY29uLXNpemU6IDFlbTsiPjxwYXRoIGQ9Ik0yMS43MSAyMC4yOSAxOCAxNi42MUE5IDkgMCAxIDAgMTYuNjEgMThsMy42OCAzLjY4YS45OTkuOTk5IDAgMCAwIDEuNDIgMCAxIDEgMCAwIDAgMC0xLjM5Wk0xMSAxOGE3IDcgMCAxIDEgMC0xNCA3IDcgMCAwIDEgMCAxNFoiPjwvcGF0aD48L3N2Zz4=){.astro-am6wa66a
.astro-dbgywo2s} [Search]{.sl-hidden .md:sl-block .astro-am6wa66a
aria-hidden="true"} [ [Ctrl]{.kbd .astro-am6wa66a}[K]{.kbd
.astro-am6wa66a} ]{.kbd .sl-hidden .md:sl-flex .astro-am6wa66a
style="display: none;"}

::: {.dialog-frame .sl-flex .astro-am6wa66a}
Cancel

::: {.search-container .astro-am6wa66a}
::: {#starlight__search .astro-am6wa66a}
:::
:::
:::
:::
:::
:::

![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9Im9wZW4tbWVudSBhc3Ryby1jaWh3amN1ZSBhc3Ryby1kYmd5d28ycyIgd2lkdGg9IjE2IiBoZWlnaHQ9IjE2IiB2aWV3Ym94PSIwIDAgMjQgMjQiIGZpbGw9ImN1cnJlbnRDb2xvciIgc3R5bGU9Ii0tc2wtaWNvbi1zaXplOiAxZW07Ij48cGF0aCBkPSJNMyA4aDE4YTEgMSAwIDEgMCAwLTJIM2ExIDEgMCAwIDAgMCAyWm0xOCA4SDNhMSAxIDAgMCAwIDAgMmgxOGExIDEgMCAwIDAgMC0yWm0wLTVIM2ExIDEgMCAwIDAgMCAyaDE4YTEgMSAwIDAgMCAwLTJaIj48L3BhdGg+PC9zdmc+){.open-menu
.astro-cihwjcue .astro-dbgywo2s}
![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9ImNsb3NlLW1lbnUgYXN0cm8tY2lod2pjdWUgYXN0cm8tZGJneXdvMnMiIHdpZHRoPSIxNiIgaGVpZ2h0PSIxNiIgdmlld2JveD0iMCAwIDI0IDI0IiBmaWxsPSJjdXJyZW50Q29sb3IiIHN0eWxlPSItLXNsLWljb24tc2l6ZTogMWVtOyI+PHBhdGggZD0ibTEzLjQxIDEyIDYuMy02LjI5YTEuMDA0IDEuMDA0IDAgMSAwLTEuNDItMS40MkwxMiAxMC41OWwtNi4yOS02LjNhMS4wMDQgMS4wMDQgMCAwIDAtMS40MiAxLjQybDYuMyA2LjI5LTYuMyA2LjI5YTEgMSAwIDAgMCAwIDEuNDIuOTk4Ljk5OCAwIDAgMCAxLjQyIDBsNi4yOS02LjMgNi4yOSA2LjNhLjk5OS45OTkgMCAwIDAgMS40MiAwIDEgMSAwIDAgMCAwLTEuNDJMMTMuNDEgMTJaIj48L3BhdGg+PC9zdmc+){.close-menu
.astro-cihwjcue .astro-dbgywo2s}

::: {#starlight__sidebar .sidebar-pane .astro-na5krsqx}
::: {.sidebar-content .sl-flex .astro-na5krsqx}
-   [[Intro]{.astro-ggcky6yv}](/docs/){.large .astro-ggcky6yv
    aria-current="false"}

-   [[Config]{.astro-ggcky6yv}](/docs/config/){.large .astro-ggcky6yv
    aria-current="false"}

-   [[Providers]{.astro-ggcky6yv}](/docs/providers/){.large
    .astro-ggcky6yv aria-current="false"}

-   [[Network]{.astro-ggcky6yv}](/docs/network/){.large .astro-ggcky6yv
    aria-current="false"}

-   [[Enterprise]{.astro-ggcky6yv}](/docs/enterprise/){.large
    .astro-ggcky6yv aria-current="false"}

-   [[Troubleshooting]{.astro-ggcky6yv}](/docs/troubleshooting/){.large
    .astro-ggcky6yv aria-current="false"}

-   [[Windows]{.astro-ggcky6yv}](/docs/windows-wsl){.large
    .astro-ggcky6yv aria-current="false"}

-   ::: {.group-label .astro-ggcky6yv}
    [Usage]{.large .astro-ggcky6yv}
    :::

    ![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9ImNhcmV0IGFzdHJvLWdnY2t5Nnl2IGFzdHJvLWRiZ3l3bzJzIiB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCIgZmlsbD0iY3VycmVudENvbG9yIiBzdHlsZT0iLS1zbC1pY29uLXNpemU6IDEuMjVyZW07Ij48cGF0aCBkPSJtMTQuODMgMTEuMjktNC4yNC00LjI0YTEgMSAwIDEgMC0xLjQyIDEuNDFMMTIuNzEgMTJsLTMuNTQgMy41NGExIDEgMCAwIDAgMCAxLjQxIDEgMSAwIDAgMCAuNzEuMjkgMSAxIDAgMCAwIC43MS0uMjlsNC4yNC00LjI0YTEuMDAyIDEuMDAyIDAgMCAwIDAtMS40MloiPjwvcGF0aD48L3N2Zz4=){.caret
    .astro-ggcky6yv .astro-dbgywo2s}
    -   [[Go]{.astro-ggcky6yv}](/docs/go/){.astro-ggcky6yv
        aria-current="false"}
    -   [[TUI]{.astro-ggcky6yv}](/docs/tui/){.astro-ggcky6yv
        aria-current="false"}
    -   [[CLI]{.astro-ggcky6yv}](/docs/cli/){.astro-ggcky6yv
        aria-current="false"}
    -   [[Web]{.astro-ggcky6yv}](/docs/web/){.astro-ggcky6yv
        aria-current="false"}
    -   [[IDE]{.astro-ggcky6yv}](/docs/ide/){.astro-ggcky6yv
        aria-current="false"}
    -   [[Zen]{.astro-ggcky6yv}](/docs/zen/){.astro-ggcky6yv
        aria-current="false"}
    -   [[Share]{.astro-ggcky6yv}](/docs/share/){.astro-ggcky6yv
        aria-current="false"}
    -   [[GitHub]{.astro-ggcky6yv}](/docs/github/){.astro-ggcky6yv
        aria-current="false"}
    -   [[GitLab]{.astro-ggcky6yv}](/docs/gitlab/){.astro-ggcky6yv
        aria-current="false"}

-   ::: {.group-label .astro-ggcky6yv}
    [Configure]{.large .astro-ggcky6yv}
    :::

    ![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9ImNhcmV0IGFzdHJvLWdnY2t5Nnl2IGFzdHJvLWRiZ3l3bzJzIiB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCIgZmlsbD0iY3VycmVudENvbG9yIiBzdHlsZT0iLS1zbC1pY29uLXNpemU6IDEuMjVyZW07Ij48cGF0aCBkPSJtMTQuODMgMTEuMjktNC4yNC00LjI0YTEgMSAwIDEgMC0xLjQyIDEuNDFMMTIuNzEgMTJsLTMuNTQgMy41NGExIDEgMCAwIDAgMCAxLjQxIDEgMSAwIDAgMCAuNzEuMjkgMSAxIDAgMCAwIC43MS0uMjlsNC4yNC00LjI0YTEuMDAyIDEuMDAyIDAgMCAwIDAtMS40MloiPjwvcGF0aD48L3N2Zz4=){.caret
    .astro-ggcky6yv .astro-dbgywo2s}
    -   [[Tools]{.astro-ggcky6yv}](/docs/tools/){.astro-ggcky6yv
        aria-current="false"}
    -   [[Rules]{.astro-ggcky6yv}](/docs/rules/){.astro-ggcky6yv
        aria-current="false"}
    -   [[Agents]{.astro-ggcky6yv}](/docs/agents/){.astro-ggcky6yv
        aria-current="false"}
    -   [[Models]{.astro-ggcky6yv}](/docs/models/){.astro-ggcky6yv
        aria-current="false"}
    -   [[Themes]{.astro-ggcky6yv}](/docs/themes/){.astro-ggcky6yv
        aria-current="false"}
    -   [[Keybinds]{.astro-ggcky6yv}](/docs/keybinds/){.astro-ggcky6yv
        aria-current="false"}
    -   [[Commands]{.astro-ggcky6yv}](/docs/commands/){.astro-ggcky6yv
        aria-current="false"}
    -   [[Formatters]{.astro-ggcky6yv}](/docs/formatters/){.astro-ggcky6yv
        aria-current="false"}
    -   [[Permissions]{.astro-ggcky6yv}](/docs/permissions/){.astro-ggcky6yv
        aria-current="false"}
    -   [[LSP Servers]{.astro-ggcky6yv}](/docs/lsp/){.astro-ggcky6yv
        aria-current="false"}
    -   [[MCP
        servers]{.astro-ggcky6yv}](/docs/mcp-servers/){.astro-ggcky6yv
        aria-current="false"}
    -   [[ACP Support]{.astro-ggcky6yv}](/docs/acp/){.astro-ggcky6yv
        aria-current="false"}
    -   [[Agent Skills]{.astro-ggcky6yv}](/docs/skills/){.astro-ggcky6yv
        aria-current="page"}
    -   [[Custom
        Tools]{.astro-ggcky6yv}](/docs/custom-tools/){.astro-ggcky6yv
        aria-current="false"}

-   ::: {.group-label .astro-ggcky6yv}
    [Develop]{.large .astro-ggcky6yv}
    :::

    ![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9ImNhcmV0IGFzdHJvLWdnY2t5Nnl2IGFzdHJvLWRiZ3l3bzJzIiB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCIgZmlsbD0iY3VycmVudENvbG9yIiBzdHlsZT0iLS1zbC1pY29uLXNpemU6IDEuMjVyZW07Ij48cGF0aCBkPSJtMTQuODMgMTEuMjktNC4yNC00LjI0YTEgMSAwIDEgMC0xLjQyIDEuNDFMMTIuNzEgMTJsLTMuNTQgMy41NGExIDEgMCAwIDAgMCAxLjQxIDEgMSAwIDAgMCAuNzEuMjkgMSAxIDAgMCAwIC43MS0uMjlsNC4yNC00LjI0YTEuMDAyIDEuMDAyIDAgMCAwIDAtMS40MloiPjwvcGF0aD48L3N2Zz4=){.caret
    .astro-ggcky6yv .astro-dbgywo2s}
    -   [[SDK]{.astro-ggcky6yv}](/docs/sdk/){.astro-ggcky6yv
        aria-current="false"}
    -   [[Server]{.astro-ggcky6yv}](/docs/server/){.astro-ggcky6yv
        aria-current="false"}
    -   [[Plugins]{.astro-ggcky6yv}](/docs/plugins/){.astro-ggcky6yv
        aria-current="false"}
    -   [[Ecosystem]{.astro-ggcky6yv}](/docs/ecosystem/){.astro-ggcky6yv
        aria-current="false"}

::: md:sl-hidden
::: {.mobile-preferences .sl-flex .astro-hn22yo3f}
::: {.social-icons .astro-hn22yo3f}
[[GitHub]{.sr-only
.astro-wuribpbk}![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9ImFzdHJvLXd1cmlicGJrIGFzdHJvLWRiZ3l3bzJzIiB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCIgZmlsbD0iY3VycmVudENvbG9yIiBzdHlsZT0iLS1zbC1pY29uLXNpemU6IDFlbTsiPjxwYXRoIGQ9Ik0xMiAuM2ExMiAxMiAwIDAgMC0zLjggMjMuMzhjLjYuMTIuODMtLjI2LjgzLS41N0w5IDIxLjA3Yy0zLjM0LjcyLTQuMDQtMS42MS00LjA0LTEuNjEtLjU1LTEuMzktMS4zNC0xLjc2LTEuMzQtMS43Ni0xLjA4LS43NC4wOS0uNzMuMDktLjczIDEuMi4wOSAxLjgzIDEuMjQgMS44MyAxLjI0IDEuMDggMS44MyAyLjgxIDEuMyAzLjUgMSAuMS0uNzguNDItMS4zMS43Ni0xLjYxLTIuNjctLjMtNS40Ny0xLjMzLTUuNDctNS45MyAwLTEuMzEuNDctMi4zOCAxLjI0LTMuMjItLjE0LS4zLS41NC0xLjUyLjEtMy4xOCAwIDAgMS0uMzIgMy4zIDEuMjNhMTEuNSAxMS41IDAgMCAxIDYgMGMyLjI4LTEuNTUgMy4yOS0xLjIzIDMuMjktMS4yMy42NCAxLjY2LjI0IDIuODguMTIgMy4xOGE0LjY1IDQuNjUgMCAwIDEgMS4yMyAzLjIyYzAgNC42MS0yLjggNS42My01LjQ4IDUuOTIuNDIuMzYuODEgMS4xLjgxIDIuMjJsLS4wMSAzLjI5YzAgLjMxLjIuNjkuODIuNTdBMTIgMTIgMCAwIDAgMTIgLjNaIj48L3BhdGg+PC9zdmc+){.astro-wuribpbk
.astro-dbgywo2s}](https://github.com/anomalyco/opencode){.sl-flex
.astro-wuribpbk rel="me"}[[Discord]{.sr-only
.astro-wuribpbk}![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9ImFzdHJvLXd1cmlicGJrIGFzdHJvLWRiZ3l3bzJzIiB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCIgZmlsbD0iY3VycmVudENvbG9yIiBzdHlsZT0iLS1zbC1pY29uLXNpemU6IDFlbTsiPjxwYXRoIGQ9Ik0yMC4zMiA0LjM3YTE5LjggMTkuOCAwIDAgMC00LjkzLTEuNTEgMTMuNzggMTMuNzggMCAwIDAtLjY0IDEuMjggMTguMjcgMTguMjcgMCAwIDAtNS41IDAgMTIuNjQgMTIuNjQgMCAwIDAtLjY0LTEuMjhoLS4wNUExOS43NCAxOS43NCAwIDAgMCAzLjY0IDQuNCAyMC4yNiAyMC4yNiAwIDAgMCAuMTEgMTguMDlsLjAyLjAyYTE5LjkgMTkuOSAwIDAgMCA2LjA0IDMuMDNsLjA0LS4wMmExNC4yNCAxNC4yNCAwIDAgMCAxLjIzLTIuMDMuMDguMDggMCAwIDAtLjA1LS4wNyAxMy4xIDEzLjEgMCAwIDEtMS45LS45Mi4wOC4wOCAwIDAgMSAuMDItLjEgMTAuMiAxMC4yIDAgMCAwIC40MS0uMzFoLjA0YTE0LjIgMTQuMiAwIDAgMCAxMi4xIDBsLjA0LjAxYTkuNjMgOS42MyAwIDAgMCAuNC4zMi4wOC4wOCAwIDAgMS0uMDMuMSAxMi4yOSAxMi4yOSAwIDAgMS0xLjkuOTEuMDguMDggMCAwIDAtLjAyLjEgMTUuOTcgMTUuOTcgMCAwIDAgMS4yNyAyLjAxaC4wNGExOS44NCAxOS44NCAwIDAgMCA2LjAzLTMuMDV2LS4wM2EyMC4xMiAyMC4xMiAwIDAgMC0zLjU3LTEzLjY5Wk04LjAyIDE1LjMzYy0xLjE4IDAtMi4xNi0xLjA4LTIuMTYtMi40MiAwLTEuMzMuOTYtMi40MiAyLjE2LTIuNDIgMS4yMSAwIDIuMTggMS4xIDIuMTYgMi40MiAwIDEuMzQtLjk2IDIuNDItMi4xNiAyLjQyWm03Ljk3IDBjLTEuMTggMC0yLjE1LTEuMDgtMi4xNS0yLjQyIDAtMS4zMy45NS0yLjQyIDIuMTUtMi40MiAxLjIyIDAgMi4xOCAxLjEgMi4xNiAyLjQyIDAgMS4zNC0uOTQgMi40Mi0yLjE2IDIuNDJaIj48L3BhdGg+PC9zdmc+){.astro-wuribpbk
.astro-dbgywo2s}](https://opencode.ai/discord){.sl-flex .astro-wuribpbk
rel="me"}
:::

[Select theme]{.sr-only .astro-yk3v7tmu}
![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9Imljb24gbGFiZWwtaWNvbiBhc3Ryby15azN2N3RtdSBhc3Ryby1kYmd5d28ycyIgd2lkdGg9IjE2IiBoZWlnaHQ9IjE2IiB2aWV3Ym94PSIwIDAgMjQgMjQiIGZpbGw9ImN1cnJlbnRDb2xvciIgc3R5bGU9Ii0tc2wtaWNvbi1zaXplOiAxZW07Ij48cGF0aCBkPSJNMjEgMTRoLTFWN2EzIDMgMCAwIDAtMy0zSDdhMyAzIDAgMCAwLTMgM3Y3SDNhMSAxIDAgMCAwLTEgMXYyYTMgMyAwIDAgMCAzIDNoMTRhMyAzIDAgMCAwIDMtM3YtMmExIDEgMCAwIDAtMS0xWk02IDdhMSAxIDAgMCAxIDEtMWgxMGExIDEgMCAwIDEgMSAxdjdINlY3Wm0xNCAxMGExIDEgMCAwIDEtMSAxSDVhMSAxIDAgMCAxLTEtMXYtMWgxNnYxWiI+PC9wYXRoPjwvc3ZnPg==){.icon
.label-icon .astro-yk3v7tmu .astro-dbgywo2s} DarkLightAuto
![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9Imljb24gY2FyZXQgYXN0cm8teWszdjd0bXUgYXN0cm8tZGJneXdvMnMiIHdpZHRoPSIxNiIgaGVpZ2h0PSIxNiIgdmlld2JveD0iMCAwIDI0IDI0IiBmaWxsPSJjdXJyZW50Q29sb3IiIHN0eWxlPSItLXNsLWljb24tc2l6ZTogMWVtOyI+PHBhdGggZD0iTTE3IDkuMTdhMSAxIDAgMCAwLTEuNDEgMEwxMiAxMi43MSA4LjQ2IDkuMTdhMSAxIDAgMSAwLTEuNDEgMS40Mmw0LjI0IDQuMjRhMS4wMDIgMS4wMDIgMCAwIDAgMS40MiAwTDE3IDEwLjU5YTEuMDAyIDEuMDAyIDAgMCAwIDAtMS40MloiPjwvcGF0aD48L3N2Zz4=){.icon
.caret .astro-yk3v7tmu .astro-dbgywo2s}

[Select language]{.sr-only .astro-yk3v7tmu}
![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9Imljb24gbGFiZWwtaWNvbiBhc3Ryby15azN2N3RtdSBhc3Ryby1kYmd5d28ycyIgd2lkdGg9IjE2IiBoZWlnaHQ9IjE2IiB2aWV3Ym94PSIwIDAgMjQgMjQiIGZpbGw9ImN1cnJlbnRDb2xvciIgc3R5bGU9Ii0tc2wtaWNvbi1zaXplOiAxZW07Ij48cGF0aCBmaWxsLXJ1bGU9ImV2ZW5vZGQiIGQ9Ik04LjUxNiAzYS45NC45NCAwIDAgMC0uOTQxLjk0djEuMTVIMi45NGEuOTQuOTQgMCAxIDAgMCAxLjg4Mmg3LjM2MmE3LjQyMiA3LjQyMiAwIDAgMS0xLjc4NyAzLjk1OCA3LjQyIDcuNDIgMCAwIDEtMS40MjItMi40MjUuOTQuOTQgMCAxIDAtMS43NzQuNjI3IDkuMzAzIDkuMzAzIDAgMCAwIDEuNzg1IDMuMDQzIDcuNDIyIDcuNDIyIDAgMCAxLTQuMTY0IDEuMjc4Ljk0Ljk0IDAgMSAwIDAgMS44ODEgOS4zMDMgOS4zMDMgMCAwIDAgNS41NzUtMS44NTUgOS4zMDMgOS4zMDMgMCAwIDAgNC4xMSAxLjc0bC0uNzYzIDEuNTI1YS45NjguOTY4IDAgMCAwLS4wMTYuMDM0bC0xLjM4NSAyLjc3YS45NC45NCAwIDEgMCAxLjY4My44NDFsMS4xMzMtMi4yNjdoNS44MDZsMS4xMzQgMi4yNjdhLjk0Ljk0IDAgMCAwIDEuNjgzLS44NDFsLTEuMzg1LTIuNzY5YS45NS45NSAwIDAgMC0uMDE4LS4wMzZsLTMuNDc2LTYuOTUxYS45NC45NCAwIDAgMC0xLjY4MiAwbC0xLjgyIDMuNjM5YTcuNDIzIDcuNDIzIDAgMCAxLTMuNTkzLTEuMjU2IDkuMzAzIDkuMzAzIDAgMCAwIDIuMjctNS4yMDNoMS44OTRhLjk0Ljk0IDAgMCAwIDAtMS44ODFIOS40NTZWMy45NEEuOTQuOTQgMCAwIDAgOC41MTYgM1ptNi40MjYgMTEuNzk0YTEuMDY4IDEuMDY4IDAgMCAxLS4wMi4wMzlsLS43MDMgMS40MDdoMy45MjRsLTEuOTYyLTMuOTI0LTEuMjQgMi40NzhaIiBjbGlwLXJ1bGU9ImV2ZW5vZGQiPjwvcGF0aD48L3N2Zz4=){.icon
.label-icon .astro-yk3v7tmu .astro-dbgywo2s}
EnglishالعربيةBosanskiDanskDeutschEspañolFrançaisItaliano日本語한국어Norsk
BokmålPolskiPortuguês (Brasil)РусскийไทยTürkçe简体中文繁體中文
![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9Imljb24gY2FyZXQgYXN0cm8teWszdjd0bXUgYXN0cm8tZGJneXdvMnMiIHdpZHRoPSIxNiIgaGVpZ2h0PSIxNiIgdmlld2JveD0iMCAwIDI0IDI0IiBmaWxsPSJjdXJyZW50Q29sb3IiIHN0eWxlPSItLXNsLWljb24tc2l6ZTogMWVtOyI+PHBhdGggZD0iTTE3IDkuMTdhMSAxIDAgMCAwLTEuNDEgMEwxMiAxMi43MSA4LjQ2IDkuMTdhMSAxIDAgMSAwLTEuNDEgMS40Mmw0LjI0IDQuMjRhMS4wMDIgMS4wMDIgMCAwIDAgMS40MiAwTDE3IDEwLjU5YTEuMDAyIDEuMDAyIDAgMCAwIDAtMS40MloiPjwvcGF0aD48L3N2Zz4=){.icon
.caret .astro-yk3v7tmu .astro-dbgywo2s}
:::
:::
:::
:::

::: {.main-frame .astro-na5krsqx}
::: {.lg:sl-flex .astro-hlhocvxd}
::: {.right-sidebar .astro-hlhocvxd}
::: {.lg:sl-hidden .astro-cumn5vcy}
::: {.toggle .sl-flex .astro-itzxs6wz}
On this
page![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9ImNhcmV0IGFzdHJvLWl0enhzNnd6IGFzdHJvLWRiZ3l3bzJzIiB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCIgZmlsbD0iY3VycmVudENvbG9yIiBzdHlsZT0iLS1zbC1pY29uLXNpemU6IDFyZW07Ij48cGF0aCBkPSJtMTQuODMgMTEuMjktNC4yNC00LjI0YTEgMSAwIDEgMC0xLjQyIDEuNDFMMTIuNzEgMTJsLTMuNTQgMy41NGExIDEgMCAwIDAgMCAxLjQxIDEgMSAwIDAgMCAuNzEuMjkgMSAxIDAgMCAwIC43MS0uMjlsNC4yNC00LjI0YTEuMDAyIDEuMDAyIDAgMCAwIDAtMS40MloiPjwvcGF0aD48L3N2Zz4=){.caret
.astro-itzxs6wz .astro-dbgywo2s}
:::

[]{.display-current .astro-itzxs6wz}

::: {.dropdown .astro-itzxs6wz}
-   [[Overview]{.astro-dah7nouw
    style="--depth: 0;"}](#_top){.astro-dah7nouw style="--depth: 0;"}
-   [[Place files]{.astro-dah7nouw
    style="--depth: 0;"}](#place-files){.astro-dah7nouw
    style="--depth: 0;"}
-   [[Understand discovery]{.astro-dah7nouw
    style="--depth: 0;"}](#understand-discovery){.astro-dah7nouw
    style="--depth: 0;"}
-   [[Write frontmatter]{.astro-dah7nouw
    style="--depth: 0;"}](#write-frontmatter){.astro-dah7nouw
    style="--depth: 0;"}
-   [[Validate names]{.astro-dah7nouw
    style="--depth: 0;"}](#validate-names){.astro-dah7nouw
    style="--depth: 0;"}
-   [[Follow length rules]{.astro-dah7nouw
    style="--depth: 0;"}](#follow-length-rules){.astro-dah7nouw
    style="--depth: 0;"}
-   [[Use an example]{.astro-dah7nouw
    style="--depth: 0;"}](#use-an-example){.astro-dah7nouw
    style="--depth: 0;"}
-   [[Recognize tool description]{.astro-dah7nouw
    style="--depth: 0;"}](#recognize-tool-description){.astro-dah7nouw
    style="--depth: 0;"}
-   [[Configure permissions]{.astro-dah7nouw
    style="--depth: 0;"}](#configure-permissions){.astro-dah7nouw
    style="--depth: 0;"}
-   [[Override per agent]{.astro-dah7nouw
    style="--depth: 0;"}](#override-per-agent){.astro-dah7nouw
    style="--depth: 0;"}
-   [[Disable the skill tool]{.astro-dah7nouw
    style="--depth: 0;"}](#disable-the-skill-tool){.astro-dah7nouw
    style="--depth: 0;"}
-   [[Troubleshoot loading]{.astro-dah7nouw
    style="--depth: 0;"}](#troubleshoot-loading){.astro-dah7nouw
    style="--depth: 0;"}
:::
:::

::: {.right-sidebar-panel .sl-hidden .lg:sl-block .astro-cumn5vcy}
::: {.sl-container .astro-cumn5vcy}
## On this page {#starlight__on-this-page}

-   [[Overview]{.astro-dah7nouw
    style="--depth: 0;"}](#_top){.astro-dah7nouw style="--depth: 0;"}
-   [[Place files]{.astro-dah7nouw
    style="--depth: 0;"}](#place-files){.astro-dah7nouw
    style="--depth: 0;"}
-   [[Understand discovery]{.astro-dah7nouw
    style="--depth: 0;"}](#understand-discovery){.astro-dah7nouw
    style="--depth: 0;"}
-   [[Write frontmatter]{.astro-dah7nouw
    style="--depth: 0;"}](#write-frontmatter){.astro-dah7nouw
    style="--depth: 0;"}
-   [[Validate names]{.astro-dah7nouw
    style="--depth: 0;"}](#validate-names){.astro-dah7nouw
    style="--depth: 0;"}
-   [[Follow length rules]{.astro-dah7nouw
    style="--depth: 0;"}](#follow-length-rules){.astro-dah7nouw
    style="--depth: 0;"}
-   [[Use an example]{.astro-dah7nouw
    style="--depth: 0;"}](#use-an-example){.astro-dah7nouw
    style="--depth: 0;"}
-   [[Recognize tool description]{.astro-dah7nouw
    style="--depth: 0;"}](#recognize-tool-description){.astro-dah7nouw
    style="--depth: 0;"}
-   [[Configure permissions]{.astro-dah7nouw
    style="--depth: 0;"}](#configure-permissions){.astro-dah7nouw
    style="--depth: 0;"}
-   [[Override per agent]{.astro-dah7nouw
    style="--depth: 0;"}](#override-per-agent){.astro-dah7nouw
    style="--depth: 0;"}
-   [[Disable the skill tool]{.astro-dah7nouw
    style="--depth: 0;"}](#disable-the-skill-tool){.astro-dah7nouw
    style="--depth: 0;"}
-   [[Troubleshoot loading]{.astro-dah7nouw
    style="--depth: 0;"}](#troubleshoot-loading){.astro-dah7nouw
    style="--depth: 0;"}
:::
:::
:::

::: {.main-pane .astro-hlhocvxd}
::: {.astro-ynnt4rov role="main" pagefind-body="" lang="en" dir="ltr"}
::: {.content-panel .astro-b7rksiuz}
::: {.sl-container .astro-b7rksiuz}
# Agent Skills {#_top .astro-kc6gb2go}

Define reusable behavior via SKILL.md definitions
:::
:::

::: {.content-panel .astro-b7rksiuz}
::: {.sl-container .astro-b7rksiuz}
::: sl-markdown-content
Agent skills let OpenCode discover reusable instructions from your repo
or home directory. Skills are loaded on-demand via the native
`skill`{dir="auto"} tool---agents see available skills and can load the
full content when needed.

------------------------------------------------------------------------

## [Place files](#place-files)

Create one folder per skill name and put a `SKILL.md`{dir="auto"} inside
it. OpenCode searches these locations:

-   Project config: `.opencode/skills/<name>/SKILL.md`{dir="auto"}
-   Global config:
    `~/.config/opencode/skills/<name>/SKILL.md`{dir="auto"}
-   Project Claude-compatible:
    `.claude/skills/<name>/SKILL.md`{dir="auto"}
-   Global Claude-compatible:
    `~/.claude/skills/<name>/SKILL.md`{dir="auto"}
-   Project agent-compatible:
    `.agents/skills/<name>/SKILL.md`{dir="auto"}
-   Global agent-compatible:
    `~/.agents/skills/<name>/SKILL.md`{dir="auto"}

------------------------------------------------------------------------

## [Understand discovery](#understand-discovery)

For project-local paths, OpenCode walks up from your current working
directory until it reaches the git worktree. It loads any matching
`skills/*/SKILL.md`{dir="auto"} in `.opencode/`{dir="auto"} and any
matching `.claude/skills/*/SKILL.md`{dir="auto"} or
`.agents/skills/*/SKILL.md`{dir="auto"} along the way.

Global definitions are also loaded from
`~/.config/opencode/skills/*/SKILL.md`{dir="auto"},
`~/.claude/skills/*/SKILL.md`{dir="auto"}, and
`~/.agents/skills/*/SKILL.md`{dir="auto"}.

------------------------------------------------------------------------

## [Write frontmatter](#write-frontmatter)

Each `SKILL.md`{dir="auto"} must start with YAML frontmatter. Only these
fields are recognized:

-   `name`{dir="auto"} (required)
-   `description`{dir="auto"} (required)
-   `license`{dir="auto"} (optional)
-   `compatibility`{dir="auto"} (optional)
-   `metadata`{dir="auto"} (optional, string-to-string map)

Unknown frontmatter fields are ignored.

------------------------------------------------------------------------

## [Validate names](#validate-names)

`name`{dir="auto"} must:

-   Be 1--64 characters
-   Be lowercase alphanumeric with single hyphen separators
-   Not start or end with `-`{dir="auto"}
-   Not contain consecutive `--`{dir="auto"}
-   Match the directory name that contains `SKILL.md`{dir="auto"}

Equivalent regex:

::: expressive-code
<figure class="frame not-content">
<pre data-language="text"><code>^[a-z0-9]+(-[a-z0-9]+)*$</code></pre>
<div class="copy">
<div aria-live="polite">

</div>
<div>

</div>
</div>
</figure>
:::

------------------------------------------------------------------------

## [Follow length rules](#follow-length-rules)

`description`{dir="auto"} must be 1-1024 characters. Keep it specific
enough for the agent to choose correctly.

------------------------------------------------------------------------

## [Use an example](#use-an-example)

Create `.opencode/skills/git-release/SKILL.md`{dir="auto"} like this:

::: expressive-code
<figure class="frame not-content">
<pre data-language="markdown"><code>---name: git-releasedescription: Create consistent releases and changelogslicense: MITcompatibility: opencodemetadata:  audience: maintainers  workflow: github---
## What I do
- Draft release notes from merged PRs- Propose a version bump- Provide a copy-pasteable `gh release create` command
## When to use me
Use this when you are preparing a tagged release.Ask clarifying questions if the target versioning scheme is unclear.</code></pre>
<div class="copy">
<div aria-live="polite">

</div>
<div>

</div>
</div>
</figure>
:::

------------------------------------------------------------------------

## [Recognize tool description](#recognize-tool-description)

OpenCode lists available skills in the `skill`{dir="auto"} tool
description. Each entry includes the skill name and description:

::: expressive-code
<figure class="frame not-content">
<pre data-language="xml"><code>&lt;available_skills&gt;  &lt;skill&gt;    &lt;name&gt;git-release&lt;/name&gt;    &lt;description&gt;Create consistent releases and changelogs&lt;/description&gt;  &lt;/skill&gt;&lt;/available_skills&gt;</code></pre>
<div class="copy">
<div aria-live="polite">

</div>
<div>

</div>
</div>
</figure>
:::

The agent loads a skill by calling the tool:

::: expressive-code
<figure class="frame not-content">
<pre data-language="plaintext"><code>skill({ name: &quot;git-release&quot; })</code></pre>
<div class="copy">
<div aria-live="polite">

</div>
<div>

</div>
</div>
</figure>
:::

------------------------------------------------------------------------

## [Configure permissions](#configure-permissions)

Control which skills agents can access using pattern-based permissions
in `opencode.json`{dir="auto"}:

::: expressive-code
<figure class="frame not-content">
<pre data-language="json"><code>{  &quot;permission&quot;: {    &quot;skill&quot;: {      &quot;*&quot;: &quot;allow&quot;,      &quot;pr-review&quot;: &quot;allow&quot;,      &quot;internal-*&quot;: &quot;deny&quot;,      &quot;experimental-*&quot;: &quot;ask&quot;    }  }}</code></pre>
<div class="copy">
<div aria-live="polite">

</div>
<div>

</div>
</div>
</figure>
:::

  Permission            Behavior
  --------------------- -------------------------------------------
  `allow`{dir="auto"}   Skill loads immediately
  `deny`{dir="auto"}    Skill hidden from agent, access rejected
  `ask`{dir="auto"}     User prompted for approval before loading

Patterns support wildcards: `internal-*`{dir="auto"} matches
`internal-docs`{dir="auto"}, `internal-tools`{dir="auto"}, etc.

------------------------------------------------------------------------

## [Override per agent](#override-per-agent)

Give specific agents different permissions than the global defaults.

**For custom agents** (in agent frontmatter):

::: expressive-code
<figure class="frame not-content">
<pre data-language="yaml"><code>---permission:  skill:    &quot;documents-*&quot;: &quot;allow&quot;---</code></pre>
<div class="copy">
<div aria-live="polite">

</div>
<div>

</div>
</div>
</figure>
:::

**For built-in agents** (in `opencode.json`{dir="auto"}):

::: expressive-code
<figure class="frame not-content">
<pre data-language="json"><code>{  &quot;agent&quot;: {    &quot;plan&quot;: {      &quot;permission&quot;: {        &quot;skill&quot;: {          &quot;internal-*&quot;: &quot;allow&quot;        }      }    }  }}</code></pre>
<div class="copy">
<div aria-live="polite">

</div>
<div>

</div>
</div>
</figure>
:::

------------------------------------------------------------------------

## [Disable the skill tool](#disable-the-skill-tool)

Completely disable skills for agents that shouldn't use them:

**For custom agents**:

::: expressive-code
<figure class="frame not-content">
<pre data-language="yaml"><code>---tools:  skill: false---</code></pre>
<div class="copy">
<div aria-live="polite">

</div>
<div>

</div>
</div>
</figure>
:::

**For built-in agents**:

::: expressive-code
<figure class="frame not-content">
<pre data-language="json"><code>{  &quot;agent&quot;: {    &quot;plan&quot;: {      &quot;tools&quot;: {        &quot;skill&quot;: false      }    }  }}</code></pre>
<div class="copy">
<div aria-live="polite">

</div>
<div>

</div>
</div>
</figure>
:::

When disabled, the `<available_skills>`{dir="auto"} section is omitted
entirely.

------------------------------------------------------------------------

## [Troubleshoot loading](#troubleshoot-loading)

If a skill does not show up:

1.  Verify `SKILL.md`{dir="auto"} is spelled in all caps
2.  Check that frontmatter includes `name`{dir="auto"} and
    `description`{dir="auto"}
3.  Ensure skill names are unique across all locations
4.  Check permissions---skills with `deny`{dir="auto"} are hidden from
    agents
:::

::: {.meta .sl-flex .astro-sz7xmlte}
::: astro-sz7xmlte
[![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9ImFzdHJvLXN6N3htbHRlIGFzdHJvLWRiZ3l3bzJzIiB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCIgZmlsbD0iY3VycmVudENvbG9yIiBzdHlsZT0iLS1zbC1pY29uLXNpemU6IDFlbTsiPjxwYXRoIGQ9Ik0yMiA3LjI0YTEgMSAwIDAgMC0uMjktLjcxbC00LjI0LTQuMjRhMSAxIDAgMCAwLTEuMS0uMjIgMSAxIDAgMCAwLS4zMi4yMmwtMi44MyAyLjgzTDIuMjkgMTYuMDVhMSAxIDAgMCAwLS4yOS43MVYyMWExIDEgMCAwIDAgMSAxaDQuMjRhMSAxIDAgMCAwIC43Ni0uMjlsMTAuODctMTAuOTNMMjEuNzEgOGMuMS0uMS4xNy0uMi4yMi0uMzNhMSAxIDAgMCAwIDAtLjI0di0uMTRsLjA3LS4wNVpNNi44MyAyMEg0di0yLjgzbDkuOTMtOS45MyAyLjgzIDIuODNMNi44MyAyMFpNMTguMTcgOC42NmwtMi44My0yLjgzIDEuNDItMS40MSAyLjgyIDIuODItMS40MSAxLjQyWiI+PC9wYXRoPjwvc3ZnPg==){.astro-sz7xmlte
.astro-dbgywo2s}Edit
page](https://github.com/anomalyco/opencode/edit/dev/packages/web/src/content/docs/skills.mdx){.sl-flex
.astro-sz7xmlte target="_blank"
rel="noopener noreferrer"}[![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9ImFzdHJvLXN6N3htbHRlIGFzdHJvLWRiZ3l3bzJzIiB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCIgZmlsbD0iY3VycmVudENvbG9yIiBzdHlsZT0iLS1zbC1pY29uLXNpemU6IDFlbTsiPjxwYXRoIGQ9Ik0xMiAuM2ExMiAxMiAwIDAgMC0zLjggMjMuMzhjLjYuMTIuODMtLjI2LjgzLS41N0w5IDIxLjA3Yy0zLjM0LjcyLTQuMDQtMS42MS00LjA0LTEuNjEtLjU1LTEuMzktMS4zNC0xLjc2LTEuMzQtMS43Ni0xLjA4LS43NC4wOS0uNzMuMDktLjczIDEuMi4wOSAxLjgzIDEuMjQgMS44MyAxLjI0IDEuMDggMS44MyAyLjgxIDEuMyAzLjUgMSAuMS0uNzguNDItMS4zMS43Ni0xLjYxLTIuNjctLjMtNS40Ny0xLjMzLTUuNDctNS45MyAwLTEuMzEuNDctMi4zOCAxLjI0LTMuMjItLjE0LS4zLS41NC0xLjUyLjEtMy4xOCAwIDAgMS0uMzIgMy4zIDEuMjNhMTEuNSAxMS41IDAgMCAxIDYgMGMyLjI4LTEuNTUgMy4yOS0xLjIzIDMuMjktMS4yMy42NCAxLjY2LjI0IDIuODguMTIgMy4xOGE0LjY1IDQuNjUgMCAwIDEgMS4yMyAzLjIyYzAgNC42MS0yLjggNS42My01LjQ4IDUuOTIuNDIuMzYuODEgMS4xLjgxIDIuMjJsLS4wMSAzLjI5YzAgLjMxLjIuNjkuODIuNTdBMTIgMTIgMCAwIDAgMTIgLjNaIj48L3BhdGg+PC9zdmc+){.astro-sz7xmlte
.astro-dbgywo2s}Found a bug? Open an
issue](https://github.com/anomalyco/opencode/issues/new){.sl-flex
.astro-sz7xmlte target="_blank"
rel="noopener noreferrer"}[![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9ImFzdHJvLXN6N3htbHRlIGFzdHJvLWRiZ3l3bzJzIiB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdib3g9IjAgMCAyNCAyNCIgZmlsbD0iY3VycmVudENvbG9yIiBzdHlsZT0iLS1zbC1pY29uLXNpemU6IDFlbTsiPjxwYXRoIGQ9Ik0yMC4zMiA0LjM3YTE5LjggMTkuOCAwIDAgMC00LjkzLTEuNTEgMTMuNzggMTMuNzggMCAwIDAtLjY0IDEuMjggMTguMjcgMTguMjcgMCAwIDAtNS41IDAgMTIuNjQgMTIuNjQgMCAwIDAtLjY0LTEuMjhoLS4wNUExOS43NCAxOS43NCAwIDAgMCAzLjY0IDQuNCAyMC4yNiAyMC4yNiAwIDAgMCAuMTEgMTguMDlsLjAyLjAyYTE5LjkgMTkuOSAwIDAgMCA2LjA0IDMuMDNsLjA0LS4wMmExNC4yNCAxNC4yNCAwIDAgMCAxLjIzLTIuMDMuMDguMDggMCAwIDAtLjA1LS4wNyAxMy4xIDEzLjEgMCAwIDEtMS45LS45Mi4wOC4wOCAwIDAgMSAuMDItLjEgMTAuMiAxMC4yIDAgMCAwIC40MS0uMzFoLjA0YTE0LjIgMTQuMiAwIDAgMCAxMi4xIDBsLjA0LjAxYTkuNjMgOS42MyAwIDAgMCAuNC4zMi4wOC4wOCAwIDAgMS0uMDMuMSAxMi4yOSAxMi4yOSAwIDAgMS0xLjkuOTEuMDguMDggMCAwIDAtLjAyLjEgMTUuOTcgMTUuOTcgMCAwIDAgMS4yNyAyLjAxaC4wNGExOS44NCAxOS44NCAwIDAgMCA2LjAzLTMuMDV2LS4wM2EyMC4xMiAyMC4xMiAwIDAgMC0zLjU3LTEzLjY5Wk04LjAyIDE1LjMzYy0xLjE4IDAtMi4xNi0xLjA4LTIuMTYtMi40MiAwLTEuMzMuOTYtMi40MiAyLjE2LTIuNDIgMS4yMSAwIDIuMTggMS4xIDIuMTYgMi40MiAwIDEuMzQtLjk2IDIuNDItMi4xNiAyLjQyWm03Ljk3IDBjLTEuMTggMC0yLjE1LTEuMDgtMi4xNS0yLjQyIDAtMS4zMy45NS0yLjQyIDIuMTUtMi40MiAxLjIyIDAgMi4xOCAxLjEgMi4xNiAyLjQyIDAgMS4zNC0uOTQgMi40Mi0yLjE2IDIuNDJaIj48L3BhdGg+PC9zdmc+){.astro-sz7xmlte
.astro-dbgywo2s}Join our Discord
community](https://opencode.ai/discord){.sl-flex .astro-sz7xmlte
target="_blank" rel="noopener noreferrer"} [Select language]{.sr-only
.astro-yk3v7tmu}
![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9Imljb24gbGFiZWwtaWNvbiBhc3Ryby15azN2N3RtdSBhc3Ryby1kYmd5d28ycyIgd2lkdGg9IjE2IiBoZWlnaHQ9IjE2IiB2aWV3Ym94PSIwIDAgMjQgMjQiIGZpbGw9ImN1cnJlbnRDb2xvciIgc3R5bGU9Ii0tc2wtaWNvbi1zaXplOiAxZW07Ij48cGF0aCBmaWxsLXJ1bGU9ImV2ZW5vZGQiIGQ9Ik04LjUxNiAzYS45NC45NCAwIDAgMC0uOTQxLjk0djEuMTVIMi45NGEuOTQuOTQgMCAxIDAgMCAxLjg4Mmg3LjM2MmE3LjQyMiA3LjQyMiAwIDAgMS0xLjc4NyAzLjk1OCA3LjQyIDcuNDIgMCAwIDEtMS40MjItMi40MjUuOTQuOTQgMCAxIDAtMS43NzQuNjI3IDkuMzAzIDkuMzAzIDAgMCAwIDEuNzg1IDMuMDQzIDcuNDIyIDcuNDIyIDAgMCAxLTQuMTY0IDEuMjc4Ljk0Ljk0IDAgMSAwIDAgMS44ODEgOS4zMDMgOS4zMDMgMCAwIDAgNS41NzUtMS44NTUgOS4zMDMgOS4zMDMgMCAwIDAgNC4xMSAxLjc0bC0uNzYzIDEuNTI1YS45NjguOTY4IDAgMCAwLS4wMTYuMDM0bC0xLjM4NSAyLjc3YS45NC45NCAwIDEgMCAxLjY4My44NDFsMS4xMzMtMi4yNjdoNS44MDZsMS4xMzQgMi4yNjdhLjk0Ljk0IDAgMCAwIDEuNjgzLS44NDFsLTEuMzg1LTIuNzY5YS45NS45NSAwIDAgMC0uMDE4LS4wMzZsLTMuNDc2LTYuOTUxYS45NC45NCAwIDAgMC0xLjY4MiAwbC0xLjgyIDMuNjM5YTcuNDIzIDcuNDIzIDAgMCAxLTMuNTkzLTEuMjU2IDkuMzAzIDkuMzAzIDAgMCAwIDIuMjctNS4yMDNoMS44OTRhLjk0Ljk0IDAgMCAwIDAtMS44ODFIOS40NTZWMy45NEEuOTQuOTQgMCAwIDAgOC41MTYgM1ptNi40MjYgMTEuNzk0YTEuMDY4IDEuMDY4IDAgMCAxLS4wMi4wMzlsLS43MDMgMS40MDdoMy45MjRsLTEuOTYyLTMuOTI0LTEuMjQgMi40NzhaIiBjbGlwLXJ1bGU9ImV2ZW5vZGQiPjwvcGF0aD48L3N2Zz4=){.icon
.label-icon .astro-yk3v7tmu .astro-dbgywo2s}
EnglishالعربيةBosanskiDanskDeutschEspañolFrançaisItaliano日本語한국어Norsk
BokmålPolskiPortuguês (Brasil)РусскийไทยTürkçe简体中文繁體中文
![](data:image/svg+xml;base64,PHN2ZyBhcmlhLWhpZGRlbj0idHJ1ZSIgY2xhc3M9Imljb24gY2FyZXQgYXN0cm8teWszdjd0bXUgYXN0cm8tZGJneXdvMnMiIHdpZHRoPSIxNiIgaGVpZ2h0PSIxNiIgdmlld2JveD0iMCAwIDI0IDI0IiBmaWxsPSJjdXJyZW50Q29sb3IiIHN0eWxlPSItLXNsLWljb24tc2l6ZTogMWVtOyI+PHBhdGggZD0iTTE3IDkuMTdhMSAxIDAgMCAwLTEuNDEgMEwxMiAxMi43MSA4LjQ2IDkuMTdhMSAxIDAgMSAwLTEuNDEgMS40Mmw0LjI0IDQuMjRhMS4wMDIgMS4wMDIgMCAwIDAgMS40MiAwTDE3IDEwLjU5YTEuMDAyIDEuMDAyIDAgMCAwIDAtMS40MloiPjwvcGF0aD48L3N2Zz4=){.icon
.caret .astro-yk3v7tmu .astro-dbgywo2s}
:::

::: astro-sz7xmlte
© [Anomaly](https://anoma.ly){.astro-sz7xmlte target="_blank"
rel="noopener noreferrer"}

Last updated: May 5, 2026
:::
:::
:::
:::
:::
:::
:::
:::
:::
