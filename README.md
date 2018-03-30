<!--
  This file was generated by emdaer

  Its template can be found at .emdaer/README.emdaer.md
-->

<p align="center"><img src="hero.png" alt="emdaer" /></p>

<p><h1 id="emdaer-travis-https-img-shields-io-travis-emdaer-emdaer-svg-style-flat-square-https-travis-ci-org-emdaer-emdaer-documented-with-emdaer-https-img-shields-io-badge-documented-20with-20emdaer-f06632-svg-style-flat-square-https-github-com-emdaer-emdaer-maintained-with-lerna-https-img-shields-io-badge-maintained-20with-20lerna-cc00ff-svg-style-flat-square-https-lernajs-io-">emdaer · <a href="https://travis-ci.org/emdaer/emdaer/"><img src="https://img.shields.io/travis/emdaer/emdaer.svg?style=flat-square" alt="Travis"></a> <a href="https://github.com/emdaer/emdaer"><img src="https://img.shields.io/badge/📓-documented%20with%20emdaer-F06632.svg?style=flat-square" alt="Documented with emdaer"></a> <a href="https://lernajs.io/"><img src="https://img.shields.io/badge/🐉-maintained%20with%20lerna-cc00ff.svg?style=flat-square" alt="Maintained with lerna"></a></h1></p>
<p>📓 emdaer is a tool for creating and maintaining better READMEs</p>
<!-- toc -->
<ul>
<li><a href="#what-is-emdaer">What is emdaer?</a></li>
<li><a href="#how-emdaer-works">How emdaer works</a><ul>
<li><a href="#plugins--transforms">Plugins &amp; Transforms</a></li>
</ul>
</li>
<li><a href="#adding-emdaer-to-your-project">Adding emdaer to your project</a></li>
<li><a href="#contributing">Contributing</a></li>
<li><a href="#this-readme">This README</a></li>
</ul>
<!-- tocstop -->
<h2 id="what-is-emdaer-">What is emdaer?</h2>
<p>emdaer lets you to use plugins and transforms within markdown files because READMEs (and other documentation) are crucial files that are often lackluster and/or incomplete and have a tendency to become stale</p>
<p>A couple use cases that illustrate the power of emdaer:</p>
<ul>
<li>🤝 <strong>Keep it in sync</strong> Create templates for use across all of your organizations projects to promote synchronicity and reduce doing the same work over and over</li>
<li>🗃 <strong>Keep it organized</strong> Keep your documentation DRY and organized by importing content from your codebase, splitting large documents into chunks, and formatting it with <a href="https://github.com/prettier/prettier">Prettier</a>.</li>
<li>🍋 <strong>Keep it fresh</strong> Ensure your documents stay up to date by pulling in new data from various sources with every build</li>
</ul>
<h2 id="how-emdaer-works">How emdaer works</h2>
<p>emdaer processes template files and writes the resulting files to your project.</p>
<p>We match <code>.emdaer/(*<em>/</em>).emdaer(.md)</code> and use the captured part of each matched file to determine the path for the output.</p>
<h3 id="plugins-transforms">Plugins &amp; Transforms</h3>
<!-- prettier-ignore -->
<pre><code class="lang-md"># &lt;!--emdaer-p
  - &#39;@emdaer/plugin-value-from-package&#39;
  - value: name
--&gt;

Hello, World!

&lt;!--emdaer-t
  - &#39;@emdaer/transform-smartypants&#39;
  - options: qe
--&gt;
</code></pre>
<p>This example includes one plugin call (<code>emdaer-p</code>) and one transform call (<code>emdaer-t</code>).</p>
<p>Both of these calls take the form of yaml tuples where the first item is the name of the function to call and the second item is an options object that is passed to that function.</p>
<p>For plugins, the result of the call replaces the corresponding comment block.</p>
<p>For transforms, the function acts on the entire document and rewrites the entire file.</p>
<h2 id="adding-emdaer-to-your-project">Adding emdaer to your project</h2>
<p>We recommend using emdaer with <a href="https://github.com/typicode/husky">husky</a>.</p>
<p>Install dependencies:</p>
<pre><code class="lang-sh">npm install --save-dev @emdaer/cli @emdaer/plugin-value-from-package husky
</code></pre>
<p>Add a <code>precommit</code> script:</p>
<pre><code class="lang-json">  &quot;scripts&quot;: {
    &quot;emdaer&quot;: &quot;emdaer &amp;&amp; git add *.md&quot;,
    &quot;precommit&quot;: &quot;npm run emdaer&quot;
  }
</code></pre>
<p>Add a <code>.emdaer/README.emdaer.md</code> file:</p>
<!-- prettier-ignore -->
<pre><code class="lang-md"># &lt;!--emdaer-p
  - &#39;@emdaer/plugin-value-from-package&#39;
  - value: name
--&gt;
</code></pre>
<p>And give it a whirl:</p>
<pre><code class="lang-sh">npm run emdaer
</code></pre>
<p><h2 id="core-plugins">Core Plugins</h2></p>
<ul>
<li><strong><a href="packages/plugin-contributors-details-github">@emdaer/plugin-contributors-details-github</a></strong> An emdaer plugin that gathers and renders contributor details from GitHub</li>
<li><strong><a href="packages/plugin-details">@emdaer/plugin-details</a></strong> An emdaer plugin that renders HTML5 details elements from which users can retrieve additional information</li>
<li><strong><a href="packages/plugin-documentation">@emdaer/plugin-documentation</a></strong> An emdaer plugin to generate documentation from your code comments using documentationjs</li>
<li><strong><a href="packages/plugin-image">@emdaer/plugin-image</a></strong> An emdaer plugin that renders HTML img elements</li>
<li><strong><a href="packages/plugin-import">@emdaer/plugin-import</a></strong> An emdaer plugin that imports content from another file</li>
<li><strong><a href="packages/plugin-license-reference">@emdaer/plugin-license-reference</a></strong> An emdaer plugin that renders license information from the package</li>
<li><strong><a href="packages/plugin-link">@emdaer/plugin-link</a></strong> An emdaer plugin that renders anchor elements</li>
<li><strong><a href="packages/plugin-list">@emdaer/plugin-list</a></strong> An emdaer plugin that renders HTML list element.</li>
<li><strong><a href="packages/plugin-list-lerna-packages">@emdaer/plugin-list-lerna-packages</a></strong> An emdaer plugin that generate a list of lerna packages in a project.</li>
<li><strong><a href="packages/plugin-node-package">@emdaer/plugin-node-package</a></strong> An emdaer plugin that requires a file and optionally executes it with provided arguments.</li>
<li><strong><a href="packages/plugin-shields">@emdaer/plugin-shields</a></strong> An emdaer plugin that renders metadata badges for open source projects from shields.io</li>
<li><strong><a href="packages/plugin-table">@emdaer/plugin-table</a></strong> An emdaer plugin that renders HTML tables</li>
<li><strong><a href="packages/plugin-value-from-package">@emdaer/plugin-value-from-package</a></strong> An emdaer plugin that retrieves and renders values from package.json</li>
</ul>

<p><h2 id="core-transforms">Core Transforms</h2></p>
<ul>
<li><strong><a href="packages/transform-github-emoji">@emdaer/transform-github-emoji</a></strong> An emdaer transformation that renders GitHub-flavored emoji codes</li>
<li><strong><a href="packages/transform-prettier">@emdaer/transform-prettier</a></strong> An emdaer transformation that formats markdown, including code blocks, using prettier</li>
<li><strong><a href="packages/transform-smartypants">@emdaer/transform-smartypants</a></strong> An emdaer transformation that translates ASCII punctuation characters into typographic punctuation HTML entities</li>
<li><strong><a href="packages/transform-table-of-contents">@emdaer/transform-table-of-contents</a></strong> An emdaer transformation that generates a table of contents</li>
</ul>

<h2 id="contributing">Contributing</h2>
<p>If you’d like to make emdaer better, please read our <a href="./CONTRIBUTING.md">guide to contributing</a>.</p>
<!--emdaer-p
  - '@emdaer/plugin-contributors-details-github'
-->
<h2 id="this-readme">This README</h2>
<p>This README was generated with emdaer. However, it is special in that it shares its content with the <a href="emdaer.me">emdaer website</a> via the <a href="https://www.npmjs.com/package/@emdaer/meta">@emdaer/meta</a> and <a href="https://www.npmjs.com/package/@emdaer/plugin-node-package">@emdaer/plugin-node-package</a> packages. <a href="https://www.npmjs.com/package/@emdaer/meta">@emdaer/meta</a> exports each section of this README as a node module which <a href="https://www.npmjs.com/package/@emdaer/plugin-node-package">@emdaer/plugin-node-package</a> imports like so:</p>
<!-- prettier-ignore -->
<pre><code class="lang-md">&lt;!--emdaer-p
  - &#39;@emdaer/plugin-node-package&#39;
  - path: &#39;@emdaer/meta/lib/README/this-readme.js&#39;
--&gt;
</code></pre>
<p><h2 id="license">License</h2></p>
<p>emdaer is <a href="./LICENSE">MIT licensed</a>.</p>




