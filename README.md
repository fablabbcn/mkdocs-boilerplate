# README

This is a small demo repository for nesting (i.e. including files from the same repo or other repos) in the `mkdocs` building process. Builds on top of the `macros-plugin` and draws from [`mkdocs-snippet-plugin`](https://github.com/mprivat/mkdocs-snippet-plugin) and the [markdown snippet](https://facelessuser.github.io/pymdown-extensions/extensions/snippets/) extension.

Three modes are supported:

* Relative imports (make sure to include the whole path relative to the repo main dir):

```
{{ get_snippet_rel('docs/index.md', '## Commands')}}
```

* Remote imports:

You can do the same from an external url (it has to be a `.md` file if you want it to be rendered):

```
{{ get_snippet_url('https://raw.githubusercontent.com/fablabbcn/smartcitizen-docs/master/docs/index.md', '## Sections')}}
```

Or from an external git repo (same as above) - **but very slow!** (make sure it has https or your repo has access to the remote git repo):

```
{{ get_snippet_git('https://github.com/fablabbcn/smartcitizen-minke-docs', 'docs/Guides/getting started/Debugging your sensors.md', '# Debugging your sensors')}}
```

**May take a while**: It may take a while if you use this last option because the repo is cloned everytime. It is clone in your `/tmp` folder (by default - you can change it in your `mkdocs.yml` file) - so if something doesn't work check your terminal output (not tested on every platform)

When doing it from a remote git repo, make sure to:

- Make the `config.local` to false
- Make sure you understand the:
	- `site_url`: if not specified, it's because you don't have a custom domain. `repo_name` will be used. Otherwise, will leave an empty relative url for deploy
	- `repo_name`: the name of the repo. Normally used for the xxx.github.io/repo_name/
	- `extra.local`: to make it easier to see whether you have a local deployment or not. If you have a domain name set with `site_url` it doesn't really matter
	- `extra.tmp_dir`: where the remote repos will be cloned (default `/tmp`)
	- `extra.base_dir`: the base directory of your documentation with respect to the main dir (default `docs`)
	- `extra.site_dir: the base directory of the build process with respect to the main dir - before moving to deploy branch... (default `site`)
