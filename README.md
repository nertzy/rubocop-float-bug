# rubocop-float-bug

Reproduction of [Rubocop issue #13051](https://github.com/rubocop/rubocop/issues/13051).

Run `bundle exec rake` to see the bug in action.


Output:

```
❯ rake
bundle exec rspec spec.rb
.

Finished in 0.00294 seconds (files took 0.04485 seconds to load)
1 example, 0 failures

bundle exec rubocop -d spec.rb
For /Users/grant/projects/rubocop-float-bug: Default configuration from /Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-1.65.0/config/default.yml
Use parallel by default.
Skipping parallel inspection: only a single file needs inspection
Inspecting 1 file
Scanning /Users/grant/projects/rubocop-float-bug/spec.rb
An error occurred while Lint/FloatComparison cop was inspecting /Users/grant/projects/rubocop-float-bug/spec.rb:3:7.
undefined method `value' for an instance of RuboCop::AST::Node
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-1.65.0/lib/rubocop/cop/lint/float_comparison.rb:69:in `literal_zero?'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-1.65.0/lib/rubocop/cop/lint/float_comparison.rb:46:in `on_send'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-1.65.0/lib/rubocop/cop/commissioner.rb:143:in `public_send'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-1.65.0/lib/rubocop/cop/commissioner.rb:143:in `block (2 levels) in trigger_restricted_cops'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-1.65.0/lib/rubocop/cop/commissioner.rb:171:in `with_cop_error_handling'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-1.65.0/lib/rubocop/cop/commissioner.rb:142:in `block in trigger_restricted_cops'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-1.65.0/lib/rubocop/cop/commissioner.rb:141:in `each'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-1.65.0/lib/rubocop/cop/commissioner.rb:141:in `trigger_restricted_cops'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-1.65.0/lib/rubocop/cop/commissioner.rb:70:in `on_send'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-ast-1.31.3/lib/rubocop/ast/traversal.rb:158:in `on_block'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-1.65.0/lib/rubocop/cop/commissioner.rb:71:in `on_block'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-ast-1.31.3/lib/rubocop/ast/traversal.rb:137:in `block in on_dstr'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-ast-1.31.3/lib/rubocop/ast/traversal.rb:137:in `each'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-ast-1.31.3/lib/rubocop/ast/traversal.rb:137:in `on_dstr'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-1.65.0/lib/rubocop/cop/commissioner.rb:71:in `on_begin'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-ast-1.31.3/lib/rubocop/ast/traversal.rb:158:in `on_block'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-1.65.0/lib/rubocop/cop/commissioner.rb:71:in `on_block'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-ast-1.31.3/lib/rubocop/ast/traversal.rb:20:in `walk'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-1.65.0/lib/rubocop/cop/commissioner.rb:87:in `investigate'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-1.65.0/lib/rubocop/cop/team.rb:164:in `investigate_partial'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-1.65.0/lib/rubocop/cop/team.rb:102:in `investigate'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-1.65.0/lib/rubocop/runner.rb:349:in `block in inspect_file'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-1.65.0/lib/rubocop/runner.rb:348:in `each'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-1.65.0/lib/rubocop/runner.rb:348:in `flat_map'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-1.65.0/lib/rubocop/runner.rb:348:in `inspect_file'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-1.65.0/lib/rubocop/runner.rb:291:in `block in do_inspection_loop'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-1.65.0/lib/rubocop/runner.rb:325:in `block in iterate_until_no_changes'
<internal:kernel>:187:in `loop'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-1.65.0/lib/rubocop/runner.rb:318:in `iterate_until_no_changes'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-1.65.0/lib/rubocop/runner.rb:287:in `do_inspection_loop'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-1.65.0/lib/rubocop/runner.rb:168:in `block in file_offenses'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-1.65.0/lib/rubocop/runner.rb:193:in `file_offense_cache'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-1.65.0/lib/rubocop/runner.rb:167:in `file_offenses'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-1.65.0/lib/rubocop/runner.rb:158:in `process_file'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-1.65.0/lib/rubocop/runner.rb:139:in `block in each_inspected_file'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-1.65.0/lib/rubocop/runner.rb:138:in `each'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-1.65.0/lib/rubocop/runner.rb:138:in `reduce'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-1.65.0/lib/rubocop/runner.rb:138:in `each_inspected_file'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-1.65.0/lib/rubocop/runner.rb:124:in `inspect_files'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-1.65.0/lib/rubocop/runner.rb:77:in `run'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-1.65.0/lib/rubocop/cli/command/execute_runner.rb:26:in `block in execute_runner'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-1.65.0/lib/rubocop/cli/command/execute_runner.rb:52:in `with_redirect'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-1.65.0/lib/rubocop/cli/command/execute_runner.rb:25:in `execute_runner'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-1.65.0/lib/rubocop/cli/command/execute_runner.rb:17:in `run'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-1.65.0/lib/rubocop/cli/command.rb:11:in `run'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-1.65.0/lib/rubocop/cli/environment.rb:18:in `run'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-1.65.0/lib/rubocop/cli.rb:122:in `run_command'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-1.65.0/lib/rubocop/cli.rb:129:in `execute_runners'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-1.65.0/lib/rubocop/cli.rb:51:in `block in run'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-1.65.0/lib/rubocop/cli.rb:81:in `profile_if_needed'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-1.65.0/lib/rubocop/cli.rb:43:in `run'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-1.65.0/exe/rubocop:19:in `block in <top (required)>'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/3.3.0/benchmark.rb:313:in `realtime'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-1.65.0/exe/rubocop:19:in `<top (required)>'
/Users/grant/.rbenv/versions/3.3.4/bin/rubocop:25:in `load'
/Users/grant/.rbenv/versions/3.3.4/bin/rubocop:25:in `<top (required)>'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/bundler-2.5.15/lib/bundler/cli/exec.rb:58:in `load'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/bundler-2.5.15/lib/bundler/cli/exec.rb:58:in `kernel_load'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/bundler-2.5.15/lib/bundler/cli/exec.rb:23:in `run'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/bundler-2.5.15/lib/bundler/cli.rb:455:in `exec'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/bundler-2.5.15/lib/bundler/vendor/thor/lib/thor/command.rb:28:in `run'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/bundler-2.5.15/lib/bundler/vendor/thor/lib/thor/invocation.rb:127:in `invoke_command'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/bundler-2.5.15/lib/bundler/vendor/thor/lib/thor.rb:527:in `dispatch'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/bundler-2.5.15/lib/bundler/cli.rb:35:in `dispatch'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/bundler-2.5.15/lib/bundler/vendor/thor/lib/thor/base.rb:584:in `start'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/bundler-2.5.15/lib/bundler/cli.rb:29:in `start'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/bundler-2.5.15/exe/bundle:28:in `block in <top (required)>'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/bundler-2.5.15/lib/bundler/friendly_errors.rb:117:in `with_friendly_errors'
/Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/bundler-2.5.15/exe/bundle:20:in `<top (required)>'
/Users/grant/.rbenv/versions/3.3.4/bin/bundle:25:in `load'
/Users/grant/.rbenv/versions/3.3.4/bin/bundle:25:in `<main>'
C

Offenses:

spec.rb:1:1: C: [Correctable] Style/FrozenStringLiteralComment: Missing frozen string literal comment.
describe '0.2r + 0.2r' do
^

1 file inspected, 1 offense detected, 1 offense autocorrectable

1 error occurred:
An error occurred while Lint/FloatComparison cop was inspecting /Users/grant/projects/rubocop-float-bug/spec.rb:3:7.
configuration from /Users/grant/.rbenv/versions/3.3.4/lib/ruby/gems/3.3.0/gems/rubocop-1.65.0/config/default.yml
Errors are usually caused by RuboCop bugs.
Please, report your problems to RuboCop's issue tracker.
https://github.com/rubocop/rubocop/issues

Mention the following information in the issue report:
1.65.0 (using Parser 3.3.4.0, rubocop-ast 1.31.3, running on ruby 3.3.4) [arm64-darwin23]
Finished in 0.1659060000001773 seconds
rake aborted!
Command failed with status (1): [bundle exec rubocop -d spec.rb]
/Users/grant/projects/rubocop-float-bug/Rakefile:3:in `block in <top (required)>'
Tasks: TOP => default
(See full trace by running task with --trace)
```