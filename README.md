# Jump to Tests

<!-- [![build](https://github.com/schmas/vscode-jump-to-tests/workflows/build/badge.svg?branch=master)]() -->

Switch between the code and the test file.

## Features

On MacOS, press `Shift+Cmd+T`.

On Windows / Linux, press `Shift+Ctrl+T`.

The following formats are supported:

| framework               | application file       | unit test file          |
| ----------------------- | ---------------------- | ----------------------- |
| JavaScript / TypeScript | `*.js` †               | `__tests__/*.test.js`   |
| JavaScript / TypeScript | `*.js` †               | `test/*.test.js`        |
| JavaScript / TypeScript | `*.js` †               | `test/suite/*.test.js`  |
| JavaScript / TypeScript | `*.js` †               | `*.test.js`             |
| Python                  | `*.py`                 | `test/test_*.py`        |
| Python                  | `src/*/*.py`           | `test/*/test_*.py`      |
| Go                      | `*.go`                 | `*_test.go`             |
| Ruby on Rails 1-5       | `app/*/*.rb`           | `spec/*/*_spec.rb`      |
| Ruby on Rails 6+        | `app/*/*.rb`           | `test/*/*_test.rb`      |
| Ruby minitest           | `app/*.rb`             | `test/unit/*_test.rb`   |
| Ruby minitest           | `app/controllers/*.rb` | `test/integration/*.rb` |

† Also supports `.jsx`, `.ts`, `.tsx`.

## Requirements

If you have any requirements or dependencies, add a section describing those and how to install and configure them.

## Extension Settings

You can add your own formats by editing `jump-to-tests.rules`.

Here's what it would look like to add Ruby on Rails support:

```json
"jump-to-tests.rules": [
  { "pattern": "app/(.*)\\.rb", "replacement": "spec/$1_spec.rb" },
  { "pattern": "spec/(.*)_spec\\.rb", "replacement": "app/$1.rb" },
]
```

Effectively, this extension runs `path.replace(new RegExp(pattern), replacement)`. If the source file matches the regex the replaced filename exists, you'll switch to that file. Otherwise, it will try the next rule.

## Release Notes

See [CHANGELOG.md](./CHANGELOG.md).

## Similar Projects

- [Test Switcher](https://github.com/bmalehorn/vscode-test-switcher) (Based on this)
- [Rails Go to Spec](https://marketplace.visualstudio.com/items?itemName=sporto.rails-go-to-spec)
- [File Switcher](https://marketplace.visualstudio.com/items?itemName=johnathanludwig.fileswitcher)
