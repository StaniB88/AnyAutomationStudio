# AnyAutomation Studio — Changelog

User-facing changes, newest first.

## v1.128.1

- AI Chat – long conversations stay fast and leaner, and a cancelled action no longer gets the chat stuck.
- AI Chat – the context details show a Session total of all tokens the conversation has used.
- AI Chat – the context details show a request's total input tokens across all rounds.
- AI Chat – other installed extensions now need your one-time permission before they can use your configured AI models.
- AI Chat – your model list and the Manage Models button stay available even after another extension signs in to GitHub.
- AI Chat – the assistant loads its programming reference guides on demand, keeping conversations lean when working with PLC code.
- AI Chat – the assistant follows large instruction files in full.
- AI Chat – the assistant's edits and actions complete more reliably, with incomplete block edits caught before anything is saved.
- AI Chat – the assistant can replace every occurrence of a text in a file or block in one step.
- AI Chat – compile and import results in the assistant's reply name the affected blocks, with line numbers for compile errors and warnings.
- AI Chat – failed requests show a clear error message in the chat.
- TIA Portal – open block editors pick up imported changes, and saving warns when the block changed in the meantime.
- TIA Portal – opening an inconsistent block shows a notice to compile it in TIA Portal first.
- TIA Portal – compile results show the message text for every reported problem.

## v1.128.0

- AI Chat – the OpenAI model picker offers GPT-5.6 Sol, Terra, and Luna, with thinking effort up to Max.
- TIA Portal – the live-value popup shows how old a value is in milliseconds.
- TIA Portal – the editor outline shows SCL code with untitled regions.
- TIA Portal – a project opened directly from disk without TIA Portal now shows its technology objects, and each opens read-only to show its type.
- TIA Portal – every project opened directly from disk shows its blocks, data types and tag tables, and very large projects load with all their content.
- TIA Portal – blocks in a project opened directly from disk show their interface details accurately, including access levels, setpoints, retentivity, reference types and data-type names.
- TIA Portal – when watching a block live, code branches the CPU is not currently running are greyed out.
- TIA Portal – when watching a LAD or FBD block live, the parts of each network that carry power light up green as the CPU runs.
- TIA Portal – a project opened directly from disk without TIA Portal can now go online to its CPU and watch its blocks update live.
- TIA Portal – going online works with older-firmware S7 CPUs that do not support secured communication, with a clear warning that the connection is unauthenticated and unencrypted.
- TIA Portal – the Go Online dialog shows which interface, for example X1 or X2, each configured address belongs to.
- AI Chat – the Forge agent can define machine templates, export the machine catalog or push it to the CMS, materialize configurations from a file or straight from the CMS, and send as-built manifests back, each step only after your confirmation.
- Forge – the machine catalog and CMS commands sit behind a cloud button with a dropdown on the Project Graphs list.
- Forge – load a project graph directly from its file on disk via a new button on the Project Graphs list, even when it is stored outside the configured folder.
- Forge – a reload button on the Project Graphs list re-reads the graphs folder, and changing the graphs folder in the settings refreshes the list right away.
- Forge – the settings describe where project graphs live on disk and what a graph folder looks like, so picking the right folder is easier.
- Forge – clearing a device binding field removes its value.
- TIA Portal – with several projects open, the project dropdown marks projects whose tree is still loading, and switching projects shows a loading indicator while the tree builds.
- TIA Portal – the Project Explorer tree scrolls all the way down to its last entry.
- TIA Portal – data blocks open as editable source text; edit and save uploads the change like any other block, and a right-click offers Open as XML to view and edit the block as XML.
- TIA Portal – blocks that can only be shown as XML open without misleading error squiggles.
- TIA Portal – after importing selected changes in the folder compare, the list updates right away instead of making you wait for a full recompare.
- TIA Portal – opening a block from the folder compare shows the project source next to the file on disk for every file format.
- Setup – choose which features to install; deselected features can be added later by running the setup again, and Studio points the way when one is missing.
- TIA Portal – temporary compare, import, and block-editing files are kept in a hidden .tmp folder inside your working folder, so you control where they go; with no working folder set they use a neutral location, never your export or import folder.
- Password Vault – right-click a single block to unprotect just that block with its stored password; the tree-wide commands are now named Bulk Protect and Bulk Unprotect.
- TIA Portal – block compare and import handle deeply nested folder structures.
- CODESYS – open a CODESYS project in the side bar, browse its objects as a tree, and export them to PLCopenXML files (Pro plans).
- CODESYS – click a block in the tree to open its Structured Text source read-only in the editor (Pro plans).
- CODESYS – a new Import / Export panel in the side bar exports objects and imports PLCopenXML files back into the open project, replacing objects of the same name after you confirm (Pro plans).
- CODESYS – the Import / Export panel shows a checkable file tree of the export folder with filter, refresh and reveal buttons, drag to import or export, right-click file management, and export checkboxes on the project tree (Pro plans).
- CODESYS – the AI assistant can see your connected CODESYS project, list and open its objects, read their code, and export or import them, with a dedicated CODESYS Structured Text specialist (Pro plans).
- AI Chat – in Agent mode the file you have open is offered as a suggestion you can add with one click instead of being attached automatically.
- PLC Online – connecting to an OPC UA server with an unknown certificate shows the certificate and asks whether to trust it permanently, accept it for this session, or cancel.
- AI Chat – long conversations and large attached files keep working and stay responsive as they grow; the chat frees up space automatically, and you can also do it yourself with /compact.
- AI Chat – conversation summaries keep your latest question and key details more reliably, and the chat tells you when it is filling up or summarizing, including while it works on a long reply.
- AI Chat – optionally let Anthropic models clear older tool results on their side to keep long conversations within the context window.
- AI Chat – the context-usage details show a local model's true context window and the input budget available for your messages.
- Setup – the installation is smaller and installs faster.
- Forge – connect a Machine Catalog CMS to publish your machine catalog, pick and materialize configurations straight from it, and send the as-built manifest back after a deploy.
- Forge – mark blocks as SCADA interfaces, then turn a canvas selection into a SCADA configuration you can save as a file or send to your Machine Catalog CMS.
- TIA Portal – right-click a data block, tag table, or folder in the Project Explorer and export it straight to a JSON SCADA configuration file, with its tags and constants.
- TIA Portal – right-click a CPU in the Project Explorer to export its OPC UA server interface to an XML file.
- SCADA – turn an exported SCADA configuration into a runnable web dashboard and send it to your FUXA instance, or save it to import into FUXA yourself.
- SCADA – generate a runnable web dashboard directly from a CPU's OPC UA nodes, wired to their real addresses, then save it or send it to your FUXA instance.
- SCADA – a dedicated SCADA page gathers connecting to FUXA, browsing a CPU's OPC UA nodes, picking exactly what to include, and generating or sending the dashboard into one place.
- SCADA – start, stop, and deploy a FUXA instance with Docker straight from the SCADA page, on your own machine or a remote host.
- SCADA – open the SCADA page from a dedicated SCADA icon in the activity bar.
- AI Chat – ask the SCADA Builder assistant to design dashboard screens on the open SCADA page; it picks the tags, shows a preview, and sends to your FUXA instance only after you confirm.
- SCADA – Check Docker fills in the FUXA address from an already-running container automatically, using its actual port.
- SCADA – the OPC UA Endpoint field starts with a sample address so you do not have to type it from scratch.

## v1.127.1

- AI Chat – the assistant carries what its earlier tools found into your follow-up questions.
- AI Chat – Session Info gives a token breakdown of your conversation by category.
- AI Chat – generating a block into TIA Portal checks the block name in your code against the name you gave and flags a mismatch.
- TIA Portal – importing or generating blocks tells you which items were added to the project.
- AI Chat – TIA actions follow the approval mode you pick in the chat and your per-tool approval settings.

## v1.127.0

- Agent Window — choosing a different folder in the Files panel switches to that workspace.
- AI Chat — a specialist assistant you select works on your request directly, with the tools for its job.
- AI Chat – every message uses noticeably fewer of your model's context tokens.
- AI Chat – the context-usage details show unattributed tokens (provider overhead and tokenizer) as their own line.
- TIA Portal – the Import/Export file list can be filtered the same way as the Project Explorer.
- AI Chat – in projects without TIA Portal content the assistant works as a regular coding assistant and brings up TIA Portal only when you ask for it.
- AI Chat – conversations in projects without TIA Portal content use noticeably less of your model's context window.
- AI Chat – the assistant recognizes a TIA Portal connection you made yourself and does not connect again.
- AI Chat — your model-provider sign-in stays active throughout a conversation.
- AI Chat — models you gain access to appear in the picker right after you sign in.
- AI Chat — OpenAI Provider, images you attach to a message reach the model.

## v1.121.13

- AI Chat — Google Gemini models reply in Agent mode.
- AI Chat — when a model provider declines a request, the chat shows the provider's own reason.
- AI Chat — the message box stays ready after you close Settings or another pop-up editor.
- Forge — removing a node can also remove the objects only that node references; the dialog lists them, and anything still used elsewhere stays.
- Forge — build a machine template with options and per-device quantities, turn any configuration of it into a complete wired and addressed project, and export a machine catalog or an as-built manifest for other systems.
- AI Chat — the assistant can look at on-screen application windows and, after you confirm, click or type into the applications you allow.
- AI Chat — the Tool Approvals page is arranged in clear cards, and you can choose which applications the assistant may see there.
- AI Chat — runs quietly in the background while you are not chatting.
- AI Chat — long agent conversations use far less of your model provider's token quota.
- AI Chat — the context-usage details show what share of your prompt was served from the model's cache.
- AI Chat — optionally keep Claude's prompt cache warm for an hour to speed up long sessions with pauses between messages.
- AI Chat — follow-up messages on ChatGPT models send less and respond faster.

## v1.121.12

- Extensions — installing a marketplace extension checks its signature automatically.

## v1.121.11

- Editor — choose whether a data type opens as readable .udt source or as XML.
- TIA Portal — choose whether data types also export as an editable .udt source next to the XML.
- TIA Portal — when a data type is in your import folder as both a .udt and an XML, choose which one Import All uses.
- TIA Portal — the project tree refreshes on its own after Import All.
- Git — set your commit-message and pull-request styleguide in the AnyAutomation settings, with a Browse button to point at a styleguide file on disk.
- Git — save your own commit-message and pull-request styleguide in Settings, and generated text follows your conventions.
- AI Chat — optimized agent context: the assistant loads reference material only when it is relevant.
- AI Chat — the first message responds faster.
- PLC Online — a new OPC UA connection starts with a default endpoint address already filled in.
- Compare — comparing your project to its export folder is much faster once you have exported it.
- Forge — capture a device from your project as a reusable device type.
- TIA Portal — a block's interface opens faster, and reopening one you have already viewed is instant.
- Hardware Simulation — the Force, Watch, Function and Linker panels show their contents as soon as you open it.
- Hardware Simulation — functions and forces drive their tags over an OPC UA connection.
- Unit Testing — the Failures view's buttons and filter field match the app theme.
- TIA Portal — exporting compiles the PLC beforehand, and importing compiles it once the files are in.
- TIA Portal — import, compare and find-unused show their progress and cancel option in the status bar, keeping your workspace clear.

## v1.121.10

- PLC Online — Live Values also shows a function block's interface, InOut and data block members inline.
- TIA Portal — with Export Fingerprints turned on, the fingerprint file is saved at the top of the export folder you chose.
- Forge — deploying a graph also brings the data types its blocks rely on, so their interfaces resolve in TIA Portal.
- Forge — giving a block a library type pulls the data types it needs into the graph for you.
- Extensions — open the marketplace and search the catalog.
- TIA Portal — filter the Project Explorer: click the filter icon in its header (or press Ctrl+Alt+F) and type to narrow to matching blocks, folders and tags anywhere in the project.
- TIA Portal — compare two open projects side by side and copy selected blocks from one into the other.
- Sign-in — works on company networks that reach the internet through an HTTP proxy or inspect HTTPS with a corporate certificate.
- AI — Sign in to or out of GitHub Copilot from Agent Customizations → Providers, alongside your other model providers.
- SCL editor — the error checker accepts compound and chained assignment, bit-slice access, symbolic CASE labels, nested comments and organization blocks.
- SCL editor — Go to Definition on a nested interface member jumps to that member's row in the open block's interface, expanding the path to it.
- SCL editor — right-click a member in the block interface (or press Shift+F12) to see every place it is used in the block's code.

## v1.121.9

- TIA Portal — going online to a password-protected CPU prompts for your user name and password, so its program can be compared and read with your own access rights.
- TIA Portal — when a PLC is too old for secured communication, going online explains the cause and points you to OPC UA.
- AI Chat — the assistant can read the live values shown inline in an open block when you ask about them.
- Updates — after installing an update, a What's New page opens in the app showing that release's changes.
- TIA Portal — connecting to a running TIA Portal starts without a permission prompt.

- PLC Online — the Live Values toggle connects to the PLC as soon as you switch it on.
- PLC Online — local and temporary block variables show their live values when you go online with the toggle.

- Welcome — a new "AI & Agentic Coding" walkthrough shows how to set up chat agents, index your codebase, search your documentation, and choose the model behind every AI feature.
- Welcome — new walkthroughs for Unit Testing, Hardware Simulation and Forge show how to set up connections, run tests, simulate I/O and generate code.
- TIA Offline — Edit a project's SCL/AWL blocks without TIA Portal and save them as files.
- TIA Offline — Export a project's blocks, data types and tags to files without TIA Portal.
- EPLAN → TIA — import an EPLAN project's PLC hardware into TIA Portal and compare it against the project's existing hardware.
- TIA Portal — Export project library types to files by dragging them onto the Export Folder, or with the new Library option in Import/Export.
- PLC Online — Live Values shows a block's local and temporary variables inline, alongside its inputs, outputs and tags.
- TIA Portal — multi-line labels on classic WinCC panel screens display on separate lines.
- TIA Portal — a classic WinCC panel screen draws the content of every one of its layers.
- TIA Portal — a classic WinCC panel screen's objects are grouped by layer in a collapsible list, so you can see what sits on each layer.
- TIA Portal — view a classic WinCC panel screen with the project opened offline, no connection needed (read-only).
- Forge — the Mixing Plant example is grouped under its own folder in the block-type library.
- Report Issue — optionally attach each feature's log (Openness Manager, Forge, EPLAN, PLC Online, Unit Testing, Hardware Simulation) to your bug report.

- Welcome — a Learn the Fundamentals walkthrough introduces the essentials: connecting to TIA Portal, editing a block, the AI assistant, going online with a PLC, building with Forge, and unit testing.
- Forge — opens with a ready-made Mixing Plant example so you can explore a working graph right away.
- Languages — the Welcome screen, onboarding and dialogs now follow your chosen display language in all 14 languages.

- AI — Add `/background` before a task to let the assistant work on it while you keep going; follow its progress in the Sessions view and get notified when it finishes.
- PLC Online — see a live block's values inline in the SCL editor: turn on Live Values to show each operand's current value next to it as it changes, hover for detail, and pin a value above its line; if the CPU is not online yet, turning it on opens the Go Online dialog so a single click connects and starts the values.
- AI — Add your own documentation websites (from the command palette or by asking in chat) and the assistant searches them to answer your questions.
- AI — Inline chat (Ctrl+I) applies your requested change straight to the file in the editor, and the input stays ready for your next request.
- AI — Attach an earlier conversation to a new chat and the assistant picks up where it left off.
- Forge — one click creates a new TIA project for your CPU and pushes the generated program into it.
- Forge — give an I/O point a structured S7 address and use it in generated code.
- AI — The chat agent can pull your current Git changes (which files changed and their diffs) into a conversation on its own.
- AI — Switch between your open TIA projects from the agent window's Project Explorer, now the first tab in its panel.
- AI — The chat assistant can read the exact live content of an open tab, including your unsaved edits, for TIA blocks and files.
- AI — Ask the chat assistant to change an open TIA Portal block and it makes a precise inline edit, touching only the lines that need it, shown as a reviewable diff you upload when you save.
- Block editor — open and edit ladder, function-plan and S7-GRAPH blocks as source, toggle to the graphical view, and save to update the project (TIA Portal V20 and newer).
- TIA Portal — open a classic WinCC (Comfort/Advanced) panel screen, see it drawn as on the panel, and ask the chat assistant to move, restyle, label, add or remove objects before saving back to TIA.
- AI — The chat assistant can see which editor tabs you have open (TIA blocks and files), so it can work with what you are looking at.
- AI — Let the chat assistant search the web during a conversation, on any model, and choose your search provider (turn it on in settings).
- TIA Commissioning — download a project to a CPU over a chosen network adapter.
- TIA Commissioning — download only the changed blocks to a CPU, keeping it running where possible.
- TIA Commissioning — upload a CPU's blocks, data types and tags back into your project to match what is running.
- TIA Project Explorer — after going online, each folder shows a sync dot at a glance: green when every block inside matches the PLC, or a change marker when something inside differs.
- TIA Project Explorer — a single Connect button now opens a menu with every way to start: attach, open a project, browse offline, create a new project, or work with a Multi-User server.
- AI — Turn on automatic codebase context to have the most relevant workspace code attached to each chat message, with a toolbar indicator showing when it is ready.

- AI — See and change which model powers each AI feature (inline completion, next-edit, apply, summarization, ambient hints) in one place under Agent Customizations → Feature Models.
- AI — Ask the chat agent to read and write complex structured (UDT) values over OPC UA on a live PLC, and to look up a method's arguments and the server's data types.
- AI — Ask the chat agent to build a WinCC Unified HMI screen; it knows the available screen item types and their properties.
- AI — Step through a session's changed files one at a time with Previous and Next buttons, and see how far along you are.
- AI — Dictate a chat message by voice and have it sent automatically when you finish with a spoken keyword.
- AI — Undo applying a session's changes to your repository straight from the confirmation that it worked.
- AI — Ask the chat agent to create a new TIA Portal project, or to build a fully populated one (devices, modules, networking, blocks and tag tables) in a single step.
- TIA Portal — open password-protected projects by entering your project user name and password.
- Multi-User — open a Multi-User session in Studio (pick its session file, an existing session, or check one out from your server), then commit your changes to the Multi-User server, all without keeping TIA Portal open.
- Multi-User — upload a project to your Multi-User server straight from Studio.
- Multi-User — review your changes and resolve conflicts before committing, and pick exactly what to check in.
- Multi-User — see which server projects are locked, and by whom, when you check out from your server.
- Multi-User — manage your server connections from Studio: change a server's host, port, or protocol, remove a connection, and clean up old local sessions.
- Block editor — FBD blocks display as graphical function-block diagrams, in the familiar TIA Portal style.
- Block editor — S7-GRAPH blocks open as a compact sequence chart in the familiar TIA Portal style (steps, transitions, parallel and alternative branches, jumps); click a step or transition to expand its actions or condition logic, or hover for the details.
- Data types — open and edit a UDT as compact source, and save to update the project.
- TIA Project Explorer — S7-GRAPH blocks display as their sequence chart when a project is opened offline.
- Languages — Studio's interface is now available in 14 languages; pick yours with Configure Display Language.
- AI — Long conversations stay responsive: older messages are summarized automatically, with a /compact command to do it on demand.
- AI — Select code in the editor to edit it, ask a quick question about it, or send it to chat from a floating toolbar.
- AI — The chat agent now shows a live checklist of its plan and progress on multi-step tasks.
- AI — After the chat agent edits your files it now checks its own work and fixes any new errors before finishing.
- AI — Inline code completion (Tab) now works with your own AI provider's coder model.
- AI — Accept a code suggestion one word (Ctrl/Cmd+Right) or one line (Ctrl/Cmd+Down) at a time, or all of it with Tab.
- AI — Hover a blame annotation to get a short AI explanation of why that change was made, using your own AI model (turn it on in settings).
- AI — Before running a terminal command that needs your approval, optionally have your AI model add a one-line risk note to the confirmation (turn it on in settings).
- AI — Choose which AI model writes the blame explanations and terminal risk notes, from the command palette (Select AI Blame & Terminal Risk Model).
- AI — Commit-message, rename, and terminal-fix suggestions now work with your own AI provider key.
- AI — The chat assistant stays fast and accurate even with many tools or MCP servers connected.
- AI — Find and install MCP servers from a built-in marketplace in the Agent Customizations panel.
- AI — The chat agent can create and edit files with your own AI provider, shown as a reviewable diff before applying.
- AI — The chat agent can now ask you structured clarifying questions mid-task and wait for your answer before continuing.
- AI — The chat agent now picks up your project's rule files (.cursor/rules, .cursorrules, AGENTS.md): always-on rules, file-pattern rules, rules it loads on demand, and rules you invoke with @name.
- Canvas — ask the chat assistant to build a live, interactive dashboard on a visual canvas bound to your controller's values, and interact with it to write values back.
- AI — Run a Local chat session in isolation so its edits stay separate from your open files until you apply them from the Changes view; tabs showing a file from an isolated session are marked with a coloured edge.
- AI — Run the same chat prompt several ways at once with Best-of-N, optionally each on a different model, then keep the best result and discard the rest.
- AI — Right-click a session that is running in isolation to copy its isolated working-folder path to the clipboard.
- SCL editor — Find All References (Shift+F12) on a block lists everywhere it is used across the project; on an instance, it also points to the function block it is based on.
- SCL editor — autocomplete is ready the moment you connect, and project actions like export start right away.
- Unit Testing — find gaps in your test suites: surviving "mutants" of a block are highlighted in the editor and listed with a quality score.
- Unit Testing — prepare and author test suites without TIA Portal open, using a block you exported earlier; if the block hasn't been exported yet, Studio tells you to export it first.
- Unit Testing — pick a folder of exported blocks to analyze and run tests without TIA Portal open.
- Unit Testing — running over OPC UA works without TIA Portal open, and finds the controller's namespace automatically, with a manual override for unusual servers.
- Unit Testing — choose the PLCSim network mode for a run, to avoid connection problems on machines with more than one network adapter.
- Unit Testing — run your test suites against a controller over an OPC UA connection, and browse its address space right in the pane.
- Unit Testing — run your test suites against a real controller over a direct S7 connection.
- Unit Testing — a saved test suite keeps only the settings for the connection you chose, so its configuration stays tidy and easy to follow.
- Unit Testing — pick the folder that holds your test suites, so they reappear right after a restart without reconnecting to a project.
- Unit Testing — the generated CI/CD pipeline can be set to run on push, on pull request, or on a schedule, not just manually.
- Unit Testing — generate a build matrix to run your tests across multiple projects and suite filters in parallel.
- Unit Testing — the build matrix now works for Jenkins pipelines too, alongside GitHub Actions, GitLab CI, and Azure DevOps.
- Unit Testing — the command-line runner opens TIA Portal without a window during a run; pass `--show-ui` to watch it on screen while debugging.
- Unit Testing — flaky test cases are flagged in the Test Suites list and counted in run results (the flag clears once a test settles into a steady result), and the command-line runner can list them and skip flaky failures so they don't break the build.
- Unit Testing — the command-line runner can re-run a known-flaky test once if it fails; if the re-run passes, it counts as a pass so a one-off flake doesn't break your build.
- Unit Testing — more ways to check a value in a test: ranges, approximate and bitmask checks, text contains/starts/ends/regex, and whole-array, all/any/none, and deep struct comparisons, with a pointer to the first element that differs.
- Unit Testing — see how much of each block your tests cover (requirements, interface pins, and called blocks), export it for CI, and fail the build below a coverage threshold.
- Unit Testing — see which lines and branches of your block actually ran during a test, in the coverage view and as a colored heatmap in the editor.
- Unit Testing — generated CI/CD pipelines can publish test coverage to GitLab, Azure DevOps, Jenkins, and GitHub.
- Unit Testing — run tests with one click from the list, watch them tick over live, re-run just the failures, and hear when a run finishes.
- Unit Testing — a Failures tab lists every failed test across suites with filters by status, suite, block, tag, and requirement.
- Unit Testing — SCL block source shows a CodeLens to run the block's tests and see the last run's results.
- PLC Online — an Offline Compare panel for S7 connections: pick an offline project, press Compare, and each block shows a green, orange, or grey sync dot against what is running on the controller — no TIA Portal needed.
- Import/Export — S7DCL files can be imported from the export folder or via drag & drop (TIA Portal V20 or newer); if the same block also exists alongside as SCL, AWL, or XML, that version is imported instead.
- Hardware — right-click a device, rack, or module in the project tree to add, move, copy, change the type of, or remove individual modules (also available to the AI assistant).
- Project Explorer — the header shows the active project's name; click it to switch between connected projects or add another, and the sidebar gains the space of the former title row.
- Project Explorer — Go Online on a CPU connects to the controller — type the controller's IP address yourself or search the network for it — and marks every block, tag table, folder, and the CPU with a sync dot showing how your project compares to what is running; the dots stay until you go offline, and Refresh Compare updates them.
- Project Explorer — opening a project file from disk without TIA Portal shows the HMI panel and its screens, tags, connections, and lists in the tree alongside the controllers.
- Import/Export — running operations show a live stopwatch next to the progress, and the total duration stays visible after they finish.
- Import/Export — after the last exported item, the progress shows the remaining preparation steps, and cancelling during them warns which files were left unprepared.
- Import/Export — source files you add to the export folder yourself are imported into their matching program folder by Import All.
- Help — the About dialog now lists the support e-mail, website, and source-code repository.

- Forge — large project graphs open as a searchable dependency browser: browse blocks as a folder tree, see what uses a block and what it uses, filter by relationship, and switch to a neighborhood view around any block.
- Forge — install a ready-made example library and project graph to see how block generation works.
- Forge — choose where your Block Type Library is stored and version it with Git.
- Forge — Project Graphs are saved with your project, or in a folder you pick, and can be versioned with Git.
- Forge — rename a project graph by right-clicking it in the Project Graphs list, and the new name shows everywhere.
- Forge — a captured project graph is named after the project.
- Forge — the Block Type Library keeps folders collapsed until you open them, and remembers which ones you expanded.
- Forge — define a monitor field with color-coded states on a library block type, and see each block's live state as a label, a dot, or a badge in the Project Objects table, tree, and graph.
- Forge — open a project graph in the Project Objects table, press **Monitor**, and the table shows the current PLC value for each tag row next to its configuration — updated live while you work.
- Forge — start Monitor and go online directly from the project graph.
- Forge — click the eye on a row in the project-objects table to watch just that value live, without turning on Monitor for everything.
- Forge — run **Clean Up Software-Unit Library Duplicates** from the Block Type Library to remove duplicate block-type entries left over from re-capturing a project.
- Forge — capturing a project into the Block Type Library groups its block types under a folder named after the project, so several projects stay separate.
- Forge — each Block Type Library entry shows a short type tag — SCL, DB, UDT, or XML — and the code generator is listed as TIA SCL.
- AI Chat — watch a dispatched agent's progress live inside its card while it works.
- AI Chat — local AI servers (Ollama, LM Studio, vLLM, SGLang) and any OpenAI-compatible endpoint can now be used as chat providers.
- AI Chat — 19 cloud AI providers (OpenRouter, Mistral, Groq, DeepSeek, Together, Hugging Face, and more) can now be connected with an API key, including region selection and custom model lists.
- AI Chat — Cloudflare AI Gateway and Google Antigravity join the provider list: route chats through your own gateway, or sign in with a Google account for the Antigravity model sandbox.
- AI Chat — Azure OpenAI and Google Vertex AI join the provider list: connect with your Azure resource or a Google Cloud project to use those models.
- AI Chat — the file you're currently editing is shared with the AI automatically while you chat, including when using an agent, so you can ask about it without attaching it.
- AI Chat — ask the AI to change a block-type template you have open, and it shows the edit for review before you keep and save it.
- Updates — Studio keeps itself up to date: new versions install in the background and apply with Restart to Update.
- Settings — the update check offers Automatic and Off modes, and Check Now explains when updates are unavailable in the current install.

- Welcome — a guided first-run walkthrough greets new installs, brings your VS Code settings, keybindings, and extensions across, lets you pick a theme, and signs you in.

- Appearance — a new black theme with orange accents is the default look, alongside the existing dark and light themes.

- Editor — open a block with its declaration interface as a table above the code, like TIA, and save both together.
- Editor — show or hide the block interface table, and resize its columns.
- Editor — expand a member typed as a data type or array to see its fields and elements.
- Editor — rename members, change data types, edit values, comments, and HMI options, set retain, add or remove members, and reorder them.
- Editor — see which places use a member before you rename or remove it.
- Editor — after you save, see compile errors and warnings and click one to open the affected block.
- Editor — view and edit a tag table's tags and constants.
- Editor — open a local source file to view and edit its interface, then save it.
- Editor — write SCL with live error checking, completion, hover, an outline, go-to-definition, find-references, rename, semantic coloring, one-click quick fixes, and Format Document, aware of your connected project's blocks.
- Editor — type a dot after a block or instance to suggest its members, hover a member to see its type, and jump to the member's owning block.

- Compare — review which blocks differ between your connected project and your export folder, open any block to see the differences side by side, then import the changes you select back into your project.

- Hardware — see every station of the open project with article numbers, firmware, IP addresses, and PROFINET names in one table, and export the list to CSV.
- Hardware — edit IP addresses, PROFINET names, and card I/O start addresses and save them straight into the project.

- HMI — open an HMI tag table to view its tags in a table (name, data type, connection, PLC tag, acquisition, comment).
- HMI — edit HMI tags and save your changes back to TIA Portal.
- HMI — open a WinCC Unified screen on a canvas, move / rename / edit / show-hide / delete its items, and save back to TIA Portal.

- Agent Window — the in-session AI assistant can read and modify your connected TIA Portal project.
- Agent Window — the local AI follows your project's rule files and can load your skills on demand.
- Agent Window — the local AI can delegate focused sub-tasks to your custom agents.
- Agent Window — a delegated custom agent runs on its own AI model when it specifies one.
- Agent Window — a delegated custom agent uses only the tools its definition allows.
- Agent Window — expand a delegated agent to see which tools it used and its result.

- Chat — the context indicator shows a color-coded breakdown with exact token counts for what's filling your context window.
- Chat — ask about your live PLC connections, current values, trace recordings, and Forge project graphs right from the default agent.
- Chat — pick the PLC Online Operator agent to write values, call methods, and record signal traces on a live PLC, or the Forge Engineer agent to edit project graphs, generate code, and import it into TIA.
- Chat — the Forge Engineer agent knows the block-type templating language and helps you write, review, and debug your own code-generation templates.
- Chat — ask the Forge Engineer or the standard agent about your Block Type Library and it reads your own captured and authored block types, organized by folder.

- EPLAN Electric P8 — open a project, browse its pages and devices, preview schematics, and export to PXF or PDF.
- EPLAN Electric P8 — edit device properties, drag devices to reposition them, and save or discard your changes.
- EPLAN Electric P8 — generate project reports as PDF, Excel, CSV, XML, text, or DXF/DWG.
- EPLAN Electric P8 — drive your project from the AI chat: open, explore pages and devices, edit, export, and report.
- EPLAN Electric P8 — ask the chat what's open in EPLAN, or pick the EPLAN Engineer agent for page, device, export, and report work.

- PLC Online — if a controller rejects the stored security certificate, a banner lets you forget it and reconnect in one click.
- PLC Online — after a restart, your saved connections come back ready to connect; nothing connects until you press Connect.

- AI Chat — pick a skill from the chat toolbar to run it instantly.
- AI Chat — more OpenAI models are available in the model picker when you sign in with ChatGPT.
- AI Chat — the assistant can read and write live PLC values, run Forge code generation, and record signal traces for you, asking you to confirm each change to a PLC first.
- AI Chat — your agent now runs your configured hooks (e.g. confirm before PLC writes, post-import reminders) and can remember context across sessions.
- AI Chat — pick a thinking effort and a context size for models that support them, right next to the model name.
- AI Chat — watch the model's reasoning in a collapsible section while it answers.
- AI Chat — turn on the Anthropic 1M-context option per model, right next to the model name.

- Unit Testing — open a full-page Unit Testing workspace to connect to your project, pick a PLC and block, author test suites, and run them all in one place.
- Unit Testing — create test suites for your SCL blocks and run them against a PLC, with live pass/fail results and totals.
- Unit Testing — build test cases visually — inputs, expected values, reorderable multi-phase steps, a watch list, tags, priority, owner, requirements, and a per-case timeout; duplicate a case; or edit them as JSON.
- Unit Testing — analyze a block to see its interface, suggested boundary values, and its dependencies before you write a test.
- Unit Testing — see how watched values changed during a run on a timeline chart.
- Unit Testing — browse past runs, compare two of them side by side, and view pass/fail trends over time.
- Unit Testing — export a test report as HTML or JUnit XML.
- Unit Testing — generate a ready-to-use CI pipeline for GitHub, GitLab, Azure, or Jenkins.
- Unit Testing — run your test suites on a build server and publish JUnit and HTML reports.
- Unit Testing — set each suite's connection target and save a default for new suites.
- Unit Testing — open a block's exported XML to inspect it.
- Unit Testing — start a PLCSIM simulation straight from the Unit Testing toolbar.
- Unit Testing — switch a test suite between a visual, JSON, and SCL view, import generated test blocks into TIA, and generate cases from input boundaries.
- Unit Testing — edit the generated SCL test code directly in the suite editor; your changes flow back into the test cases.
- Openness Manager — open a project file or archive to browse it and read block code without opening TIA Portal.
- Openness Manager — "Export All" empties the target folder first so it exactly mirrors the project; a setting lets you keep merging into existing files instead.
- Openness Manager — go online and offline with a CPU from the Project Explorer, with a live online/offline indicator.
- Openness Manager — going online opens a connection dialog: pick the PG/PC interface and target address, search for reachable devices and adopt one with a click, and your last choice comes preselected next time.
- Openness Manager — while online, each block shows whether it matches the version in the controller, with a one-click "Compare to Online".
- Openness Manager — create a new TIA project through a guided wizard (CPU, modules, and network), browsing CPUs and modules in a catalog tree.
- Openness Manager — right-click a Program blocks, PLC data types, or PLC tags folder to add a new group, block, data type, or tag table, or press F7 to jump to a block or data type.
- Openness Manager — open additional projects straight from the toolbar via the new + button.
- Openness Manager — the Project Explorer's top-level folders show the names you set under Folder Names, updating as you type.
- Openness Manager — data types can be exported as editable source files and imported back, including data types that build on other data types.
- Openness Manager — export and import show progress unobtrusively, let you cancel a run in progress, and list any items that failed.
- Openness Manager — a single, clearer set of version-control export options with the recommended one marked, and S7DCL export flags when it needs a newer TIA Portal version.
- Openness Manager — import applies your structural-change, missing-reference, and fault-tolerant choices.
- Openness Manager — choose the timestamp format for archive file names.
- Openness Manager — Import All skips the items you marked as protected.
- Openness Manager — when an import is rolled back, the notification names the cause and links the log.
- Find Unused — a progress notification shows the current scan step, including the block being processed.
- Find Unused — opens from its own activity bar entry.
- Find Unused — function blocks that are never called are listed as unused even when their data is still read elsewhere.
- Settings — the Log Folder and Working Folder fields preview their default location and add an Open Folder button to open either folder.
- Settings — choose a folder for TIA diagnostic logs.
- Settings — turn on Debug Logging to capture detailed diagnostics from TIA, PLC Online, and Unit Testing for troubleshooting.
- Unit Testing — find its diagnostics in a dedicated Output log.
- Openness Manager — export and import use a default working folder when you haven't chosen one.

- PLC Online — open a live PLC view to browse a controller's address space, watch and write values in real time, and read its diagnostics.
- PLC Online — connect to several PLCs at once and switch between them with tabs.
- PLC Online — the address-space browser shows a distinct icon for each kind of node.
- PLC Online — for S7 controllers, each program and data block in the address space shows its block-type icon (OB, FB, FC, DB, UDT).
- PLC Online — drag tags into a watch list to follow their values live, and type a new value to write it back; subscribe or pause the live view, clear the list, or save it to a file.
- PLC Online — drill into structured and array values, edit and write a struct's fields, and edit a matrix value in a grid.
- PLC Online — browse a node's references and call a controller method with its inputs and outputs.
- PLC Online — read a tag's history and view it as a chart over a chosen time range.
- PLC Online — see live events and alarms, filter them by severity, and export the list to a file.
- PLC Online — review and manage the security certificates a controller presents.
- PLC Online — for S7 controllers, browse the program blocks and data blocks, watch and write tag values live, and read the controller's identity, protection level, memory usage, cycle time, diagnostic buffer, and alarms in tabs.
- PLC Online — if the connection drops, a banner offers to reconnect and restores your tabs.
- PLC Online — connection setup and panels have a cleaner, easier-to-read layout in both light and dark themes.
- PLC Online — discover a controller's available endpoints, pick one from a list with the most secure shown first and selected for you, and connect with its security setting.
- PLC Online — when connecting or looking up endpoints fails, open the log straight from the message to see what happened.
- PLC Online — reach PLC Online from the activity bar and open it from there.
- PLC Online — the address-space browser docks in the activity-bar sidebar and follows the connection you are viewing.
- PLC Online — open, connect, disconnect, and refresh with the keyboard.
- PLC Online — set the history chart processing interval in seconds.
- PLC Online — show or hide each tool panel, and save your connections and layout to a workspace file to reopen later.
- PLC Online — adjust logging, certificate handling, and other settings per connection.

- Trace — visualize live PLC signals over time as an oscilloscope: pick signals from the address-space tree, zoom and measure with two cursors, group signals onto separate Y axes, arm a single-shot trigger, view the FFT, and export the recording as CSV.
- Trace — click a signal's color dot in the signal table to pick its curve color.

- PLC Simulation — manage PLCSIM Advanced simulation instances and read or write live simulation tags from a dedicated panel.

- Hardware Simulation — open it from its own activity-bar icon to feed a controller simulated field signals over OPC UA so you can exercise your program without wiring up real hardware.
- Hardware Simulation — connect and browse the device hardware in a side panel, see each channel's current value in a table, and type a value to drive an input, while the editing workspace stays open beside it.
- Hardware Simulation — force a tag to a fixed value, and turn each force on or off.
- Hardware Simulation — drive a tag automatically with a constant, step, ramp, pulse, sine, or PI function.
- Hardware Simulation — link tags with rules ("when this, set that") built visually or written as an expression, with optional delays.
- Hardware Simulation — keep a watch list of tags and follow their values live while the simulation runs.
- Hardware Simulation — connect to a running PLCSIM instance to drive real peripheral inputs and exercise safety channels.
- Hardware Simulation — pick which source to view, add extra OPC UA sources, browse their address space, and add any variable to the watch list to follow its value live.

- AI Chat — an animated robot mascot in the chat header blinks and follows your pointer at rest, taps its keyboard while the assistant is thinking, and closes its eyes with a code-rain effect during longer responses.
- AI Chat — the context-window meter breaks your token usage down by category — system prompt, tools, MCP, and messages.
- Agents — open another workspace straight from the sessions sidebar to start sessions in it.
- AI Chat — when a TIA project is connected, the assistant automatically knows the project name and PLCs.
- AI Chat — the assistant greets you as AnyAutomation Studio and offers what it can help with.
- Extensions — search and install from the full Microsoft extension catalog.
- AI Chat — manage AI provider sign-ins directly from the chat input.
- AI Chat — sign out of an AI provider to fully disconnect it, and switching your Claude account in another app is picked up automatically.
- AI Chat — more OpenAI Codex models to pick from, and your Claude model list matches what your account offers.
- AI Chat — sign in with your xAI (Grok) or Qwen account and use their models in chat.
- AI Chat — choose between subscription sign-in and your own API key for each AI provider.
- AI Chat — the GitHub Copilot status appears in the status bar while you are signed in to Copilot.
- AI Chat — TIA Portal tools, skills, expert agents, and built-in Siemens reference guides are available in chat to read, analyze, generate, and change your project.
- AI Chat — decide once whether each AI tool may run: allow, allow for the session, or block.
- AI Chat — ask the assistant to edit an open block and review its change as an inline diff with Keep or Undo; keep refining, then save once to send it to TIA Portal.
- Block Editor — edit a block's code and save it straight back to TIA Portal.
- Block Editor — compile errors and warnings appear in the Problems panel and jump to the block at the error line when you click them.
- Block Editor — SCL code shows guide lines connecting bracket pairs and auto-indents structured blocks more cleanly.
- TIA — a TIA action log is available in the Output panel.
- TIA — every action (connect, export, import, protect, compile) writes to a single log in the Output panel.
- TIA — Import Selected imports the files you check in the export folder.
- TIA — Import All re-imports the chosen PLC's export folder after a confirmation, replacing its existing blocks; a live notification shows each step and lets you cancel, and if nothing could be applied, the message tells you why.
- TIA Project Explorer — safety controllers show a Safety Administration section listing each runtime group's blocks; click one to jump to it.
- TIA Project Explorer — search blocks, data types, and tags from Quick Open and jump straight to the source.
- TIA Project Explorer — toolbar buttons to create, save, compile, and archive the open project, plus a safety login/logout toggle.
- TIA Project Explorer — archiving opens with a suggested file name built from the project name, your archive suffix, and an optional date stamp, set to the project's archive type.
- TIA Project Explorer — Software Units show their namespace, and keep their namespace, author, and comment when you export and re-import them.
- TIA Project Explorer — save your protection selection, import/export options, and export folder as named profiles and reapply them in one click; the profile you used last comes back when you reopen the project.
- TIA Project Explorer — a badge shows how many blocks you have selected for protection, with one click to clear the selection.
- TIA Project Explorer — OBs selected for protection show C and A toggles to allow code updates and attribute updates during import.
- TIA Project Explorer — delete blocks and folders directly from the tree.

- Find Unused — scan a PLC to find the blocks, data blocks, UDTs, and tags that nothing else uses, listed by type in a dedicated tab.
- Find Unused — export the unused-item list to a text file or copy it to the clipboard.
- Find Unused — delete unused blocks, data blocks, UDTs, and tags by category or selection, with a confirmation step.

- Settings — a dedicated AnyAutomation settings screen groups working folders, folder names, archive naming, and import/export options in one place.
- Settings — the settings screen explains each option, lets you choose how HMI is exported, and offers fine-grained version-control cleanup for exported files.
- Export Folder — files and folders show TIA icons matching each block's actual type, tick files to choose them for import, and drag files straight into the project to import them.
- Export Folder — open files by clicking, and right-click to rename, delete, create, and cut/copy/paste like a normal file explorer.
- Import/Export — selection, actions, the export folder and its file list live in a single panel.
- Import/Export — export the screens, tags, and lists of the HMI device you pick straight into your Export Folder, and import HMI files back into that device.
- Settings — the settings screen has category icons, a tighter compact layout, and marks changed options with an accent bar and a one-click reset to default.

- Agents — a new Project Explorer panel lists the open TIA Portal project, and clicking a block opens it in the editor.
- Agents — the new-session composer shows your selected AI provider and lets you switch it.
- Agents — open a different folder directly from the Files panel toolbar.
- AI Chat — an animated assistant appears in the chat header.
- Agents — new chats start with your local AI provider.
- Agents — the session list shows the chats you start in the Studio.
- Agents — create a new file or folder straight from the Files panel toolbar.

- Forge — browse project graphs and inspect them on an interactive read-only canvas.
- Forge — generate PLC code from a project graph and browse the generated files.
- Forge — review the generator's warnings and errors, and jump from one to its node on the canvas.
- Forge — open a generated file in a read-only editor.
- Forge — add and remove nodes and connections directly on the project-graph canvas.
- Forge — create project graphs, and select one or several in the Project Graphs list to delete them in one step.
- Forge — an open project graph refreshes on its own when it changes.
- Forge — select any node or connection on the canvas and edit its properties in the Inspector.
- Forge — import a project graph's generated code straight into the open TIA Portal project.
- Forge — build your own reusable block types (SCL, UDT, data blocks) in a global library and use them in every project.
- Forge — capture a project's blocks, data types and tag tables into your Block Type Library from the TIA Project Explorer, organized into folders that match the project.
- Forge — deploy your whole Block Type Library into a connected PLC with one click, with blocks grouped as in the library.
- Forge — deploy a project graph straight into a connected PLC as blocks, data types and tag tables with one click.
- Forge — turn a connected TIA project into a project graph with matching library types, ready to build and deploy back.
- Forge — browse a project graph's objects as a folder tree in the side bar, and jump from any object to the Inspector or to its place on the canvas.
- Forge — open a project graph's objects in a filterable table, edit a value in place, and set one property across many objects at once.
- Forge — preview the generated source of the selected object read-only beside your work, and have it follow your selection automatically.
- Forge — validate a project graph to flag objects that stand out from their peers, and click a finding to reveal its object.
- Forge — let the AI assistant read and edit project-graph objects and connections, asking you to confirm each change first.
- Forge — find its diagnostics in a dedicated Output log.
- Forge — the Inspector shows which library block type a node is linked to.
- Forge — the AI chat sees the template you are editing in the block type editor, and templates can also be opened, edited and saved in a regular text editor tab.
- Forge — set a node's block kind and its library block type as two separate Inspector fields, each with its own picker; the library picker offers every block type in your library and a None entry to remove the link.
- Forge — Inspector edits save when you click away.
- Password Vault — keep your own block know-how-protection passwords in one encrypted, password-protected vault, open it from the activity bar, reveal and copy a stored password, and apply your stored passwords to your own blocks without retyping.
- Password Vault — assigned blocks highlight automatically and can be protected or unprotected with your stored password straight from the Vault menu.
