# Installation



To install these modules, you can use a `Puppetfile`

```text
forge "http://forge.enterprisemodules.com"

mod 'enterprisemodules/ora_install'               ,'x.x.x'
```

Then use the `librarian-puppet` or `r10K` to install the software.

You can also install the software using the `puppet module` command:

```text
puppet module install enterprisemodules-ora_install --version x.x.x
```

