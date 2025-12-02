<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lucio AI | PromptLayer Integration Report</title>
    <script src="https://cdn.jsdelivr.net/npm/mermaid/dist/mermaid.min.js"></script>
    <style>
        /* Lucio AI Theme - Refined */
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600&family=Playfair+Display:ital,wght@0,400;0,600;0,700;1,400&display=swap');

        :root {
            --bg-color: #ffffff;
            --text-color: #1a1a1a;
            --text-secondary: #4a5568;
            --accent-green-bg: #e6f4ea;
            --accent-green-text: #064e3b;
            --button-dark: #1a202c;
            --button-light: #f3f4f6;
            --border-color: #e2e8f0;
            --card-bg: #ffffff;
            --section-bg: #f9fafb;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: 'Inter', sans-serif;
            background-color: var(--bg-color);
            color: var(--text-color);
            line-height: 1.6;
            -webkit-font-smoothing: antialiased;
        }

        /* Typography */
        h1,
        h2,
        h3,
        h4,
        h5,
        h6 {
            font-family: 'Playfair Display', serif;
            font-weight: 400;
            color: var(--text-color);
            letter-spacing: -0.01em;
        }

        h1 {
            font-size: 3.5rem;
            line-height: 1.2;
            margin-bottom: 1.5rem;
        }

        h2 {
            font-size: 2.5rem;
            margin-bottom: 1.5rem;
        }

        h3 {
            font-size: 1.5rem;
            font-weight: 600;
            margin-bottom: 0.5rem;
        }

        p {
            margin-bottom: 1.5rem;
            font-size: 1.1rem;
            color: var(--text-secondary);
        }

        a {
            color: var(--text-color);
            text-decoration: none;
            font-weight: 500;
            transition: color 0.2s;
        }

        a:hover {
            color: #000;
        }

        /* Layout */
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 2rem;
        }

        /* Header */
        header {
            background-color: var(--bg-color);
            padding: 1.5rem 0;
            position: sticky;
            top: 0;
            z-index: 100;
            border-bottom: 1px solid transparent;
            transition: border-color 0.3s;
        }

        header.scrolled {
            border-color: var(--border-color);
        }

        header .container {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-family: 'Playfair Display', serif;
            font-size: 1.8rem;
            font-weight: 600;
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        .logo span {
            font-family: 'Inter', sans-serif;
            font-size: 0.9rem;
            font-weight: 400;
            color: var(--text-secondary);
            margin-left: 0.5rem;
            padding-left: 0.5rem;
            border-left: 1px solid var(--border-color);
        }

        nav ul {
            list-style: none;
            display: flex;
            gap: 2.5rem;
            align-items: center;
        }

        nav a {
            font-size: 0.95rem;
            color: var(--text-secondary);
        }

        nav a:hover {
            color: var(--text-color);
        }

        .btn-primary {
            background-color: var(--button-dark);
            color: #fff;
            padding: 0.6rem 1.2rem;
            border-radius: 4px;
            font-size: 0.9rem;
            font-weight: 500;
            transition: opacity 0.2s;
        }

        .btn-primary:hover {
            opacity: 0.9;
            color: #fff;
        }

        /* Hero Section */
        .hero {
            padding: 6rem 0 5rem;
            text-align: center;
            background: radial-gradient(circle at 50% 0%, #f7fafc 0%, #ffffff 70%);
        }

        .badge {
            display: inline-block;
            background-color: var(--accent-green-bg);
            color: var(--accent-green-text);
            padding: 0.4rem 1rem;
            border-radius: 50px;
            font-size: 0.85rem;
            font-weight: 600;
            margin-bottom: 2rem;
        }

        .hero p {
            font-size: 1.25rem;
            max-width: 700px;
            margin: 0 auto 2.5rem;
        }

        .hero-actions {
            display: flex;
            gap: 1rem;
            justify-content: center;
        }

        .btn-secondary {
            background-color: var(--button-light);
            color: var(--text-color);
            padding: 0.8rem 1.5rem;
            border-radius: 4px;
            font-size: 1rem;
            font-weight: 500;
        }

        .btn-secondary:hover {
            background-color: #e2e8f0;
        }

        /* Content Sections */
        section {
            padding: 5rem 0;
        }

        .section-bg {
            background-color: var(--section-bg);
        }

        .grid-2 {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 4rem;
            align-items: start;
        }

        /* Cards */
        .card {
            background: var(--card-bg);
            padding: 2rem;
            border-radius: 12px;
            border: 1px solid var(--border-color);
            transition: box-shadow 0.2s;
        }

        .card:hover {
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.05);
        }

        /* Code Blocks */
        pre {
            background-color: #f8fafc;
            padding: 1.5rem;
            border-radius: 8px;
            overflow-x: auto;
            border: 1px solid var(--border-color);
            font-size: 0.9rem;
        }

        /* Mermaid */
        .mermaid {
            background: #fff;
            padding: 2rem;
            border-radius: 12px;
            border: 1px solid var(--border-color);
            display: flex;
            justify-content: center;
            margin-top: 2rem;
        }

        /* Tables */
        table {
            width: 100%;
            border-collapse: separate;
            border-spacing: 0;
            border: 1px solid var(--border-color);
            border-radius: 8px;
            overflow: hidden;
        }

        th,
        td {
            padding: 1rem 1.5rem;
            text-align: left;
            border-bottom: 1px solid var(--border-color);
        }

        th {
            background-color: #f8fafc;
            font-weight: 600;
            font-size: 0.9rem;
            text-transform: uppercase;
            letter-spacing: 0.05em;
            color: var(--text-secondary);
        }

        tr:last-child td {
            border-bottom: none;
        }

        /* Footer */
        footer {
            border-top: 1px solid var(--border-color);
            padding: 4rem 0;
            margin-top: 4rem;
            text-align: center;
        }

        /* Responsive */
        @media (max-width: 768px) {
            h1 {
                font-size: 2.5rem;
            }

            .grid-2 {
                grid-template-columns: 1fr;
                gap: 2rem;
            }

            nav ul {
                display: none;
            }
        }
    </style>
</head>

<body>

    <header>
        <div class="container">
            <div class="logo">
                Lucio <span>PromptLayer Report</span>
            </div>
            <nav>
                <ul>
                    <li><a href="#">Home</a></li>
                    <li><a href="#core">Features</a></li>
                    <li><a href="#registry">Registry</a></li>
                    <li><a href="#integration">Integration</a></li>
                    <li><a href="#pricing">Pricing</a></li>
                </ul>
            </nav>
            <div style="display: flex; gap: 1.5rem; align-items: center;">
                <a href="https://docs.promptlayer.com/features/prompt-registry/overview" target="_blank"
                    class="btn-primary">Read Official Docs</a>
            </div>
        </div>
    </header>

    <main>
        <section class="hero">
            <div class="container">
                <div class="badge">Technical Report</div>
                <h1>PromptLayer Integration Strategy</h1>
                <p>A technical analysis for integrating PromptLayer's Prompt Registry into the Lucio AI ecosystem to
                    accelerate legal intelligence.</p>

                <div class="hero-actions">
                    <a href="#core" class="btn-primary" style="padding: 0.8rem 1.5rem;">Read Report</a>
                    <a href="https://docs.promptlayer.com/features/prompt-registry/overview" target="_blank"
                        class="btn-secondary">View Documentation</a>
                </div>
            </div>
        </section>

        <section id="core">
            <div class="container">
                <div style="text-align: center; max-width: 800px; margin: 0 auto 4rem;">
                    <h2>Core Functionality</h2>
                    <p>PromptLayer acts as a middleware between your application and LLM providers, providing tools for
                        tracking, managing, and optimizing prompts.</p>
                </div>

                <div class="grid-2">
                    <div class="card">
                        <h3>Prompt Registry (CMS)</h3>
                        <p>A centralized repository to store, version, and manage prompt templates. Decouples prompt
                            engineering from code deployment.</p>
                    </div>
                    <div class="card">
                        <h3>Observability</h3>
                        <p>Logs every request made to the LLM, capturing inputs, outputs, latency, cost, and timestamps
                            for full transparency.</p>
                    </div>
                    <div class="card">
                        <h3>Analytics</h3>
                        <p>Visualizes usage data to identify trends, expensive prompts, or high-latency models across
                            your user base.</p>
                    </div>
                    <div class="card">
                        <h3>Collaboration</h3>
                        <p>Allows non-technical domain experts (lawyers) to edit prompts visually without touching the
                            codebase.</p>
                    </div>
                </div>
            </div>
        </section>

        <section id="registry" class="section-bg">
            <div class="container">
                <div style="text-align: center; margin-bottom: 3rem;">
                    <h2>Prompt Registry (CMS)</h2>
                    <p>The "Content Management System" for your AI prompts. Fetch them dynamically instead of
                        hardcoding.</p>
                </div>

                <!-- Usability Overview -->
                <div style="margin-bottom: 4rem;">
                    <div class="grid-2">
                        <div class="card">
                            <h3>For Developers</h3>
                            <p>Functions like a package manager. You "pull" prompts by name and "push" new versions
                                programmatically via SDKs.</p>
                        </div>
                        <div class="card">
                            <h3>For Domain Experts</h3>
                            <p>Offers a visual dashboard to edit text, change models, and save versions without touching
                                a single line of code.</p>
                        </div>
                    </div>
                </div>

                <!-- Detailed Features -->
                <h3 style="margin-bottom: 2rem;">Core Features & Functions</h3>
                <div class="grid-2">
                    <div>
                        <h4>A. Centralized Storage</h4>
                        <p>All prompts live in one searchable registry. Organize by tags (<code>legal</code>,
                            <code>engineering</code>) or metadata.</p>
                    </div>
                    <div>
                        <h4>B. Version Control</h4>
                        <p>Every save creates an immutable version with commit messages. Includes Diff View and Instant
                            Rollback.</p>
                    </div>
                    <div>
                        <h4>C. Release Labels</h4>
                        <p>Dynamic pointers like <code>prod</code> or <code>dev</code>. Supports A/B testing by
                            splitting traffic (e.g., 90% to v12, 10% to v13).</p>
                    </div>
                    <div>
                        <h4>D. Programmatic Access</h4>
                        <p>Full API access for fetching, publishing, and tracking prompts.</p>
                    </div>
                </div>

                <!-- API Reference -->
                <h3 style="margin-top: 4rem; margin-bottom: 1.5rem;">API Reference</h3>
                <div class="card" style="padding: 0; overflow: hidden; border: none;">
                    <table>
                        <thead>
                            <tr>
                                <th>Function</th>
                                <th>Description</th>
                                <th>Code Snippet</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td><strong>Get</strong></td>
                                <td>Fetch a specific prompt version.</td>
                                <td><code>pl.templates.get("my_prompt", label="prod")</code></td>
                            </tr>
                            <tr>
                                <td><strong>Publish</strong></td>
                                <td>Create or update a prompt.</td>
                                <td><code>pl.templates.publish(name="my_prompt", template=...)</code></td>
                            </tr>
                            <tr>
                                <td><strong>Track</strong></td>
                                <td>Link a runtime execution.</td>
                                <td><code>pl.track.prompt(request_id, prompt_name="my_prompt")</code></td>
                            </tr>
                        </tbody>
                    </table>
                </div>

                <!-- Architecture Diagram -->
                <h3 style="margin-top: 4rem;">Integrations & Architecture</h3>
                <div class="mermaid">
                    graph TD
                    subgraph "Your Application"
                    Code[Application Code]
                    SDK[PromptLayer SDK]
                    end

                    subgraph "PromptLayer Cloud"
                    Registry[(Prompt Registry)]
                    Dashboard[Visual Dashboard]
                    end

                    subgraph "AI Provider"
                    LLM{OpenAI / Anthropic}
                    end

                    Dashboard --"1. Edit & Save"--> Registry
                    Code --"2. Fetch('prod')"--> SDK
                    SDK --"3. Get Template"--> Registry
                    Registry --"4. Return Template"--> SDK
                    SDK --"5. Run Prompt"--> LLM
                    LLM --"6. Response"--> SDK
                    SDK --"7. Log Execution"--> Registry
                </div>

                <!-- Pros & Cons -->
                <h3 style="margin-top: 4rem; margin-bottom: 2rem;">Pros & Cons</h3>
                <div class="grid-2">
                    <div class="card" style="background-color: var(--button-dark); color: #fff; border: none;">
                        <h4
                            style="color: #fff; border-bottom: 1px solid #444; padding-bottom: 0.5rem; margin-bottom: 1rem;">
                            Pros</h4>
                        <ul style="color: #cbd5e0; margin-left: 1.5rem; line-height: 1.8;">
                            <li><strong>Decoupling:</strong> Code doesn't change when prompts change.</li>
                            <li><strong>Visibility:</strong> Everyone sees what's running in production.</li>
                            <li><strong>A/B Testing:</strong> Native support for traffic splitting.</li>
                            <li><strong>History:</strong> Full commit log and accountability.</li>
                        </ul>
                    </div>
                    <div class="card" style="background-color: var(--button-dark); color: #fff; border: none;">
                        <h4
                            style="color: #fff; border-bottom: 1px solid #444; padding-bottom: 0.5rem; margin-bottom: 1rem;">
                            Cons</h4>
                        <ul style="color: #cbd5e0; margin-left: 1.5rem; line-height: 1.8;">
                            <li><strong>Cost:</strong> Enterprise features scale with usage.</li>
                        </ul>
                    </div>
                </div>
            </div>
        </section>

        <section id="integration">
            <div class="container">
                <div style="text-align: center; margin-bottom: 3rem;">
                    <h2>Integration Strategy</h2>
                    <p>Seamlessly embedding PromptLayer into the Lucio ecosystem.</p>
                </div>

                <div class="card" style="margin-bottom: 2rem; border-left: 4px solid var(--button-dark);">
                    <h3>A. Lucio AI Word Plugin</h3>
                    <p><strong>Goal:</strong> Enable lawyers to use the latest prompts directly within Microsoft Word.
                    </p>
                    <ol style="margin-left: 1.5rem; margin-top: 1rem; color: var(--text-secondary);">
                        <li style="margin-bottom: 0.5rem;"><strong>Fetch:</strong> Plugin queries PromptLayer for active
                            <code>word-plugin</code> prompts.</li>
                        <li style="margin-bottom: 0.5rem;"><strong>Cache:</strong> Prompts cached locally for speed and
                            offline capability.</li>
                        <li style="margin-bottom: 0.5rem;"><strong>Execute:</strong> Plugin sends text to LLM via
                            PromptLayer proxy.</li>
                        <li><strong>Track:</strong> Request logged with metadata (<code>user_id</code>,
                            <code>plugin_version</code>).</li>
                    </ol>
                </div>

                <div class="grid-2">
                    <div class="card">
                        <h3>B. Lucio Desktop App</h3>
                        <p>Similar to the Word Plugin but for system-wide tasks. Supports offline access by downloading
                            "Production" bundles on startup.</p>
                    </div>
                    <div class="card">
                        <h3>C. Centralized Dashboard</h3>
                        <p>A web portal for the Admin to manage versions, promote from <code>dev</code> to
                            <code>prod</code>, and view cost analytics per client.</p>
                    </div>
                </div>

                <h3 style="margin-top: 3rem; margin-bottom: 1.5rem;">Deep Integration (Python SDK)</h3>
                <p>PromptLayer provides a drop-in replacement for the OpenAI client, making integration trivial.</p>
                <div class="card" style="background-color: #f8fafc; border: 1px solid var(--border-color);">
                    <pre><code style="color: #333;">from promptlayer import PromptLayer

# Initialize PromptLayer
promptlayer_client = PromptLayer()

# Swap out 'from openai import OpenAI'
OpenAI = promptlayer_client.openai.OpenAI
client = OpenAI()

# Make requests as usual - they are automatically logged!
completion = client.chat.completions.create(
  model="gpt-3.5-turbo",
  messages=[
    {"role": "system", "content": "You are a legal assistant."},
    {"role": "user", "content": "Draft a confidentiality clause."}
  ],
  pl_tags=["legal-drafting"]
)</code></pre>
                </div>
            </div>
        </section>

        <section id="pricing" class="section-bg">
            <div class="container">
                <div style="text-align: center; margin-bottom: 3rem;">
                    <h2>Pricing & Plans</h2>
                    <p>Flexible options for teams of all sizes.</p>
                </div>
                <div class="grid-2" style="grid-template-columns: repeat(4, 1fr); gap: 1rem;">
                    <div class="card" style="text-align: center;">
                        <h3>Free</h3>
                        <p style="font-size: 1.2rem; font-weight: 600; margin-bottom: 0.5rem;">$0 <span
                                style="font-size: 0.9rem; font-weight: 400; color: #666;">/ month</span></p>
                        <hr style="margin: 1rem 0; border: 0; border-top: 1px solid #eee;">
                        <ul style="list-style: none; text-align: left; font-size: 0.9rem;">
                            <li>• 5,000 Requests / mo</li>
                            <li>• 7-Day Log Retention</li>
                            <li>• Basic Prompt Management</li>
                        </ul>
                    </div>
                    <div class="card" style="text-align: center; border: 2px solid var(--button-dark);">
                        <h3>Pro</h3>
                        <p style="font-size: 1.2rem; font-weight: 600; margin-bottom: 0.5rem;">$50 <span
                                style="font-size: 0.9rem; font-weight: 400; color: #666;">/ user / mo</span></p>
                        <hr style="margin: 1rem 0; border: 0; border-top: 1px solid #eee;">
                        <ul style="list-style: none; text-align: left; font-size: 0.9rem;">
                            <li>• 100,000 Requests / mo</li>
                            <li>• Unlimited Log Retention</li>
                            <li>• Collaboration Tools</li>
                        </ul>
                    </div>
                    <div class="card" style="text-align: center;">
                        <h3>Team</h3>
                        <p style="font-size: 1.2rem; font-weight: 600; margin-bottom: 0.5rem;">Custom</p>
                        <hr style="margin: 1rem 0; border: 0; border-top: 1px solid #eee;">
                        <ul style="list-style: none; text-align: left; font-size: 0.9rem;">
                            <li>• Higher Rate Limits</li>
                            <li>• Role-Based Access</li>
                            <li>• Advanced Analytics</li>
                        </ul>
                    </div>
                    <div class="card" style="text-align: center;">
                        <h3>Enterprise</h3>
                        <p style="font-size: 1.2rem; font-weight: 600; margin-bottom: 0.5rem;">Custom</p>
                        <hr style="margin: 1rem 0; border: 0; border-top: 1px solid #eee;">
                        <ul style="list-style: none; text-align: left; font-size: 0.9rem;">
                            <li>• SSO / SAML</li>
                            <li>• Deployment Approvals</li>
                            <li>• Dedicated Support</li>
                        </ul>
                    </div>
                </div>
            </div>
        </section>

        <section id="use-case">
            <div class="container">
                <div style="text-align: center; margin-bottom: 3rem;">
                    <h2>Use Case: Legal Contract Review</h2>
                    <p>Scenario: A lawyer needs to review a Non-Disclosure Agreement (NDA) for risky clauses.</p>
                </div>

                <div class="grid-2">
                    <div class="card">
                        <h3>1. Creation</h3>
                        <p>Lead Legal Engineer creates <code>nda-risk-scanner</code> in PromptLayer with system
                            instructions to identify non-standard clauses.</p>
                    </div>
                    <div class="card">
                        <h3>2. Deployment</h3>
                        <p>The prompt is tagged <code>prod</code>. No code deployment is required.</p>
                    </div>
                    <div class="card">
                        <h3>3. Usage</h3>
                        <p>Lawyer selects "Scan for Risks" in the Lucio Plugin. The plugin fetches the latest prompt and
                            analyzes the document.</p>
                    </div>
                    <div class="card">
                        <h3>4. Iteration</h3>
                        <p>If a "False Positive" is flagged, the Engineer updates the prompt in the Registry. The new
                            version is instantly available to all lawyers.</p>
                    </div>
                </div>
            </div>
        </section>

    </main>

    <footer>
        <div class="container">
            <div class="logo" style="justify-content: center; margin-bottom: 1rem;">Lucio</div>
            <p>&copy; 2025 Lucio AI. All rights reserved.</p>
        </div>
    </footer>

    <script>
        mermaid.initialize({ startOnLoad: true, theme: 'neutral' });
    </script>
</body>

</html>
