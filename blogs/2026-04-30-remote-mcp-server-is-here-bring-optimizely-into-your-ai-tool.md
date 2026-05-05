---
title: "Remote MCP Server is here: Bring Optimizely into your AI tools"
url: "https://www.optimizely.com/insights/blog/experimentation-mcp-server/"
date: "2026-04-30T09:08:10Z"
author: ""
feed_url: "https://www.optimizely.com/insights//blog/rss"
---
<p>At Optimizely, we're always looking for ways to make experimentation more seamless, intuitive, and integrated into your daily workflow. When we introduced the Optimizely MCP Server, we brought experimentation into the developer's Integrated Development Environment (IDE). Today, we're opening it up to the rest of your team with the <strong>Optimizely Remote MCP Server for Experimentation</strong>.</p>
<p>It's a shift in how your whole team interacts with experimentation. Imagine managing feature flags, querying experiment results, and reporting on your program's health, directly from the AI tools you already use. And chances are, you already use them.</p>
<p>Many teams are already using tools like ChatGPT, Claude, or Cursor in their day-to-day work. Now, you can use Optimizely directly from those tools. With the Remote MCP Server, you can query experimentation data, create and update flags, and manage experiments using natural language, without switching tools or writing scripts.</p>
<blockquote>
<p>That's available <em>today</em> &mdash; but <strong>that's just the beginning</strong>. Remote MCP support for Optimizely CMS and Optimizely Analytics is coming soon, meaning you'll be able to manage content, run experiments, and surface insights across your entire stack, all from the AI tools you already work in. More on that below.</p>
</blockquote>
<h2>What is MCP?</h2>
<p>You might be wondering, "What's MCP?" MCP stands for <strong>Model Context Protocol. </strong>It's an open standard that lets AI products talk to external tools and services. Think of it as a universal translator between your AI tool and the platforms you use every day. Instead of building custom integrations for every AI client, MCP gives us a common language. Any compatible AI assistant can communicate with any MCP-enabled service.</p>
<p>Our Remote MCP Server uses this protocol to give AI products native access to our experimentation platform. So, your AI assistant doesn't just help you write code or draft a plan, it can create feature flags, configure experiments, and analyze your program as naturally as it helps you debug a function or summarize a doc. It's about making AI a true experimentation collaborator.</p>
<h3>Key capabilities: Experimentation in the tools your team already uses</h3>
<p>The Optimizely Remote MCP Server brings the full power of Web Experimentation and Feature Experimentation into your AI tool of choice.</p>
<video controls="controls" width="400"><source src="https://uxwamy.files.cmp.optimizely.com/download/29cc7ac63fcd11f1b471ba1d48904351?attachment=false" type="video/mp4" /></video>

<p>Here's a peek at what you can do:</p>
<h3>1. Manage experimentation without leaving your AI tool</h3>
<p>Create and configure feature flags and experiments by asking for what you need in plain language:</p>
<ul class="BulletListStyle1 SCXW213085932 BCX4 list-arrows">
<li>
<p>&ldquo;Create a feature flag called pricing_redesign with control and treatment variations&rdquo;</p>
</li>
<li>
<p>"Set up an A/B test for the checkout flow with 3 variations, tracking conversion on purchase_completed"</p>
</li>
<li>
<p>"Enable the new_onboarding flag for 20% of users in staging"</p>
</li>
</ul>
<p>What used to take multiple API calls, creating flags, setting up variables, configuring environments, establishing audiences, and setting rollout rules, now happens with a single command. The MCP Server handles all the orchestration, making sure everything is created in the right order with proper dependencies.</p>
<h3>2. Ask for answers in seconds</h3>
<p>Get experiment results, flag status, active experiments, and audience details in plain language:</p>
<ul class="BulletListStyle1 SCXW74470533 BCX4 list-arrows">
<li>
<p>"What audiences are being used in running experiments?"</p>
</li>
<li>
<p>"What experiment contains the custom JavaScript that's throwing 'undefined is not a function' errors?"</p>
</li>
<li>
<p>"Show me the targeting conditions for the checkout_flow experiment"</p>
</li>
</ul>
<p>Get immediate insights into flag evaluation, targeting rules, and configuration issues without digging through multiple screens. It's about getting you back to building, or back to your analysis, faster.</p>
<h3>3. Manage the full flag lifecycle from your IDE</h3>
<p>Developers can get onboarded to Optimizely's SDKs, implement feature flags in the codebase, and clean up stale flags without leaving their editor:</p>
<ul class="BulletListStyle1 SCXW91586732 BCX4 list-arrows">
<li>
<p>"Which flags in my codebase haven't been updated in a while?"</p>
</li>
<li>
<p>"Show me unused flags in the authentication service codebase"</p>
</li>
<li>
<p>"Generate a cleanup plan for stale flags in production"</p>
</li>
</ul>
<p>The server cross-references your codebase with Optimizely and gives you actionable recommendations for keeping your experimentation setup clean and tidy.</p>
<h3>4. Generate SDK integration code</h3>
<p>Stop copying boilerplate code from documentation. Get production-ready code instantly:</p>
<ul class="BulletListStyle1 SCXW241386538 BCX4 list-arrows">
<li>
<p>"Generate React SDK integration for the recommendation_engine flag"</p>
</li>
<li>
<p>"Implement event tracking for when a user submits the form"</p>
</li>
<li>
<p>"Show me how to implement the checkout_flow flag with proper error handling"</p>
</li>
</ul>
<p>The generated code includes error handling, fallback values, and follows best practices for your specific framework.</p>
<h3>5. Open experimentation beyond developers</h3>
<p>PMs, program managers, and experimentation teams can now interact with Optimizely directly through the AI tools they already use. Because the server is hosted, browser-based tools like ChatGPT and Claude.ai work out of the box. No code editor, no terminal, no API knowledge required. Someone who's never touched an API script can ask for experiment results, pull audience details, or draft a new test, all in natural language.</p>
<h2>How it works: Smart, secure, seamless</h2>
<p>The Optimizely Remote MCP Server is hosted by Optimizely and connects your AI tool directly to our experimentation APIs. Here's what that means in practice:</p>
<ol class="list-large-numbers">
<li><strong>Simple setup with OAuth: </strong>Authenticate with your existing Optimizely login. No API keys to manage, no packages to install, no local server to run. The same credentials you already use.</li>
<li><strong>Broad client compatibility: </strong>Works with any MCP-compatible client, including ChatGPT, Claude, Cursor, VS Code with Copilot, Claude Code, Windsurf, and other IDE-based tools.</li>
<li><strong>Tool coverage: </strong>It supports both Web Experimentation and Feature Experimentation, with querying, creating, and updating entities across core API operations.</li>
<li><strong>Inherited permissions: </strong>The server respects the same user permissions as the Optimizely platform. People can only do through MCP what they can already do in the UI.</li>
<li><strong>Context-aware:</strong> It understands your project structure and can make intelligent suggestions based on your codebase.</li>
</ol>
<h2>What&rsquo;s next: The future of AI-driven experimentation</h2>
<p>As MCP adoption grows across the development ecosystem, we&rsquo;re excited about the possibilities ahead. We&rsquo;re envisioning a future where AI agents can:</p>
<ol class="list-large-numbers">
<li><strong>Orchestrate complex marketing workflows:</strong> Imagine autonomous campaign management agents creating dozens of interconnected personalization campaigns, managing cascading audiences, and updating priorities across your entire program.</li>
<li><strong>Suggest proactive optimizations:</strong> AI agents could analyze your code and suggest where feature flags could reduce risk, before you even think to ask.</li>
<li><strong>Deliver intelligent experiment analysis:</strong> Get natural language queries about experiment performance and automated insights, helping you make data-driven decisions faster.</li>
<li><strong>Connect your entire martech stack:</strong> An extensible plugin architecture will let you extend the MCP Server&rsquo;s capabilities, syncing audience segments from Optimizely Data Platform and automatically creating targeted experiments.</li>
</ol>
<h2>Beyond experimentation: MCP across the full Optimizely platform</h2>
<p>The Experimentation Remote MCP Server is live today, but as we've already hinted to: we're not stopping there. <strong>Remote MCP support for Optimizely CMS and Optimizely Analytics</strong> is on the way.</p>
<p>That means your AI tools will soon be able to create and publish content, run and analyze experiments, and pull performance insights, all from a single natural language interface, without switching platforms or writing a single line of code.</p>
<p>This is what it looks like for Optimizely to be fully set up for the agentic future: every part of your stack accessible, orchestratable, and actionable through AI. MCP is how we get there.</p>
<p>Stay tuned for updates on CMS and Analytics MCP availability, and in the meantime, get strarted with the Experimentation Remote MCP Server today. 👇</p>
<h2>Be part of the future</h2>
<p>The Optimizely MCP Server for Experimentation is available to all Optimizely Experimentation customers, for both Web and Feature Experimentation. No separate sign-up, no waitlist.</p>
<p>To get started:</p>
<ul class="list-arrows">
<li>Connect the MCP Server to your AI client of choice</li>
<li>Point it at your Optimizely account</li>
<li>Start building, querying, and updating experiments from wherever you work</li>
</ul>
<p>We can't wait to see what you build with it.</p>
