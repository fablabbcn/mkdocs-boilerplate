# Demo includes

!!! warning "Advanced"
	Make sure you check the source code of this page to understand what's going on, as it can be confusing...

## Same project includes

This will include the snippet from the same directory:

{{ get_snippet_rel('docs/index.md')}}

!!! warning "Paths"
	Note that the paths inside the functions are relative to the `repository`, while the paths inside the markdown files are rleat

You can also select a section:

{{ get_snippet_rel('docs/index.md', '## Commands')}}

!!! warning "Check locally first"
	Check the output of your local development mkdocs server before deploying.

	**Also, make sure you set all the links/images with absolute paths**:

		- This is good:  `![](/assets/images/photo.png)`
		- This is **bad**:  `![](/assets/images/photo.png)`

## Remote includes

You can do the same from an external url (it has to be a `.md` file if you want it to be rendered):

{{ get_snippet_url('https://raw.githubusercontent.com/fablabbcn/smartcitizen-docs/master/docs/index.md', '## Sections')}}

Or from an external git repo (same as above) - **but very slow!** (make sure it has https or your repo has access to the remote git repo):

{{ get_snippet_git('https://github.com/fablabbcn/smartcitizen-docs.git', 'docs/Guides/deployments/Water sensors.md', '# Water sensors')}}

!!! warning "May take a while"
	It may take a while if you use this last option because the repo is cloned everytime. It is clone in your `/tmp` folder - so if something doesn't work check your terminal output (not tested on every platform)

!!! info "Credit"
	This is an extension of the functionality given by [`mkdocs-snippet-plugin`](https://github.com/mprivat/mkdocs-snippet-plugin) and the [markdown snippet](https://facelessuser.github.io/pymdown-extensions/extensions/snippets/) extension.

	This simply tries to combine both in a simpler way.
