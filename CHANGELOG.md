# AnyAutomation Studio — Changelog

User-facing changes, newest first. The newest section is titled "Unreleased" until the release
fixes the version number; scripts/release.ps1 and scripts/publish.ps1 refuse to run until it is
renamed to the actual "## v<version>".

## v1.142.0

### Release highlights

This release puts TIA Portal projects under version control, brings global libraries, library updates and much more hardware configuration into the Project Explorer, and lets the assistant find usages, unused objects and safety settings for you.

- [Version Control Workspaces](#version-control-workspaces): keep blocks, data types, tag tables and technology objects as files and version them with the tool you already use.
- [TIA Portal V15.1 Support](#tia-portal-v151-support): open, attach and import V15.1 projects like every other version.
- [Global Libraries](#global-libraries): open your company and system libraries next to the Project Library and use their types and master copies.
- [Find References Down to the Location](#find-references-down-to-the-location): jump straight to the network, the line, the member or the tag where a block is used.
- [CPU Protection, Users, Certificates and Syslog (Pro)](#cpu-protection-users-certificates-and-syslog-pro): set a CPU's protection, users, certificates and syslog without opening TIA Portal.
- [Safety Validation and Safety Settings Through the Assistant (Pro)](#safety-validation-and-safety-settings-through-the-assistant-pro): let the assistant prepare activation tests and write the acceptance report.

### Version Control

#### Version Control Workspaces

Until now, keeping the program of a TIA Portal project under version control meant exporting blocks by hand and keeping the files in step yourself. Now a workspace links blocks, PLC data types, tag tables and technology objects of the project to files in a folder you choose, one file per object. By default the files go into subfolders that follow the block groups of the project, so you can version the folder with Git, SVN or any other tool you already use.

Right-click **Version Control Workspaces** at the end of the **Project Explorer** and choose **New Workspace...**, then use **Version Control Workspaces** > **Export to Workspace...** or **Connect to Workspace...** on blocks or folders. The workspaces are saved with the project. You can see workspaces and their status on every plan. Creating, changing, connecting, exporting and importing need Pro. Managing workspaces is available from TIA Portal V17, and connecting, exporting and synchronizing from TIA Portal V20.

The assistant can also set up workspaces, export objects into them, read their status and synchronize them. It shows you what it will change before it touches the project.

Learn more in [Version Control with Workspaces](https://anyautomation.ch/en/docs/version-control)

#### Workspace Status

Until now, you could not tell whether an object had changed in the project, in its file or in both places. Double-click a workspace to open its **Workspace Status**. Each connected object is listed with its state: **Equal**, **Project changed**, **File changed**, **Both changed** or **File missing**.

Tick the objects you want and choose **Export Selected to Workspace** or **Import Selected from Workspace**. Studio asks before every import. For an object changed on both sides, choose **Keep Project Version** or **Keep File Version** in its row. Available from TIA Portal V20.

TIA Portal reads the files of a workspace as they are. If you edit SCL files of a workspace in Studio, run **Format Document** before you import them, so they arrive in the TIA Portal layout. After the update, enter your TIA Portal values once under **Settings** > **Editor** > **SCL Formatting**.

Learn more in [Version Control with Workspaces](https://anyautomation.ch/en/docs/version-control)

#### More Version Control Improvements

- The **Version Control Workspaces** folder and its workspaces use the TIA Portal icons, drawn in the modern style of the Project Explorer.

### TIA Portal

#### TIA Portal V15.1 Support

Until now, TIA Portal V15.1 could not be used with Studio. V15.1 now connects like every other version. Its projects and archives (.ap15_1, .zap15_1) open, attach and import, and **New Project** offers V15.1.

Learn more in [Installation](https://anyautomation.ch/en/docs/installation)

#### SCL Blocks Arrive in the TIA Portal Layout

Until now, a block edited outside TIA Portal, including one the AI wrote, arrived in TIA Portal with its own indentation. Now Studio lays out every SCL block the way the TIA Portal editor does before it imports it: with **Import Selected**, **Import All**, a drag onto the **Project Explorer**, saving a block in the editor, a block the AI assistant writes or changes, and a deploy from Forge. **Format Document** in the editor uses the same layout.

Studio takes the tab width, indent mode and parameter alignment you enter under **Settings** > **Editor** > **SCL Formatting**. Enter the same values as in TIA Portal, and a block looks the same in both. To import SCL blocks exactly as written, turn off **Format SCL Blocks Before Import** in the same section. It is on by default. If a block cannot be formatted, it is imported as written, and the import message names it.

![The SCL Formatting section in the Settings with tab width, indent, parameter alignment and the Format SCL Blocks Before Import switch](https://anyautomation.ch/video/releasenotes/scl-formatting-1.142.png)

Learn more in [Import / Export](https://anyautomation.ch/en/docs/import-export)

#### Global Libraries

Until now, the Project Explorer showed only the **Project Library**, so working with the standard blocks of your company meant going back to TIA Portal. The new **Global Libraries** branch sits next to the **Project Library**. Right-click it and choose **Open Global Library...** or **Open System Library...**, and the library's **Master Copies** and **Types** appear in the tree. Badges show whether a library is **Read-only** or **Modified**.

You can also create libraries with **New Global Library...**, and use **Save**, **Save As...**, **Archive...**, **Retrieve Global Library...** and **Close**. A library from an older TIA Portal version opens as an upgraded copy, and the original stays unchanged. You can instantiate, export and manage the types and master copies of a global library just like those of the Project Library. The assistant can open, manage and work with global libraries too.

Opening a library read-only works on every plan. Opening with write access, creating, saving, archiving and retrieving need Pro.

![The Project Explorer with the Global Libraries branch open, showing the system library Long Functions as read-only with its master copies](https://anyautomation.ch/video/releasenotes/global-libraries-1.142.png)

Learn more in [Library Management](https://anyautomation.ch/en/docs/library-management)

#### Find References Down to the Location

Until now, Find References showed which objects use a block, and you still had to search each object for the place where the block is used. Now the **TIA References** view puts every location on its own line under the object it belongs to and names the kind of access. Click a location and Studio takes you there: a graphical block opens at the **network**, an SCL block at the first use in its code, a data block or PLC data type at the **member**, and a tag or constant opens its tag table with the tag shown.

Monitoring, modifying, forcing, alarms and declarations are listed in their own **Other accesses** group. When a location is on another device, for example an HMI device, the row names that device. Right-click a location for **Go to Reference**, **Go to Definition**, **Reveal in Project Explorer** or **Copy Reference Location**.

![The TIA References view listing every read and write of a data block on its own line, with the kind of access and the location](https://anyautomation.ch/video/releasenotes/tia-references-1.142.png)

Learn more in [Find in Project](https://anyautomation.ch/en/docs/find-in-project)

#### CPU Protection, Users, Certificates and Syslog (Pro)

Until now, a CPU's protection and user settings could only be changed in TIA Portal. Right-click a CPU now to reach **PLC Protection…**, **OPC UA Users…**, **Web Server Users…**, **Certificate Management…** and **Syslog…**. Each command reads the current setting first and offers only what the CPU's firmware supports. You can set the access level and its passwords, choose access control with a UMC server, and turn on account locking. You can also add, change and delete OPC UA and web server users and switch the system web pages on or off.

You enter every password twice in masked fields, and it never appears again. The assistant can read and change a CPU's protection, users, certificate management and syslog. Adding a user and setting a password are left to you in the Project Explorer. Certificate management needs TIA Portal V18, syslog V19 and account locking V21.

Learn more in [Hardware](https://anyautomation.ch/en/docs/hardware)

#### Safety Validation and Safety Settings Through the Assistant (Pro)

Until now, the activation tests of the **Safety Validation Assistant** and the safety settings of a fail-safe PLC were set up in TIA Portal only. Now the assistant lists the activation tests with their groups, safety functions and conditions, checks whether a test is complete enough to run, and creates, changes, exports and imports tests after you confirm. It also writes the acceptance report as an Excel workbook. You still run the activation test itself in TIA Portal.

The assistant also reads and sets the F-block number ranges and the safety system version. Ask it to set or remove the password of the safety program and Studio asks you for the password in a masked field, so the assistant never sees it.

The Safety Validation Assistant tools work from TIA Portal V21, the safety settings and the password from TIA Portal V17. Available with Pro.

Learn more in [AI Chat](https://anyautomation.ch/en/docs/ai-chat)

#### Ask the Assistant Where Something Is Used

Until now, the assistant could only tell you where a block is used. Now you can ask it where a PLC data type, a tag table, a tag or a constant is used, and it lists every location with its kind of access and its device. It can also open the block at the network, the data block at the member or the tag table at the tag it talks about, so you land on that spot.

You can also ask which objects of a PLC nothing uses. The assistant lists the blocks, data blocks, PLC data types, tags and constants that nothing refers to, without compiling or exporting the PLC. For a single OB, FB, FC or data block it lists which interface members are used and which are not.

Listing unused objects and interface members is available with Pro, from TIA Portal V18.

Learn more in [AI Chat](https://anyautomation.ch/en/docs/ai-chat)

#### Keep the Project Up to Date with a Library

Until now, you had to open TIA Portal to find out-of-date library instances and update them. Open the **Library Updates** submenu on a library, a type folder or a type. **Check for Updates...** then lists the instances in the project that are out of date, device by device.

**Update Project...** and **Update Library...** bring the project or another library in line with the source library. **Harmonize Project...** aligns the paths and names of the instances with their library types. Before anything changes, a confirmation tells you what TIA Portal will change. Afterwards, the message counts the library types that were added, changed and removed, and **Show Details** lists them by name.

**Compare to...** on a library row shows the differences between two libraries, element by element. The assistant can check for updates, update and compare libraries for you as well. Checking for updates and comparing work on every plan, and comparing needs TIA Portal V18. Update Project, Update Library and Harmonize Project need Pro.

Learn more in [Library Management](https://anyautomation.ch/en/docs/library-management)

#### Find, Compare and Mark Library Types

If you know a library type only by its GUID, for example from a log or a colleague, run **Go to Library Type by GUID...**. It searches the project library and every open global library, and opens the matching type or type version. **Copy GUID** copies the identifier of a type or version to the clipboard.

**Compare with...** shows the differences between two library types, two type versions or two master copies, property by property, from TIA Portal V18.

Types can now be marked in the **Library** submenu and on the **Library Type** page. **Mark as Do Not Use** is available from TIA Portal V20, and **Mark for Update** from TIA Portal V18 in a global library opened with write access. Changing the marks needs Pro.

Learn more in [Library Management](https://anyautomation.ch/en/docs/library-management)

#### Port Cabling in the Project Explorer (Pro)

Until now, to see or change which port is cabled to which, you had to open the topology view in TIA Portal. Now each port under a network interface in the Project Explorer shows its partner as device and port, for example `Switch_1 / Port_8`.

Right-click a port and choose **Connect Port…** to pick the device and one of its free ports. **Disconnect Port** removes the cable after you confirm, and the question names the current partner. You can also ask the assistant which ports are cabled together, or have it connect or disconnect two ports. It asks before every change.

Learn more in [Hardware](https://anyautomation.ch/en/docs/hardware)

#### Set Several Attributes at Once (Pro)

Right-click a device, module, interface, port, subnet or IO system and choose **Set Attributes…**. Tick the attributes you want to change, enter the values, then choose **Apply What TIA Portal Takes** or **Apply All or Nothing**. The message afterwards lists every value that was set and, for each value TIA Portal did not take, the reason. The assistant can list the attributes you can write and set several of them in one step.

Available with Pro, from TIA Portal V18.

Learn more in [Hardware](https://anyautomation.ch/en/docs/hardware)

#### Hardware from Master Copies (Pro)

You can now create stations, modules, subnets and device groups from a master copy without leaving Studio. Right-click a master copy in the **Project Library** or under **Global Libraries** and choose **Create Hardware from Master Copy…**, or right-click **Hardware** and choose **Add Station from Master Copy…**. If the name is already taken, TIA Portal gives the new object another name, and the message shows both names. The assistant can create hardware from a master copy of the project library or a global library.

Learn more in [Hardware](https://anyautomation.ch/en/docs/hardware)

#### I-Devices and Redundancy Domains (Pro)

A CPU interface can now work as an I-device and keep its controller role. Right-click the interface and choose **Set Operating Mode…**. Its transfer areas appear as rows under the interface, and you add or remove them with **Create Transfer Area…** and **Delete Transfer Area**. To hand the I-device to an IO controller in another project, choose **Export I-Device GSD…**. This export works from TIA Portal V21.

MRP and sync domains now appear under their Ethernet subnet in the **Networks** branch. You can create them with **Create Redundancy Domain…**, add interfaces with **Add Participants…** and remove a domain with **Delete Redundancy Domain**. The assistant can do all of this on request and asks before every change.

Learn more in [Hardware](https://anyautomation.ch/en/docs/hardware)

#### Communication Connections (Pro)

A CPU or HMI panel now has a **Connections** branch with one row per connection, showing the type and the partner. Incomplete connections are marked. Right-click the device and choose **Create Connection…** to set up an S7, TCP, UDP, ISO-on-TCP or HMI connection, and use **Delete Connection** to remove one. The assistant can list, create and delete connections.

Available with Pro, from TIA Portal V21.

Learn more in [Hardware](https://anyautomation.ch/en/docs/hardware)

#### Compare Hardware (Pro)

Right-click a device or a module and choose **Compare Hardware With…** to compare two stations or two modules. The **Hardware Comparison** page shows both sides as a tree. Each object is marked in a **Result** column, for example **Identical**, **Different** or **Only on the left**, and a summary counts the objects in each state. The assistant can run the same comparison and report the result in the chat.

Learn more in [Hardware](https://anyautomation.ch/en/docs/hardware)

#### Unsaved Profile Changes

The **Save** icon in the **Profiles** bar now shows how many changes are not yet saved to the profile. Marking or unmarking an item, changing an import/export setting or changing the export folder each count as one change. Before Studio closes, before you disconnect and before another project becomes active, Studio lists these changes and asks you to **Save**, **Don't Save** or **Cancel**.

Learn more in [Protected Items](https://anyautomation.ch/en/docs/protected-items)

#### More TIA Portal Improvements

- Library types show whether they are an FB, FC or PLC data type, each row names its default version, and the hover adds the programming language and block number.
- Master copies show what they hold in the Project Explorer, and their hover names the author, the creation date and the content.
- Before a Multi-User check-in, the objects you changed are shown as yours, and any you untick are left out of the check-in.
- Find Unused counts a function block as used when another block holds it as a multi-instance.
- You can read, discover and write the parameter data of a module described by a GSD file, byte by byte (Pro).
- You can switch the communication of a telecontrol CP on and off, and export, import and create its data points, from TIA Portal V20 (Pro).
- You can export a project's system diagnostics settings to a file and import them again (Pro).
- You can export a software controller's resource assignment from TIA Portal V21, and export the PC system configuration file for stations that support it (Pro).
- **Show in Hardware Editor…** opens a device or the whole project hardware in the device, network or topology view of TIA Portal (Pro).
- A progress bar runs in the header of the Import / Export view while the export folder is re-read, also after a branch switch in that folder.
- The export folder tree hides the .git folder of a Git repository.
- **Filter** and **Refresh** are now on the first row of the export folder tree, and **Reveal in File Explorer** is next to the folder button.
- The **Security settings** folder with its **Settings** and **Users and roles** rows uses the same modern icon style as the rest of the Project Explorer.
- **Export as JSON** shows its progress, the elapsed time and **Cancel** in the **Import / Export** section, like every other export.

### Forge

#### Build and Deploy Errors That Lead You to the Cause

Until now, you had to search the template yourself when a build failed. Now the **Build Output** view shows a failed build with its reason and names the block type, the template and the line, and **Open Template** takes you to that line. When TIA Portal reports a compile error after a deploy, a double-click on the error opens the generated block at the statement.

Learn more in [Forge](https://anyautomation.ch/en/docs/forge)

#### Modules with Instances (Pro+)

Until now, a function block that your project calls several times, each time with its own instance data block, data blocks and tags, had to be copied and adapted by hand for every further use. Now right-click the function block in the **Block Type Library** and choose **Parameterise as Module**. After a preview of the places it touches and a dry run, the project graph holds one node per module instance, and the blocks and tag tables that mention the instances are generated from the instance list.

Right-click an instance node and choose **Add Module Instance** to add the next instance with its connections, or **Remove Node** to remove one; Studio names the blocks that generate code for it. **Create Project Graph from Library** shows module instances as nodes, and **Deploy Graph to TIA Portal** brings the data blocks of every instance along under their instance names. **Duplicate Block Type** on a module copies the plain captured block. Available with Pro+.

Learn more in [Forge](https://anyautomation.ch/en/docs/forge)

#### More Forge Improvements

- Large project graphs build to the end, however long the build takes.

### AI Chat

#### Assistant Exports Follow Your Export Settings

Until now, you could not be sure an export the assistant ran matched one you ran yourself. Now every export the assistant runs uses your export options from **Settings** > **Import/Export Settings**, with the same default values, document info and version control preparation as **Export Selected**. You cannot change these options from the chat, so every export uses your settings.

Learn more in [Import / Export](https://anyautomation.ch/en/docs/import-export)

#### Model Picker with a Tab per Provider

The model picker in the chat input now shows the models of each provider on their own tab, so you can switch models quickly. Point at a model to open its details card, where you set its thinking level and context size if the model offers them.

Learn more in [AI Chat](https://anyautomation.ch/en/docs/ai-chat)

#### More AI Chat Improvements

- The chat keeps answering after you trust a folder or enable an extension, without reloading the window.
- The chat title shows which harness runs the session, next to the session name.

### Agent Window

#### Choose Where a New Session Works

Until now, you set up each new session's working copy yourself. Now a new session works in the folder you opened. To let the agent work in a separate copy that you merge only when you are happy with it, choose **New Worktree** above the input. Studio keeps the choice for your next sessions.

Learn more in [Agents Window](https://anyautomation.ch/en/docs/agents-window)

#### More Agent Window Improvements

- **Filter Sessions** lists the harnesses Studio offers: Copilot, Claude and Local.
- Right-click a panel tab and choose **Align Panel** to lay out the bottom panel **Center** or **Justify**. The choice is kept per profile.

### Editor

#### Markdown Editor

Choose **Open With** on a Markdown file and pick the **Markdown Editor** to edit the file in its rendered form. While you edit, every source line stays on its own line. You can paste a screenshot straight into the document, rename a file link everywhere with **Rename Symbol**, move around with the outline and breadcrumbs, and copy any code block with its own copy button.

#### More Editor Improvements

- **Settings** > **Text Editor** > **Occurrences Highlight From All Providers** shows the document highlights of every provider together.

### Licensing

#### More Licensing Improvements

- When you activate on another computer after using up all machine switches of the last 30 days, the **License** window says so.

### Studio

#### More Studio Improvements

- The release notes show a table of contents beside the text that marks the section you are reading, and their headings take the accent color of your theme.

### Removed and changed

- Terminal sandboxing for local sessions is no longer offered.

## v1.141.0

### TIA Portal

- Disconnect from TIA Portal asks whether to save a project with unsaved changes before TIA Portal closes with it.
- A block imported from a single file lands in its project folder.
- Delete leaves a PLC's default tag table in place and says so, also inside a deleted folder, and the assistant declines to delete it.
- Properties on a block or a data type shows its header, dates, memory, state and the title and comment in every project language.
- Export Snapshot on a data block shows the snapshot values in a table and saves them as XML into the export folder.
- The PLC data types folder lists the system data types of the PLC on demand, as its last entry and greyed like in TIA Portal.
- Create Instance in PLC on a library type version or a master copy, and Add from Library on a block or PLC data types folder, place the library object in the folder you choose (Pro).
- Delete Software Unit names what the unit holds before it removes it, and Edit Properties changes its namespace preset, author and comment per project language.
- New Software Unit from Master Copy on the Software units folder creates a unit from the project library (Pro).
- Export Source with Dependencies on a block or PLC data type writes one source file with everything it uses into the export folder, and Show Source with Dependencies opens that source read-only from the open editor.
- ProDiag alarms and supervisions of a ProDiag function block, the supervisions of a whole PLC and the supervision settings export into the ProDiag folder of the export folder.
- Properties on a function block shows how many supervisions it carries.
- The tag table editor lists the table's system constants, read-only, at the end of the grid.
- Comments by Language below the tag table shows a tag's comment in every active project language and writes the ones you change.
- Export Selected Tags in the tag table saves the selected tags and user constants as single files into the Tags folder of the export folder.
- Import Tags into Table on a tag table imports single tag and user constant files and names every file it could not take, with the reason.
- Watch table folders appear in the Project Explorer, where New Watch Table, New Folder, Delete, Rename (TIA Portal V21) and Show Entries manage watch tables.
- Compile on a block, PLC data type, folder, technology object, device or module compiles only that object, and the warnings of a device show in the TIA Portal log.
- Compiling a PLC whose safety program needs your login offers the Safety Login (Pro).
- Properties on the project shows its header, size, state, used products and history, and writes the project comment in each active project language.
- Project Languages on the project shows the editing, reference, active and available languages of the project and changes them.
- Export Project Texts on the project, a PLC or a device writes the project texts into Excel workbooks for the languages you pick, on TIA Portal V21 also for only that PLC or device.
- Import Project Texts brings a translated workbook back into the project and warns before the import that empty cells clear translations.
- Save Project As saves the project into a new folder and continues there, and the Project Explorer, its profiles and the open project tabs follow it.
- Archive Project offers a compressed archive or a project copy in a folder, each with or without restorable data.
- Import AML asks whether existing devices are overwritten, kept or moved to the parking lot, and both AML commands list what TIA Portal reported (Pro).
- AML export and import are not available on TIA Portal V18 (Pro).
- The TIA Portal Settings entry in the project menu lists the settings of the connected TIA Portal and changes the ones Studio may change, such as the user interface language.
- Attributes on the project, a block, a data type, a tag table or a hardware item (Pro) lists every attribute with its value, changes the writable ones and shows the available actions.
- The TIA Portal entry in the status bar lists the installed TIA Portal products and options when you point at it.
- Cycles and slide-in screens of a classic HMI device export and import with the other HMI items, and an unchanged standard cycle is skipped.
- The Project Explorer lists the slide-in screens of a classic HMI device, and Import Selected in the export folder imports the checked files of a classic HMI device into that device.
- Instantiate in HMI on a master copy or on a screen or VB script type version places it on a classic HMI device in the folder or tag table you choose (Pro).
- Upload from Device and Upload Station Export ask for your sign-in when a CPU requires one; the password is entered in Studio, never stored and never passed to the assistant (Pro+).
- Go Online in TIA Portal asks for your sign-in on TIA Portal V21; on older versions and for the master secret commands Studio points you to the sign-in dialog of TIA Portal (Pro+).
- Upload Station Export on a CPU uploads its station and exports the blocks, PLC data types and PLC tags into a folder you choose, without changing the open project (Pro+).
- Upload Parameters on a drive in the hardware tree reads the parameters of the drive into the project over the interface and address you choose, on TIA Portal V21 (Pro+).
- Go Online in TIA Portal and Go Offline in TIA Portal on a CPU take the CPU online and offline in TIA Portal itself, so a compare with the CPU and the assistant's online reads can use that connection (Pro+).
- The CPU context menu offers Set Master Secret and Reset Master Secret; a reset asks for confirmation because it deletes any existing secret (Pro+).
- Write Protection on an organization block, function block or function defines, changes, enables and disables its write protection on TIA Portal V21, and a WP badge marks a write-protected block (Pro).
- Know-how protection with a stored vault password leaves a write-protected block untouched and names it (Pro), and an import that replaces a write-protected block tells you its write protection is gone.
- Create Snapshot, Load Snapshot as Actual Values and Load Start Values as Actual Values on a data block work with the online CPU on TIA Portal V21 and ask before they replace a stored snapshot or change values on the CPU (Pro+).

### WinCC Unified

- A screen whose dynamization was switched to another condition type opens; the entries of the earlier type are left out and the load message names them.
- The condition type and the flashing rate of a screen's colour and value conditions are saved with the screen.
- The connection view of a device lists the driver settings, changes them and the driver in place, and sets the connection's user name and password without ever showing them (Pro).
- Import OPC UA Alarms from File on an OPC UA connection of a device imports the alarm file of the OPC UA server and lists the alarms directly below its root folder (Pro).
- Describe Type on an entry of the object palette in the screen editor lists the attributes, default values and compositions of that screen item type (Pro).
- An open object pane follows the changes the assistant makes.

### SCADA

- Toggle buttons on a sent page switch their signal on each click (Pro).
- The signals you check in the Signals view are saved with the project and come back when you reopen it (Pro).
- Load From TIA Project in the Signals view is available as soon as the project is connected (Pro).
- Renaming a page also renames the navigation tiles and buttons that show its name (Pro).
- Apply Rules after Propose Screens updates the proposed widgets to your own rules (Pro).
- The Button Action in the Properties view shows what a click on the button does (Pro).
- The Events section in the Properties view names the page a click opens and warns when a card event will be ignored (Pro).
- The legend and the badge hover in the page editor explain each finding in a sentence (Pro).
- A symbol without a signal shows its drawing in the page editor (Pro).
- Widget labels placed close together stay fully readable in the page editor and on the dashboard (Pro).
- The examples on an alarm rule card in the rule editor show the alarm text in the project's default language (Pro).
- Import Text List offers the languages of your project (Pro).
- The Send view shows how many pages each send wrote (Pro).

### Unit Testing

- Add Input and Add Write Variable start with an empty row, and its Variable list shows every member of the block interface (Pro+).
- History marks a run with failed cases as failed and a run that stopped early as an error (Pro+).
- Each suite and case in Test Suites shows a Run button when you point at it (Pro+).
- Several edits the assistant stages in an open suite add up, and Keep or Undo applies to all of them (Pro+).
- The generated CI pipeline runs on your own Windows build agent, and an optional agent label picks a specific one (Pro+).
- The traceability report is saved next to the reports you last exported (Pro+).
- The command-line runner prints only warnings and errors unless you choose another log level, and shows its help in English unless you choose another language (Pro+).
- A new report export sits at the top of its folder, earlier reports are kept in their own subfolder, and the export message names the folder and opens it (Pro+).

### Hardware Simulation

- An OPC UA connection or source lets you choose the server endpoint with its security mode and policy, and signs in anonymously or with a user name and password (Pro+).

### Forge

- Remove Node in the project graph also offers the instance DBs of the removed block, listed on their own, and takes along what only the block and its instance DBs used (Pro+).
- Capture to Forge Library keeps the XML of every block next to its source, like Export All, and Deploy to TIA Portal brings both along (Pro+).
- The project tree of a graph and the Block Type Library show the project, its Source folder, the PLC and the Blocks, Datatypes and Tags folders the way the Project Explorer does, with the same icons on folders and blocks (Pro+).
- An Activity pane in the Forge view shows the running graph creation, build, deploy, capture or integration with its progress, the item it is on and a Cancel button, and lists the finished runs with their result (Pro+).
- Create a project graph straight from the block type library, a library folder or selected block types, with the library folders as its project tree, the tag tables as nodes of their own, and the blocks connected the way they call and use each other and their tags (Pro+).
- Integrate Project into Coupled Library, in the context menu of a PLC, shows each step with its progress, from the export to the opened project graph, and can be cancelled (Pro+).
- The code generator for TIA Portal ships with the installed Studio, so Build and Deploy Graph to TIA Portal are available (Pro+).
- Deploy Graph to TIA Portal brings the tag tables with the user constants of an integrated project along (Pro+).
- Deploying a graph or the library to TIA Portal replaces the content of the PLC and keeps protected items (Pro+).
- The file pickers of Materialize Machine Configuration and Scaffold Project and Deploy Graph open in the workspace folder (Pro+).

### Password Vault

- Each stored password has its own Protect and Unprotect buttons for the blocks assigned to it (Pro).
- Each stored password can get a color, and the Vault checkboxes of its blocks in the Project Explorer show that color (Pro).
- Unchecking the Vault checkbox of a block inside an assigned folder takes that block out of the stored password and keeps the rest of the folder (Pro).

### AI Chat

- Loaded tools and loaded skills show as completed steps in the chat.
- A block the assistant imports from the export folder lands in the project folder that matches its sub-folder.
- The assistant can create, rename, move and delete folders under Program blocks, PLC data types and PLC tags and move blocks, data types and tag tables into folders, and it asks you to confirm each change.
- The assistant opens, retrieves, closes and archives projects, saves the open project into a new folder, and asks you before each step.
- The assistant works with Multi-User Engineering: it lists servers, server projects and local sessions, checks a session out, saves it, marks objects and checks them in, and manages server connections (Pro).
- The assistant manages the project library: master copies, folders, renaming, deleting, exporting a type version and cleaning up (Pro).
- The assistant replaces the whole program of a PLC from an export folder (Import All) after your confirmation.
- The assistant reads the project properties, languages and history and the products installed in TIA Portal, and changes the project languages and the project comment after you confirm.
- The assistant reads every attribute of the project, a block, a data type, a tag table or a hardware object (Pro); changing them stays with you.
- The assistant reads the TIA Portal settings; changing them stays with you.
- The assistant exports the project texts to a workbook for translation and imports the translated workbook after you confirm.
- The assistant imports hardware from an AutomationML file, with your choice for devices whose names are already taken, and changes single hardware settings, network addresses and module start addresses (Pro).
- The assistant renames blocks, creates instance data blocks and PLC data types, reads, creates and changes PLC tags, deletes several tags or a whole tag table, and reads and edits the interface of data blocks.
- The assistant exports and imports watch and force tables, exports technology objects, and exports blocks and data types as XML only.
- The assistant reads the properties of a block or PLC data type, its write protection included, exports the snapshot of a data block with its values and lists the system data types of a PLC.
- The assistant creates instances from library types and master copies and creates software units from master copies (Pro).
- The assistant lists and manages the software units of a PLC and their blocks, and exports a source with its dependencies and the ProDiag information.
- The assistant sets the access flags and the comments per language of PLC tags, lists the system constants, exports and imports single tags, creates, renames and deletes watch tables and their folders, imports watch tables into a folder, reads their entries, and compiles a single block, folder or device.
- The assistant reads classic HMI screens with resolved colors, screen overviews, faceplate types, text and graphic lists and graphics, imports a classic screen, and exports, imports and deletes the items of a classic HMI device, cycles and slide-in screens included, after you confirm.
- The assistant reads the online state and the connection options of a PLC, searches reachable devices, compares the project with the online CPU, goes online and offline, previews and runs a download, and uploads from a PLC into a folder or into the project (Pro+).
- The assistant reads the safety login state, runtime groups and F-signatures, exports the F-signatures, writes the safety printout and logs out of the safety program; it never handles the safety password (Pro).
- The tool picker shows the new groups TIA Online Connection, TIA Safety Program, TIA Multi-User Sessions and Servers and Manage TIA Project Library next to the existing TIA Portal groups.
- While an answer runs, a progress line at the bottom shows what the assistant is working on, and finished tool steps fold into one row you can expand.
- Follow-up messages in a long chat start faster.
- Add Context opens right next to its button and closes when you select the button again.
- In a narrow chat view the toolbar buttons that do not fit are available under More Actions.
- Tool servers in Agent Customizations are grouped by where they come from: your profile, the workspace, plugins, extensions and built-in.
- Claude Opus 5.5 and Claude Haiku 5.5 can give longer answers.
- Changing the reasoning effort between turns and loading more tools mid-conversation are cheaper on Claude Opus 5.5, Sonnet 5.5 and Haiku 5.5.
- GPT-6.1 Sol, GPT-6 Sol and GPT-6 Luna are in the OpenAI model picker, and GPT-6 Sol and GPT-6 Luna can run with reasoning off.
- Mistral models offer the reasoning levels they support, including off.
- When the model list cannot be loaded, the Claude and OpenAI pickers offer the current models.
- The model pickers of OpenAI-compatible providers list chat models only.
- A conversation that outgrows the model context on Z.AI, xAI, Groq, MiniMax or Alibaba Model Studio is compacted and continues.
- When a provider is busy or fails before its answer has started, the request is retried; a failure during an answer is reported.
- A provider sign-in can be cancelled from its progress notification.
- When the sign-in port is taken or blocked, Studio names the likely cause and lets you paste the address from the browser.
- Screenshots too large for the provider are skipped with a note, and the rest of the message is sent.
- Thinking can be switched off on Claude Sonnet 5.5 and Claude Haiku 5.5.
- Sending a message before an AI provider is set up asks you to choose one first, opens the provider list in one click and keeps your message in the input.
- The assistant writes the driver settings of a WinCC Unified connection after you confirm; the user name and password stay with you (Pro).
- The assistant creates a screen, a screen template, a pop-up screen, a tag table, a tag or a VB script on a classic HMI device from a master copy or a type version after you confirm (Pro).
- The assistant imports an OPC UA alarm file into a WinCC Unified connection after you confirm and lists the alarms at its top level (Pro).
- The assistant describes a WinCC Unified screen item type with its attributes, defaults and compositions (Pro).
- The assistant uses your export folder, or the open workspace folder, for its exports and imports without asking for the path.

### Agent Window

- Drag sessions beside, above or below each other to arrange them in a grid with resizable panes, kept after a restart.
- Filter Sessions narrows the list by environment, harness and the application that created a session, next to the ordering and grouping choices.
- The compact layout density is available for the Agents window too, under View, Layout Density, for that window alone.
- The side pane of a session has a Project Explorer tab next to Changes and Files.
- A new session starts as a Local session with the AI providers you have set up.

### Editor

- A column selection pasted at a single cursor fills the following lines as a block, padded with spaces where lines are shorter.

### Appearance

- Menus, the Command Palette and other pop-ups show a softly blurred background, and how see-through it is can be adjusted in Settings.

### Studio

- Report Issue attaches the report TIA Portal writes when it ends during an operation.

## v1.140.0

### SCADA

<video src="https://anyautomation.ch/video/releasenotes/scada-workspace-1.140.0.mp4" poster="https://anyautomation.ch/video/releasenotes/scada-workspace-1.140.0.jpg" autoplay loop muted controls playsinline></video>

[The SCADA Workspace: From PLC Signals to a Live Web Dashboard (YouTube)](https://www.youtube.com/watch?v=XLyOr9n7XhM)

- The SCADA icon opens a side bar with the views Project, Signals, Pages, Symbols and Rules, where you load signals, arrange pages, pick symbols and switch rules on and off (Pro).
- A page opens in a page editor where you move and resize widgets, and Preview tries out the page with simulated values, including the cards it opens (Pro).
- Drag a symbol from the Symbols view onto a page to place it, or drag signals onto an empty spot to place widgets for them (Pro).
- A signal dropped on a symbol binds to it, with a choice of slot when the symbol has several, and one dropped on a marked part makes that part follow the signal (Pro).
- A binding set by hand can be saved as the default of its symbol or as a rule for every signal of the same type (Pro).
- The SCADA Properties view on the right shows the properties, bindings, states and rule of the selected widget, and its States tab sets colour, visibility, blinking and motion per signal value in a table (Pro).
- The SCADA panel lists the problems of the project, the past sends with their backups and the signals each rule hits, and marks the problems in the files (Pro).
- The status bar shows the SCADA target with its stage and FUXA version, the owner of the open page, the rules in use, the signal source and whether live mode is on (Pro).
- Live mode, switched on with Toggle Live Mode, sends every save of the project to a development target a second later and switches itself off when a send needs your confirmation (Pro).
- Load From CPU in the Signals view reads the signals of a CPU you connected in PLC Online and never writes to it (Pro).
- Open FUXA and View in FUXA show the dashboard in a browser tab inside Studio, and the SCADA target in the status bar also opens it in your system browser (Pro).
- The assistant places, moves, resizes, removes and binds widgets on a page, renders a page as an image to check it, and loads the signals of a CPU connected in PLC Online (Pro).
- Alarm rules in the rules file raise alarms for every matching signal of the default PLC, also without a widget on a page, with a level, a text from the signal comment or a template, a group, and one alarm per bit of a status word (Pro).
- A signal of the default PLC marked as an alarm in its comment raises its alarm even when no page shows the signal (Pro).
- Every sent project raises an alarm when the connection to a PLC is lost (Pro).
- The alarm table can be filtered by level, text, group and signals (Pro).
- A message table shows the current entries of a message buffer with the columns you choose (Pro).
- Text lists can be imported from CSV or JSON files (Pro).
- The assistant reads and edits alarm rules and imports text lists (Pro).
- A send tells you when it changes the alarms and that every active alarm is then reset (Pro).
- An alarm that the runtime already holds under another name is reported and not added a second time (Pro).
- The Rules view lists your alarm rules with a switch and the number of alarms each one raised (Pro).
- The Rule Hits panel lists the alarms of the last build per rule and jumps to the signal of an alarm (Pro).
- The filter of an alarm table and the buffer, slots and columns of a message table are edited in the Properties view (Pro).
- Insert Widget places an alarm table, a message table or a navigation tile from the toolbar or a right click on the page (Pro).
- The preview shows what an alarm table filters and which columns and slots a message table has (Pro).
- Alarm problems name the rule or the signal they concern and open it on a click (Pro).
- The Project view lists the text lists with their language and number of entries and offers the import in its title bar (Pro).
- The assistant sets the alarm filter and the message table columns of a widget (Pro).
- A send you start opens one dialog with the target, the pages to send, the backup and every check, before anything is written (Pro).
- A page you uncheck in the send dialog stays as it is on the runtime (Pro).
- The send dialog lets you choose for each send whether the dashboard is merged into the project on the instance or replaces it (Pro).
- Edit in the Runtime Editor hands a page over to the runtime's browser editor, and Studio then shows it read-only and leaves it out of every send (Pro).
- Restore Studio State backs up the runtime's version of a page, shows the differences and takes the page back (Pro).
- Replacing the whole project, restoring the runtime volumes and deploying a compose file over the container are refused while a page belongs to the runtime's browser editor (Pro).
- When pages were changed on the runtime since your last send, the send dialog lets you cancel, overwrite them after the backup, or hand them over to the runtime's browser editor (Pro).
- Rules files open in a rule editor with a form next to the JSON, the hits of every rule and the alarms of the last build (Pro).
- Edit Symbol States sets the default states of a symbol next to its drawing, with a preview of every state and checks for common mistakes (Pro).
- The assistant can hand a page over, take it back, send to a production target, replace the whole project and set the default states of a symbol, and Studio asks you before each of these changes anything (Pro).
- A project can read several PLCs, and every page and every widget shows the signals of its own PLC (Pro).
- A target connects each PLC of the project on its own, and a send is refused when the target leaves out a PLC the project uses (Pro).
- The Signals view lists the signals of every PLC under a row of their own, and Set PLC of Page and the PLC button in the Bindings tab choose the PLC of a page and a widget (Pro).
- The status bar lists the connection of every PLC, and a problem that concerns a PLC names it and shows it in the Signals view (Pro).
- Roles decide for each page, widget and alarm who sees it and who may operate or acknowledge it, and the runtime applies them for signed-in users (Pro).
- The runtime shows your project in several languages, with a language switch in its header and translated texts for alarms, titles and navigation (Pro).
- Alarm notifications send an e-mail or call a web address for the alarm levels you choose, and you enter each receiver in Studio yourself, never through the assistant (Pro).
- A page can be the detail view of a data type, and every structure of that type opens it as a card with its own values (Pro).
- The assistant sets up PLCs, roles, languages, detail views and notifications, and never sees the receiver of a notification (Pro).

### PLC Online

- A Disconnect button in the connection header ends the connection while it is up (Pro).
- Closing a connection tab, or the PLC Online editor, disconnects its connections (Pro).
- A reopened PLC Online editor brings back its endpoints and watch items but waits for you to press Connect (Pro).
- A Refresh button above the address-space tree reloads the whole tree from the server and keeps the branches you had open (Pro).
- The status bar counts a connection as soon as it is up (Pro).
- A reopened PLC Online editor shows the endpoint of each restored connection in the connection header (Pro).
- Over an S7 connection the address-space tree and the watch table show and read the variables inside a PLC data type element of a data block (Pro).
- Over an S7 connection arrays expand to their elements in the address-space tree, and every element and the variables inside an element of a PLC data type array can be watched and written (Pro).
- Over an S7 connection texts, hardware identifiers and connection identifiers read with their proper type and value (Pro).
- Over an S7 connection the variables inside an element of a PLC data type array can be watched and written in data blocks with standard block access as well (Pro).
- Large watch tables and many writes over an S7 connection stay within what the controller accepts (Pro).
- When the controller declines a request over an S7 connection, the message names the controller's reason (Pro).

### TIA Portal

- The protection marks on data types and tag tables stay in place after a refresh of the Project Explorer, also after an import by the assistant, and the profile you last applied is fully restored when you open the project.
- The profiles bar is ready when you open the Project Explorer after connecting to a project.
- The Hardware, the HMI devices and the Project Library of the Project Explorer are read only when you click the load icon next to them, so the tree appears sooner after connecting.
- One click on the load icon of any HMI device reads all HMI devices of the project.
- Load Hardware, Load HMI and Load Project Library under Project Explorer in the Settings read these parts as soon as the project connects.
- Find References answers within seconds when you search the same project again, also after a restart of Studio as long as the project has not changed.
- Live Values in an online block also work for blocks with standard block access (Pro+).

### Compare Editor

- Comparing a project with a folder exports the PLC only the first time; later comparisons read again only the items that changed.
- After Import Selected the comparison refreshes itself without exporting the whole PLC again.
- The progress of a comparison names each step and counts the items while it checks the PLC for changes.
- Clicking Compare while the comparison is still refreshing itself after an import or a save shows that refresh to its end.
- Export Selected writes the checked changes from the project into the compared folder and removes the items the project no longer has, after asking.

### Project Search

- The first search of a project prepares its data blocks together with the other blocks, so it finishes in a fraction of the time on a large project.
- The prepared sources stay with the project after a restart of Studio; the first search of a new session only checks for changed blocks.
- While a search checks the project for changed blocks, the progress counts the blocks checked so far.

### WinCC Unified

- Screens with range conditions on tags that are not whole-number tags, such as Real or String, or on expressions open on TIA Portal V18 and newer; saving or copying such a screen from Studio is refused and names the affected conditions.

### Unit Testing

- The Test Suite Editor lists every test case as one row and edits the selected case below the list, so a suite with dozens of cases stays readable at a glance (Pro+).
- Requirements, priority and tags of a case show in the case list, and the list can be filtered by text, status, priority and requirement (Pro+).
- Clicking a test case in the Test Suites view opens it in the editor with that case selected (Pro+).
- The Test Suites view keeps its main actions in the title bar and the rest in its overflow menu (Pro+).
- Keyboard shortcuts in the Test Suite Editor add, duplicate, move and remove test cases, run the selected ones with Ctrl+Enter and switch between the Visual, JSON and SCL views (Pro+).
- The lower part of the Test Suite Editor collapses and expands with a click or Ctrl+Shift+J, and both parts scroll on their own (Pro+).
- The remove icons of inputs, assertions, steps and watch entries are always visible (Pro+).
- The editor header highlights the active view, Visual, JSON or SCL, in the colour of the current theme (Pro+).
- The inputs, assertions, steps and watch rows of a test case show the data type of the selected variable (Pro+).
- A test suite that was open when Studio closed shows its cases again right after the next start (Pro+).
- Each test input can be wired to the data block variable the calling program passes to the block, chosen right in the input row from the data blocks of the project, so tests also run on blocks that are called with parameters (Pro+).
- A run stops before the first test case and names the variable when a wired variable cannot be found on the controller, and the variables keep their previous values after the run (Pro+).
- A test input that cannot be written fails its test case with a message naming the variable (Pro+).
- Test inputs of type TIME, DATE and TIME_OF_DAY reach the simulation, so a start delay set in a test case takes effect (Pro+).
- On S7 connections inputs reach variables inside PLC data types and array elements, also inside a PLC data type array, and TIME and S5TIME inputs reach the controller (Pro+).
- A suite can be run again right after the previous run (Pro+).
- When the block of a suite cannot be read from the project, the message names the reason, for example that the block is not compiled (Pro+).
- The Unit Testing pane is now the Test Bench: choose the PLC, the block and the test suite in its header and run the suite from there (Pro+).
- Choosing a block in the Test Bench shows its interface, including deeply nested data types and the members of each multi-instance, and its boundary values, with progress while it reads the block (Pro+).
- One Run tab in the Test Bench shows the results, assertions and variable timeline of a run, also for runs opened from the run history (Pro+).
- A status bar item shows the progress and the result of the last test run and opens it with one click (Pro+).
- The Test Bench keeps the chosen PLC, block, suite and the shown run across a restart (Pro+).
- Column widths of the test case tables are remembered (Pro+).
- Show Coverage Heatmap and Show Mutation Markers are in the menu of the Test Bench (Pro+).
- The arrow next to Run opens a dialog that runs all suites, one suite, its failed test cases or the selected test cases (Pro+).
- The same dialog runs a suite with coverage, mutation testing or an interface contract check, and turns on flaky re-runs, quarantine or the update of snapshot baselines (Pro+).
- A plain click on Run keeps the last flaky re-run and quarantine choice (Pro+).
- Flaky re-runs and quarantine work for runs started in Studio (Pro+).
- A suite with unsaved changes asks to be saved before any run from the Test Bench or the Test Suite Editor (Pro+).
- Connection settings open as a page for each suite, with a Test Connection check for PLCSIM Advanced and OPC UA (Pro+).
- Saving connection settings keeps the passwords you did not change (Pro+).
- New test suites start with the connection you saved as default (Pro+).
- Isolation settings of a suite are edited on the connection page (Pro+).
- The History tab shows each test run with its results at a glance, and you choose the columns (Pro+).
- Select two runs to compare them, or switch to Trend for pass rate, duration and case history, all in the History tab (Pro+).
- Export a report from History or the Run tab in one small form (Pro+).
- The Quality tab shows coverage and mutation results of the suite in the Test Bench, each with its own run button (Pro+).
- Type the OPC UA endpoint right in the Address Space tab to browse a server (Pro+).
- Set up CI pipelines on their own page and see the generated files update as you type (Pro+).
- Generated GitHub Actions, GitLab CI, Azure DevOps and Jenkins pipelines run their test step in bash, so a Windows build agent needs Git Bash (Pro+).
- Requirement ids from every suite of the test folder are suggested while you type them, and ids that differ only in spelling are pointed out (Pro+).
- Requirements and tags of a test case are edited as chips, and pasted lists become one chip per entry (Pro+).
- A Traceability tab in the Test Bench shows every requirement with its test cases and their latest results, and exports it as CSV or HTML (Pro+).
- Import a requirement list so requirements without a test show as uncovered (Pro+).
- The command-line runner can fail a CI build on failed or uncovered requirements (Pro+).
- Sign off a completed test run from the Run tab or History with your account and a comment, and revoke it with a reason (Pro+).
- History and Traceability show the sign-off of each run, and a later change to the suite or to the recorded run is flagged on the sign-off (Pro+).
- A signed-off run cannot be deleted until its sign-off is revoked, and only the account that signed it off can revoke it (Pro+).
- Reports carry the sign-off of the run, and the command-line runner checks it when it verifies a report (Pro+).
- The Interface tab of the Test Bench shows structures, data types and instances collapsed; expand them as needed (Pro+).
- A new test suite starts with an empty test case; add the variables you need (Pro+).

### AI Chat

- A message you send while a block upload to TIA Portal is still running goes out right away.
- The assistant finds where a name is used from the prepared project sources, so a lookup on a large project takes a fraction of the time and also works on a project opened offline.
- The assistant can operate PLC Online over OPC UA in a visible connection tab: it connects, browses and searches the address space, reads and writes values, watches values and events, fills the watch table, reads history and diagnostics, calls methods, manages certificates and disconnects (Pro).
- The assistant looks up how a block is called in the project, wires the test inputs accordingly and tells you which inputs the program fixes (Pro+).
- Right-click a link in an answer to copy it, or to open a linked file in an editor of your choice.
- Each tool server in Agent Customizations shows the file that defines it, and a click on it opens that file.
- Adding a tool server to a workspace folder saves it in a .mcp.json file at the folder root and asks which file to use when the folder already has a server file.
- Install Plugin from Source offers a button that picks a local plugin folder.
- Terminal output in an answer can keep the width of the terminal and scroll sideways, switched in the chat settings.
- The assistant asks before it clicks, types, drags or hovers in a page of the integrated browser.
- The assistant always asks before it creates and runs a task, also when its actions are approved automatically.
- The assistant asks before it runs a git diff that writes its output to a file.

### Agent Window

- The mode and the permission level you choose under the input of a new session apply to the requests of that session.
- Marking a running session as done stops it first, and the session stays in the list when it cannot be stopped.
- The active chat tab and the active side-panel tab join their surface with the same connected style as editor tabs.
- Tint Window to Match Background in the chat background menu colors the window after your background image.

### Editor

- Selecting further occurrences of the selected text can match upper and lower case exactly or ignore it, independent of the Find options, chosen in the editor settings.

### Settings

- A Project Explorer category holds the settings of the project tree.

## v1.139.1

### SCADA

- A SCADA project lives as files in your workspace, one file per screen, so you can create it, open it again later, import a screen plan you saved earlier and keep it in version control (Pro).
- Set Target Login and Stage stores the login and the stage (Development, Test or Production) of your FUXA instance, and a test or production instance takes a send only once they are set (Pro).
- A send to a production instance asks a second time and names the instance and its stage (Pro).
- Test Connection shows the FUXA version of your instance and whether Studio has checked it, and a version Studio has not checked only warns (Pro).
- The FUXA Install Folder setting lets Test Connection read the exact version of a FUXA you installed directly (Pro).
- Every send first saves the project that is on the FUXA instance into the backups folder of your SCADA project and records the send in the project's publish log (Pro).
- When a send has to restart the FUXA runtime, the confirmation says why and how many alarms are active on the instance (Pro).
- When only pages, the header or the navigation changed since the last send, the send updates the running dashboard without a restart, active alarms stay and open viewers show the change once they reload (Pro).
- A merge send also removes from the FUXA instance the pages, alarms and devices you deleted from the project, after asking, and leaves everything made in FUXA alone (Pro).
- A send stops before writing anything when a page has the name of a page made in FUXA, and names both pages (Pro).
- A send stops and names the effects when the pages use effects the FUXA version on the instance cannot show (Pro).
- Apply Rules turns your signals into widgets and pages from the built-in rules or your own rules file, shows every change in a preview first and keeps what you set by hand (Pro).
- Run Why This Widget? to see which rule chose the kind, label and page of a widget, which rules were overruled and why its page appears in the navigation (Pro).
- The project, page, target, rules and symbol files offer completion and hovers in the editor.
- Symbols follow the plant state: marked parts of your SVG symbols and of a page background change colour, show, hide, blink, turn or move with the signals a rule, the page file or the assistant binds to them (Pro).
- The navigation of the dashboard shows an icon per page and leaves out detail pages, and the header can show the date and time and the signed-in user, all set in the project (Pro).
- Header and navigation changes made in the FUXA editor show as a difference before the next send, and the entries and buttons added there stay (Pro).
- A command button writes a fixed value to the PLC on each click and leaves the reset to the PLC program, and a tile shows several values under one title (Pro).
- A page can open as a card on top of the current screen (Pro).
- Deploy FUXA in Docker installs a FUXA release Studio has checked, keeps it running after a reboot, reachable only on the Docker host unless you choose a network address, and keeps your symbol library across updates (Pro).
- Replacing an existing FUXA container backs up its volumes first and puts the old container back when the new one does not start (Pro).
- Back Up FUXA Volumes, Restore FUXA Volumes, Load FUXA Image from File and Export Docker Compose Template back up and restore FUXA, install it on a machine without internet access and write a Compose file (Pro).
- The first Deploy FUXA in Docker, or Enable FUXA Login at any time, turns on the FUXA login with a new administrator password (Pro).
- The assistant works on the open SCADA project from the chat: it creates and opens projects, changes pages, the header and the navigation, applies rules through the same preview, sets symbol states, explains widgets and runs FUXA in Docker (Pro).
- The assistant sends only by merge and only to a development or test instance, and each of its SCADA tools can be denied for good in Tool Approvals (Pro).

### PLC Online

- Structured variables in the OPC UA address space (PLC data types, structs, arrays and timer instances) open to their members, level by level, and the tree shows the data type of every variable (Pro).
- A member picked from inside a structure or an array keeps its full path as its name in the Watch Table (Pro).
- Struct Fields lists the members of a structure in their declared order, and an array of structures shows one entry per element (Pro).
- When some nodes cannot be added to the Watch Table, the others are still added and one message names the ones that failed (Pro).
- When the server publishes no members for a structure, Struct Fields says so and tells you to make the elements of its data type accessible from HMI/OPC UA in TIA Portal (Pro).
- Edit Matrix appears in the context menu of a two-dimensional array variable (Pro).
- Very large data blocks are faster to add to the Watch Table and to read again (Pro).

### TIA Portal

- Click the project name at the top of the Project Explorer to switch projects or to connect, open or create another one.
- Closing an offline project brings the connected project back into the Project Explorer (Pro).
- The Find Unused icon opens the Find Unused page right away, with a Connect button until a project is connected, and the scan starts when you select Find All Unused (Pro).
- Data types export without a .udt source by default, and an import takes the XML when a data type is there as both .udt and XML.
- Data Types as .udt Source and Prefer .udt over .xml in the Import/Export settings switch the .udt handling back on, for you and for the chat assistant.
- An export that writes no .udt source removes an older .udt of the same data type from the export folder.
- The blocks folder of a safety software unit shows the program blocks icon and the name set under Folder Names, and deleting it deletes the blocks inside, like in a standard software unit.
- Ticking an Export or Vault box keeps the keyboard in the Project Explorer, so the arrow keys and the tree shortcuts keep working.

### Unit Testing

- Structured and array variables in the OPC UA address space open to their members and show their data type name (Pro+).
- Test cases that run over OPC UA reach array elements and timer members of a data block by their path, such as `DB_Motor.Setpoints[3]` or `DB_Motor.StartTimer.Q` (Pro+).

### Hardware Simulation

- Structured and array variables of an OPC UA source open to their members in the address space and show their data type name (Pro+).
- Members of a structure are picked, dragged and added as tags under their full path, and forces and functions keep that name (Pro+).
- Forces, functions and linker rules write integer, date and time tags of an OPC UA source (Pro+).
- Add to Watch on a variable of an OPC UA source shows the new row in the Watch panel right away (Pro+).

### Project Search

- The Project Search icon opens the search page right away, with a Connect button until a project is open.

### Password Vault

- The Password Vault icon opens the Password Vault right away (Pro).

### Trace

- The Trace icon opens Trace right away.

### PLC Simulation

- The PLCSim Advanced icon opens the PLCSim Advanced dashboard right away (Pro).

### Forge

- Two new settings decide whether data types go into the Block Type Library as .udt source and whether a deployment prefers the .udt over the XML, both off by default (Pro+).
- Pressing Delete in a text field of the project graph editor edits the text and leaves the selected node in place (Pro+).

### AI Chat

- The GitHub Copilot Auto model completes requests that use tools, in the chat and in specialist agents.
- Folding or unfolding a tool group on the Tool Approvals page keeps the list where it is.
- An Excel workbook (.xlsx) attached to a message reaches the assistant as a table, sheet by sheet, so it can read, sum and compare the cells.
- The assistant recognizes an attached PDF, Word file, archive or other binary file and tells you what it can do with it.
- The assistant can list and read the files of a folder attached to a message.
- More terminal commands ask for confirmation before the assistant runs them, among them git commands that pass configuration and package installs with extra arguments.
- A sub-agent stays visible as a pill in the response that started it, from start to finish.
- Tool confirmations appear once, in the carousel above the input, which also collects approvals from sub-agents and earlier responses.
- Mermaid diagrams in an answer stay in place while the answer streams.
- Editing an earlier message brings back the model and the thinking level that request used.
- A file reference in the input stays in place when you edit the text before it.
- Tool servers from the gallery that need a value in their address ask for it when you install them.
- Enabled tool servers are listed first in Agent Customizations.
- Dictation reuses its downloaded speech model after a restart.

### Agent Window

- Compact View in the sessions list shows only the titles and keeps workspace and time in the hover.
- Empty groups and an empty Chats section can be hidden with the Empty Groups filter.
- Sessions and chats are renamed in place with F2, a double-click on the title or Rename in the context menu.
- Show Chat Tabs in the session menu shows the chats of a session as tabs or only the active chat.
- Alt-click on Fork Conversation opens the fork beside the source conversation.
- Workspace headings in the sessions list offer Mark All as Read.
- A session you marked as unread stays unread while it is open.
- Ignore Input Needed on a session is remembered after a restart.
- HTML files open in the integrated browser inside the Agents window.

### Editor

- Wrapped lines can be marked with an arrow at the wrap column, switched on in the editor settings.
- Open With offers Markdown Preview and Markdown Editor for every Markdown file extension.
- Configure Snippets lists the language of the current file first.
- OpenAPI, Arazzo and Overlay JSON files are validated against their public schemas.

### Terminal

- Suggestions in the terminal cover cargo commands and options.

### Appearance

- The active editor tab joins the editor surface with rounded shoulders, and separate rounded pills can be chosen in Settings.
- Toggle buttons such as Match Case show an outline when reached with the keyboard.

### Studio

- Right-click Studio in the Windows taskbar and pick Agents Window to open it directly.
- Keyboard Shortcuts opens in a centered overlay above the editor.

## v1.138.0

### TIA Portal

- Right-click a LAD, FBD or GRAPH block in the Project Explorer and open it in the Automation Compare Tool installed on your PC.
- The F-signature export lists the collective F-signatures of the safety program above the block signatures, on TIA Portal V21 and newer (Pro).
- Comparing an open block with a file shows both sides in the format the block is shown in.
- Large exports finish in about half the time, and Studio stays responsive while they run.
- A large export or import pauses the project search in TIA Portal while it runs, which you can switch off in the settings.
- The Project Explorer appears a few seconds after you connect, with the PLC program first, while the data types, tags, hardware, HMI and library branches fill in behind it.
- A CPU placed inside a device folder shows up in the Project Explorer like any other CPU.
- The F-signature column fills in a moment after you switch it on.
- An Import All that stops early says whether the project has already been saved and what to do next.
- Edit Interface on a source file tab opens the interface of the tab you right-clicked.

### Compare Editor

- Right-click a graphical block in the result list to see both sides next to each other in the Automation Compare Tool.
- Safety blocks have their own filter chips, so fail-safe blocks and data types can be narrowed by kind next to OB, FB, FC, DB, UDT and TAGS.
- The Compare Editor icon opens the editor right away.

### SCADA

- The SCADA icon opens the SCADA page and leaves the side bar as it is (Pro).
- The FUXA instance, the Docker host, the plant connection with its OPC UA security and the send mode are set in Settings under SCADA (Pro).
- The SCADA page shows the FUXA address, the plant connection and the send mode it will use, each with a link straight into the SCADA settings (Pro).
- FUXA in Docker is checked, deployed, started, stopped and restarted, and your symbol folder is staged into it, from Settings under SCADA or the Command Palette (Pro).
- Your own SVG symbols are exported into a FUXA you installed directly, so they appear in its editor after it restarts (Pro).

### AI Chat

- Tool servers configured in the root of a trusted project start on their own, without a separate approval.
- A failing tool server shows its error on its card, with the full text one click away.
- Anything you paste into the chat input becomes an attachment, even a single line.
- Agent Customizations opens straight from the chat view.
- The assistant sees the full content of a file it reads or a search result it finds, in that answer and in later ones.
- A file or folder the assistant names relative to your project is found.
- The assistant opens a graphical LAD or FBD block in the block editor.
- A PLC connection the assistant cannot make is reported as a failure, with the reason (Pro).
- Stopping an answer leaves the conversation as it was.
- GPT-6 Astra is offered with a ChatGPT sign-in and with an API key, with its five thinking levels and image input.
- A thinking level picked for a Claude message applies to that whole answer, and a change takes effect with your next message.
- Mistral reasoning models offer a Thinking Effort control.
- Claude models on OpenRouter and on the Vercel AI Gateway offer a Thinking Effort control.
- DeepSeek V4.1 Flash can be picked in chat and for inline completions, with the thinking levels it supports.
- Qwen3.8 Flash can be picked on the Alibaba Model Studio Token Plan.
- Each Gemini model offers the thinking levels it supports.
- A tool the assistant loads during an answer stays available for the rest of the conversation.
- A message sent after a long tool run with Claude is answered faster.
- How much room a model keeps for its answer, and how much of the recent conversation stays word for word after a summary, can be set for all models or per model.
- A vLLM server started with priority scheduling can be told which priority Studio's requests carry.
- A thinking model served by your own llama.cpp server gets a thinking switch on the Custom provider.
- A conversation that grows too large on Cerebras or Claude is summarized automatically and continues.

### Agent Window

- Long lines can be wrapped in the code and comparison views, switched from the More Actions menu of the editor title.
- The chat tabs and the actions of the selected session can be driven from the keyboard.
- Alt-click on New Session opens it beside the current one.
- A session that was grouped under a heading can be dragged back into its workspace section.
- Picking a recent folder that is missing says so right away and drops it from the list.
- Searching inside a session and attaching files leave out the files your project ignores.
- A pinned session is marked in its toolbar.

### Editor

- An organization block can use its start information, such as Initial_Call or LostRetentive, in its code.
- Typing # inside a block suggests its local tags, and inside an organization block also its start information.
- The start information of an organization block shows its data type on hover, and is coloured and highlighted like the block's other tags.
- An organization block folds like every other block.
- While a block is still missing its end, the blocks after it in the same source keep working, and the quick fix inserts the missing end before the next block.
- Chinese, Japanese and Korean text can be set to take exactly two character cells so it lines up with Latin text.
- Commit messages with umlauts and accents are shown as written in history, blame and the timeline.
- Auto-closing brackets respect a closing bracket that is already there.

### Appearance

- Chat questions and their links stay legible in light and high-contrast themes.
- New colour options cover the window frame, panel borders, resize handles and the status bar of an inactive window.

### Studio

- A progress notification closes itself once its task is done.

## v1.137.0

### Graphical Blocks

<video src="https://anyautomation.ch/video/releasenotes/graphical-blocks-1.137.0.mp4" poster="https://anyautomation.ch/video/releasenotes/graphical-blocks-1.137.0.jpg" autoplay loop muted controls playsinline></video>

[AI Writes Graphical PLC Blocks: LAD and FBD in an IDE (YouTube)](https://www.youtube.com/watch?v=xGkH5kO6tkM)

- A graphical LAD or FBD block can be shown as its networks or as its source text, switched in the block editor.
- An edit typed into the source text of a graphical block, including new elements and network titles, is saved back into the project on TIA Portal V20 and newer.
- The assistant reads, edits and uploads graphical LAD and FBD blocks the same as it works with text blocks, and reports the compile result so it can fix any errors itself.

### Project Security

<video src="https://anyautomation.ch/video/releasenotes/project-security-1.137.0.mp4" poster="https://anyautomation.ch/video/releasenotes/project-security-1.137.0.jpg" autoplay loop muted controls playsinline></video>

[Project Security and User Management for a TIA Portal Project (YouTube)](https://www.youtube.com/watch?v=QxcEWQ22dpc)

- Security settings and user management open from the project tree: the project protection and the password policies on one page, the users, user groups and roles on another.
- Users and the password policies are edited in Studio and written back to the project (Pro).
- Passwords are set from Studio with the project's own password rules checked as you type (Pro).
- Roles and their engineering and runtime rights are edited in Studio, and new roles and custom runtime rights are created and deleted (Pro).
- An unprotected project is given its first administrator and protection from Studio, after a confirmation that this cannot be undone (Pro).
- The assistant reads the security settings, the users, the user groups, the roles and the rights of a project.
- The assistant changes a project's users, its anonymous user and its password settings on request, and previews every change before writing (Pro).
- The assistant creates roles and sets the engineering and runtime rights each one carries (Pro).

### TIA Portal

- A hardware change TIA Portal does not accept is reported with its reason, in the editor and in the assistant (Pro).
- The project library shows whether a type is a faceplate, a script module or a block type, with every version and its state under it.
- A library type opens in its own view with its versions and where it is used.
- A version of a library type is created, released, discarded, set as default and deleted from the project tree (Pro).
- A library type is exported as documents in the formats TIA Portal offers for it, and a type or a new version of a type is imported from documents (Pro).
- The assistant reads the types of the project library, exports and imports as documents the types TIA Portal offers a format for, finds where a type is used, and creates, releases, discards, sets as default and deletes the versions of a type (Pro).
- The Project Explorer shows the networks of the project, with their subnets and the interfaces that sit on them (Pro).
- Subnets of every kind are created and deleted from the Project Explorer and by the assistant (Pro).
- A network interface is connected to a subnet, moved to another one, disconnected and given its address, from the Project Explorer and by the assistant (Pro).
- The Project Explorer shows the IO systems of a network with their controller and the devices assigned to them (Pro).
- An IO system is created and deleted from the Project Explorer and by the assistant (Pro).
- A device is assigned to an IO system, moved to another one and released, from the Project Explorer and by the assistant (Pro).
- The assistant exports the hardware configuration of the project as AML (Pro).
- The assistant exports the OPC UA server interface of a PLC (Pro).
- The assistant reads the attributes of a hardware item (Pro).
- The Project Explorer shows fail-safe PLC data types with their own icon.
- A fail-safe PLC data type opens as editable source on TIA Portal V20 and newer and, with the safety login, is saved back into the project.
- Fail-safe PLC data types stay fail-safe through export and import.
- Fail-safe items that cannot be imported without the safety login are named, with a button to log in (Pro).
- A project that cannot be opened names the reason, and a protected project's password prompt gives up after three wrong passwords.
- An item marked as protected, or kept in a marked folder, is never overwritten by an import, an editor save or the assistant.
- The Compare Editor names why an item could not be compared, for example a block that is not compiled, a project that compiled with errors or a safety program that must be logged in first.
- A file that differs from the project only in its line endings is shown as unchanged in the Compare Editor.
- An import and export profile keeps the data type format choice with its other settings.
- Exported F-signatures are saved as a tab-delimited text file (Pro).
- Exported blocks keep uniform line endings.

### Project Search

- A project opened without TIA Portal is searched: the code of its SCL and STL blocks, and its data blocks, PLC data types and tag tables in the form the editor shows them (Pro).
- The search page opens beside the project tree when a project is open, with or without TIA Portal.
- Replacing in a project opened without TIA Portal keeps the changed blocks for the session, to be exported or saved as files (Pro).
- A fail-safe PLC data type outside a software unit is searched in its source text on TIA Portal V20 and newer, and a match opens it at the matched line.

### WinCC Unified

- The object and property columns of the screen editor can be resized and keep their width.
- A screen and its objects are drawn with their own background and fill colours, including gradients and hatch patterns, and an object without a fill is drawn without one.
- A screen is drawn with the colours, spacing, text weight and line wrapping of its device style, and a caption longer than its object wraps inside it and is cut with an ellipsis.
- A screen on a dark background is drawn in the dark style, and the style can be fixed in the settings.
- The font used for screens can be set.
- A text or graphic bound to a list shows the list's default entry on the screen.
- Trend, alarm, parameter and diagnosis controls on a screen show their bars, axes and table headers.
- A screen window shows the screen it references.
- Graphic views, buttons and switches show their picture on the screen.
- Custom widgets show their drawing on the screen, including ones placed from the installed symbol library.
- A custom widget on a screen is drawn with the colours and the state its configuration sets.
- An HMI export includes the pictures its screens use.
- A screen opened from the export folder shows its pictures and its list entries.
- An exported screen inside a screen folder saves back to its device (Pro).
- Tag tables of a WinCC Unified device open on TIA Portal V21.
- A tag with limits shows its upper and lower thresholds under it in the tag table, and their value and value type can be changed there (Pro).
- The export and import of a WinCC Unified device include its system text lists.
- A tag is renamed in the tag table, an alarm in the alarm editor, and tag tables, alarms, alarm classes, connections, logs, logging tags and OPC UA alarm types from the project tree or their detail view (Pro).
- The alarm editor shows the acknowledgment control tag and the bit numbers of a discrete alarm.
- Alarms created in bulk from a file carry their event text (Pro).
- A text typed for a new alarm in the alarm editor is saved with the alarm (Pro).
- A script module of a WinCC Unified device is created from the project tree and opens right away (Pro).
- A script module opens and saves straight from the project tree (Pro).
- Saving a screen keeps the bindings and event scripts of a control's columns, curves, axes and tool bar elements, and a script binding's trigger type and trigger tags (Pro).
- Bindings and event scripts of a screen object and of its parts are added, changed and removed in the bindings panel of the screen editor (Pro).
- An object palette in the screen editor adds shapes, widgets, controls and containers by click or by dragging onto the screen, with the defaults TIA Portal gives a new object (Pro).
- A faceplate container is added to a screen with the faceplate type and version it shows, picked from the project library (Pro).
- Screen objects are duplicated, copied and pasted, aligned, distributed and brought to the front or sent to the back (Pro).
- A screen can be resized to the display of its device (Pro).
- The plant view of a project and its nodes are shown in the project tree, where a view or a node is created, renamed and deleted and a node takes its plant object type (Pro).
- The plant object tags of a WinCC Unified device are listed under the device with their members and logging tags, and their acquisition cycle, acquisition mode, connection and PLC tag are changed in the detail view (Pro).
- A setting TIA Portal does not keep is reported as not applied.
- A folder of exported text lists imports back complete.
- A comment typed into a tag table lands in the project language the column shows (Pro).
- An empty text property of a WinCC Unified object, such as the comment of a connection, can be filled in from the detail view (Pro).
- The assistant can add, change and remove bindings and event scripts on a screen object and on its parts (Pro).
- The assistant adds a faceplate container with its type, duplicates, aligns, distributes and reorders objects, and resizes a screen to its device (Pro).
- The assistant reads the plant model of a project, creates, renames and deletes plant views and nodes, and changes the plant object tags of a device (Pro).
- The assistant renames tags, tag tables, alarms, alarm classes, connections, logs and audit classes on a WinCC Unified device (Pro).
- The assistant has TIA Portal check a WinCC Unified device, whole or narrowed to one tag table, on every plan.
- The assistant sees every open HMI editor: screens, tag tables, alarm tabs, object details and scripts.
- The assistant lays its changes into the open tag table or alarm editor as unsaved edits you review before saving (Pro).
- The assistant creates discrete alarms from a table of rows (Pro).
- The assistant duplicates and deletes screens of a WinCC Unified device (Pro).
- The assistant finds the tag table a tag belongs to.
- The assistant exports the files of a WinCC Unified device, as exchange documents or as a workbook.
- The assistant imports exported device files back into a WinCC Unified device (Pro).
- The assistant re-words the entries of a system text list and sets the comment and the value range of a text or graphic list (Pro).
- The assistant changes the value and value type of a tag's thresholds and works on a tag's logging tags (Pro).
- The assistant tells which WinCC Unified devices a project holds and which languages it carries.
- The assistant reads the script modules of a WinCC Unified device, changes a line or the whole source, and creates a module (Pro).
- The assistant's summary of a screen lists the interface values of a faceplate instance.
- The assistant names the screen properties the installed TIA Portal version cannot read.

### EPLAN

- A missing EPLAN API Extension module is named as the reason a connection fails, with a link to the documentation (Pro+).
- The variant picker lists only the EPLAN installations that can open a project (Pro+).
- The hardware import from EPLAN into TIA Portal can be started from the chat (Pro+).
- The page list of an EPLAN project is filtered by a page's description as well as its name (Pro+).
- Changes to an EPLAN project take effect immediately and cannot be taken back from Studio (Pro+).

### SCADA

- Generated dashboards connect to PLCs whose OPC UA server requires signing, encryption or a user login (Pro).
- A generated dashboard connects over a direct S7 link, an MQTT broker or OPC UA, with the SCADA page showing the fields each one needs, including the rack and slot of an S7 PLC (Pro).
- On an S7 connection, signals without a fixed hardware address are listed as left out and need OPC UA (Pro).
- On an MQTT dashboard, a read/write signal sends its value back to its topic when you change it from an input field or a button (Pro).
- A signal comment can bind an MQTT signal to a member of a JSON message on a topic, and set which topic it uses (Pro).
- Trend charts keep their history and open already filled (Pro).
- Values show the unit and the decimals noted in the signal comment, and input fields keep entries within the signal's limits (Pro).
- A signal can be marked as an alarm, in its comment or by the assistant, and the dashboard raises it and shows an alarm banner in its header (Pro).
- A screen can show a table of the active alarms with their time, message, group and acknowledgment (Pro).
- An On Send choice on the SCADA page and in the assistant picks whether a send merges into the FUXA project you already have, keeping the screens, devices and alarms you made there by hand, or replaces it (Pro).
- Before a dashboard replaces the project on your FUXA instance, the confirmation tells you how many devices, views and tags are there now (Pro).
- Open FUXA straight from the SCADA page or from the message after sending (Pro).
- A folder of your own SVG symbols is read including its subfolders (Pro).

### AI Chat

- Tool approvals are grouped the way the tool picker groups tools, each group foldable and with one choice in its header setting the approval level for every tool in it.
- An open tag table, alarm tab or object detail view can be attached to a chat turn.
- With a GitHub account signed in, an issue or pull request can be attached to a chat turn from Add Context or by pasting its link into the input.
- A fresh installation starts with the chat assistant ready to use.
- A finished answer folds its working steps away and keeps the final reply in view.
- Scrolling back through a long conversation keeps the request you are reading pinned to the top.
- The permissions button under the input can run the terminal commands the assistant proposes in a sandbox.
- The assistant asks first before changing the files that configure your tools or package sources.
- Agent Customizations lists your instructions, skills, agents, tools and servers as cards and opens the details of each one in the same view.
- Output that a tool returns is shown with the highlighting of its own format.
- The controls under the input stay usable in a narrow panel, and the input keeps its height when those controls change.

### Agent Window

- Starting a session brings the prompt, the model and the folder together in one input.
- The chats of a session are listed under it, each with its own title, status and pending approval, and each can be opened, renamed or removed from there.
- F2 renames what you have selected in the session list, Delete archives a session, and the chat shortcut jumps to the session you are working in.
- The bottom panel keeps its place across restarts, each session returns with the view it had open there, and the side pane keeps its width.
- The chat surface can carry a background, a built-in icon pattern or an image of your own, placed as you choose and kept separately for dark and light themes.
- While screen reader optimized mode is on, a badge in the title bar shows it and turns it off when selected.

### Editor

- A file comparison can be set to inline, side by side or automatic from its overflow menu, and automatic shows which layout it is using.
- A changed image or other binary file stays listed in a multi-file comparison and opens in its own comparison.
- Choosing which editor opens a file keeps that choice for the same kind of file and switches the open file over.
- Wrapped lines stay inside the visible width when a line carries colour swatches, inlay hints or breakpoint markers.
- The integrated browser opens saved web pages, and right-clicking a misspelled word offers corrections and adding it to the dictionary.
- The integrated browser can be set to share one session with the pages the assistant opens, so both see the same signed-in state.
- Dictation keeps the text it heard when you stop and ends a forgotten recording on its own.
- A speech model you downloaded is installed from its archive.

### Terminal

- A terminal in its own window draws box and powerline characters.

### Appearance

- A compact layout density, picked from the settings menu, closes the gaps between the side bars, the panel and the editor to leave more room for content.
- Tabs, headings and icons share one size and weight across the refreshed look.

### Studio

- All new views, dialogs and messages of this release are available in all 14 display languages.

## v1.135.0

### WinCC Unified

- The project tree shows every part of a WinCC Unified device in the order TIA Portal uses: runtime settings, screens, tag tables with their folders, system tags, connections, alarms, alarm classes, historical data, scripts, and text and graphic lists.
- Alarms, alarm classes, connections, data logs, alarm logs, audit trails, logging tags, system tags, OPC UA alarms, text lists, system text lists, graphic lists and the runtime settings open in a detail view listing every property, with read-only values marked.
- Multilingual texts in the detail view appear in the display language, with the other project languages listed below.
- Tree rows show only the checkboxes that apply to them: a screen offers export and protection, an alarm none.
- A very large folder lists its first entries and says how many more the project holds.
- The runtime settings, alarm classes, OPC UA alarms, connections, data logs, alarm logs, audit trails and logging tags can be changed in the detail view.
- A connection offers its comment, communication driver, initial address and startup setting, a log its storage, retention, segment and backup settings, and a logging tag every setting it has.
- The colours of an alarm class are set in the detail view and shown as a colour patch next to the value.
- The start time of a log segment and the time settings of a logging tag are shown in the detail view.
- Double-clicking a single alarm opens its settings and its texts for editing, one row per project language.
- Screens in nested screen folders appear in the project tree and open like any other screen.
- A screen saved to TIA Portal stays in the screen folder it came from.
- Screens can be created, renamed and duplicated from the project tree, in any screen folder; the new or renamed screen is shown and selected, and a renamed screen that is open keeps its editor tab and its unsaved changes.
- Creating, renaming or copying a screen with a name the device already uses is refused.
- Screen folders and tag table folders can be created, renamed and deleted from the project tree; a delete removes everything inside the folder, after a confirmation that names how many.
- The screen canvas draws lines, polygons, circles, arcs, text and buttons as the shapes they are, in the place they sit.
- Lines, polylines and polygons on a screen can be moved like any other object.
- The property panel only offers the position, size and visibility fields the selected object can take.
- Properties TIA Portal does not let you change, such as the screen a screen window opens, are shown as read-only.
- Selecting an object on a screen lists its tag bindings and its event scripts, and a bound tag opens its tag table, also when the tag is a member of a structure tag.
- An IO field shows the tag its value is bound to.
- Saving a screen keeps the tag connections and the value mappings of its objects, and the scripts and events that belong to the screen itself.
- A screen with alarm or trend controls keeps its objects and its scripts when it is saved.
- The save names the parts of the screen it could not write, and those parts carry TIA Portal's default settings afterwards.
- A screen that holds a system diagnostics control exports and saves on TIA Portal V21.
- After a screen is saved or renamed, Studio says how many validation messages TIA Portal has for it, and the Openness Manager output lists each one.
- Saving a screen that was renamed or removed in TIA Portal after it was opened says so.
- Opening or saving a Unified screen on a TIA Portal version without WinCC Unified names the version it needs.
- Tag tables of a WinCC Unified device open in the HMI Tags editor, and the changes save back to the device.
- A Unified tag table also shows each tag's address and whether it is persistent, and on TIA Portal V21 its display name.
- Scripts of a WinCC Unified device open as JavaScript in the editor and save back to the device.
- Discrete alarms, analog alarms and alarm classes of a WinCC Unified device open in an alarm editor, where an alarm can be added, changed and removed, and the changes save back to the device.
- Alarm text is written in the project language you choose, and a panel under the table shows the text of the selected alarm in every project language at once.
- The trigger tag and the alarm class of an alarm are picked from the lists the device already holds, so a typed name cannot point at something that is not there.
- Alarm classes can be added and removed in the alarm editor, and the project tree shows them right away.
- Right-clicking the Discrete Alarms folder offers Create Discrete Alarms in Bulk, which reads a file with name, trigger tag, bit, alarm text and alarm class per line, checks every row and then creates several hundred alarms in one run.
- Data logs, alarm logs, alarm classes and connections can be created from the project tree, and the new object opens in its detail view.
- Alarm classes, data logs, alarm logs, text lists and graphic lists can be deleted from the project tree.
- Unified screens can be exported as Excel workbooks, edited in Excel and imported back; the Import/Export settings pick the format.
- Screens are exported into the screen folders they have in the project and imported back into them; a screen that is missing on the device goes back into the folder it was exported from.
- Tag tables that sit in a tag table folder are exported and imported with that folder.
- Empty screen folders and tag table folders of a WinCC Unified device appear in the export folder as well.
- Exported tag tables, scripts, text lists and graphic lists are listed in the export-folder tree.
- Importing HMI items from a folder also picks up the WinCC Unified export files.
- The assistant answers questions about a WinCC Unified screen from a short overview of the screen and the tags it uses.
- The full properties of a single object on a Unified screen are read on request.
- The assistant answers questions about the tags, alarms, alarm classes, connections, text and graphic lists and logs of a WinCC Unified device, and reads the full properties of any of them by name.
- On a device with thousands of tags the assistant's list can be narrowed by name or by tag table, and it says how many entries it left out.
- The assistant reads the entries of a text list or a graphic list, with the value or the range each one covers and the text in every project language or the graphic it shows.
- The assistant changes single objects on a Unified screen, moving, resizing or renaming them, changing their text and adding or removing them, and every object it does not name stays as it was.
- While the screen is open in the editor, the change the assistant makes lands there unsaved, so you see it before it goes into the project.
- The assistant creates and renames screens on a WinCC Unified device, and creates, renames and deletes screen folders.
- The assistant adds, changes and removes the tags, tag tables, alarms, alarm classes, connections, data logs and alarm logs of a WinCC Unified device, changes its audit trails, and asks before each change, naming the device and the objects it touches.
- The assistant adds, changes and removes the entries of a text list or a graphic list, creates a list that is missing, and asks before each change.
- The assistant removes text lists and graphic lists of a WinCC Unified device after asking first; the list's entries go with it, and a screen object that shows the list is left as it is.
- The assistant reads and changes the runtime settings of a WinCC Unified device.
- The assistant can have TIA Portal check a WinCC Unified device and report what it objects to, without changing anything.
- Creating, changing or deleting anything on a WinCC Unified device is part of the Pro plan and unlocked during the free trial; reading and exporting stay available on every plan.

### TIA Portal

- Screens, tag tables and lists of an HMI device inside a device folder open like any other.
- Right-clicking a TIA project file or archive in the file explorer offers Open with Openness Manager.
- Archived projects (.zap15 - .zap21) open from the file explorer and from the Open TIA Project dialog: pick a target folder and the project is restored there and opened.
- Password-protected archives ask for the project user name and password, the same way protected projects do.
- Closing a screen, HMI tag table, interface or block editor with unsaved changes asks whether to save them.
- Edits made in an HMI tag table save back to the device.
- When TIA Portal goes away during an operation, also while a screen is loading, the message names what was interrupted and offers Reconnect.
- Report Issue can also attach the detailed Openness Manager log and a record of lost TIA Portal connections.
- Connecting to TIA Portal V21 works right after installation, without a confirmation prompt.
- Every row in the project tree offers Copy Name and Copy Path, and a folder offers Refresh This Folder, which reloads that part of the project and keeps the tree expanded as it was.

### AI Chat

- Switching to a specialist agent from the chat agent menu applies its role and tools to your next message.
- An HMI Engineer specialist for WinCC Unified devices is available in the chat agent menu.
- Editing an earlier message asks before your typed changes are discarded, and slash commands are suggested while you edit.
- Searching the conversation steps through the matches starting at the newest one.
- Reasoning output keeps its formatting, and its header stays in place while the answer streams.
- Every MCP server appears only once in the tools list, each tool names the server it belongs to, and a failing server opens its log with one click.
- When a request fails, the message names the reason: a rate limit, a rejected request, an account out of credit, a problem on the provider's side, an unreachable provider, a conversation that no longer fits the model, or too many tools for the model, and keeps the provider's own details.
- When every tool is switched off in Configure Tools, the chat says so and offers to open Configure Tools.
- Google Gemini connects with a Gemini API key entered on its provider card; the Google account sign-in and the Antigravity provider are retired.
- A Gemini API key of the wrong type is explained with a link to create the right one.
- Claude Opus 4.8, Sonnet 5 and Fable 5 offer the Extra High and Max thinking levels.
- MCP tools work on the Claude Pro/Max sign-in.
- The ChatGPT model list shows the models your account can use.
- Grok 4.6 offers the Extra High thinking level, and OpenAI models can switch thinking off.
- Claude 4.6 and newer models on OpenRouter work in agent mode.
- Kimi and Moonshot models can use the chat tools, and their usage shows cached input.
- Z.AI, MiniMax, Moonshot AI, Ollama and Kimi Coding models offer a Thinking Effort control.
- Gemini 3 models work in agent mode, and Vertex AI offers the Gemini 3 models.
- LM Studio, vLLM and SGLang accept the server address with or without the API path.
- Long agent tasks on Mistral, Fireworks, OpenRouter and Cloudflare AI Gateway reuse the prompt cache.
- Alibaba Model Studio Token Plan is available as a provider, and the suggested model lists for DeepSeek, Z.AI, MiniMax, Alibaba, OpenRouter, Vercel, xAI and Kimi name the current models.
- Two open Studio windows share one provider sign-in, and when another tool takes over the same sign-in Studio asks you to sign in again.
- When the provider stops responding or returns an empty reply, the chat says so.
- A thinking model can be chosen as the conversation summarization model.
- Configure Tools lists the TIA Portal tools in five groups, all switched on to begin with: projects, blocks, hardware, WinCC Unified screens and objects, and WinCC Comfort and Advanced screens.
- A tip above the chat input suggests switching off the tools you do not use in Configure Tools to save tokens.

### Agent Window

- The session view and its editors share one pane with a single tab bar, leaving more room for the conversation.
- File comparisons pick the layout that fits: side by side when there is room, inline when the pane is narrow, with an option to always stay inline.
- The session header puts the title first and moves secondary actions into an overflow menu.
- While the assistant works, pills above the input show what the turn is doing, and the turn's file changes stay one click away; the pills can be hidden.
- Studio notifies you through the system when a session finishes, fails or needs your input while the window is in the background.

### Editor

- Holding Alt offers Close Others only on the tab under the mouse, and not at all when a group holds a single tab.

### Appearance

- The refreshed look gains further polish: clearer activity-bar states, a slimmer status bar and restyled notifications.
- The file explorer heading keeps the exact casing of your workspace name.

### Studio

- Automatic updates wait while you are on a metered connection and resume on their own once you are back on an unmetered one.
- Uninstalling Studio on Windows also removes its log files.
- Other extensions you install must ask once before they may use the Studio tools, run its automation or read its protected content on your behalf, and you can withdraw that access at any time from the Accounts menu.

## v1.134.2

### Project Search

<video src="https://anyautomation.ch/video/releasenotes/project-search-1.134.2.mp4" poster="https://anyautomation.ch/video/releasenotes/project-search-1.134.2.jpg" autoplay loop muted controls playsinline></video>

[Search and Replace Across a Whole TIA Portal Project (YouTube)](https://www.youtube.com/watch?v=f_UsWdy0OoY)

- A Project Search icon in the activity bar searches the content of every block in the connected TIA project.
- Clicking the icon opens the search page on the right, the project tree stays visible on the left.
- A replace line under the search box turns the page into project-wide search and replace.
- Replace All changes every shown match outside tag tables and graphical blocks after a confirmation, imports the changed blocks and runs the search again as verification.
- Matches also replace one by one: the block opens beside the search with the change ready to review, and saving it imports the block.
- Arrow buttons in the replace line jump from match to match, and the Replace button changes the current match and moves on to the next.
- PLC tag tables are searched too: tag names, data types, addresses, comments and user constants; a click opens the tag table.
- Matches narrow by block type (OB, FB, FC, DB, UDT, Tags) and to hits in the interface or in the code, with counts on every filter.
- Picking type filters before searching prepares only the selected types, which makes the search faster.
- Graphical blocks (LAD, FBD, GRAPH) are searched through their text form on TIA Portal V20 and newer.
- Match case, whole word and regular expressions refine the query.
- Every match shows its line with the hit highlighted, and a click opens the block at that line.
- Results group per block and start collapsed as an overview; expand a block for its matches, or expand and collapse all at once.
- A right click on a result offers Open, Open to the Side, Reveal in Project Explorer, copying the line, name or path, and removing the entry from the results.
- The first search prepares the project and can take a moment; repeat searches only pick up changed blocks and are fast.
- While a search runs, a counter over all blocks and the elapsed time are shown beside the project tree, and the counter in the status bar.
- Searching is included from the Basic plan; replacing needs the Pro plan.

### Compare Editor

- The status counts above the comparison list are filters: click Changed, Only in either side, Unchanged or Inconsistent to narrow the list to that status, click again to release it.
- A new Does not exist filter narrows the comparison list to every item that is missing on one side.
- In a folder comparison every block shows its type icon and counts under its type filter.
- Choosing Project to Folder asks which folder to compare against: your export folder, or any folder you pick.

### TIA Portal

- When attaching to a running instance or switching between instances, each entry shows the project's file path, so two projects with the same name are easy to tell apart.
- Find Unused recognizes a data block created from a PLC data type as a use of that type.

### Studio

- General improvements.

## v1.134.1

### AI Chat

- The tool picker, the expert agents and the skills come ready for your plan, and an upgrade takes effect right away, with no restart and no setup.

### Studio

- General improvements.

## v1.134.0

### Compare Editor

<video src="https://anyautomation.ch/video/releasenotes/compare-editor-1.134.0.mp4" poster="https://anyautomation.ch/video/releasenotes/compare-editor-1.134.0.jpg" autoplay loop muted controls playsinline></video>

[Compare Two TIA Portal Projects Block by Block, and Merge the Difference Back (YouTube)](https://www.youtube.com/watch?v=gi87Uq_gyDs)

- A Compare icon in the activity bar compares your project against a second project or your export folder, with source and target changeable in the editor.
- The comparison list shows both sides next to each other, and a side an item is missing on says so.
- A name filter above the list narrows it while you type, and the folder structure can be switched off for a flat list.
- A shield button hides all safety blocks from the comparison list.
- Each row shows who last changed the block and when, with author and both timestamps in its tooltip.
- The comparison list can also be narrowed to tag tables, and tag tables carry their own icon.
- The comparison list starts with nothing selected; you tick the entries you want to import or copy.
- The column dividers can be dragged to re-proportion source, status and target, each one moving only the two columns it separates, and the widths are remembered.
- The target side of a project comparison can be edited and saved straight from the diff, including taking a change over from the other side.
- Included from the Basic plan.
- Each row in the comparison list shows the icon of its block type.
- The comparison list can be narrowed to OB, FB, FC, DB or UDT, with a count per type.

### Commissioning Report

<video src="https://anyautomation.ch/video/releasenotes/commissioning-report-1.134.0.mp4" poster="https://anyautomation.ch/video/releasenotes/commissioning-report-1.134.0.jpg" autoplay loop muted controls playsinline></video>

[FAT and SAT Protocols Without the Paperwork: Live IO Checks, Signed and Exported (YouTube)](https://www.youtube.com/watch?v=VsYjdSAuV_o)

- Create FAT/SAT acceptance reports from the open TIA project: the report collects stations, modules, network data and an IO checklist, you tick off each point during commissioning, and export a print-ready HTML or PDF document with your company data on the cover and your own footer line, editable per report, on every PDF page (Pro+).
- With a connected PLC the report also captures the CPU's actual state: serial number, firmware, protection level, memory usage, cycle times and the diagnostic buffer, with deviations between project and CPU highlighted (Pro+).
- The IO checklist can run live against the connected PLC: it shows live values, points you actuate on site are ticked off automatically with your name and time, and outputs can be set from the list after a confirmation (Pro+).
- A Commissioning icon in the activity bar lists the reports in your working folder; one click opens a report, a plus button creates a new one.
- Function test checklists can be filled from the project: a filter picker lists the functions and function blocks of every PLC, and each added function shows its author plus creation and last-change timestamps (Pro+).
- Every test step can state the expected result next to the observed remark.
- Analog IO points take a target and a measured value, and during a live check one click captures the current value (Pro+).
- A result summary shows totals for the IO checklist, function tests and deviations, on screen and in the exported document.
- A commissioning diary records what was done on which day and prints with the report.
- A participants list on the cover page gives every attendee a personal signature block in the exported document.
- Reports can be finalized: a finalized report is locked and exports without the draft watermark, and reopening it asks for a reason that lands in the revision history.
- Photos can be attached to an IO point, a function test, a deviation or the report itself, from the appendix or straight from the row you are working on; they print as captioned figures in the report's appendix.
- An enclosures list names the external documents that belong to the report, such as the safety printout, and prints in the appendix.
- Function test checklists can be saved as a template and added to any other report, with a ready-made template for alarm and message tests included.
- A site acceptance can take over the results of an earlier report, either everything recorded or only the passed points so the rest stays open for the re-test; what was already checked on site stays as it is, results of a block or safety program whose recorded version differs between the two reports stay open as well, the revision history names the report the results came from, and a report from another project asks first.
- One click adds a prefilled test checklist for every fail-safe runtime group of the project, with its signature recorded (Pro+).

### PLC Online

- A PLC connection stays up while you work in another tab, and the status bar keeps showing how many connections are live.
- A CPU panel that cannot be read says so on its own tab and offers Retry, and a CPU without a diagnostic buffer says that plainly.

### TIA Portal

- Standard blocks whose names begin with F_ export with their SCL or STL source and keep their regular block icon; only fail-safe blocks are shown and exported as safety blocks.

### SCADA

- Input fields on generated FUXA screens accept typed values and show live values.

### Unit Testing

- The command-line test runner needs a licence file, which you save from the Generate CI Pipeline dialog (Pro+).

### AI Chat

- Ctrl+F searches the whole conversation and steps through the matches, with match-case, whole-word and regular-expression options.
- In a long conversation the prompt you scrolled past stays pinned at the top of the chat, and a click on it jumps back to it.
- Expanded terminal output re-wraps to the width of the chat as you resize it.
- Agent plugins install from the Extensions view or a local folder and bring their agents, commands, rules and MCP servers into the chat.
- Press the microphone in the chat input to dictate your message; speech is turned into text on your machine, and the speech model downloads once at first use.
- The assistant can read your hardware configuration and draft the descriptive text for a commissioning report from real project data.
- The TIA, EPLAN, Visual Context and Commissioning tools follow the approval level you set for them without exception: Allow in This Session or Always Allow lets a tool run without asking again, Always Deny refuses it without a card.
- Once you let the chat approve tool calls for you, the live PLC, Forge, SCADA and CODESYS tools run without asking as well; leave the chat on its default approval setting to keep being asked.
- On a confirmation card the highlighted button allows the tool for the rest of the session; pick Allow Once from the card to let it run a single time.
- The assistant can read and fill a commissioning report: cover data, test checklists and steps, results with remarks and measured values, deviations, diary, participants, photos and templates, and it can collect project data and export the document (Pro+).

### Agent Window

- A timeline beside the conversation marks each of your prompts: hover it to list them, pick one to jump back, and prompts that changed files show how many lines were added and removed.
- A session can hold several chats: open another with the plus button, drag the tabs to place chats side by side or below each other, and the arrangement comes back when you return to the session.

### Editor

- Start Dictation in Editor and the terminal's Start Dictation command dictate into the active editor or terminal.
- When a file can be opened in more than one way, a picker in the breadcrumb bar switches between them and can set your choice as the default.
- A Markdown file can open as a formatted document, in reading mode until you switch it to editing; the Agent Window opens Markdown that way by default.
- A Markdown comparison can be switched to the formatted view, with added, changed and deleted content marked in the margin.
- A local HTML file opened in the integrated browser refreshes whenever the file changes, and the integrated browser can be set as the default editor for HTML files.
- In the integrated browser you can pick elements on the page, add a comment to each and send them to the chat.
- Holding Alt turns a tab's close button into Close Others, so one click closes the other editors in that group.

### Terminal

- The size overlay shown while resizing a terminal can be switched off in the settings (Terminal, Resize Dimensions Overlay).
- With a screen reader, your reading position in the terminal's accessible view stays where you left it as new output arrives, once you choose Always in the settings (Terminal, Accessible View Preserve Cursor Position).

### Appearance

- Studio opens with the refreshed look: the side bars and the bottom panel appear as floating cards with rounded corners; the classic layout stays available in the settings (Workbench, Modern UI).

### Settings

- A new Company Profile page stores your company name, address, logo and default commissioning engineer for generated reports.

### Licensing

- PLC Online over S7 is part of the Pro plan and unlocked during the free trial.
- Online commissioning, the commissioning report, Unit Testing and Hardware Simulation are part of the Pro+ plan, all unlocked during the free trial.
- Enterprise accounts can use PLC Online over S7, online commissioning, Forge, EPLAN and Hardware Simulation.
- Studio keeps running on your licence when the licence service cannot be reached.
- A renewal payment that is still being confirmed does not interrupt your work.
- An organization seat you accept in the browser is active as soon as you return to Studio.
- Organization members see their machine switches in the License window and can release a machine on their account page.
- When your licence is bound to another machine, the License window tells you what to do next.

### Studio

- Every scrollbar in the AnyAutomation views, dialogs and reports follows the colour theme.

## v1.130.4

- AI Chat – long conversations keep getting full answers.
- AI Chat – every model in the picker can answer your messages.
- AI Chat – the model picker shows your provider's full list of models.
- AI Chat – each model shows its true context size.
- AI Chat – each model offers the thinking depth levels it supports, including off.
- AI Chat – you can watch a reasoning model think on many more providers.
- AI Chat – an answer that was cut off, refused or blocked tells you so.
- AI Chat – the assistant keeps going through a brief connection problem.
- AI Chat – the assistant can run several actions at the same time.
- AI Chat – conversations with emoji and special characters keep working.
- AI Chat – the assistant sees an image a tool returns, whichever model you use.
- Inline Chat – every model edits the file directly.
- AI Chat – with an xAI connection, your prompts and replies are not kept on the service.
- AI Chat – the model picker offers the latest Gemini Pro, Flash and Flash Lite.
- AI Chat – Kimi Coding answers your messages.

## v1.130.3

- AI Chat – every Studio tool sits under one AnyAutomation Studio Tools entry in the tool picker, grouped into categories with an on/off switch per category.
- AI Chat – every tool the assistant can use has exactly one entry in the tool picker, and switching it off keeps it off.
- AI Chat – the tool picker offers only the tool categories your plan covers, for example SCADA and OPC UA with the Pro plan, EPLAN and Forge with the Pro+ plan.
- Agent Window – tool switches in the Tools list apply to the session.
- AI Chat – the assistant sees images and screenshots you attach, throughout the conversation, and more models let you attach them.
- AI Chat – every message uses noticeably less of your quota, most of all in small conversations.
- AI Chat – consulting a specialist uses far less quota, and asking the same specialist again costs less still.
- AI Chat – conversations with large attached files stay fast.
- AI Chat – a conversation that outgrows the model's context window, or the Context Size you picked for it, is summarized automatically and continues.
- AI Chat – with automatic summarization turned off, an oversized chat tells you how to continue.
- AI Chat – Claude models with a large context window use their full window by default.
- AI Chat – changing a local AI model's context size takes effect on your next message.
- AI Chat – when a reply fails, the chat shows the reason the AI provider reported.
- AI Chat – the token numbers in Session Info match the provider's own count.
- AI Chat – signed in with a Claude or OpenAI account, a provider icon in the status bar opens a usage overview with your plan, your session and weekly limits, and when each one resets.
- AI Chat – an expired Claude sign-in can be renewed with Sign In on the provider card.
- AI Chat – the Auto entry appears in the model picker only while signed in to GitHub Copilot.
- SCL editor – valid code shows far fewer wrong error markers.
- SCL editor – renaming a local variable changes only that variable.

## v1.130.2

- SCADA – included in the Pro plan.
- SCADA – the plan notice shown on SCADA actions names SCADA as the feature to unlock.

## v1.130.1

- Terminal – the integrated terminal opens and runs commands again.
- AI Chat – the first chat reply starts right away even while a project export or import is running.
- AI Chat – pressing Stop also cancels a TIA action the assistant is waiting on.
- AI Chat – the conversation keeps working after you stop the assistant during a tool action.
- TIA Portal – when no working folder is set, temporary files are kept in the computer's temporary folder and never appear in the opened folder.
- TIA Portal – when no working folder and no export target are set, exports go to an AnyAutomationStudio folder in your user profile.

## v1.130.0

- Unit Testing – exported test reports and comparison reports show all run details; needs the Pro plan.
- Unit Testing – Export Report and generated CI pipelines write the JUnit XML file; needs the Pro plan.
- Unit Testing – Generate CI Pipeline lists every existing file it will replace and asks for confirmation before writing; needs the Pro plan.
- Unit Testing – Build Matrix cells you add or edit in the Generate CI Pipeline dialog are kept; needs the Pro plan.
- AI Chat – an AI workflow can run any number of specialist agents at once, set on the Workflows card of the Tool Approvals page; needs the Pro plan.
- Settings – number fields apply their value when you press Enter or leave the field.
- Community – Join Us on YouTube in the Help menu opens Studio's channel with short feature videos.
- TIA Portal – any number of projects can be connected at the same time.
- TIA Portal – the shown number of connected projects always matches the projects you have open.
- Agent Window – the assistant loads its programming reference guides when working with PLC code.
- Languages – all 14 display languages are fully translated, with more natural wording.

## v1.128.5

- TIA Portal – disconnecting from a project takes effect right away.
- TIA Portal – switching back to an already open block tab is instant, and saving a block starts faster.
- AI Chat – the assistant can run larger multi-step jobs that fan out work to several specialist agents, with live progress, a confirmation before it starts, and a cap on how many agents run at once; needs the Pro plan.
- AI Chat – a new Ultracode switch in the model menu lets the assistant run larger multi-step jobs on its own without confirming each one; works on any model, needs the Pro plan.
- AI Chat – long conversations run into connection errors less often, and specialist requests cost less.
- AI Chat – the assistant corrects and completes failed actions more often.
- AI Chat – the assistant tells user constants and tags apart more reliably, and edits comments in your project's editing language, keeping comments in other languages intact.

## v1.128.4

- TIA Portal – technology objects can be created, edited and deleted from the project tree and from AI chat, and most types open as editable XML.
- PLC Online – a certificate warning when connecting appears only if the controller's certificate has changed.
- PLC Online – a certificate mismatch offers the Forget Pinned Certificate action, and a failed retry after forgetting shows a clear error message.
- TIA Portal – Import All finishes much faster on large projects.
- AI Chat – the assistant can create, edit and delete user constants in tag tables, and edit existing tags.
- AI Chat – the assistant sees tag comments when it reads tag tables.
- AI Chat – sign-in works with more MCP servers.
- SCADA – the assistant proposes a structured SCADA with an overview, one screen per plant module, gauges, indicators, buttons and navigation.
- SCADA – you can use your own symbol as an on/off switch that is bound to a variable and changes color between its off and on states.
- SCADA – navigation on generated screens only leads to screens that exist.
- SCADA – fault lamps on module screens show the same colors as the overview tiles.
- Licensing – Enterprise organization members see their plan as Enterprise.
- Licensing – Studio starts and keeps working offline after you have signed in once, and offers an offline option when the licensing service can't be reached.

## v1.128.3

- AI Chat – every action the assistant runs is shown live in the chat, labeled with what it was asked to do, and finished actions expand to their full details.
- TIA Portal – the project-wide reference search now finds PLC constants, including their uses as array limits in data types, and also covers safety and software-unit blocks.
- TIA Portal – searching for an exact name in the project-wide reference search is now fast even on large projects.
- TIA Portal – cancelling a project-wide reference search stops it right away.
- AI Chat – delegated research agents can now search and read the project.
- AI Chat – the assistant rereads its earlier results without a confirmation prompt.
- AI Chat – the Session total in the context details shows an accurate token count.
- TIA Portal – when TIA Portal closes, its connection disappears from Studio and a notification names the disconnected project.
- TIA Portal – temporary files are kept in a tmp folder inside your working folder.
- TIA Portal – Export as JSON also exports PLC data types (UDTs) with their full member structure, default values, comments, external access and setpoint marks, from the right-click menu or the export checkboxes.
- TIA Portal – interface views show the comments and default values defined in the underlying PLC data types for nested members.
- SCADA – the SCADA page can propose a screen plan from the selected signals: an overview with navigation tiles, one screen per plant module, and detail screens for large groups.
- SCADA – screen plans can be renamed, reordered, merged, saved and loaded, and Generate and Send builds the planned multi-screen project.
- SCADA – every planned screen can carry an SVG background image such as a plant picture, with unsafe content removed automatically.
- SCADA – a folder of SVG symbols can be staged into FUXA as its own symbol library and used when editing the generated screens.
- SCADA – the SCADA page scrolls all the way down to its full content.
- Languages – all feature text is now translated in all 14 display languages.

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
