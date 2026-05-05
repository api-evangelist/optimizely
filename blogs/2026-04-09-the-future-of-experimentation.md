---
title: "The future of experimentation"
url: "https://www.optimizely.com/insights/blog/the-future-of-experimentation/"
date: "2026-04-09T13:29:34Z"
author: ""
feed_url: "https://www.optimizely.com/insights//blog/rss"
---
<p>The Red Queen told Alice it takes all the running you can do just to stay in the same place. AI delivered exactly that dynamic to digital organizations. Teams generate ideas faster, produce content faster, and run experiments faster than ever. So do their competitors.</p>
<p>At the same time, AI is compressing the top of the funnel. Fewer interactions are making it all the way to your owned surfaces, which means many teams now face two shifts at once: the cost of launching experiments is collapsing, and the traffic available to learn from is getting scarcer.</p>
<p>That changes the game. Running more experiments faster is no longer a competitive advantage on its own. Many teams can now do that. The advantage comes from learning faster under tighter constraints.</p>
<h2 class="no-toc"><em>The execution-clarity paradox</em></h2>
<p>This is the central tension.</p>
<blockquote>
<p>AI has made it dramatically cheaper to act, but not cheaper to know what action is worth taking.</p>
</blockquote>
<p>Execution costs are collapsing. The cost of clarity, knowing what to test, what metric matters, and what the result actually means, is rising. The teams that mistake cheaper execution for easier learning will optimize faster toward the wrong outcomes.</p>
<h2>The model of experimentation was built for scarcity</h2>
<p>For most of the last decade, experimentation programs were organized around scarcity. Statistical expertise sat with small data science teams. Engineering time was scarce, so tests competed with roadmap work. Analyst bandwidth was limited, so interpretation often happened days or even weeks after a test ended</p>
<p>Those constraints are fast disappearing. Implementation used to be the gating function for experimentation. Increasingly, it is not.</p>
<p>We are already seeing AI systems surface hypotheses, generate production-quality variations, accelerate test setup, summarize results, produce executive-ready readouts, and recommend next-best actions. For a large share of common experiments in content, messaging, and layout, the marginal cost of execution is approaching zero.</p>
<p>The data backs this up.</p>
<p class="alert note">According to a Gartner forecast (March 2026), by 2030 the cost of performing inference on a trillion-parameter LLM will fall by over 90% compared to 2025. That trajectory is collapsing execution costs across every AI-assisted workflow, experimentation included.</p>
<p class="alert note">Meanwhile, McKinsey's 2025 global survey found that 88% of organizations now use AI in at least one business function, yet the majority remain in piloting stages, not yet realizing enterprise-wide impact. Adoption is scaling faster than the ability to learn from it, which is exactly the gap experimentation programs need to close.</p>
<p>But removing scarcity does not remove complexity. It relocates it. The bottleneck has not disappeared. It has moved upstream.</p>
<p>Cheap execution increases volume faster than it increases understanding. The real questions are now harder:</p>
<blockquote>
<p>What are we trying to learn?<br />Which outcome matters?<br />Which metric indicates true signal, not just noise?</p>
</blockquote>
<p>Three things become critical human responsibilities.</p>
<ol class="list-large-numbers">
<li><strong>Defining the metric framework:</strong> The metric framework is the set of leading indicators that should predict the business outcome you care about. If the loop targets day-7 activation but that doesn&rsquo;t predict 12-month retention, the organization has built an efficient machine pointed at the wrong target.</li>
<li><strong>Setting guardrails:</strong> A loop optimized only for conversion will eventually find the most aggressive path to conversion, whether or not it creates long-term value. Someone still has to define the constraints.</li>
<li><strong>Knowing when to override the system:</strong> Some strategic moves underperform in the short term. The system will try to revert to the local optimum. Knowing when to hold course is still human judgment.</li>
</ol>
<p>Most experimentation teams are organized around running experiments. When AI owns that, the job moves upstream. It is deciding what is worth learning, what business outcome is worth moving, and which metrics actually tell you if you succeeded.</p>
<h2>Are you still testing pages or testing decision policies?</h2>
<p>The old mental model of experimentation was static comparison: A versus B. Two variations, one winner, ship it. That model is not dead. But it is no longer the center of gravity.</p>
<p>Increasingly, the object being tested is not a page or a variation. It is a decision policy: what to show, when to intervene, how to route, which offer or model or prompt to invoke, across web, app, and email.</p>
<p>A variation is a fixed experience. A policy is a set of rules, probabilities, or learned behaviors that determines which experience gets delivered under which conditions. It has to be evaluated across contexts, channels, user segments, and time, not just declared a winner and shipped.</p>
<blockquote>
<p>The question is no longer which version performs better. It is which decision logic consistently produces better outcomes.</p>
</blockquote>
<p>The teams that recognize this early will stop treating experimentation as a page-level optimization function and start treating it as a system for evaluating decision quality.</p>
<h2>How do evals and experiments connect into one learning loop?</h2>
<p>As decision systems become more dynamic, not every candidate should go straight into live traffic. This is where evals become essential.</p>
<p>Evals are the screening layer used to assess quality, consistency, and safety before a candidate reaches live users. In practice, that can mean curated golden datasets, unit tests for expected behavior, or model-based judging against defined criteria. Live experiments remain the proof layer to show whether a change actually moved behavior or business outcomes in real conditions. Neither alone is sufficient.</p>
<p class="alert note">Andrej Karpathy ran 700 experiments in 48 hours with no human intervention through his open-source autoresearch system &mdash; because it had a reliable offline eval metric. The agent found 20 genuine improvements that months of manual work had missed. Shopify's CEO replicated the pattern overnight for a 19% gain. The lesson: when you have a trustworthy eval, experiment cost collapses to near zero. Without one, volume is just noise</p>
<p>Evals without experiments produce quality assessments, not causal evidence. Experiments without evals waste live traffic on candidates that should never have been promoted.</p>
<p>The architecture that works is straightforward:</p>
<ul class="list-checkmarks">
<li>Define the policy</li>
<li>Test it offline</li>
<li>Send stronger candidates into traffic</li>
<li>Measure causal impact</li>
<li>Feed failures back into the eval system</li>
</ul>
<p><strong>Evals filter. Experiments prove.</strong></p>
<p>This is already visible in ad tech. Google&rsquo;s Performance Max and Meta&rsquo;s Advantage+ generate and evaluate candidate policies continuously. The loop runs continuously rather than waiting for a human to declare a winner.</p>
<p>Over the last 1&ndash;2 years, the most forward-looking product and engineering leaders I speak with have started treating evals as the way to ensure the quality of what they ship. But A/B testing remains the gold standard for proving those experiences actually improve outcomes, especially when they are LLM-based and non-deterministic.</p>
<p>The strongest teams will stop treating evals and experiments as separate practices run by different people with different goals. The tooling to support this end-to-end is still maturing across the industry, but the architectural pattern is clear: they connect into one learning loop.</p>
<h2>The COE does not disappear. Its job changes.</h2>
<p>If the learning loop increasingly runs itself by surfacing hypotheses, generating variations, and interpreting results, the question becomes who sets the boundaries it operates within.</p>
<p>As experimentation is becoming easier to launch, more distributed across teams, and less dependent on engineering, a central team cannot remain the reviewer of every test, the interpreter of every result, and the human backstop for every bad decision.</p>
<p>That does not mean governance becomes less important. It means governance will increasingly sit in the system itself: setup guardrails, design checks, metric warnings, standard evaluation loops, and clearer escalation paths for the cases that actually require human judgment.</p>
<p>The point is not to remove rigor from experimentation. It is to stop requiring a small number of people to manually carry all of it. The COE still matters because humans still have to shape the process, handle exceptions, and drive adoption across the organization.</p>
<p>The COE becomes less of a throughput bottleneck and more of a standards owner, change agent, and escalation path. It defines constraints, sets quality bars, decides where human oversight remains non-negotiable, and helps the organization adopt new ways of working without losing rigor.</p>
<blockquote>
<p>The old COE protected the discipline by centralizing judgment. The next one will protect it by designing the system and organizational habits that democratize judgment safely.</p>
</blockquote>
<h2>Statistical rigor becomes the compounding advantage</h2>
<p>Bad statistical inference scales just as easily as good inference. You are no longer risking one bad test. You are risking a system that gets better and better at optimizing the wrong thing.</p>
<p>Most experimentation programs were built when traffic was abundant enough to tolerate weak methodology. Teams could afford noisy tests, blunt metrics, and a fair amount of waste. Many cannot anymore. If execution cost is falling while the traffic available to learn from is getting scarcer, the organizations that learn efficiently gain a real edge.</p>
<p>That is why statistical rigor stops being methodology hygiene and becomes a structural advantage. Plugging data into an LLM and asking for a conclusion is not statistical rigor. Methods that improve signal efficiency and raise the standard of proof will matter more: variance reduction, sequential approaches, stronger proxy design, false-positive control, and tighter causal discipline.</p>
<blockquote>
<p>More experiments are not the goal. More reliable learning is.</p>
</blockquote>
<p>The winners in the next era will not simply be the teams that can launch more tests. They will be the ones that can learn faster under tighter constraints without lowering the standard of proof.</p>
<h2>Wrapping up...</h2>
<p><strong>When execution gets cheap, clarity gets expensive.</strong> The next era of experimentation will not be won by the organizations that run the most tests. It will be won by the ones that know what they are trying to change, define the business outcome that matters, and can prove they changed it. As experimentation gets cheaper and more distributed, the real advantage shifts to judgment, governance, and rigor.</p>
<p>Check out <a href="https://www.optimizely.com/solutions/experience-optimization/">Optimizely Experience Optimization</a> platform</p>
<hr />
<p><strong>Sources</strong></p>
<ol class="NumberListStyle1 SCXW261498005 BCX4 list-large-numbers" start="1">
<li>
<p>Gartner. <a href="https://www.gartner.com/en/newsroom/press-releases/2026-03-25-gartner-predicts-that-by-2030-performing-inference-on-an-llm-with-1-trillion-parameters-will-cost-genai-providers-over-90-percent-less-than-in-2025" rel="noopener" target="_blank">Gartner Predicts That by 2030</a>, Performing Inference on an LLM Will Cost Over 90% Less Than in 2025. Press release, March 25, 2026.</p>
</li>
<li>
<p>McKinsey &amp; Company. <a class="Hyperlink SCXW261498005 BCX4" href="https://www.mckinsey.com/capabilities/quantumblack/our-insights/the-state-of-ai" rel="noopener" target="_blank">The State of AI in 2025: Agents, Innovation, and Transformation</a>. November 2025.</p>
</li>
<li>Karpathy, A. <a class="Hyperlink SCXW261498005 BCX4" href="https://github.com/karpathy/autoresearch" rel="noopener" target="_blank">autoresearch</a>. GitHub, March 2026. Coverage: <a class="Hyperlink SCXW261498005 BCX4" href="https://fortune.com/2026/03/17/andrej-karpathy-loop-autonomous-ai-agents-future/" rel="noopener" target="_blank">Fortune</a>, March 17, 2026.</li>
</ol>
