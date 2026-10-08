# Search Job Scheduler Prompt Tool

Turn your preferences and a Google Sheet link into **two complete scheduler prompts**: one discovers companies, the other finds matching jobs at those companies. Generate once, copy both prompts into your scheduler, and regenerate whenever your preferences change.

No Python installation or API key is needed to use this Markdown skill. You need an AI that can read these files. Running the resulting tasks also requires web access and a Google Sheets connection with read/write capabilities in that task's environment.

## Quick start

1. Download this repository. Open it with your AI coding assistant, or upload `SKILL.md`, `profile-example.md`, both files in `templates/`, `references/google-sheet-contract.md`, and `tests/acceptance-cases.md` to a file-capable chat, keeping their names identifiable.
2. Browse the [example profile](profile-example.md). Use it unchanged, edit a local copy, or describe your preferences in chat.
3. Provide a Google Sheet link; a new empty Sheet is enough. The AI checks it, creates **Companies**, **Open Jobs**, and **Runs** if missing, and adds headers to empty target tabs. Compatible existing data and unrelated tabs are preserved. Authorize a Sheet-capable connection if requested. No pre-existing company list is required.
4. Ask your AI:

   > Read SKILL.md, prepare my Google Sheet, and generate both scheduler prompts. Use the example profile. My Google Sheet is [paste your link]. Use Companies, Open Jobs and Runs as the tab names. Save the outputs in this project's output/ directory. Do not run the searches or create schedules yet.

5. Open the generated files and copy **each file's entire contents** into its own scheduler task. Complete the connection setup below before enabling recurring runs.

For a personal profile, you can instead say:

> Generate both prompts for frontend roles using React and TypeScript, 5 years of experience, based in New York, strictly US remote. Remove conflicting backend defaults. Use my Sheet link and keep the remaining example preferences where relevant; tell me what you retained.

## Where the files go

```text
local/profile.md                       Your resolved preferences (private)
local/settings.md                      Sheet link, tab names, timing (private)
output/find-companies-prompt.md         Copy all into the company task
output/find-jobs-prompt.md              Copy all into the jobs task
```

Paths are relative to this project's root, not the assistant's working directory. The AI should return clickable output links. If the chat cannot write to your computer, it supplies same-named downloads or two clearly labeled copyable text blocks. The generated prompts contain their own rules and preferences; your scheduled tasks do not need access to this repository.

No profile supplied? The AI uses the example and tells you. No Sheet link supplied? It can provide an explicitly labeled draft, but not a completed binding.

The one-time setup is safe to repeat: already compatible tabs are reused without rewriting them. If an existing populated tab has incompatible headers, the AI asks how to map them. If the environment lacks a Sheet write tool or permission, prompts can still be generated with setup marked pending; connect an appropriate tool to complete setup. Manual [header preparation](references/google-sheet-contract.md#headers) is an optional fallback, not the normal workflow. An explicit generate-only request skips Sheet writes.

## What you can customize

[profile-example.md](profile-example.md) is a readable, sanitized backend/cloud example: roughly 4 years of experience, Python/Terraform/AWS/database/ETL strengths, US roles, remote preferred and Houston as home area. It includes editable company preferences, scoring weights, role filters and alert thresholds. Unknown legal eligibility stays unknown.

Change the file or chat with the AI. Explicit preferences override saved profile settings; the example fills remaining gaps. Company size and Tier are separate. Score weights and numeric location ratings are editable examples, not objective hiring standards.

Ask to regenerate both prompts after changing your profile, Sheet tabs or field mapping, then replace both scheduler prompts. Updating a local profile alone does not update existing schedules.

## Connect and schedule

1. Connect a Google Sheets-capable tool in the chat/environment where the tasks will run and authorize access to your Sheet. A URL or “anyone can edit” sharing setting does not install a write tool or grant a connector account access automatically. You do not need to make a private Sheet public.
2. The generation assistant reports that it created or reused the three tabs. Verify the actual task environment can read them using its own connection; setup in one chat does not grant another environment access.
3. Create a company-discovery task with the full company prompt. Suggested default: **daily at 08:00 America/Chicago**.
4. Create a job-discovery task with the full jobs prompt. Suggested default: **hourly**, using the same timezone. Run company discovery first so there are Active companies to scan.
5. Review initial runs. Jobs performs an initial baseline without individual new-job alerts, then highlights new qualifying jobs. Every run returns a short chat summary; platform notification settings control push delivery.

In ChatGPT, use **Scheduled** to manage tasks and verify the prompt, time, timezone and connected tools. Web tasks can use tools available to their chat but cannot directly access your local repository. Availability depends on the environment and its permissions; successful generation does not establish unattended write access. See the [official scheduled-task documentation](https://learn.chatgpt.com/docs/automations).

The tool does not create schedules itself. No universal prompt-length limit is assumed: confirm the complete text is accepted by your scheduler. If it is too long, ask the AI to compact it while preserving filters and storage rules; do not truncate it or replace rules with local file references.

## How the two tasks cooperate

- **Companies** stores company identity, priority Tier, personal score and tracking Status. New strong matches become Active under the example policy; you can change a company to Watch or Ignore, which subsequent runs preserve.
- **Open Jobs** stores verified openings linked by Company ID, scores, evidence and your review decisions. “First Seen” is distinct from the employer's posting date.
- **Runs** stores what each run actually completed. Jobs targets all Active companies each run and reports failures and unfinished companies. Large lists may exceed one run's capacity; it does not pretend that full coverage was achieved.

Both tasks deduplicate before writing and preserve human notes/statuses. A website failure is not evidence that a job closed. Baseline inventories, reopened roles and score changes are not newly discovered-job alerts. Sheet writes and chat delivery cannot guarantee exactly-once notifications.

## Install as a skill (optional)

Ask a skill-capable assistant to install the **whole repository folder** as one skill, following that environment's installation conventions. The root `SKILL.md` is the entrypoint; keep its relative resource files together. For assistants using workspace instruction indexes, ask them to add one pointer to this root skill. No installation is necessary if you explicitly ask the AI to read the files.

Different assistants may generate these text prompts; this does not imply every assistant provides a scheduler or a Google Sheets write connection.

## Privacy and maintenance

The public example has no contact details, credentials, real Sheet IDs or local machine paths. `local/` and `output/` are Git-ignored because they hold your actual preferences and bindings. Do not upload those folders when sharing the tool. Keep credentials in your provider's connection flow, not in a profile or prompt.

Maintainers: use the [acceptance cases](tests/acceptance-cases.md) to review generation behavior. They distinguish prompt checks, Sheet integration and actual scheduled execution; none is a substitute for the others.

## 中文快速开始

1. 下载整个项目，把文件交给 AI，并让它读取 `SKILL.md`。
2. 浏览 `profile-example.md`：不提供个人资料时使用这个示例；也可以直接说出自己的岗位、技术、地点和公司偏好。
3. 提供自己的 Google Sheet 链接，空表即可。AI 会自动检查并创建缺少的 Companies、Open Jobs、Runs tabs 和表头；已有兼容数据会保留，不需要手工粘贴。需要连接授权时，按提示完成即可。
4. 把链接给 AI，让它生成两份 prompt。文件固定放在根目录的 `output/` 中，每份全文复制到一个 scheduler。
5. 在真正运行任务的环境中连接并授权 Google Sheets。默认公司发现每天美中时间早上八点、职位发现每小时一次；频率可以修改。
6. 修改个人偏好后，让 AI 重新生成两份文件，并替换定时任务中的旧 prompt。单独修改本地 profile 不会自动影响已经建立的任务。

这是一次性的 prompt 生成工具。你使用的 AI 是否能运行定时任务、访问网站和写入表格，需要在实际运行环境中确认。生成完整文件与验证真实定时运行是两个不同的结果。

## License

[MIT](LICENSE).
