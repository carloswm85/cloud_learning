# Azure web hosting options by application complexity

Azure provides several ways to deploy websites and web applications, ranging from simple static HTML pages to enterprise applications with APIs, databases, Docker containers, and microservices.

The most important distinction is between applications that require a server to execute code and those that can run entirely in the user's browser.

## (1) Azure hosting options by complexity

| Level | Application type                       | Recommended Azure service         | Free option            |
| ----- | -------------------------------------- | --------------------------------- | ---------------------- |
| 1     | Static HTML/CSS/JS website             | Azure Static Web Apps             | Yes                    |
| 1     | Basic static website or files          | Azure Blob Storage                | Pay-as-you-go          |
| 2     | React / Angular / Vue SPA              | Azure Static Web Apps             | Yes                    |
| 3     | SPA with lightweight serverless API    | Static Web Apps + Azure Functions | Yes, within limits     |
| 4     | ASP.NET Core MVC / Razor Pages         | Azure App Service                 | F1 Free                |
| 4     | ASP.NET Core Web API                   | Azure App Service                 | F1 Free                |
| 5     | Full-stack application with SQL Server | App Service + Azure SQL Database  | Partial                |
| 6     | Dockerized web application / API       | Azure Container Apps              | Consumption free grant |
| 7     | Multiple containerized services        | Azure Container Apps              | Limited free grant     |
| 8     | Enterprise microservices / Kubernetes  | Azure Kubernetes Service (AKS)    | Infrastructure costs   |
| 9     | Fully customized server hosting        | Azure Virtual Machines            | Generally paid         |

These levels represent increasing architectural and operational complexity, not necessarily increasing application quality.&#x20;

[image](https://www.google.com/s2/favicons?domain=https://learn.microsoft.com&sz=32)

Microsoft Learn

+2

## (2) Understanding static versus dynamic applications

Static hosting

Browser

HTML, CSS, JavaScript

Static files

Azure Static Web Apps

No continuously running application server required.

Dynamic hosting

Browser

ASP\\.NET Core API

SQL Database

Server-side processing, business logic and persistent data.

A React or Angular SPA can be hosted statically even when it displays dynamic information obtained from an API. Static hosting refers to how the frontend is delivered, not whether its content changes.

Conversely, an ASP\\.NET Core MVC application that renders HTML on the server generally requires App Service or another service capable of running its .NET backend.

## (3) Which Azure service should you choose?

Choose your application type

HTML, CSS and JavaScript website

Angular / React / Vue SPA

ASP\\.NET Core MVC / Razor Pages

ASP\\.NET Core Web API

Dockerized application

Microservices architecture

Do you need a backend?

No backend

Small serverless API

Dedicated ASP\\.NET Core API

Recommended hosting

## Azure Static Web Apps

Ideal for a compiled Angular, React or Vue application that executes in the browser.

Azure App Service if you need server-side rendering or custom server behavior.

Create deployment lab&#x20;

## (4) Important free-tier differences

| Service              | Free-tier details                                        | Main limitation                                  |
| -------------------- | -------------------------------------------------------- | ------------------------------------------------ |
| Static Web Apps Free | Free static hosting, managed APIs, SSL, 2 custom domains | No SLA; usage and feature limits                 |
| App Service F1       | Shared compute for development/testing                   | CPU quotas and restricted features               |
| Blob Storage         | Usage-based billing                                      | No integrated application authentication         |
| Azure Functions      | Consumption-based free grant                             | Execution and resource limits                    |
| Container Apps       | Monthly consumption free grant                           | Charges beyond grant and for other resources     |
| AKS                  | Free control-plane option                                | Worker nodes and other infrastructure cost money |

For Azure Container Apps Consumption, the published monthly free grant includes 180,000 vCPU-seconds, 360,000 GiB-seconds and 2 million requests per subscription.&#x20;

[image](https://www.google.com/s2/favicons?domain=https://learn.microsoft.com&sz=32)

Microsoft Learn

For Static Web Apps Free, Azure supports three staging environments and a 250 MB maximum application size.&#x20;

[image](https://www.google.com/s2/favicons?domain=https://learn.microsoft.com&sz=32)

Microsoft Learn

## (5) Recommended architecture for your .NET and frontend projects

For a project using Angular or React with an ASP.NET Core 10 API and SQL Server, you can separate hosting responsibilities:

\#chatgpt-mermaid-\_r_ko\_{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;fill:rgb(237, 237, 237);}@keyframes edge-animation-frame{from{stroke-dashoffset:0;}}@keyframes dash{to{stroke-dashoffset:0;}}#chatgpt-mermaid-\_r_ko\_ .edge-animation-slow{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 50s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_ko\_ .edge-animation-fast{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 20s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_ko\_ .error-icon{fill:#a44141;}#chatgpt-mermaid-\_r_ko\_ .error-text{fill:#ddd;stroke:#ddd;}#chatgpt-mermaid-\_r_ko\_ .edge-thickness-normal{stroke-width:1px;}#chatgpt-mermaid-\_r_ko\_ .edge-thickness-thick{stroke-width:3.5px;}#chatgpt-mermaid-\_r_ko\_ .edge-pattern-solid{stroke-dasharray:0;}#chatgpt-mermaid-\_r_ko\_ .edge-thickness-invisible{stroke-width:0;fill:none;}#chatgpt-mermaid-\_r_ko\_ .edge-pattern-dashed{stroke-dasharray:3;}#chatgpt-mermaid-\_r_ko\_ .edge-pattern-dotted{stroke-dasharray:2;}#chatgpt-mermaid-\_r_ko\_ .marker{fill:rgb(175, 175, 175);stroke:rgb(175, 175, 175);}#chatgpt-mermaid-\_r_ko\_ .marker.cross{stroke:rgb(175, 175, 175);}#chatgpt-mermaid-\_r_ko\_ svg{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:16px;}#chatgpt-mermaid-\_r_ko\_ p{margin:0;}#chatgpt-mermaid-\_r_ko\_ .label{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";color:rgb(237, 237, 237);}#chatgpt-mermaid-\_r_ko\_ .cluster-label text{fill:rgb(237, 237, 237);}#chatgpt-mermaid-\_r_ko\_ .cluster-label span{color:rgb(237, 237, 237);}#chatgpt-mermaid-\_r_ko\_ .cluster-label span p{background-color:transparent;}#chatgpt-mermaid-\_r_ko\_ .label text,#chatgpt-mermaid-\_r_ko\_ span{fill:rgb(237, 237, 237);color:rgb(237, 237, 237);}#chatgpt-mermaid-\_r_ko\_ .node rect,#chatgpt-mermaid-\_r_ko\_ .node circle,#chatgpt-mermaid-\_r_ko\_ .node ellipse,#chatgpt-mermaid-\_r_ko\_ .node polygon,#chatgpt-mermaid-\_r_ko\_ .node path{fill:rgb(9, 23, 44);stroke:rgb(31, 78, 148);stroke-width:1px;}#chatgpt-mermaid-\_r_ko\_ .rough-node .label text,#chatgpt-mermaid-\_r_ko\_ .node .label text,#chatgpt-mermaid-\_r_ko\_ .image-shape .label,#chatgpt-mermaid-\_r_ko\_ .icon-shape .label{text-anchor:middle;}#chatgpt-mermaid-\_r_ko\_ .node .katex path{fill:#000;stroke:#000;stroke-width:1px;}#chatgpt-mermaid-\_r_ko\_ .rough-node .label,#chatgpt-mermaid-\_r_ko\_ .node .label,#chatgpt-mermaid-\_r_ko\_ .image-shape .label,#chatgpt-mermaid-\_r_ko\_ .icon-shape .label{text-align:center;}#chatgpt-mermaid-\_r_ko\_ .node.clickable{cursor:pointer;}#chatgpt-mermaid-\_r_ko\_ .root .anchor path{fill:rgb(175, 175, 175)!important;stroke-width:0;stroke:rgb(175, 175, 175);}#chatgpt-mermaid-\_r_ko\_ .arrowheadPath{fill:rgb(175, 175, 175);}#chatgpt-mermaid-\_r_ko\_ .edgePath .path{stroke:rgb(175, 175, 175);stroke-width:1px;}#chatgpt-mermaid-\_r_ko\_ .flowchart-link{stroke:rgb(175, 175, 175);fill:none;}#chatgpt-mermaid-\_r_ko\_ .edgeLabel{background-color:rgb(0, 0, 0);text-align:center;}#chatgpt-mermaid-\_r_ko\_ .edgeLabel p{background-color:rgb(0, 0, 0);}#chatgpt-mermaid-\_r_ko\_ .edgeLabel rect{opacity:0.5;background-color:rgb(0, 0, 0);fill:rgb(0, 0, 0);}#chatgpt-mermaid-\_r_ko\_ .labelBkg{background-color:rgba(0, 0, 0, 0.5);}#chatgpt-mermaid-\_r_ko\_ .cluster rect{fill:rgb(48, 48, 48);stroke:rgba(255, 255, 255, 0.15);stroke-width:1px;}#chatgpt-mermaid-\_r_ko\_ .cluster text{fill:rgb(237, 237, 237);}#chatgpt-mermaid-\_r_ko\_ .cluster span{color:rgb(237, 237, 237);}#chatgpt-mermaid-\_r_ko\_ div.mermaidTooltip{position:absolute;text-align:center;max-width:200px;padding:2px;font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";font-size:12px;background:rgb(48, 48, 48);border:1px solid rgba(255, 255, 255, 0.25);border-radius:2px;pointer-events:none;z-index:100;}#chatgpt-mermaid-\_r_ko\_ .flowchartTitleText{text-anchor:middle;font-size:18px;fill:rgb(237, 237, 237);}#chatgpt-mermaid-\_r_ko\_ rect.text{fill:none;stroke-width:0;}#chatgpt-mermaid-\_r_ko\_ .icon-shape,#chatgpt-mermaid-\_r_ko\_ .image-shape{background-color:rgb(0, 0, 0);text-align:center;}#chatgpt-mermaid-\_r_ko\_ .icon-shape p,#chatgpt-mermaid-\_r_ko\_ .image-shape p{background-color:rgb(0, 0, 0);padding:2px;}#chatgpt-mermaid-\_r_ko\_ .icon-shape .label rect,#chatgpt-mermaid-\_r_ko\_ .image-shape .label rect{opacity:0.5;background-color:rgb(0, 0, 0);fill:rgb(0, 0, 0);}#chatgpt-mermaid-\_r_ko\_ .label-icon{display:inline-block;height:1em;overflow:visible;vertical-align:-0.125em;}#chatgpt-mermaid-\_r_ko\_ .node .label-icon path{fill:currentColor;stroke:revert;stroke-width:revert;}#chatgpt-mermaid-\_r_ko\_ .node .neo-node{stroke:rgb(31, 78, 148);}#chatgpt-mermaid-\_r_ko\_ [data-look="neo"].node rect,#chatgpt-mermaid-\_r_ko\_ [data-look="neo"].cluster rect,#chatgpt-mermaid-\_r_ko\_ [data-look="neo"].node polygon{stroke:url(#chatgpt-mermaid-\_r_ko\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_ko\_ [data-look="neo"].swimlane.cluster rect{filter:none;}#chatgpt-mermaid-\_r_ko\_ [data-look="neo"].node path{stroke:url(#chatgpt-mermaid-\_r_ko\_-gradient);stroke-width:1px;}#chatgpt-mermaid-\_r_ko\_ [data-look="neo"].node .outer-path{filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_ko\_ [data-look="neo"].node .neo-line path{stroke:rgb(31, 78, 148);filter:none;}#chatgpt-mermaid-\_r_ko\_ [data-look="neo"].node circle{stroke:url(#chatgpt-mermaid-\_r_ko\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_ko\_ [data-look="neo"].node circle .state-start{fill:#000000;}#chatgpt-mermaid-\_r_ko\_ [data-look="neo"].icon-shape .icon{fill:url(#chatgpt-mermaid-\_r_ko\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_ko\_ [data-look="neo"].icon-shape .icon-neo path{stroke:url(#chatgpt-mermaid-\_r_ko\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_ko\_ :root{--mermaid-font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,"Segoe UI",Helvetica,"Apple Color Emoji",Arial,sans-serif,"Segoe UI Emoji","Segoe UI Symbol";}BrowserAzure Static Web AppsAngular / ReactAzure App ServiceASP.NET Core 10 APIAzure SQL Database\~ Azure full-stack hosting \~

The diagram assumes that the frontend calls the API directly. You would configure CORS, authentication, HTTPS and appropriate network access. Static Web Apps Standard also supports linking an App Service backend, which can simplify API routing.&#x20;

[image](https://www.google.com/s2/favicons?domain=https://learn.microsoft.com&sz=32)

Microsoft Learn

A separate consideration is Next.js. Static HTML exports fit Static Web Apps; server-side rendering requires a compatible runtime. Azure also documents hybrid Next.js support in preview.&#x20;

[image](https://www.google.com/s2/favicons?domain=https://learn.microsoft.com&sz=32)

Microsoft Learn

My suggested starting points for your projects:

- Personal portfolio or documentation: Static Web Apps Free.
- React or Angular learning project: Static Web Apps Free.
- ASP.NET Core MVC development/testing: App Service F1.
- Full-stack production system: Static Web Apps + App Service + SQL database.
- Docker and distributed application experiments: Container Apps.

You do not need to move to Docker, Kubernetes or virtual machines merely because an application grows. Start with the simplest hosting service that satisfies its runtime, availability, security and scaling requirements.

Microsoft's general hosting decision guide is available at .
