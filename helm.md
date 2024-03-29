<!DOCTYPE html>
<html>

<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Welcome file</title>
  <link rel="stylesheet" href="https://stackedit.io/style.css" />
</head>

<body class="stackedit">
  <div class="stackedit__left">
    <div class="stackedit__toc">
      
<ul>
<li><a href="#туториал-первое-знакомство-с-helm---управление-приложениями-kubernetes-с-помощью-helm">Туториал: первое знакомство с Helm - управление приложениями Kubernetes с помощью Helm</a>
<ul>
<li><a href="#введение-в-helm">Введение в Helm</a></li>
<li><a href="#установка-helm">Установка Helm</a></li>
<li><a href="#создание-helm-chart">Создание Helm Chart</a></li>
<li><a href="#конфигурация-helm-chart">Конфигурация Helm Chart</a></li>
<li><a href="#обновление-helm-chart">Обновление Helm Chart</a></li>
<li><a href="#отладка-helm-charts">Отладка Helm Charts</a></li>
<li><a href="#управление-helm-releases">Управление Helm Releases</a></li>
<li><a href="#использование-helm-repositories">Использование Helm Repositories</a></li>
<li><a href="#работа-с-helm-hooks">Работа с Helm Hooks</a></li>
<li><a href="#заключение">Заключение</a></li>
</ul>
</li>
<li><a href="#synchronization">Synchronization</a>
<ul>
<li><a href="#open-a-file">Open a file</a></li>
<li><a href="#save-a-file">Save a file</a></li>
<li><a href="#synchronize-a-file">Synchronize a file</a></li>
<li><a href="#manage-file-synchronization">Manage file synchronization</a></li>
</ul>
</li>
<li><a href="#publication">Publication</a>
<ul>
<li><a href="#publish-a-file">Publish a File</a></li>
<li><a href="#update-a-publication">Update a publication</a></li>
<li><a href="#manage-file-publication">Manage file publication</a></li>
</ul>
</li>
<li><a href="#markdown-extensions">Markdown extensions</a>
<ul>
<li><a href="#smartypants">SmartyPants</a></li>
<li><a href="#katex">KaTeX</a></li>
<li><a href="#uml-diagrams">UML diagrams</a></li>
</ul>
</li>
</ul>

    </div>
  </div>
  <div class="stackedit__right">
    <div class="stackedit__html">
      <h1 id="туториал-первое-знакомство-с-helm---управление-приложениями-kubernetes-с-помощью-helm">Туториал: первое знакомство с Helm - управление приложениями Kubernetes с помощью Helm</h1>
<p><img src="https://helm.sh/img/helm.svg" alt="HELM"></p>
<p><strong>Helm</strong> (Harnessing Efficient Kubernetes Management) - это пакетный менеджер для Kubernetes, предоставляющий простой способ упаковывания, распространения и управления приложениями в Kubernetes-кластерах.</p>
<p><strong>Helm</strong> упрощает процесс установки, обновления и удаления приложений на платформе Kubernetes, предоставляя концепцию “Charts” - пакетов, содержащих описание приложения и его зависимостей.</p>
<h2 id="введение-в-helm">Введение в Helm</h2>
<ol>
<li>
<p>Helm упрощает установку приложений и их зависимостей в Kubernetes. Он предоставляет простой интерфейс командной строки для управления развертыванием, что особенно важно для сложных многокомпонентных приложений.</p>
</li>
<li>
<p>Helm позволяет параметризовать конфигурацию приложения, делая его более гибким и настраиваемым. Модульная структура Charts позволяет легко настраивать различные аспекты приложения без изменения самого кода, а также позволяет объединять и переиспользовать части конфигурации.</p>
</li>
<li>
<p>Helm автоматически управляет зависимостями между компонентами приложений. Это упрощает интеграцию с другими сервисами.</p>
</li>
<li>
<p>Helm предоставляет механизм версионирования для Charts и позволяет легко обновлять приложения с минимальным риском. В случае проблем можно быстро откатиться к предыдущей версии приложения.</p>
</li>
<li>
<p>Helm облегчает управление жизненным циклом приложений от установки до обновления и удаления. Это особенно полезно в динамичных средах, где приложения часто изменяются.</p>
</li>
<li>
<p>Helm использует шаблоны Kubernetes (Go Templates) для генерации конфигураций, что обеспечивает совместимость с существующими манифестами Kubernetes и упрощает перенос приложений в Kubernetes.</p>
</li>
<li>
<p>Helm поддерживает создание удаленных репозиториев, где можно хранить и обмениваться готовыми Charts.</p>
</li>
</ol>
<h2 id="установка-helm">Установка Helm</h2>
<h3 id="необходимые-компоненты">Необходимые компоненты</h3>
<p>Для успешного и надежного использования Helm необходимы:</p>
<ol>
<li>
<p><strong>Kubernetes кластер:</strong> Helm предназначен для управления приложениями в Kubernetes. Убедитесь, что у вас установлен и настроен Kubernetes кластер.</p>
</li>
<li>
<p><strong>kubectl:</strong> Убедитесь, что у вас установлен инструмент командной строки kubectl, который используется для взаимодействия с кластером Kubernetes.</p>
</li>
<li>
<p>Установленный в локальной ОС клиент HELM. Клиентская часть Helm должна быть установлена на локальной машине. Для установки можно использовать предварительно скомпилированные бинарные файлы или менеджеры пакетов.</p>
</li>
<li>
<p>Доступ к Интернету (опционально):</p>
</li>
</ol>
<p>Если вы планируете использовать предварительно созданные Helm Charts из общедоступных репозиториев, убедитесь, что у вас есть доступ к интернету.</p>
<h3 id="установка-helm-клиента">Установка HELM-клиента</h3>
<p>Проект Helm предоставляет два официальных метода получения и установки Helm.</p>
<p>В дополнение к этому сообщество Helm предоставляет методы установки Helm через различные менеджеры пакетов.</p>
<ol>
<li>Из Binary Релизов: этот способ установки описывать не будем, есть мануал из</li>
</ol>
<p><a href="https://helm.sh/docs/intro/install/#from-the-binary-releases">официальной документации</a></p>
<ol start="2">
<li>Используя скрипт установки (на Linux или macOS):</li>
</ol>
<p>Скрипт установки автоматически загружает последнюю версию Helm и устанавливает его локально.</p>
<pre><code>
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3

chmod +x get_helm.sh

./get_helm.sh

</code></pre>
<ol start="3">
<li>Используя менеджеры пакетов (на Linux, macOS, Windows):</li>
</ol>
<ul>
<li>
<p>Homebrew (для macOS): <code>brew install helm</code></p>
</li>
<li>
<p>Chocolatey (для Windows): <code>choco install kubernetes-helm</code></p>
</li>
<li>
<p>apt (для Debian/Ubuntu Linux): <code>sudo apt-get update &amp;&amp; sudo apt-get install -y helm</code></p>
</li>
<li>
<p>yum (для CentOS/Fedora Linux): <code>sudo yum install -y helm</code></p>
</li>
</ul>
<p>После успешной установки Helm, вы можете проверить его версию с помощью команды: <code>helm version</code></p>
<h2 id="создание-helm-chart">Создание Helm Chart</h2>
<p>All your files and folders are presented as a tree in the file explorer. You can switch from one to another by clicking a file in the tree.</p>
<h2 id="конфигурация-helm-chart">Конфигурация Helm Chart</h2>
<p>You can rename the current file by clicking the file name in the navigation bar or by clicking the <strong>Rename</strong> button in the file explorer.</p>
<h2 id="обновление-helm-chart">Обновление Helm Chart</h2>
<p>You can delete the current file by clicking the <strong>Remove</strong> button in the file explorer. The file will be moved into the <strong>Trash</strong> folder and automatically deleted after 7 days of inactivity.</p>
<h2 id="отладка-helm-charts">Отладка Helm Charts</h2>
<p>You can export the current file by clicking <strong>Export to disk</strong> in the menu. You can choose to export the file as plain Markdown, as HTML using a Handlebars template or as a PDF.</p>
<h2 id="управление-helm-releases">Управление Helm Releases</h2>
<p>You can export the current file by clicking <strong>Export to disk</strong> in the menu. You can choose to export the file as plain Markdown, as HTML using a Handlebars template or as a PDF.</p>
<h2 id="использование-helm-repositories">Использование Helm Repositories</h2>
<p>You can export the current file by clicking <strong>Export to disk</strong> in the menu. You can choose to export the file as plain Markdown, as HTML using a Handlebars template or as a PDF.</p>
<h2 id="работа-с-helm-hooks">Работа с Helm Hooks</h2>
<p>You can export the current file by clicking <strong>Export to disk</strong> in the menu. You can choose to export the file as plain Markdown, as HTML using a Handlebars template or as a PDF.</p>
<h2 id="заключение">Заключение</h2>
<p>HELM представляет собой мощный и гибкий инструмент в области управления контейнеризированными приложениями, разработанный с учетом особенностей современных инфраструктурных требований. Этот программный продукт создан для облегчения и ускорения процессов развертывания, масштабирования и управления контейнерами в среде Kubernetes. HELM предоставляет надежное решение для оркестрации и управления контейнерами, предоставляя разработчикам и администраторам инструменты, необходимые для более эффективного и удобного управления микросервисами.</p>
<p>Сочетая в себе простоту использования с высокой настраиваемостью, HELM обеспечивает универсальное решение для команд разработки и DevOps-специалистов. Этот инструмент не только ускоряет процессы разработки, но и обеспечивает надежность при управлении контейнерами в среде Kubernetes. Независимо от размера проекта, HELM предоставляет интуитивно понятные решения, сокращая время и ресурсы, затрачиваемые на управление микросервисами.</p>
<h1 id="synchronization">Synchronization</h1>
<p>Synchronization is one of the biggest features of StackEdit. It enables you to synchronize any file in your workspace with other files stored in your <strong>Google Drive</strong>, your <strong>Dropbox</strong> and your <strong>GitHub</strong> accounts. This allows you to keep writing on other devices, collaborate with people you share the file with, integrate easily into your workflow… The synchronization mechanism takes place every minute in the background, downloading, merging, and uploading file modifications.</p>
<p>There are two types of synchronization and they can complement each other:</p>
<ul>
<li>The workspace synchronization will sync all your files, folders and settings automatically. This will allow you to fetch your workspace on any other device.</li>
</ul>
<blockquote>
<p>To start syncing your workspace, just sign in with Google in the menu.</p>
</blockquote>
<ul>
<li>The file synchronization will keep one file of the workspace synced with one or multiple files in <strong>Google Drive</strong>, <strong>Dropbox</strong> or <strong>GitHub</strong>.</li>
</ul>
<blockquote>
<p>Before starting to sync files, you must link an account in the <strong>Synchronize</strong> sub-menu.</p>
</blockquote>
<h2 id="open-a-file">Open a file</h2>
<p>You can open a file from <strong>Google Drive</strong>, <strong>Dropbox</strong> or <strong>GitHub</strong> by opening the <strong>Synchronize</strong> sub-menu and clicking <strong>Open from</strong>. Once opened in the workspace, any modification in the file will be automatically synced.</p>
<h2 id="save-a-file">Save a file</h2>
<p>You can save any file of the workspace to <strong>Google Drive</strong>, <strong>Dropbox</strong> or <strong>GitHub</strong> by opening the <strong>Synchronize</strong> sub-menu and clicking <strong>Save on</strong>. Even if a file in the workspace is already synced, you can save it to another location. StackEdit can sync one file with multiple locations and accounts.</p>
<h2 id="synchronize-a-file">Synchronize a file</h2>
<p>Once your file is linked to a synchronized location, StackEdit will periodically synchronize it by downloading/uploading any modification. A merge will be performed if necessary and conflicts will be resolved.</p>
<p>If you just have modified your file and you want to force syncing, click the <strong>Synchronize now</strong> button in the navigation bar.</p>
<blockquote>
<p><strong>Note:</strong> The <strong>Synchronize now</strong> button is disabled if you have no file to synchronize.</p>
</blockquote>
<h2 id="manage-file-synchronization">Manage file synchronization</h2>
<p>Since one file can be synced with multiple locations, you can list and manage synchronized locations by clicking <strong>File synchronization</strong> in the <strong>Synchronize</strong> sub-menu. This allows you to list and remove synchronized locations that are linked to your file.</p>
<h1 id="publication">Publication</h1>
<p>Publishing in StackEdit makes it simple for you to publish online your files. Once you’re happy with a file, you can publish it to different hosting platforms like <strong>Blogger</strong>, <strong>Dropbox</strong>, <strong>Gist</strong>, <strong>GitHub</strong>, <strong>Google Drive</strong>, <strong>WordPress</strong> and <strong>Zendesk</strong>. With <a href="http://handlebarsjs.com/">Handlebars templates</a>, you have full control over what you export.</p>
<blockquote>
<p>Before starting to publish, you must link an account in the <strong>Publish</strong> sub-menu.</p>
</blockquote>
<h2 id="publish-a-file">Publish a File</h2>
<p>You can publish your file by opening the <strong>Publish</strong> sub-menu and by clicking <strong>Publish to</strong>. For some locations, you can choose between the following formats:</p>
<ul>
<li>
<p>Markdown: publish the Markdown text on a website that can interpret it (<strong>GitHub</strong> for instance),</p>
</li>
<li>
<p>HTML: publish the file converted to HTML via a Handlebars template (on a blog for example).</p>
</li>
</ul>
<h2 id="update-a-publication">Update a publication</h2>
<p>After publishing, StackEdit keeps your file linked to that publication which makes it easy for you to re-publish it. Once you have modified your file and you want to update your publication, click on the <strong>Publish now</strong> button in the navigation bar.</p>
<blockquote>
<p><strong>Note:</strong> The <strong>Publish now</strong> button is disabled if your file has not been published yet.</p>
</blockquote>
<h2 id="manage-file-publication">Manage file publication</h2>
<p>Since one file can be published to multiple locations, you can list and manage publish locations by clicking <strong>File publication</strong> in the <strong>Publish</strong> sub-menu. This allows you to list and remove publication locations that are linked to your file.</p>
<h1 id="markdown-extensions">Markdown extensions</h1>
<p>StackEdit extends the standard Markdown syntax by adding extra <strong>Markdown extensions</strong>, providing you with some nice features.</p>
<blockquote>
<p><strong>ProTip:</strong> You can disable any <strong>Markdown extension</strong> in the <strong>File properties</strong> dialog.</p>
</blockquote>
<h2 id="smartypants">SmartyPants</h2>
<p>SmartyPants converts ASCII punctuation characters into “smart” typographic punctuation HTML entities. For example:</p>
<p>| |ASCII |HTML |</p>
<p>|----------------|-------------------------------|-----------------------------|</p>
<p>|Single backticks|<code>'Isn't this fun?'</code> |‘Isn’t this fun?’ |</p>
<p>|Quotes |<code>"Isn't this fun?"</code> |“Isn’t this fun?” |</p>
<p>|Dashes |<code>-- is en-dash, --- is em-dash</code>|-- is en-dash, — is em-dash|</p>
<h2 id="katex">KaTeX</h2>
<p>You can render LaTeX mathematical expressions using <a href="https://khan.github.io/KaTeX/">KaTeX</a>:</p>
<p>The <em>Gamma function</em> satisfying <span class="katex--inline"><span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi mathvariant="normal">Γ</mi><mo stretchy="false">(</mo><mi>n</mi><mo stretchy="false">)</mo><mo>=</mo><mo stretchy="false">(</mo><mi>n</mi><mo>−</mo><mn>1</mn><mo stretchy="false">)</mo><mo stretchy="false">!</mo><mspace width="1em"></mspace><mi mathvariant="normal">∀</mi><mi>n</mi><mo>∈</mo><mi mathvariant="double-struck">N</mi></mrow><annotation encoding="application/x-tex">\Gamma(n) = (n-1)!\quad\forall n\in\mathbb N</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1em; vertical-align: -0.25em;"></span><span class="mord">Γ</span><span class="mopen">(</span><span class="mord mathnormal">n</span><span class="mclose">)</span><span class="mspace" style="margin-right: 0.277778em;"></span><span class="mrel">=</span><span class="mspace" style="margin-right: 0.277778em;"></span></span><span class="base"><span class="strut" style="height: 1em; vertical-align: -0.25em;"></span><span class="mopen">(</span><span class="mord mathnormal">n</span><span class="mspace" style="margin-right: 0.222222em;"></span><span class="mbin">−</span><span class="mspace" style="margin-right: 0.222222em;"></span></span><span class="base"><span class="strut" style="height: 1em; vertical-align: -0.25em;"></span><span class="mord">1</span><span class="mclose">)!</span><span class="mspace" style="margin-right: 1em;"></span><span class="mord">∀</span><span class="mord mathnormal">n</span><span class="mspace" style="margin-right: 0.277778em;"></span><span class="mrel">∈</span><span class="mspace" style="margin-right: 0.277778em;"></span></span><span class="base"><span class="strut" style="height: 0.68889em; vertical-align: 0em;"></span><span class="mord mathbb">N</span></span></span></span></span> is via the Euler integral</p>
<p>$$</p>
<p>\Gamma(z) = \int_0^\infty t<sup>{z-1}e</sup>{-t}dt,.</p>
<p>$$</p>
<blockquote>
<p>You can find more information about <strong>LaTeX</strong> mathematical expressions <a href="http://meta.math.stackexchange.com/questions/5020/mathjax-basic-tutorial-and-quick-reference">here</a>.</p>
</blockquote>
<h2 id="uml-diagrams">UML diagrams</h2>
<p>You can render UML diagrams using <a href="https://mermaidjs.github.io/">Mermaid</a>. For example, this will produce a sequence diagram:</p>
<pre class=" language-mermaid"><svg id="mermaid-svg-dEkOUbkM6PsEyBwQ" width="100%" xmlns="http://www.w3.org/2000/svg" height="555" style="max-width: 819px;" viewBox="-50 -10 819 555"><style>#mermaid-svg-dEkOUbkM6PsEyBwQ{font-family:"trebuchet ms",verdana,arial,sans-serif;font-size:16px;fill:#000000;}#mermaid-svg-dEkOUbkM6PsEyBwQ .error-icon{fill:#552222;}#mermaid-svg-dEkOUbkM6PsEyBwQ .error-text{fill:#552222;stroke:#552222;}#mermaid-svg-dEkOUbkM6PsEyBwQ .edge-thickness-normal{stroke-width:2px;}#mermaid-svg-dEkOUbkM6PsEyBwQ .edge-thickness-thick{stroke-width:3.5px;}#mermaid-svg-dEkOUbkM6PsEyBwQ .edge-pattern-solid{stroke-dasharray:0;}#mermaid-svg-dEkOUbkM6PsEyBwQ .edge-pattern-dashed{stroke-dasharray:3;}#mermaid-svg-dEkOUbkM6PsEyBwQ .edge-pattern-dotted{stroke-dasharray:2;}#mermaid-svg-dEkOUbkM6PsEyBwQ .marker{fill:#666;stroke:#666;}#mermaid-svg-dEkOUbkM6PsEyBwQ .marker.cross{stroke:#666;}#mermaid-svg-dEkOUbkM6PsEyBwQ svg{font-family:"trebuchet ms",verdana,arial,sans-serif;font-size:16px;}#mermaid-svg-dEkOUbkM6PsEyBwQ .actor{stroke:hsl(0,0%,83%);fill:#eee;}#mermaid-svg-dEkOUbkM6PsEyBwQ text.actor > tspan{fill:#333;stroke:none;}#mermaid-svg-dEkOUbkM6PsEyBwQ .actor-line{stroke:#666;}#mermaid-svg-dEkOUbkM6PsEyBwQ .messageLine0{stroke-width:1.5;stroke-dasharray:none;stroke:#333;}#mermaid-svg-dEkOUbkM6PsEyBwQ .messageLine1{stroke-width:1.5;stroke-dasharray:2,2;stroke:#333;}#mermaid-svg-dEkOUbkM6PsEyBwQ #arrowhead path{fill:#333;stroke:#333;}#mermaid-svg-dEkOUbkM6PsEyBwQ .sequenceNumber{fill:white;}#mermaid-svg-dEkOUbkM6PsEyBwQ #sequencenumber{fill:#333;}#mermaid-svg-dEkOUbkM6PsEyBwQ #crosshead path{fill:#333;stroke:#333;}#mermaid-svg-dEkOUbkM6PsEyBwQ .messageText{fill:#333;stroke:#333;}#mermaid-svg-dEkOUbkM6PsEyBwQ .labelBox{stroke:hsl(0,0%,83%);fill:#eee;}#mermaid-svg-dEkOUbkM6PsEyBwQ .labelText,#mermaid-svg-dEkOUbkM6PsEyBwQ .labelText > tspan{fill:#333;stroke:none;}#mermaid-svg-dEkOUbkM6PsEyBwQ .loopText,#mermaid-svg-dEkOUbkM6PsEyBwQ .loopText > tspan{fill:#333;stroke:none;}#mermaid-svg-dEkOUbkM6PsEyBwQ .loopLine{stroke-width:2px;stroke-dasharray:2,2;stroke:hsl(0,0%,83%);fill:hsl(0,0%,83%);}#mermaid-svg-dEkOUbkM6PsEyBwQ .note{stroke:hsl(60,100%,23.3333333333%);fill:#ffa;}#mermaid-svg-dEkOUbkM6PsEyBwQ .noteText,#mermaid-svg-dEkOUbkM6PsEyBwQ .noteText > tspan{fill:#333;stroke:none;}#mermaid-svg-dEkOUbkM6PsEyBwQ .activation0{fill:#f4f4f4;stroke:#666;}#mermaid-svg-dEkOUbkM6PsEyBwQ .activation1{fill:#f4f4f4;stroke:#666;}#mermaid-svg-dEkOUbkM6PsEyBwQ .activation2{fill:#f4f4f4;stroke:#666;}#mermaid-svg-dEkOUbkM6PsEyBwQ:root{--mermaid-font-family:"trebuchet ms",verdana,arial,sans-serif;}#mermaid-svg-dEkOUbkM6PsEyBwQ sequence{fill:apa;}</style><g></g><g><line id="actor15" x1="75" y1="5" x2="75" y2="544" class="actor-line" stroke-width="0.5px" stroke="#999"></line><rect x="0" y="0" fill="#eaeaea" stroke="#666" width="150" height="65" rx="3" ry="3" class="actor"></rect><text x="75" y="32.5" style="text-anchor: middle; font-weight: 400; font-family: &quot;Open-Sans&quot;, &quot;sans-serif&quot;;" dominant-baseline="central" alignment-baseline="central" class="actor"><tspan x="75" dy="0">Alice</tspan></text></g><g><line id="actor16" x1="319" y1="5" x2="319" y2="544" class="actor-line" stroke-width="0.5px" stroke="#999"></line><rect x="244" y="0" fill="#eaeaea" stroke="#666" width="150" height="65" rx="3" ry="3" class="actor"></rect><text x="319" y="32.5" style="text-anchor: middle; font-weight: 400; font-family: &quot;Open-Sans&quot;, &quot;sans-serif&quot;;" dominant-baseline="central" alignment-baseline="central" class="actor"><tspan x="319" dy="0">Bob</tspan></text></g><g><line id="actor17" x1="544" y1="5" x2="544" y2="544" class="actor-line" stroke-width="0.5px" stroke="#999"></line><rect x="469" y="0" fill="#eaeaea" stroke="#666" width="150" height="65" rx="3" ry="3" class="actor"></rect><text x="544" y="32.5" style="text-anchor: middle; font-weight: 400; font-family: &quot;Open-Sans&quot;, &quot;sans-serif&quot;;" dominant-baseline="central" alignment-baseline="central" class="actor"><tspan x="544" dy="0">John</tspan></text></g><defs><marker id="arrowhead" refX="9" refY="5" markerUnits="userSpaceOnUse" markerWidth="12" markerHeight="12" orient="auto"><path d="M 0 0 L 10 5 L 0 10 z"></path></marker></defs><defs><marker id="crosshead" markerWidth="15" markerHeight="8" orient="auto" refX="16" refY="4"><path fill="black" stroke="#000000" style="stroke-dasharray: 0px, 0px;" stroke-width="1px" d="M 9,2 V 6 L16,4 Z"></path><path fill="none" stroke="#000000" style="stroke-dasharray: 0px, 0px;" stroke-width="1px" d="M 0,1 L 6,7 M 6,1 L 0,7"></path></marker></defs><defs><marker id="filled-head" refX="18" refY="7" markerWidth="20" markerHeight="28" orient="auto"><path d="M 18,7 L9,13 L14,7 L9,1 Z"></path></marker></defs><defs><marker id="sequencenumber" refX="15" refY="15" markerWidth="60" markerHeight="40" orient="auto"><circle cx="15" cy="15" r="6"></circle></marker></defs><text x="197" y="80" text-anchor="middle" dominant-baseline="middle" alignment-baseline="middle" style="font-family: &quot;trebuchet ms&quot;, verdana, arial, sans-serif; font-weight: 400;" class="messageText" dy="1em">Hello Bob, how are you?</text><line x1="75" y1="113" x2="319" y2="113" class="messageLine0" stroke-width="2" stroke="none" style="fill: none;" marker-end="url(#arrowhead)"></line><text x="432" y="128" text-anchor="middle" dominant-baseline="middle" alignment-baseline="middle" style="font-family: &quot;trebuchet ms&quot;, verdana, arial, sans-serif; font-weight: 400;" class="messageText" dy="1em">How about you John?</text><line x1="319" y1="161" x2="544" y2="161" style="stroke-dasharray: 3px, 3px; fill: none;" class="messageLine1" stroke-width="2" stroke="none" marker-end="url(#arrowhead)"></line><text x="197" y="176" text-anchor="middle" dominant-baseline="middle" alignment-baseline="middle" style="font-family: &quot;trebuchet ms&quot;, verdana, arial, sans-serif; font-weight: 400;" class="messageText" dy="1em">I am good thanks!</text><line x1="319" y1="209" x2="75" y2="209" style="stroke-dasharray: 3px, 3px; fill: none;" class="messageLine1" stroke-width="2" stroke="none" marker-end="url(#crosshead)"></line><text x="432" y="224" text-anchor="middle" dominant-baseline="middle" alignment-baseline="middle" style="font-family: &quot;trebuchet ms&quot;, verdana, arial, sans-serif; font-weight: 400;" class="messageText" dy="1em">I am good thanks!</text><line x1="319" y1="257" x2="544" y2="257" class="messageLine0" stroke-width="2" stroke="none" style="fill: none;" marker-end="url(#crosshead)"></line><g><rect x="569" y="267" fill="#EDF2AE" stroke="#666" width="150" height="96" rx="0" ry="0" class="note"></rect><text x="644" y="272" text-anchor="middle" dominant-baseline="middle" alignment-baseline="middle" style="font-family: &quot;trebuchet ms&quot;, verdana, arial, sans-serif; font-weight: 400;" class="noteText" dy="1em"><tspan x="644">Bob thinks a long</tspan></text><text x="644" y="291" text-anchor="middle" dominant-baseline="middle" alignment-baseline="middle" style="font-family: &quot;trebuchet ms&quot;, verdana, arial, sans-serif; font-weight: 400;" class="noteText" dy="1em"><tspan x="644">long time, so long</tspan></text><text x="644" y="310" text-anchor="middle" dominant-baseline="middle" alignment-baseline="middle" style="font-family: &quot;trebuchet ms&quot;, verdana, arial, sans-serif; font-weight: 400;" class="noteText" dy="1em"><tspan x="644">that the text does</tspan></text><text x="644" y="329" text-anchor="middle" dominant-baseline="middle" alignment-baseline="middle" style="font-family: &quot;trebuchet ms&quot;, verdana, arial, sans-serif; font-weight: 400;" class="noteText" dy="1em"><tspan x="644">not fit on a row.</tspan></text></g><text x="197" y="378" text-anchor="middle" dominant-baseline="middle" alignment-baseline="middle" style="font-family: &quot;trebuchet ms&quot;, verdana, arial, sans-serif; font-weight: 400;" class="messageText" dy="1em">Checking with John...</text><line x1="319" y1="411" x2="75" y2="411" style="stroke-dasharray: 3px, 3px; fill: none;" class="messageLine1" stroke-width="2" stroke="none"></line><text x="310" y="426" text-anchor="middle" dominant-baseline="middle" alignment-baseline="middle" style="font-family: &quot;trebuchet ms&quot;, verdana, arial, sans-serif; font-weight: 400;" class="messageText" dy="1em">Yes... John, how are you?</text><line x1="75" y1="459" x2="544" y2="459" class="messageLine0" stroke-width="2" stroke="none" style="fill: none;"></line><g><rect x="0" y="479" fill="#eaeaea" stroke="#666" width="150" height="65" rx="3" ry="3" class="actor"></rect><text x="75" y="511.5" style="text-anchor: middle; font-weight: 400; font-family: &quot;Open-Sans&quot;, &quot;sans-serif&quot;;" dominant-baseline="central" alignment-baseline="central" class="actor"><tspan x="75" dy="0">Alice</tspan></text></g><g><rect x="244" y="479" fill="#eaeaea" stroke="#666" width="150" height="65" rx="3" ry="3" class="actor"></rect><text x="319" y="511.5" style="text-anchor: middle; font-weight: 400; font-family: &quot;Open-Sans&quot;, &quot;sans-serif&quot;;" dominant-baseline="central" alignment-baseline="central" class="actor"><tspan x="319" dy="0">Bob</tspan></text></g><g><rect x="469" y="479" fill="#eaeaea" stroke="#666" width="150" height="65" rx="3" ry="3" class="actor"></rect><text x="544" y="511.5" style="text-anchor: middle; font-weight: 400; font-family: &quot;Open-Sans&quot;, &quot;sans-serif&quot;;" dominant-baseline="central" alignment-baseline="central" class="actor"><tspan x="544" dy="0">John</tspan></text></g></svg></pre>
<p>And this will produce a flow chart:</p>
<pre class=" language-mermaid"><svg id="mermaid-svg-Fv3aw851hQxuvVHO" width="100%" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" height="173.60000610351562" style="max-width: 510.7300109863281px;" viewBox="0 0 510.7300109863281 173.60000610351562"><style>#mermaid-svg-Fv3aw851hQxuvVHO{font-family:"trebuchet ms",verdana,arial,sans-serif;font-size:16px;fill:#000000;}#mermaid-svg-Fv3aw851hQxuvVHO .error-icon{fill:#552222;}#mermaid-svg-Fv3aw851hQxuvVHO .error-text{fill:#552222;stroke:#552222;}#mermaid-svg-Fv3aw851hQxuvVHO .edge-thickness-normal{stroke-width:2px;}#mermaid-svg-Fv3aw851hQxuvVHO .edge-thickness-thick{stroke-width:3.5px;}#mermaid-svg-Fv3aw851hQxuvVHO .edge-pattern-solid{stroke-dasharray:0;}#mermaid-svg-Fv3aw851hQxuvVHO .edge-pattern-dashed{stroke-dasharray:3;}#mermaid-svg-Fv3aw851hQxuvVHO .edge-pattern-dotted{stroke-dasharray:2;}#mermaid-svg-Fv3aw851hQxuvVHO .marker{fill:#666;stroke:#666;}#mermaid-svg-Fv3aw851hQxuvVHO .marker.cross{stroke:#666;}#mermaid-svg-Fv3aw851hQxuvVHO svg{font-family:"trebuchet ms",verdana,arial,sans-serif;font-size:16px;}#mermaid-svg-Fv3aw851hQxuvVHO .label{font-family:"trebuchet ms",verdana,arial,sans-serif;color:#000000;}#mermaid-svg-Fv3aw851hQxuvVHO .cluster-label text{fill:#333;}#mermaid-svg-Fv3aw851hQxuvVHO .cluster-label span{color:#333;}#mermaid-svg-Fv3aw851hQxuvVHO .label text,#mermaid-svg-Fv3aw851hQxuvVHO span{fill:#000000;color:#000000;}#mermaid-svg-Fv3aw851hQxuvVHO .node rect,#mermaid-svg-Fv3aw851hQxuvVHO .node circle,#mermaid-svg-Fv3aw851hQxuvVHO .node ellipse,#mermaid-svg-Fv3aw851hQxuvVHO .node polygon,#mermaid-svg-Fv3aw851hQxuvVHO .node path{fill:#eee;stroke:#999;stroke-width:1px;}#mermaid-svg-Fv3aw851hQxuvVHO .node .label{text-align:center;}#mermaid-svg-Fv3aw851hQxuvVHO .node.clickable{cursor:pointer;}#mermaid-svg-Fv3aw851hQxuvVHO .arrowheadPath{fill:#333333;}#mermaid-svg-Fv3aw851hQxuvVHO .edgePath .path{stroke:#666;stroke-width:1.5px;}#mermaid-svg-Fv3aw851hQxuvVHO .flowchart-link{stroke:#666;fill:none;}#mermaid-svg-Fv3aw851hQxuvVHO .edgeLabel{background-color:white;text-align:center;}#mermaid-svg-Fv3aw851hQxuvVHO .edgeLabel rect{opacity:0.5;background-color:white;fill:white;}#mermaid-svg-Fv3aw851hQxuvVHO .cluster rect{fill:hsl(210,66.6666666667%,95%);stroke:#26a;stroke-width:1px;}#mermaid-svg-Fv3aw851hQxuvVHO .cluster text{fill:#333;}#mermaid-svg-Fv3aw851hQxuvVHO .cluster span{color:#333;}#mermaid-svg-Fv3aw851hQxuvVHO div.mermaidTooltip{position:absolute;text-align:center;max-width:200px;padding:2px;font-family:"trebuchet ms",verdana,arial,sans-serif;font-size:12px;background:hsl(-160,0%,93.3333333333%);border:1px solid #26a;border-radius:2px;pointer-events:none;z-index:100;}#mermaid-svg-Fv3aw851hQxuvVHO:root{--mermaid-font-family:"trebuchet ms",verdana,arial,sans-serif;}#mermaid-svg-Fv3aw851hQxuvVHO flowchart{fill:apa;}</style><g><g class="output"><g class="clusters"></g><g class="edgePaths"><g class="edgePath LS-A LE-B" style="opacity: 1;" id="L-A-B"><path class="path" d="M111.65576213783677,66.98333358764648L171.75,38.44166564941406L248.35833740234375,38.44166564941406" marker-end="url(https://stackedit.io/app#arrowhead21)" style="fill:none"></path><defs><marker id="arrowhead21" viewBox="0 0 10 10" refX="9" refY="5" markerUnits="strokeWidth" markerWidth="8" markerHeight="6" orient="auto"><path d="M 0 0 L 10 5 L 0 10 z" class="arrowheadPath" style="stroke-width: 1px; stroke-dasharray: 1px, 0px;"></path></marker></defs></g><g class="edgePath LS-A LE-C" style="opacity: 1;" id="L-A-C"><path class="path" d="M111.65576213783677,113.69999313354492L171.75,142.24166107177734L226.5500030517578,142.24166107177734" marker-end="url(https://stackedit.io/app#arrowhead22)" style="fill:none"></path><defs><marker id="arrowhead22" viewBox="0 0 10 10" refX="9" refY="5" markerUnits="strokeWidth" markerWidth="8" markerHeight="6" orient="auto"><path d="M 0 0 L 10 5 L 0 10 z" class="arrowheadPath" style="stroke-width: 1px; stroke-dasharray: 1px, 0px;"></path></marker></defs></g><g class="edgePath LS-B LE-D" style="opacity: 1;" id="L-B-D"><path class="path" d="M309.2416687011719,38.44166564941406L356.0500030517578,38.44166564941406L404.4743226877226,67.91734219875202" marker-end="url(https://stackedit.io/app#arrowhead23)" style="fill:none"></path><defs><marker id="arrowhead23" viewBox="0 0 10 10" refX="9" refY="5" markerUnits="strokeWidth" markerWidth="8" markerHeight="6" orient="auto"><path d="M 0 0 L 10 5 L 0 10 z" class="arrowheadPath" style="stroke-width: 1px; stroke-dasharray: 1px, 0px;"></path></marker></defs></g><g class="edgePath LS-C LE-D" style="opacity: 1;" id="L-C-D"><path class="path" d="M331.0500030517578,142.24166107177734L356.0500030517578,142.24166107177734L404.4743245895876,113.76598337254664" marker-end="url(https://stackedit.io/app#arrowhead24)" style="fill:none"></path><defs><marker id="arrowhead24" viewBox="0 0 10 10" refX="9" refY="5" markerUnits="strokeWidth" markerWidth="8" markerHeight="6" orient="auto"><path d="M 0 0 L 10 5 L 0 10 z" class="arrowheadPath" style="stroke-width: 1px; stroke-dasharray: 1px, 0px;"></path></marker></defs></g></g><g class="edgeLabels"><g class="edgeLabel" style="opacity: 1;" transform="translate(171.75,38.44166564941406)"><g transform="translate(-29.800003051757812,-13.358329772949219)" class="label"><rect rx="0" ry="0" width="59.600006103515625" height="26.716659545898438"></rect><foreignObject width="59.600006103515625" height="26.716659545898438"><div xmlns="http://www.w3.org/1999/xhtml" style="display: inline-block; white-space: nowrap;"><span id="L-L-A-B" class="edgeLabel L-LS-A' L-LE-B">Link text</span></div></foreignObject></g></g><g class="edgeLabel" style="opacity: 1;" transform=""><g transform="translate(0,0)" class="label"><rect rx="0" ry="0" width="0" height="0"></rect><foreignObject width="0" height="0"><div xmlns="http://www.w3.org/1999/xhtml" style="display: inline-block; white-space: nowrap;"><span id="L-L-A-C" class="edgeLabel L-LS-A' L-LE-C"></span></div></foreignObject></g></g><g class="edgeLabel" style="opacity: 1;" transform=""><g transform="translate(0,0)" class="label"><rect rx="0" ry="0" width="0" height="0"></rect><foreignObject width="0" height="0"><div xmlns="http://www.w3.org/1999/xhtml" style="display: inline-block; white-space: nowrap;"><span id="L-L-B-D" class="edgeLabel L-LS-B' L-LE-D"></span></div></foreignObject></g></g><g class="edgeLabel" style="opacity: 1;" transform=""><g transform="translate(0,0)" class="label"><rect rx="0" ry="0" width="0" height="0"></rect><foreignObject width="0" height="0"><div xmlns="http://www.w3.org/1999/xhtml" style="display: inline-block; white-space: nowrap;"><span id="L-L-C-D" class="edgeLabel L-LS-C' L-LE-D"></span></div></foreignObject></g></g></g><g class="nodes"><g class="node default" style="opacity: 1;" id="flowchart-A-88" transform="translate(62.474998474121094,90.3416633605957)"><rect rx="0" ry="0" x="-54.474998474121094" y="-23.35832977294922" width="108.94999694824219" height="46.71665954589844" class="label-container"></rect><g class="label" transform="translate(0,0)"><g transform="translate(-44.474998474121094,-13.358329772949219)"><foreignObject width="88.94999694824219" height="26.716659545898438"><div xmlns="http://www.w3.org/1999/xhtml" style="display: inline-block; white-space: nowrap;">Square Rect</div></foreignObject></g></g></g><g class="node default" style="opacity: 1;" id="flowchart-B-89" transform="translate(278.8000030517578,38.44166564941406)"><circle x="-30.441665649414062" y="-23.35832977294922" r="30.441665649414062" class="label-container"></circle><g class="label" transform="translate(0,0)"><g transform="translate(-20.441665649414062,-13.358329772949219)"><foreignObject width="40.883331298828125" height="26.716659545898438"><div xmlns="http://www.w3.org/1999/xhtml" style="display: inline-block; white-space: nowrap;">Circle</div></foreignObject></g></g></g><g class="node default" style="opacity: 1;" id="flowchart-C-91" transform="translate(278.8000030517578,142.24166107177734)"><rect rx="5" ry="5" x="-52.25" y="-23.35832977294922" width="104.5" height="46.71665954589844" class="label-container"></rect><g class="label" transform="translate(0,0)"><g transform="translate(-42.25,-13.358329772949219)"><foreignObject width="84.5" height="26.716659545898438"><div xmlns="http://www.w3.org/1999/xhtml" style="display: inline-block; white-space: nowrap;">Round Rect</div></foreignObject></g></g></g><g class="node default" style="opacity: 1;" id="flowchart-D-93" transform="translate(441.8900032043457,90.3416633605957)"><polygon points="60.83999862670898,0 121.67999725341797,-60.83999862670898 60.83999862670898,-121.67999725341797 0,-60.83999862670898" transform="translate(-60.83999862670898,60.83999862670898)" class="label-container"></polygon><g class="label" transform="translate(0,0)"><g transform="translate(-34.241668701171875,-13.358329772949219)"><foreignObject width="68.48333740234375" height="26.716659545898438"><div xmlns="http://www.w3.org/1999/xhtml" style="display: inline-block; white-space: nowrap;">Rhombus</div></foreignObject></g></g></g></g></g></g></svg></pre>

    </div>
  </div>
</body>

</html>
