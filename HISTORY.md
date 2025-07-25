# Release history

### main branch

- Added support for Grok-4 via `xai/grok-4` and `openrouter/x-ai/grok-4` model names.
- Added support for `gemini/gemini-2.5-flash-lite-preview-06-17` model, by Tamir Zahavi-Brunner.
- `/clear` now prints “All chat history cleared.” so you know it worked, by Zexin Yuan.
- `/undo` output now shows only the first line of each commit message, making it easier to read.
- Fixed an issue where new settings for an existing model didn't replace the old ones, by Andrew Grigorev.
- Aider wrote 0% of the code in this release.

### Aider v0.85.1

- Display model announcements with no-arg `/model` command.
- Aider wrote 0% of the code in this release.

### Aider v0.85.0

- Support for Responses API models like o1-pro, o3-pro.
- Updated pricing for o3.
- Added support for new Gemini models including `gemini-2.5-pro`, `gemini-2.5-flash`, and `gemini-2.5-pro-preview-06-05` with thinking tokens support.
- Updated model aliases: `flash` now points to `gemini-2.5-flash` and `gemini` now points to `gemini-2.5-pro`.
- Added `--add-gitignore-files` flag to enable adding files listed in .gitignore to Aider's editing scope, by omarcinkonis.
- Added `--commit-language` option to specify the language for commit messages, by Kyosuke Takayama.
- Enhanced thinking tokens support: can now be disabled by setting to 0, and improved help text with examples.
- Added MATLAB language support for repository maps, by Matthew Tofano.
- Added support for OpenAI o3-pro model across multiple providers.
- Improved GitHub Copilot token handling with better validation and error messages, by Vincent Taverna and Sebastian Estrella.
- Fixed encoding issues in git diff output and LLM history logging.
- Enhanced commit message generation to use system prompt prefixes, by Luke Reeves.
- Improved inline code rendering in Rich markdown output, by Vamsi Talupula.
- Fixed Vertex AI model name prefixes in settings, by Wietse Venema.
- Improved `/read-only` command to resolve literal paths correctly, by Matteo Landi.
- Skip expensive file tracking operations when `--skip-sanity-check-repo` is enabled for better performance, by Makar Ivashko.
- Ensure pip is available before package installation.
- Auto-create parent directories for chat history files to prevent startup errors, by contributor.
- Fixed search block regex to accept optional closing tags when working with HTML content, by Mathis Beer.
- Co-authored-by attribution is now enabled by default for commit messages.
- Added Clojure language support for repository maps, by Garrett Hopper.
- Added custom PostHog analytics configuration options with `--analytics-posthog-host` and `--analytics-posthog-project-api-key` flags, by Vasil Markoukin.
- Optimized chat history summarization performance, by jayeshthk.
- Improved kebab-case identifier recognition in repository maps for better code analysis.
- Increased max tokens for Deepseek models to 65536 for better performance.
- Aider wrote 21% of the code in this release.

### Aider v0.84.0

- Added support for new Claude models including the Sonnet 4 and Opus 4 series (e.g., `claude-sonnet-4-20250514`,
`claude-opus-4-20250514`) across various providers. The default `sonnet` and `opus` aliases were updated to these newer
versions.
- Added support for the `vertex_ai/gemini-2.5-flash-preview-05-20` model.
- Fixed OpenRouter token cost calculation for improved accuracy.
- Updated default OpenRouter models during onboarding to `deepseek/deepseek-r1:free` for the free tier and
`anthropic/claude-sonnet-4` for paid tiers.
- Automatically refresh GitHub Copilot tokens when used as OpenAI API keys, by Lih Chen.
- Aider wrote 79% of the code in this release.

### Aider v0.83.2

- Bumped configargparse to 1.7.1 as 1.7 was pulled.
- Added shell tab completion for file path arguments (by saviour) and for `--edit-format`/`--editor-edit-format` options.
- Improved OpenRouter model metadata handling by introducing a local cache, increasing reliability and performance.
- The `/settings` command now displays detailed metadata for active main, editor, and weak models.
- Fixed an issue where files explicitly added via the command line were not correctly ignored if listed in `.gitignore`.
- Improved automatic commit messages by providing more context during their generation, by wangboxue.

### Aider v0.83.1

- Improved user language detection by correctly normalizing hyphenated language codes (e.g., `en-US` to `en`) and enhancing the validation of locale results.
- Prevented Aider from instructing the LLM to reply in 'C' or 'POSIX' when these are detected as the system locale.
- Displayed a spinner with the model name when generating commit messages.

### Aider v0.83.0

- Added support for `gemini-2.5-pro-preview-05-06` models.
- Added support for `qwen3-235b` models.
- Added repo-map support for OCaml and OCaml interface files, by Andrey Popp.
- Added a spinner animation while waiting for the LLM to start streaming its response.
- Updated the spinner animation to a Knight Rider style.
- Introduced `--attribute-co-authored-by` option to add co-author trailer to commit messages, by Andrew Grigorev.
- Updated Gemini model aliases (e.g., `gemini`, `gemini-2.5-pro`) to point to the `05-06` preview versions.
- Marked Gemini 2.5 Pro preview models as `overeager` by default.
- Commit message prompt specifies the user's language.
- Updated the default weak model for Gemini 2.5 Pro models to `gemini/gemini-2.5-flash-preview-04-17`.
- Corrected `gemini-2.5-pro-exp-03-25` model settings to reflect its lack of support for `thinking_budget`.
- Ensured model-specific system prompt prefixes are placed on a new line before the main system prompt.
- Added tracking of total tokens sent and received, now included in benchmark statistics.
- Automatically fetch model parameters (context window, pricing) for OpenRouter models directly from their website, by Stefan Hladnik.
- Enabled support for `thinking_tokens` and `reasoning_effort` parameters for OpenRouter models.
- Improved cost calculation using `litellm.completion_cost` where available.
- Added model settings for `openrouter/google/gemini-2.5-pro-preview-03-25`.
- Added `--disable-playwright` flag to prevent Playwright installation prompts and usage, by Andrew Grigorev.
- The `aider scrape` command-line tool will now use Playwright for web scraping if it is available, by Jon Keys.
- Fixed linter command execution on Windows by adopting `oslex` for argument quoting, by Titusz Pan.
- Improved cross-platform display of shell commands by using `oslex` for robust argument quoting, by Titusz Pan.
- Improved `/ask` mode to instruct the LLM to elide unchanging code in its responses.
- Ensured web scraping in the GUI also respects Playwright availability and the `--disable-playwright` flag.
- Improved display of filenames in the prompt header using rich Text formatting.
- Enabled `reasoning_effort` for Gemini 2.5 Flash models.
- Added a `--shell-completions` argument to generate shell completion scripts (e.g., for bash, zsh).
- Explicit `--attribute-author` or `--attribute-committer` flags now override the default behavior when `--attribute-co-authored-by` is used, allowing finer control over commit attribution, by Andrew Grigorev.
- Fixed an issue where read-only status of files might not be preserved correctly by some commands (e.g. `/drop` after adding a read-only file).
- The `aider-args` utility (or `python -m aider.args`) now defaults to printing a sample YAML configuration if no arguments are provided.
- Displayed token count progress and the name of the file or identifier being processed during repo map updates.
- Extended the waiting spinner to also show for non-streaming responses and further enhanced its animation with console width clipping, cursor hiding, and a more continuous appearance.
- Dropped support for Python 3.9.
- Aider wrote 55% of the code in this release.

### Aider v0.82.3

- Add support for `gemini-2.5-flash-preview-04-17` models.
- Improved robustness of edit block parsing when filenames start with backticks or fences.
- Add new `udiff-simple` edit format, for Gemini 2.5 Pro.
- Update default weak/editor models for Gemini 2.5 Pro models to use `gemini-2.5-flash-preview-04-17`.
- Instruct models to reply in the user's detected system language.
- Fix parsing of diffs for newly created files (`--- /dev/null`).
- Add markdown syntax highlighting support when editing multi-line commit messages via `/commit`, by Kay Gosho.
- Set Gemini 2.5 Pro models to use the `overeager` prompt setting by default.
- Add common file types (`.svg`, `.pdf`) to the default list of ignored files for AI comment scanning (`--watch`).
- Skip scanning files larger than 1MB for AI comments (`--watch`).

### Aider v0.82.2

- Fix editing shell files with diff-fenced, by zjy1412.
- Improve robustness of patch application by allowing multiple update/delete actions for the same file within a single response.
- Update prompts to instruct LLMs to consolidate all edits for a given file into a single block within the patch.

### Aider v0.82.1

- Added support for `o3` and `o4-mini` including provider-specific versions for OpenAI, OpenRouter, and Azure.
- Added support for Azure specific `gpt-4.1` and `gpt-4.1-mini` models.
- Disabled streaming for `o3` models since you need identity verification to stream.
- Fixed handling of file paths in unified diffs, especially those generated by git.

### Aider v0.82.0

- Support for GPT 4.1, mini and nano.
- Added new `patch` edit format for OpenAI's GPT-4.1 model.
- Improved support for using architect mode with Gemini 2.5 Pro.
- Added new `editor-diff`, `editor-whole`, and `editor-diff-fenced` edit formats.
- Bugfix for automatically selecting the best edit format to use in architect mode.
- Added support for `grok-3-fast-beta` and `grok-3-mini-fast-beta` models.
- Aider wrote 92% of the code in this release.

### Aider v0.81.3

- Commit messages generated by aider are no longer forced to be entirely lowercase, by Peter Hadlaw.
- Updated default settings for Grok models.

### Aider v0.81.2

- Add support for `xai/grok-3-beta`, `xai/grok-3-mini-beta`, `openrouter/x-ai/grok-3-beta`, `openrouter/x-ai/grok-3-mini-beta`, and `openrouter/openrouter/optimus-alpha` models.
- Add alias "grok3" for `xai/grok-3-beta`.
- Add alias "optimus" for `openrouter/openrouter/optimus-alpha`.
- Fix URL extraction from error messages.
- Allow adding files by full path even if a file with the same basename is already in the chat.
- Fix quoting of values containing '#' in the sample `aider.conf.yml`.
- Add support for Fireworks AI model 'deepseek-v3-0324', by Felix Lisczyk.
- Commit messages generated by aider are now lowercase, by Anton Ödman.

### Aider v0.81.1

- Added support for the `gemini/gemini-2.5-pro-preview-03-25` model.
- Updated the `gemini` alias to point to `gemini/gemini-2.5-pro-preview-03-25`.
- Added the `gemini-exp` alias for `gemini/gemini-2.5-pro-exp-03-25`.

### Aider v0.81.0

- Added support for the `openrouter/openrouter/quasar-alpha` model.
  - Run with `aider --model quasar`
- Offer OpenRouter OAuth authentication if an OpenRouter model is specified but the API key is missing.
- Prevent retrying API calls when the provider reports insufficient credits.
- Improve URL detection to exclude trailing double quotes.
- Aider wrote 86% of the code in this release.

### Aider v0.80.4

- Bumped deps to pickup litellm change to properly display the root cause of OpenRouter "choices" errors.

### Aider v0.80.3

- Improve error message for OpenRouter API connection issues to mention potential rate limiting or upstream provider issues.
- Configure weak models (`gemini/gemini-2.0-flash` and `openrouter/google/gemini-2.0-flash-exp:free`) for Gemini 2.5 Pro models.
- Add model metadata for `openrouter/google/gemini-2.0-flash-exp:free`.

### Aider v0.80.2

- Bumped deps.

### Aider v0.80.1

- Updated deps for yanked fsspec and aiohttp packages #3699
- Removed redundant dependency check during OpenRouter OAuth flow, by Claudia Pellegrino.

### Aider v0.80.0

- OpenRouter OAuth integration:
  - Offer to OAuth against OpenRouter if no model and keys are provided.
  - Select OpenRouter default model based on free/paid tier status if `OPENROUTER_API_KEY` is set and no model is specified.
- Prioritize `gemini/gemini-2.5-pro-exp-03-25` if `GEMINI_API_KEY` is set, and `vertex_ai/gemini-2.5-pro-exp-03-25` if `VERTEXAI_PROJECT` is set, when no model is specified.
- Validate user-configured color settings on startup and warn/disable invalid ones.
- Warn at startup if `--stream` and `--cache-prompts` are used together, as cost estimates may be inaccurate.
- Boost repomap ranking for files whose path components match identifiers mentioned in the chat.
- Change web scraping timeout from an error to a warning, allowing scraping to continue with potentially incomplete content.
- Left-align markdown headings in the terminal output, by Peter Schilling.
- Update edit format to the new model's default when switching models with `/model`, if the user was using the old model's default format.
- Add `Ctrl-X Ctrl-E` keybinding to edit the current input buffer in an external editor, by Matteo Landi.
- Fix linting errors for filepaths containing shell metacharacters, by Mir Adnan ALI.
- Add the `openrouter/deepseek-chat-v3-0324:free` model.
- Add repomap support for the Scala language, by Vasil Markoukin.
- Fixed bug in `/run` that was preventing auto-testing.
- Fix bug preventing `UnboundLocalError` during git tree traversal.
- Handle `GitCommandNotFound` error if git is not installed or not in PATH.
- Handle `FileNotFoundError` if the current working directory is deleted while aider is running.
- Fix completion menu current item color styling, by Andrey Ivanov.
- Aider wrote 87% of the code in this release.

### Aider v0.79.2

- Added 'gemini' alias for gemini-2.5-pro model.
- Updated Gemini 2.5 Pro max output tokens to 64k.
- Added support for Lisp-style semicolon comments in file watcher, by Matteo Landi.
- Added OpenRouter API error detection and retries.
- Added openrouter/deepseek-chat-v3-0324 model.
- Aider wrote 93% of the code in this release.

### Aider v0.79.1

- Improved model listing to include all models in fuzzy matching, including those provided by aider (not litellm).

### Aider v0.79.0

- Added support for Gemini 2.5 Pro models.
- Added support for DeepSeek V3 0324 model.
- Added a new `/context` command that automatically identifies which files need to be edited for a given request.
- Added `/edit` as an alias for the `/editor` command.
- Added "overeager" mode for Claude 3.7 Sonnet models to try and keep it working within the requested scope.
- Aider wrote 65% of the code in this release.

### Aider v0.78.0

- Added support for thinking tokens for OpenRouter Sonnet 3.7.
- Added commands to switch between model types: `/editor-model` for Editor Model, and `/weak-model` for Weak Model, by csala.
- Added model setting validation to ignore `--reasoning-effort` and `--thinking-tokens` if the model doesn't support them.
- Added `--check-model-accepts-settings` flag (default: true) to force unsupported model settings.
- Annotated which models support reasoning_effort and thinking_tokens settings in the model settings data.
- Improved code block rendering in markdown output with better padding using NoInsetMarkdown.
- Added `--git-commit-verify` flag (default: False) to control whether git commit hooks are bypassed.
- Fixed autocompletion for `/ask`, `/code`, and `/architect` commands, by shladnik.
- Added vi-like behavior when pressing enter in multiline-mode while in vi normal/navigation-mode, by Marco Mayer.
- Added AWS_PROFILE support for Bedrock models, allowing use of AWS profiles instead of explicit credentials, by lentil32.
- Enhanced `--aiderignore` argument to resolve both absolute and relative paths, by mopemope.
- Improved platform information handling to gracefully handle retrieval errors.
- Aider wrote 92% of the code in this release.

### Aider v0.77.1

- Bumped dependencies to pickup litellm fix for Ollama.
- Added support for `openrouter/google/gemma-3-27b-it` model.
- Updated exclude patterns for help documentation.

### Aider v0.77.0

- Big upgrade in [programming languages supported](https://aider.chat/docs/languages.html) by adopting [tree-sitter-language-pack](https://github.com/Goldziher/tree-sitter-language-pack/).
  - 130 new languages with linter support.
  - 20 new languages with repo-map support.
- Added `/think-tokens` command to set thinking token budget with support for human-readable formats (8k, 10.5k, 0.5M).
- Added `/reasoning-effort` command to control model reasoning level.
- The `/think-tokens` and `/reasoning-effort` commands display current settings when called without arguments.
- Display of thinking token budget and reasoning effort in model information.
- Changed `--thinking-tokens` argument to accept string values with human-readable formats.
- Added `--auto-accept-architect` flag (default: true) to automatically accept changes from architect coder format without confirmation.
- Added support for `cohere_chat/command-a-03-2025` and `gemini/gemma-3-27b-it`
- The bare `/drop` command now preserves original read-only files provided via args.read.
- Fixed a bug where default model would be set by deprecated `--shortcut` switches even when already specified in the command line.
- Improved AutoCompleter to require 3 characters for autocompletion to reduce noise.
- Aider wrote 72% of the code in this release.

### Aider v0.76.2

- Fixed handling of JSONDecodeError when loading model cache file.
- Fixed handling of GitCommandError when retrieving git user configuration.
- Aider wrote 75% of the code in this release.

### Aider v0.76.1

- Added ignore_permission_denied option to file watcher to prevent errors when accessing restricted files, by Yutaka Matsubara.
- Aider wrote 0% of the code in this release.

### Aider v0.76.0

- Improved support for thinking/reasoningmodels:
  - Added `--thinking-tokens` CLI option to control token budget for models that support thinking.
  - Display thinking/reasoning content from LLMs which return it.
  - Enhanced handling of reasoning tags to better clean up model responses.
  - Added deprecation warning for `remove_reasoning` setting, now replaced by `reasoning_tag`.
- Aider will notify you when it's completed the last request and needs your input:
  - Added [notifications when LLM responses are ready](https://aider.chat/docs/usage/notifications.html) with `--notifications` flag.
  - Specify desktop notification command with `--notifications-command`.
- Added support for QWQ 32B.
- Switch to `tree-sitter-language-pack` for tree sitter support.
- Improved error handling for EOF (Ctrl+D) in user input prompts.
- Added helper function to ensure hex color values have a # prefix.
- Fixed handling of Git errors when reading staged files.
- Improved SSL verification control for model information requests.
- Improved empty LLM response handling with clearer warning messages.
- Fixed Git identity retrieval to respect global configuration, by Akira Komamura.
- Offer to install dependencies for Bedrock and Vertex AI models.
- Deprecated model shortcut args (like --4o, --opus) in favor of the --model flag.
- Aider wrote 85% of the code in this release.

### Aider v0.75.3

- Support for V3 free on OpenRouter: `--model openrouter/deepseek/deepseek-chat:free`.

### Aider v0.75.2

- Added support for Claude 3.7 Sonnet models on OpenRouter, Bedrock and Vertex AI.
- Updated default model to Claude 3.7 Sonnet on OpenRouter.
- Added support for GPT-4.5-preview model.
- Added support for Claude 3.7 Sonnet:beta on OpenRouter.
- Fixed weak_model_name patterns to match main model name patterns for some models.

### Aider v0.75.1

- Added support for `openrouter/anthropic/claude-3.7-sonnet`

### Aider v0.75.0

- Basic support for Claude 3.7 Sonnet
  - Use `--model sonnet` to use the new 3.7
  - Thinking support coming soon.
- Bugfix to `/editor` command.
- Aider wrote 46% of the code in this release.

### Aider v0.74.3

- Downgrade streamlit dependency to avoid threading bug.
- Added support for tree-sitter language pack.
- Added openrouter/o3-mini-high model configuration.
- Added build.gradle.kts to special files for Kotlin project support, by Lucas Shadler.

### Aider v0.74.2

- Prevent more than one cache warming thread from becoming active.
- Fixed continuation prompt ". " for multiline input.
- Added HCL (Terraform) syntax support, by Warren Krewenki.

### Aider v0.74.1

- Have o1 & o3-mini generate markdown by sending the magic "Formatting re-enabled." string.
- Bugfix for multi-line inputs, which should not include the ". " continuation prompt.

### Aider v0.74.0

- Dynamically changes the Ollama context window to hold the current chat.
- Better support for o3-mini, DeepSeek V3 & R1, o1-mini, o1 especially via third-party API providers.
- Remove `<think>` tags from R1 responses for commit messages (and other weak model uses).
- Can now specify `use_temperature: <float>` in model settings, not just true/false.
- The full docker container now includes `boto3` for Bedrock.
- Docker containers now set `HOME=/app` which is the normal project mount-point, to persist `~/.aider`.
- Bugfix to prevent creating incorrect filenames like `python`, `php`, etc.
- Bugfix for `--timeout`
- Bugfix so that `/model` now correctly reports that the weak model is not changed.
- Bugfix so that multi-line mode persists through ^C at confirmation prompts.
- Watch files now fully ignores top-level directories named in ignore files, to reduce the chance of hitting OS watch limits. Helpful to ignore giant subtrees like `node_modules`.
- Fast startup with more providers and when model metadata provided in local files.
- Improved .gitignore handling:
  - Honor ignores already in effect regardless of how they've been configured.
  - Check for .env only when the file exists.
- Yes/No prompts now accept All/Skip as alias for Y/N even when not processing a group of confirmations.
- Aider wrote 77% of the code in this release.

### Aider v0.73.0

- Full support for o3-mini: `aider --model o3-mini`
- New `--reasoning-effort` argument: low, medium, high.
- Improved handling of context window size limits, with better messaging and Ollama-specific guidance.
- Added support for removing model-specific reasoning tags from responses with `remove_reasoning: tagname` model setting.
- Auto-create parent directories when creating new files, by xqyz.
- Support for R1 free on OpenRouter: `--model openrouter/deepseek/deepseek-r1:free`
- Aider wrote 69% of the code in this release.

### Aider v0.72.3

- Enforce user/assistant turn order to avoid R1 errors, by miradnanali.
- Case-insensitive model name matching while preserving original case.

### Aider v0.72.2
- Harden against user/assistant turn order problems which cause R1 errors.

### Aider v0.72.1
- Fix model metadata for `openrouter/deepseek/deepseek-r1`

### Aider v0.72.0
- Support for DeepSeek R1.
  - Use shortcut: `--model r1`
  - Also via OpenRouter: `--model openrouter/deepseek/deepseek-r1`
- Added Kotlin syntax support to repo map, by Paul Walker.
- Added `--line-endings` for file writing, by Titusz Pan.
- Added examples_as_sys_msg=True for GPT-4o models, improves benchmark scores.
- Bumped all dependencies, to pick up litellm support for o1 system messages.
- Bugfix for turn taking when reflecting lint/test errors.
- Aider wrote 52% of the code in this release.

### Aider v0.71.1

- Fix permissions issue in Docker images.
- Added read-only file announcements.
- Bugfix: ASCII fallback for unicode errors.
- Bugfix: integer indices for list slicing in repomap calculations.

### Aider v0.71.0

- Prompts to help DeepSeek work better when alternating between `/ask` and `/code`.
- Streaming pretty LLM responses is smoother and faster for long replies.
- Streaming automatically turns of for model that don't support it
  - Can now switch to/from `/model o1` and a streaming model
- Pretty output remains enabled even when editing files with triple-backtick fences
- Bare `/ask`, `/code` and `/architect` commands now switch the chat mode.
- Increased default size of the repomap.
- Increased max chat history tokens limit from 4k to 8k.
- Turn off fancy input and watch files if terminal is dumb.
- Added support for custom voice format and input device settings.
- Disabled Streamlit email prompt, by apaz-cli.
- Docker container runs as non-root user.
- Fixed lint command handling of nested spaced strings, by Aaron Weisberg.
- Added token count feedback when adding command output to chat.
- Improved error handling for large audio files with automatic format conversion.
- Improved handling of git repo index errors, by Krazer.
- Improved unicode handling in console output with ASCII fallback.
- Added AssertionError, AttributeError to git error handling.
- Aider wrote 60% of the code in this release.

### Aider v0.70.0

- Full support for o1 models.
- Watch files now honors `--subtree-only`, and only watches that subtree.
- Improved prompting for watch files, to work more reliably with more models.
- New install methods via uv, including one-liners.
- Support for openrouter/deepseek/deepseek-chat model.
- Better error handling when interactive commands are attempted via `/load` or `--load`.
- Display read-only files with abs path if its shorter than rel path.
- Ask 10% of users to opt-in to analytics.
- Bugfix for auto-suggest.
- Gracefully handle unicode errors in git path names.
- Aider wrote 74% of the code in this release.

### Aider v0.69.1

- Fix for gemini model names in model metadata.
- Show hints about AI! and AI? when user makes AI comments.
- Support for running without git installed.
- Improved environment variable setup messages on Windows.

### Aider v0.69.0

- [Watch files](https://aider.chat/docs/usage/watch.html) improvements:
  - Use `# ... AI?` comments to trigger aider and ask questions about your code.
  - Now watches *all* files, not just certain source files.
  - Use `# AI comments`, `// AI comments`, or `-- AI comments` to give aider instructions in any text file.
- Full support for Gemini Flash 2.0 Exp:
  - `aider --model flash` or `aider --model gemini/gemini-2.0-flash-exp`
- [New `--multiline` flag and `/multiline-mode` command](https://aider.chat/docs/usage/commands.html#entering-multi-line-chat-messages) makes ENTER a soft newline and META-ENTER send the message, by @miradnanali.
- `/copy-context <instructions>` now takes optional "instructions" when [copying code context to the clipboard](https://aider.chat/docs/usage/copypaste.html#copy-aiders-code-context-to-your-clipboard-paste-into-the-web-ui).
- Improved clipboard error handling with helpful requirements install info.
- Ask 5% of users if they want to opt-in to analytics.
- `/voice` now lets you edit the transcribed text before sending.
- Disabled auto-complete in Y/N prompts.
- Aider wrote 68% of the code in this release.

### Aider v0.68.0

- [Aider works with LLM web chat UIs](https://aider.chat/docs/usage/copypaste.html).
  - New `--copy-paste` mode.
  - New `/copy-context` command.
- [Set API keys and other environment variables for all providers from command line or YAML conf file](https://aider.chat/docs/config/aider_conf.html#storing-llm-keys).
  - New `--api-key provider=key` setting.
  - New `--set-env VAR=value` setting.
- Added bash and zsh support to `--watch-files`.
- Better error messages when missing dependencies for Gemini and Bedrock models.
- Control-D now properly exits the program.
- Don't count token costs when API provider returns a hard error.
- Bugfix so watch files works with files that don't have tree-sitter support.
- Bugfix so o1 models can be used as weak model.
- Updated shell command prompt.
- Added docstrings for all Coders.
- Reorganized command line arguments with improved help messages and grouping.
- Use the exact `sys.python` for self-upgrades.
- Added experimental Gemini models.
- Aider wrote 71% of the code in this release.

### Aider v0.67.0

- [Use aider in your IDE or editor](https://aider.chat/docs/usage/watch.html).
  - Run `aider --watch-files` and it will watch for instructions you add to your source files.
  - One-liner `# ...` or `// ...` comments that start or end with "AI" are instructions to aider.
  - When aider sees "AI!" it reads and follows all the instructions in AI comments.
- Support for new Amazon Bedrock Nova models.
- When `/run` or `/test` have non-zero exit codes, pre-fill "Fix that" into the next message prompt.
- `/diff` now invokes `git diff` to use your preferred diff tool.
- Added Ctrl-Z support for process suspension.
- Spinner now falls back to ASCII art if fancy symbols throw unicode errors.
- `--read` now expands `~` home dirs.
- Enabled exception capture in analytics.
- [Aider wrote 61% of the code in this release.](https://aider.chat/HISTORY.html)

### Aider v0.66.0

- PDF support for Sonnet and Gemini models.
- Added `--voice-input-device` to select audio input device for voice recording, by @preynal.
- Added `--timeout` option to configure API call timeouts.
- Set cwd to repo root when running shell commands.
- Added Ctrl-Up/Down keyboard shortcuts for per-message history navigation.
- Improved error handling for failed .gitignore file operations.
- Improved error handling for input history file permissions.
- Improved error handling for analytics file access.
- Removed spurious warning about disabling pretty in VSCode.
- Removed broken support for Dart.
- Bugfix when scraping URLs found in chat messages.
- Better handling of __version__ import errors.
- Improved `/drop` command to support substring matching for non-glob patterns.
- Aider wrote 82% of the code in this release.

### Aider v0.65.1

- Bugfix to `--alias`.

### Aider v0.65.0

- Added `--alias` config to define [custom model aliases](https://aider.chat/docs/config/model-aliases.html).
- Added `--[no-]detect-urls` flag to disable detecting and offering to scrape URLs found in the chat.
- Ollama models now default to an 8k context window.
- Added [RepoMap support for Dart language](https://aider.chat/docs/languages.html) by @malkoG.
- Ask 2.5% of users if they want to opt-in to [analytics](https://aider.chat/docs/more/analytics.html).
- Skip suggesting files that share names with files already in chat.
- `/editor` returns and prefill the file content into the prompt, so you can use `/editor` to compose messages that start with `/commands`, etc.
- Enhanced error handling for analytics.
- Improved handling of UnknownEditFormat exceptions with helpful documentation links.
- Bumped dependencies to pick up grep-ast 0.4.0 for Dart language support.
- Aider wrote 81% of the code in this release.

### Aider v0.64.1

- Disable streaming for o1 on OpenRouter.

### Aider v0.64.0

- Added [`/editor` command](https://aider.chat/docs/usage/commands.html) to open system editor for writing prompts, by @thehunmonkgroup.
- Full support for `gpt-4o-2024-11-20`.
- Stream o1 models by default.
- `/run` and suggested shell commands are less mysterious and now confirm that they "Added XX lines of output to the chat."
- Ask 1% of users if they want to opt-in to [analytics](https://aider.chat/docs/more/analytics.html).
- Added support for [optional multiline input tags](https://aider.chat/docs/usage/commands.html#entering-multi-line-chat-messages) with matching closing tags.
- Improved [model settings configuration](https://aider.chat/docs/config/adv-model-settings.html#global-extra-params) with support for global `extra_params` for `litellm.completion()`.
- Architect mode now asks to add files suggested by the LLM.
- Fixed bug in fuzzy model name matching.
- Added Timeout exception to handle API provider timeouts.
- Added `--show-release-notes` to control release notes display on first run of new version.
- Save empty dict to cache file on model metadata download failure, to delay retry.
- Improved error handling and code formatting.
- Aider wrote 74% of the code in this release.

###  Aider v0.63.2

- Fixed bug in fuzzy model name matching when litellm provider info is missing.
- Modified model metadata file loading to allow override of resource file.
- Allow recursive loading of dirs using `--read`.
- Updated dependency versions to pick up litellm fix for ollama models.
- Added exponential backoff retry when writing files to handle editor file locks.
- Updated Qwen 2.5 Coder 32B model configuration.

### Aider v0.63.1

- Fixed bug in git ignored file handling.
- Improved error handling for git operations.

### Aider v0.63.0

- Support for Qwen 2.5 Coder 32B.
- `/web` command just adds the page to the chat, without triggering an LLM response.
- Improved prompting for the user's preferred chat language.
- Improved handling of LiteLLM exceptions.
- Bugfix for double-counting tokens when reporting cache stats.
- Bugfix for the LLM creating new files.
- Other small bug fixes.
- Aider wrote 55% of the code in this release.

### Aider v0.62.0

- Full support for Claude 3.5 Haiku
  - Scored 75% on [aider's code editing leaderboard](https://aider.chat/docs/leaderboards/).
  - Almost as good as Sonnet at much lower cost.
  - Launch with `--haiku` to use it.
- Easily apply file edits from ChatGPT, Claude or other web apps
  - Chat with ChatGPT or Claude via their web app. 
  - Give it your source files and ask for the changes you want.
  - Use the web app's "copy response" button to copy the entire reply from the LLM.
  - Run `aider --apply-clipboard-edits file-to-edit.js`.
  - Aider will edit your file with the LLM's changes.
- Bugfix for creating new files.
- Aider wrote 84% of the code in this release.  

### Aider v0.61.0

- Load and save aider slash-commands to files:
  - `/save <fname>` command will make a file of `/add` and `/read-only` commands that recreate the current file context in the chat.
  - `/load <fname>` will replay the commands in the file.
  - You can use `/load` to run any arbitrary set of slash-commands, not just `/add` and `/read-only`.
  - Use `--load <fname>` to run a list of commands on launch, before the interactive chat begins.
- Anonymous, opt-in [analytics](https://aider.chat/docs/more/analytics.html) with no personal data sharing.
- Aider follows litellm's `supports_vision` attribute to enable image support for models.
- Bugfix for when diff mode flexibly handles the model using the wrong filename.
- Displays filenames in sorted order for `/add` and `/read-only`.
- New `--no-fancy-input` switch disables prompt toolkit input, now still available with `--no-pretty`.
- Override browser config with `--no-browser` or `--no-gui`.
- Offer to open documentation URLs when errors occur.
- Properly support all o1 models, regardless of provider.
- Improved layout of filenames above input prompt.
- Better handle corrupted repomap tags cache.
- Improved handling of API errors, especially when accessing the weak model.
- Aider wrote 68% of the code in this release.

### Aider v0.60.1

- Enable image support for Sonnet 10/22.
- Display filenames in sorted order.

### Aider v0.60.0

- Full support for Sonnet 10/22, the new SOTA model on aider's code editing benchmark.
  - Aider uses Sonnet 10/22 by default.
- Improved formatting of added and read-only files above chat prompt, by @jbellis.
- Improved support for o1 models by more flexibly parsing their nonconforming code edit replies.
- Corrected diff edit format prompt that only the first match is replaced.
- Stronger whole edit format prompt asking for clean file names.
- Now offers to add `.env` to the `.gitignore` file.
- Ships with a small model metadata json file to handle models not yet updated in litellm.
- Model settings for o1 models on azure.
- Bugfix to properly include URLs in `/help` RAG results.
- Aider wrote 49% of the code in this release.

### Aider v0.59.1

- Check for obsolete `yes: true` in YAML config, show helpful error.
- Model settings for openrouter/anthropic/claude-3.5-sonnet:beta

### Aider v0.59.0

- Improvements to `/read-only`:
  - Now supports shell-style auto-complete of the full file system.
  - Still auto-completes the full paths of the repo files like `/add`.
  - Now supports globs like `src/**/*.py`
- Renamed `--yes` to `--yes-always`.
  - Now uses `AIDER_YES_ALWAYS` env var and `yes-always:` YAML key.
  - Existing YAML and .env files will need to be updated.
  - Can still abbreviate to `--yes` on the command line.
- Config file now uses standard YAML list syntax with `  - list entries`, one per line.  
- `/settings` now includes the same announcement lines that would print at launch.
- Sanity checks the `--editor-model` on launch now, same as main and weak models.
- Added `--skip-sanity-check-repo` switch to speedup launch in large repos.
- Bugfix so architect mode handles Control-C properly.
- Repo-map is deterministic now, with improved caching logic.
- Improved commit message prompt.
- Aider wrote 77% of the code in this release.

### Aider v0.58.1

- Fixed bug where cache warming pings caused subsequent user messages to trigger a tight loop of LLM requests.

### Aider v0.58.0

- [Use a pair of Architect/Editor models for improved coding](https://aider.chat/2024/09/26/architect.html)
  - Use a strong reasoning model like o1-preview as your Architect.
  - Use a cheaper, faster model like gpt-4o as your Editor.
- New `--o1-preview` and `--o1-mini` shortcuts.
- Support for new Gemini 002 models.
- Better support for Qwen 2.5 models.
- Many confirmation questions can be skipped for the rest of the session with "(D)on't ask again" response.
- Autocomplete for `/read-only` supports the entire filesystem.
- New settings for completion menu colors.
- New `/copy` command to copy the last LLM response to the clipboard.
- Renamed `/clipboard` to `/paste`.
- Will now follow HTTP redirects when scraping urls.
- New `--voice-format` switch to send voice audio as wav/mp3/webm, by @mbailey.
- ModelSettings takes `extra_params` dict to specify any extras to pass to `litellm.completion()`.
- Support for cursor shapes when in vim mode.
- Numerous bug fixes.
- Aider wrote 53% of the code in this release.

### Aider v0.57.1

- Fixed dependency conflict between aider-chat[help] and [playwright].

### Aider v0.57.0

- Support for OpenAI o1 models:
  - o1-preview now works well with diff edit format.
  - o1-preview with diff now matches SOTA leaderboard result with whole edit format.
  - `aider --model o1-mini`
  - `aider --model o1-preview`
- On Windows, `/run` correctly uses PowerShell or cmd.exe.
- Support for new 08-2024 Cohere models, by @jalammar.
- Can now recursively add directories with `/read-only`.
- User input prompts now fall back to simple `input()` if `--no-pretty` or a Windows console is not available.
- Improved sanity check of git repo on startup.
- Improvements to prompt cache chunking strategy.
- Removed "No changes made to git tracked files".
- Numerous bug fixes for corner case crashes.
- Updated all dependency versions.
- Aider wrote 70% of the code in this release.

### Aider v0.56.0

- Enables prompt caching for Sonnet via OpenRouter by @fry69
- Enables 8k output tokens for Sonnet via VertexAI and DeepSeek V2.5.
- New `/report` command to open your browser with a pre-populated GitHub Issue.
- New `--chat-language` switch to set the spoken language.
- Now `--[no-]suggest-shell-commands` controls both prompting for and offering to execute shell commands.
- Check key imports on launch, provide helpful error message if dependencies aren't available.
- Renamed `--models` to `--list-models` by @fry69.
- Numerous bug fixes for corner case crashes.
- Aider wrote 56% of the code in this release.

### Aider v0.55.0

- Only print the pip command when self updating on Windows, without running it.
- Converted many error messages to warning messages.
- Added `--tool-warning-color` setting.
- Blanket catch and handle git errors in any `/command`.
- Catch and handle glob errors in `/add`, errors writing files.
- Disabled built in linter for typescript.
- Catch and handle terminals which don't support pretty output.
- Catch and handle playwright and pandoc errors.
- Catch `/voice` transcription exceptions, show the WAV file so the user can recover it.
- Aider wrote 53% of the code in this release.

### Aider v0.54.12

- Switched to `vX.Y.Z.dev` version naming.

### Aider v0.54.11

- Improved printed pip command output on Windows.

### Aider v0.54.10

- Bugfix to test command in platform info.

### Aider v0.54.9

- Include important devops files in the repomap.
- Print quoted pip install commands to the user.
- Adopt setuptools_scm to provide dev versions with git hashes.
- Share active test and lint commands with the LLM.
- Catch and handle most errors creating new files, reading existing files.
- Catch and handle most git errors.
- Added --verbose debug output for shell commands.

### Aider v0.54.8

- Startup QOL improvements:
  - Sanity check the git repo and exit gracefully on problems.
  - Pause for confirmation after model sanity check to allow user to review warnings.
- Bug fix for shell commands on Windows.
- Do not fuzzy match filenames when LLM is creating a new file, by @ozapinq
- Numerous corner case bug fixes submitted via new crash report -> GitHub Issue feature.
- Crash reports now include python version, OS, etc.

### Aider v0.54.7

- Offer to submit a GitHub issue pre-filled with uncaught exception info.
- Bugfix for infinite output.

### Aider v0.54.6

- New `/settings` command to show active settings.
- Only show cache warming status update if `--verbose`.

### Aider v0.54.5

- Bugfix for shell commands on Windows.
- Refuse to make git repo in $HOME, warn user.
- Don't ask again in current session about a file the user has said not to add to the chat.
- Added `--update` as an alias for `--upgrade`.

### Aider v0.54.4

- Bugfix to completions for `/model` command.
- Bugfix: revert home dir special case.

### Aider v0.54.3

- Dependency `watchdog<5` for docker image.

### Aider v0.54.2

- When users launch aider in their home dir, help them find/create a repo in a subdir.
- Added missing `pexpect` dependency.

### Aider v0.54.0

- Added model settings for `gemini/gemini-1.5-pro-exp-0827` and `gemini/gemini-1.5-flash-exp-0827`.
- Shell and `/run` commands can now be interactive in environments where a pty is available.
- Optionally share output of suggested shell commands back to the LLM.
- New `--[no-]suggest-shell-commands` switch to configure shell commands.
- Performance improvements for autocomplete in large/mono repos.
- New `--upgrade` switch to install latest version of aider from pypi.
- Bugfix to `--show-prompt`.
- Disabled automatic reply to the LLM on `/undo` for all models.
- Removed pager from `/web` output.
- Aider wrote 64% of the code in this release.

### Aider v0.53.0

- [Keep your prompt cache from expiring](https://aider.chat/docs/usage/caching.html#preventing-cache-expiration) with `--cache-keepalive-pings`.
  - Pings the API every 5min to keep the cache warm.
- You can now bulk accept/reject a series of add url and run shell confirmations.
- Improved matching of filenames from S/R blocks with files in chat.
- Stronger prompting for Sonnet to make edits in code chat mode.
- Stronger prompting for the LLM to specify full file paths.
- Improved shell command prompting.
- Weak model now uses `extra_headers`, to support Anthropic beta features.
- New `--install-main-branch` to update to the latest dev version of aider.
- Improved error messages on attempt to add not-git subdir to chat.
- Show model metadata info on `--verbose`.
- Improved warnings when LLMs env variables aren't set.
- Bugfix to windows filenames which contain `\_`.
- Aider wrote 59% of the code in this release.

### Aider v0.52.1

- Bugfix for NameError when applying edits.

### Aider v0.52.0

- Aider now offers to run shell commands:
  - Launch a browser to view updated html/css/js.
  - Install new dependencies.
  - Run DB migrations. 
  - Run the program to exercise changes.
  - Run new test cases.
- `/read` and `/drop` now expand `~` to the home dir.
- Show the active chat mode at aider prompt.
- New `/reset` command to `/drop` files and `/clear` chat history.
- New `--map-multiplier-no-files` to control repo map size multiplier when no files are in the chat.
  - Reduced default multiplier to 2.
- Bugfixes and improvements to auto commit sequencing.
- Improved formatting of token reports and confirmation dialogs.
- Default OpenAI model is now `gpt-4o-2024-08-06`.
- Bumped dependencies to pickup litellm bugfixes.
- Aider wrote 68% of the code in this release.

### Aider v0.51.0

- Prompt caching for Anthropic models with `--cache-prompts`.
  - Caches the system prompt, repo map and `/read-only` files.
- Repo map recomputes less often in large/mono repos or when caching enabled.
  - Use `--map-refresh <always|files|manual|auto>` to configure.
- Improved cost estimate logic for caching.
- Improved editing performance on Jupyter Notebook `.ipynb` files.
- Show which config YAML file is loaded with `--verbose`.
- Bumped dependency versions.
- Bugfix: properly load `.aider.models.metadata.json` data.
- Bugfix: Using `--msg /ask ...` caused an exception.
- Bugfix: litellm tokenizer bug for images.
- Aider wrote 56% of the code in this release.

### Aider v0.50.1

- Bugfix for provider API exceptions.

### Aider v0.50.0

- Infinite output for DeepSeek Coder, Mistral models in addition to Anthropic's models.
- New `--deepseek` switch to use DeepSeek Coder.
- DeepSeek Coder uses 8k token output.
- New `--chat-mode <mode>` switch to launch in ask/help/code modes.
- New `/code <message>` command request a code edit while in `ask` mode.
- Web scraper is more robust if page never idles.
- Improved token and cost reporting for infinite output.
- Improvements and bug fixes for `/read` only files.
- Switched from `setup.py` to `pyproject.toml`, by @branchvincent.
- Bug fix to persist files added during `/ask`.
- Bug fix for chat history size in `/tokens`.
- Aider wrote 66% of the code in this release.

### Aider v0.49.1

- Bugfix to `/help`.

### Aider v0.49.0

- Add read-only files to the chat context with `/read` and `--read`,  including from outside the git repo.
- `/diff` now shows diffs of all changes resulting from your request, including lint and test fixes.
- New `/clipboard` command to paste images or text from the clipboard, replaces `/add-clipboard-image`.
- Now shows the markdown scraped when you add a url with `/web`.
- When [scripting aider](https://aider.chat/docs/scripting.html) messages can now contain in-chat `/` commands.
- Aider in docker image now suggests the correct command to update to latest version.
- Improved retries on API errors (was easy to test during Sonnet outage).
- Added `--mini` for `gpt-4o-mini`.
- Bugfix to keep session cost accurate when using `/ask` and `/help`.
- Performance improvements for repo map calculation.
- `/tokens` now shows the active model.
- Enhanced commit message attribution options:
  - New `--attribute-commit-message-author` to prefix commit messages with 'aider: ' if aider authored the changes, replaces `--attribute-commit-message`.
  - New `--attribute-commit-message-committer` to prefix all commit messages with 'aider: '.
- Aider wrote 61% of the code in this release.

### Aider v0.48.1

- Added `openai/gpt-4o-2024-08-06`.
- Worked around litellm bug that removes OpenRouter app headers when using `extra_headers`.
- Improved progress indication during repo map processing.
- Corrected instructions for upgrading the docker container to latest aider version.
- Removed obsolete 16k token limit on commit diffs, use per-model limits.

### Aider v0.48.0

- Performance improvements for large/mono repos.
- Added `--subtree-only` to limit aider to current directory subtree.
  - Should help with large/mono repo performance.
- New `/add-clipboard-image` to add images to the chat from your clipboard.
- Use `--map-tokens 1024` to use repo map with any model.
- Support for Sonnet's 8k output window.
  - [Aider already supported infinite output from Sonnet.](https://aider.chat/2024/07/01/sonnet-not-lazy.html)
- Workaround litellm bug for retrying API server errors.
- Upgraded dependencies, to pick up litellm bug fixes.
- Aider wrote 44% of the code in this release.

### Aider v0.47.1

- Improvements to conventional commits prompting.

### Aider v0.47.0

- [Commit message](https://aider.chat/docs/git.html#commit-messages) improvements:
  - Added Conventional Commits guidelines to commit message prompt.
  - Added `--commit-prompt` to customize the commit message prompt.
  - Added strong model as a fallback for commit messages (and chat summaries).
- [Linting](https://aider.chat/docs/usage/lint-test.html) improvements:
  - Ask before fixing lint errors.
  - Improved performance of `--lint` on all dirty files in repo.
  - Improved lint flow, now doing code edit auto-commit before linting.
  - Bugfix to properly handle subprocess encodings (also for `/run`).
- Improved [docker support](https://aider.chat/docs/install/docker.html):
  - Resolved permission issues when using `docker run --user xxx`.
  - New `paulgauthier/aider-full` docker image, which includes all extras.
- Switching to code and ask mode no longer summarizes the chat history.
- Added graph of aider's contribution to each release.
- Generic auto-completions are provided for `/commands` without a completion override.
- Fixed broken OCaml tags file.
- Bugfix in `/run` add to chat approval logic.
- Aider wrote 58% of the code in this release.

### Aider v0.46.1

- Downgraded stray numpy dependency back to 1.26.4.

### Aider v0.46.0

- New `/ask <question>` command to ask about your code, without making any edits.
- New `/chat-mode <mode>` command to switch chat modes:
  - ask: Ask questions about your code without making any changes.
  - code: Ask for changes to your code (using the best edit format).
  - help: Get help about using aider (usage, config, troubleshoot).
- Add `file: CONVENTIONS.md` to `.aider.conf.yml` to always load a specific file.
  - Or `file: [file1, file2, file3]` to always load multiple files.
- Enhanced token usage and cost reporting. Now works when streaming too.
- Filename auto-complete for `/add` and `/drop` is now case-insensitive.
- Commit message improvements:
  - Updated commit message prompt to use imperative tense.
  - Fall back to main model if weak model is unable to generate a commit message.
- Stop aider from asking to add the same url to the chat multiple times.
- Updates and fixes to `--no-verify-ssl`:
  - Fixed regression that broke it in v0.42.0.
  - Disables SSL certificate verification when `/web` scrapes websites.
- Improved error handling and reporting in `/web` scraping functionality
- Fixed syntax error in Elm's tree-sitter scm file (by @cjoach).
- Handle UnicodeEncodeError when streaming text to the terminal.
- Updated dependencies to latest versions.
- Aider wrote 45% of the code in this release.

### Aider v0.45.1

- Use 4o-mini as the weak model wherever 3.5-turbo was used.

### Aider v0.45.0

- GPT-4o mini scores similar to the original GPT 3.5, using whole edit format.
- Aider is better at offering to add files to the chat on Windows.
- Bugfix corner cases for `/undo` with new files or new repos.
- Now shows last 4 characters of API keys in `--verbose` output.
- Bugfix to precedence of multiple `.env` files.
- Bugfix to gracefully handle HTTP errors when installing pandoc.
- Aider wrote 42% of the code in this release.

### Aider v0.44.0

- Default pip install size reduced by 3-12x.
- Added 3 package extras, which aider will offer to install when needed:
  - `aider-chat[help]`
  - `aider-chat[browser]`
  - `aider-chat[playwright]`
- Improved regex for detecting URLs in user chat messages.
- Bugfix to globbing logic when absolute paths are included in `/add`.
- Simplified output of `--models`.
- The `--check-update` switch was renamed to `--just-check-updated`.
- The `--skip-check-update` switch was renamed to `--[no-]check-update`.
- Aider wrote 29% of the code in this release (157/547 lines).

### Aider v0.43.4

- Added scipy back to main requirements.txt.

### Aider v0.43.3

- Added build-essentials back to main Dockerfile.

### Aider v0.43.2

- Moved HuggingFace embeddings deps into [hf-embed] extra.
- Added [dev] extra.

### Aider v0.43.1

- Replace the torch requirement with the CPU only version, because the GPU versions are huge.

### Aider v0.43.0

- Use `/help <question>` to [ask for help about using aider](https://aider.chat/docs/troubleshooting/support.html), customizing settings, troubleshooting, using LLMs, etc.
- Allow multiple use of `/undo`.
- All config/env/yml/json files now load from home, git root, cwd and named command line switch.
- New `$HOME/.aider/caches` dir for app-wide expendable caches.
- Default `--model-settings-file` is now `.aider.model.settings.yml`.
- Default `--model-metadata-file` is now `.aider.model.metadata.json`.
- Bugfix affecting launch with `--no-git`.
- Aider wrote 9% of the 424 lines edited in this release.

### Aider v0.42.0

- Performance release:
  - 5X faster launch!
  - Faster auto-complete in large git repos (users report ~100X speedup)!

### Aider v0.41.0

- [Allow Claude 3.5 Sonnet to stream back >4k tokens!](https://aider.chat/2024/07/01/sonnet-not-lazy.html)
  - It is the first model capable of writing such large coherent, useful code edits.
  - Do large refactors or generate multiple files of new code in one go.
- Aider now uses `claude-3-5-sonnet-20240620` by default if `ANTHROPIC_API_KEY` is set in the environment.
- [Enabled image support](https://aider.chat/docs/usage/images-urls.html) for 3.5 Sonnet and for GPT-4o & 3.5 Sonnet via OpenRouter (by @yamitzky).
- Added `--attribute-commit-message` to prefix aider's commit messages with "aider:".
- Fixed regression in quality of one-line commit messages.
- Automatically retry on Anthropic `overloaded_error`.
- Bumped dependency versions.

### Aider v0.40.6

- Fixed `/undo` so it works regardless of `--attribute` settings.

### Aider v0.40.5

- Bump versions to pickup latest litellm to fix streaming issue with Gemini
  - https://github.com/BerriAI/litellm/issues/4408

### Aider v0.40.1

- Improved context awareness of repomap.
- Restored proper `--help` functionality.

### Aider v0.40.0

- Improved prompting to discourage Sonnet from wasting tokens emitting unchanging code (#705).
- Improved error info for token limit errors.
- Options to suppress adding "(aider)" to the [git author and committer names](https://aider.chat/docs/git.html#commit-attribution).
- Use `--model-settings-file` to customize per-model settings, like use of repo-map (by @caseymcc).
- Improved invocation of flake8 linter for python code.


### Aider v0.39.0

- Use `--sonnet` for Claude 3.5 Sonnet, which is the top model on [aider's LLM code editing leaderboard](https://aider.chat/docs/leaderboards/#claude-35-sonnet-takes-the-top-spot).
- All `AIDER_xxx` environment variables can now be set in `.env` (by @jpshack-at-palomar).
- Use `--llm-history-file` to log raw messages sent to the LLM (by @daniel-vainsencher).
- Commit messages are no longer prefixed with "aider:". Instead the git author and committer names have "(aider)" added.

### Aider v0.38.0

- Use `--vim` for [vim keybindings](https://aider.chat/docs/usage/commands.html#vi) in the chat.
- [Add LLM metadata](https://aider.chat/docs/llms/warnings.html#specifying-context-window-size-and-token-costs) via `.aider.models.json` file (by @caseymcc).
- More detailed [error messages on token limit errors](https://aider.chat/docs/troubleshooting/token-limits.html).
- Single line commit messages, without the recent chat messages.
- Ensure `--commit --dry-run` does nothing.
- Have playwright wait for idle network to better scrape js sites.
- Documentation updates, moved into website/ subdir.
- Moved tests/ into aider/tests/.

### Aider v0.37.0

- Repo map is now optimized based on text of chat history as well as files added to chat.
- Improved prompts when no files have been added to chat to solicit LLM file suggestions.
- Aider will notice if you paste a URL into the chat, and offer to scrape it.
- Performance improvements the repo map, especially in large repos.
- Aider will not offer to add bare filenames like `make` or `run` which may just be words.
- Properly override `GIT_EDITOR` env for commits if it is already set.
- Detect supported audio sample rates for `/voice`.
- Other small bug fixes.

### Aider v0.36.0

- [Aider can now lint your code and fix any errors](https://aider.chat/2024/05/22/linting.html).
  - Aider automatically lints and fixes after every LLM edit.
  - You can manually lint-and-fix files with `/lint` in the chat or `--lint` on the command line.
  - Aider includes built in basic linters for all supported tree-sitter languages.
  - You can also configure aider to use your preferred linter with `--lint-cmd`.
- Aider has additional support for running tests and fixing problems.
  - Configure your testing command with `--test-cmd`.
  - Run tests with `/test` or from the command line with `--test`.
  - Aider will automatically attempt to fix any test failures.
  

### Aider v0.35.0

- Aider now uses GPT-4o by default.
  - GPT-4o tops the [aider LLM code editing leaderboard](https://aider.chat/docs/leaderboards/) at 72.9%, versus 68.4% for Opus.
  - GPT-4o takes second on [aider's refactoring leaderboard](https://aider.chat/docs/leaderboards/#code-refactoring-leaderboard) with 62.9%, versus Opus at 72.3%.
- Added `--restore-chat-history` to restore prior chat history on launch, so you can continue the last conversation.
- Improved reflection feedback to LLMs using the diff edit format.
- Improved retries on `httpx` errors.

### Aider v0.34.0

- Updated prompting to use more natural phrasing about files, the git repo, etc. Removed reliance on read-write/read-only terminology.
- Refactored prompting to unify some phrasing across edit formats.
- Enhanced the canned assistant responses used in prompts.
- Added explicit model settings for `openrouter/anthropic/claude-3-opus`, `gpt-3.5-turbo`
- Added `--show-prompts` debug switch.
- Bugfix: catch and retry on all litellm exceptions.


### Aider v0.33.0

- Added native support for [Deepseek models](https://aider.chat/docs/llms.html#deepseek) using `DEEPSEEK_API_KEY` and `deepseek/deepseek-chat`, etc rather than as a generic OpenAI compatible API.

### Aider v0.32.0

- [Aider LLM code editing leaderboards](https://aider.chat/docs/leaderboards/) that rank popular models according to their ability to edit code.
  - Leaderboards include GPT-3.5/4 Turbo, Opus, Sonnet, Gemini 1.5 Pro, Llama 3, Deepseek Coder & Command-R+.
- Gemini 1.5 Pro now defaults to a new diff-style edit format (diff-fenced), enabling it to work better with larger code bases.
- Support for Deepseek-V2, via more a flexible config of system messages in the diff edit format.
- Improved retry handling on errors from model APIs.
- Benchmark outputs results in YAML, compatible with leaderboard.

### Aider v0.31.0

- [Aider is now also AI pair programming in your browser!](https://aider.chat/2024/05/02/browser.html) Use the `--browser` switch to launch an experimental browser based version of aider.
- Switch models during the chat with `/model <name>` and search the list of available models with `/models <query>`.

### Aider v0.30.1

- Adding missing `google-generativeai` dependency

### Aider v0.30.0

- Added [Gemini 1.5 Pro](https://aider.chat/docs/llms.html#free-models) as a recommended free model.
- Allow repo map for "whole" edit format.
- Added `--models <MODEL-NAME>` to search the available models.
- Added `--no-show-model-warnings` to silence model warnings.

### Aider v0.29.2

- Improved [model warnings](https://aider.chat/docs/llms.html#model-warnings) for unknown or unfamiliar models

### Aider v0.29.1

- Added better support for groq/llama3-70b-8192

### Aider v0.29.0

- Added support for [directly connecting to Anthropic, Cohere, Gemini and many other LLM providers](https://aider.chat/docs/llms.html).
- Added `--weak-model <model-name>` which allows you to specify which model to use for commit messages and chat history summarization.
- New command line switches for working with popular models:
  - `--4-turbo-vision`
  - `--opus`
  - `--sonnet`
  - `--anthropic-api-key`
- Improved "whole" and "diff" backends to better support [Cohere's free to use Command-R+ model](https://aider.chat/docs/llms.html#cohere).
- Allow `/add` of images from anywhere in the filesystem.
- Fixed crash when operating in a repo in a detached HEAD state.
- Fix: Use the same default model in CLI and python scripting.

### Aider v0.28.0

- Added support for new `gpt-4-turbo-2024-04-09` and `gpt-4-turbo` models.
  - Benchmarked at 61.7% on Exercism benchmark, comparable to `gpt-4-0613` and worse than the `gpt-4-preview-XXXX` models. See [recent Exercism benchmark results](https://aider.chat/2024/03/08/claude-3.html).
  - Benchmarked at 34.1% on the refactoring/laziness benchmark, significantly worse than the `gpt-4-preview-XXXX` models. See [recent refactor bencmark results](https://aider.chat/2024/01/25/benchmarks-0125.html).
  - Aider continues to default to `gpt-4-1106-preview` as it performs best on both benchmarks, and significantly better on the refactoring/laziness benchmark.

### Aider v0.27.0

- Improved repomap support for typescript, by @ryanfreckleton.
- Bugfix: Only /undo the files which were part of the last commit, don't stomp other dirty files
- Bugfix: Show clear error message when OpenAI API key is not set.
- Bugfix: Catch error for obscure languages without tags.scm file.

### Aider v0.26.1

- Fixed bug affecting parsing of git config in some environments.

### Aider v0.26.0

- Use GPT-4 Turbo by default.
- Added `-3` and `-4` switches to use GPT 3.5 or GPT-4 (non-Turbo).
- Bug fix to avoid reflecting local git errors back to GPT.
- Improved logic for opening git repo on launch.

### Aider v0.25.0

- Issue a warning if user adds too much code to the chat.
  - https://aider.chat/docs/faq.html#how-can-i-add-all-the-files-to-the-chat
- Vocally refuse to add files to the chat that match `.aiderignore`
  - Prevents bug where subsequent git commit of those files will fail.
- Added `--openai-organization-id` argument.
- Show the user a FAQ link if edits fail to apply.
- Made past articles part of https://aider.chat/blog/

### Aider v0.24.1

- Fixed bug with cost computations when --no-steam in effect

### Aider v0.24.0

- New `/web <url>` command which scrapes the url, turns it into fairly clean markdown and adds it to the chat.
- Updated all OpenAI model names, pricing info
- Default GPT 3.5 model is now `gpt-3.5-turbo-0125`.
- Bugfix to the `!` alias for `/run`.

### Aider v0.23.0

- Added support for `--model gpt-4-0125-preview` and OpenAI's alias `--model gpt-4-turbo-preview`. The `--4turbo` switch remains an alias for `--model gpt-4-1106-preview` at this time.
- New `/test` command that runs a command and adds the output to the chat on non-zero exit status.
- Improved streaming of markdown to the terminal.
- Added `/quit` as alias for `/exit`.
- Added `--skip-check-update` to skip checking for the update on launch.
- Added `--openrouter` as a shortcut for `--openai-api-base https://openrouter.ai/api/v1`
- Fixed bug preventing use of env vars `OPENAI_API_BASE, OPENAI_API_TYPE, OPENAI_API_VERSION, OPENAI_API_DEPLOYMENT_ID`.

### Aider v0.22.0

- Improvements for unified diff editing format.
- Added ! as an alias for /run.
- Autocomplete for /add and /drop now properly quotes filenames with spaces.
- The /undo command asks GPT not to just retry reverted edit.

### Aider v0.21.1

- Bugfix for unified diff editing format.
- Added --4turbo and --4 aliases for --4-turbo.

### Aider v0.21.0

- Support for python 3.12.
- Improvements to unified diff editing format.
- New `--check-update` arg to check if updates are available and exit with status code.

### Aider v0.20.0

- Add images to the chat to automatically use GPT-4 Vision, by @joshuavial

- Bugfixes:
  - Improved unicode encoding for `/run` command output, by @ctoth
  - Prevent false auto-commits on Windows, by @ctoth

### Aider v0.19.1

- Removed stray debug output.

### Aider v0.19.0

- [Significantly reduced "lazy" coding from GPT-4 Turbo due to new unified diff edit format](https://aider.chat/docs/unified-diffs.html)
  - Score improves from 20% to 61% on new "laziness benchmark".
  - Aider now uses unified diffs by default for `gpt-4-1106-preview`.
- New `--4-turbo` command line switch as a shortcut for `--model gpt-4-1106-preview`.

### Aider v0.18.1

- Upgraded to new openai python client v1.3.7.

### Aider v0.18.0

- Improved prompting for both GPT-4 and GPT-4 Turbo.
  - Far fewer edit errors from GPT-4 Turbo (`gpt-4-1106-preview`).
  - Significantly better benchmark results from the June GPT-4 (`gpt-4-0613`). Performance leaps from 47%/64% up to 51%/71%.
- Fixed bug where in-chat files were marked as both read-only and ready-write, sometimes confusing GPT.
- Fixed bug to properly handle repos with submodules.

### Aider v0.17.0

- Support for OpenAI's new 11/06 models:
  - gpt-4-1106-preview with 128k context window
  - gpt-3.5-turbo-1106 with 16k context window
- [Benchmarks for OpenAI's new 11/06 models](https://aider.chat/docs/benchmarks-1106.html)
- Streamlined [API for scripting aider, added docs](https://aider.chat/docs/faq.html#can-i-script-aider)
- Ask for more concise SEARCH/REPLACE blocks. [Benchmarked](https://aider.chat/docs/benchmarks.html) at 63.9%, no regression.
- Improved repo-map support for elisp.
- Fixed crash bug when `/add` used on file matching `.gitignore`
- Fixed misc bugs to catch and handle unicode decoding errors.

### Aider v0.16.3

- Fixed repo-map support for C#.

### Aider v0.16.2

- Fixed docker image.

### Aider v0.16.1

- Updated tree-sitter dependencies to streamline the pip install process

### Aider v0.16.0

- [Improved repository map using tree-sitter](https://aider.chat/docs/repomap.html)
- Switched from "edit block" to "search/replace block", which reduced malformed edit blocks. [Benchmarked](https://aider.chat/docs/benchmarks.html) at 66.2%, no regression.
- Improved handling of malformed edit blocks targeting multiple edits to the same file. [Benchmarked](https://aider.chat/docs/benchmarks.html) at 65.4%, no regression.
- Bugfix to properly handle malformed `/add` wildcards.


### Aider v0.15.0

- Added support for `.aiderignore` file, which instructs aider to ignore parts of the git repo.
- New `--commit` cmd line arg, which just commits all pending changes with a sensible commit message generated by gpt-3.5.
- Added universal ctags and multiple architectures to the [aider docker image](https://aider.chat/docs/install/docker.html)
- `/run` and `/git` now accept full shell commands, like: `/run (cd subdir; ls)`
- Restored missing `--encoding` cmd line switch.

### Aider v0.14.2

- Easily [run aider from a docker image](https://aider.chat/docs/install/docker.html)
- Fixed bug with chat history summarization.
- Fixed bug if `soundfile` package not available.

### Aider v0.14.1

- /add and /drop handle absolute filenames and quoted filenames
- /add checks to be sure files are within the git repo (or root)
- If needed, warn users that in-chat file paths are all relative to the git repo
- Fixed /add bug in when aider launched in repo subdir
- Show models supported by api/key if requested model isn't available

### Aider v0.14.0

- [Support for Claude2 and other LLMs via OpenRouter](https://aider.chat/docs/faq.html#accessing-other-llms-with-openrouter) by @joshuavial
- Documentation for [running the aider benchmarking suite](https://github.com/Aider-AI/aider/tree/main/benchmark)
- Aider now requires Python >= 3.9


### Aider v0.13.0

- [Only git commit dirty files that GPT tries to edit](https://aider.chat/docs/faq.html#how-did-v0130-change-git-usage)
- Send chat history as prompt/context for Whisper voice transcription
- Added `--voice-language` switch to constrain `/voice` to transcribe to a specific language
- Late-bind importing `sounddevice`, as it was slowing down aider startup
- Improved --foo/--no-foo switch handling for command line and yml config settings

### Aider v0.12.0

- [Voice-to-code](https://aider.chat/docs/usage/voice.html) support, which allows you to code with your voice.
- Fixed bug where /diff was causing crash.
- Improved prompting for gpt-4, refactor of editblock coder.
- [Benchmarked](https://aider.chat/docs/benchmarks.html) at 63.2% for gpt-4/diff, no regression.

### Aider v0.11.1

- Added a progress bar when initially creating a repo map.
- Fixed bad commit message when adding new file to empty repo.
- Fixed corner case of pending chat history summarization when dirty committing.
- Fixed corner case of undefined `text` when using `--no-pretty`.
- Fixed /commit bug from repo refactor, added test coverage.
- [Benchmarked](https://aider.chat/docs/benchmarks.html) at 53.4% for gpt-3.5/whole (no regression).

### Aider v0.11.0

- Automatically summarize chat history to avoid exhausting context window.
- More detail on dollar costs when running with `--no-stream`
- Stronger GPT-3.5 prompt against skipping/eliding code in replies (51.9% [benchmark](https://aider.chat/docs/benchmarks.html), no regression)
- Defend against GPT-3.5 or non-OpenAI models suggesting filenames surrounded by asterisks.
- Refactored GitRepo code out of the Coder class.

### Aider v0.10.1

- /add and /drop always use paths relative to the git root
- Encourage GPT to use language like "add files to the chat" to ask users for permission to edit them.

### Aider v0.10.0

- Added `/git` command to run git from inside aider chats.
- Use Meta-ENTER (Esc+ENTER in some environments) to enter multiline chat messages.
- Create a `.gitignore` with `.aider*` to prevent users from accidentally adding aider files to git.
- Check pypi for newer versions and notify user.
- Updated keyboard interrupt logic so that 2 ^C in 2 seconds always forces aider to exit.
- Provide GPT with detailed error if it makes a bad edit block, ask for a retry.
- Force `--no-pretty` if aider detects it is running inside a VSCode terminal.
- [Benchmarked](https://aider.chat/docs/benchmarks.html) at 64.7% for gpt-4/diff (no regression)


### Aider v0.9.0

- Support for the OpenAI models in [Azure](https://aider.chat/docs/faq.html#azure)
- Added `--show-repo-map`
- Improved output when retrying connections to the OpenAI API
- Redacted api key from `--verbose` output
- Bugfix: recognize and add files in subdirectories mentioned by user or GPT
- [Benchmarked](https://aider.chat/docs/benchmarks.html) at 53.8% for gpt-3.5-turbo/whole (no regression)

### Aider v0.8.3

- Added `--dark-mode` and `--light-mode` to select colors optimized for terminal background
- Install docs link to [NeoVim plugin](https://github.com/joshuavial/aider.nvim) by @joshuavial
- Reorganized the `--help` output
- Bugfix/improvement to whole edit format, may improve coding editing for GPT-3.5
- Bugfix and tests around git filenames with unicode characters
- Bugfix so that aider throws an exception when OpenAI returns InvalidRequest
- Bugfix/improvement to /add and /drop to recurse selected directories
- Bugfix for live diff output when using "whole" edit format

### Aider v0.8.2

- Disabled general availability of gpt-4 (it's rolling out, not 100% available yet)

### Aider v0.8.1

- Ask to create a git repo if none found, to better track GPT's code changes
- Glob wildcards are now supported in `/add` and `/drop` commands
- Pass `--encoding` into ctags, require it to return `utf-8`
- More robust handling of filepaths, to avoid 8.3 windows filenames
- Added [FAQ](https://aider.chat/docs/faq.html)
- Marked GPT-4 as generally available
- Bugfix for live diffs of whole coder with missing filenames
- Bugfix for chats with multiple files
- Bugfix in editblock coder prompt

### Aider v0.8.0

- [Benchmark comparing code editing in GPT-3.5 and GPT-4](https://aider.chat/docs/benchmarks.html)
- Improved Windows support:
  - Fixed bugs related to path separators in Windows
  - Added a CI step to run all tests on Windows
- Improved handling of Unicode encoding/decoding
  - Explicitly read/write text files with utf-8 encoding by default (mainly benefits Windows)
  - Added `--encoding` switch to specify another encoding
  - Gracefully handle decoding errors
- Added `--code-theme` switch to control the pygments styling of code blocks (by @kwmiebach)
- Better status messages explaining the reason when ctags is disabled

### Aider v0.7.2:

- Fixed a bug to allow aider to edit files that contain triple backtick fences.

### Aider v0.7.1:

- Fixed a bug in the display of streaming diffs in GPT-3.5 chats

### Aider v0.7.0:

- Graceful handling of context window exhaustion, including helpful tips.
- Added `--message` to give GPT that one instruction and then exit after it replies and any edits are performed.
- Added `--no-stream` to disable streaming GPT responses.
  - Non-streaming responses include token usage info.
  - Enables display of cost info based on OpenAI advertised pricing.
- Coding competence benchmarking tool against suite of programming tasks based on Execism's python repo.
  - https://github.com/exercism/python
- Major refactor in preparation for supporting new function calls api.
- Initial implementation of a function based code editing backend for 3.5.
  - Initial experiments show that using functions makes 3.5 less competent at coding.
- Limit automatic retries when GPT returns a malformed edit response.

### Aider v0.6.2

* Support for `gpt-3.5-turbo-16k`, and all OpenAI chat models
* Improved ability to correct when gpt-4 omits leading whitespace in code edits
* Added `--openai-api-base` to support API proxies, etc.

### Aider v0.5.0

- Added support for `gpt-3.5-turbo` and `gpt-4-32k`.
- Added `--map-tokens` to set a token budget for the repo map, along with a PageRank based algorithm for prioritizing which files and identifiers to include in the map.
- Added in-chat command `/tokens` to report on context window token usage.
- Added in-chat command `/clear` to clear the conversation history.
