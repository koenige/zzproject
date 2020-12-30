# Zugzwang Project: Modules

## Installation

Modules are installed inside the folder `_inc/modules`. Each module must have a unique name. It is recommended to install them as submodule via `git`. If downloaded from git then run: `git submodule update --init`

## Creation of a module

This is the recommended file structure for a module `example`:

- `_inc/example/behaviour`
- `_inc/example/docs`
- `_inc/example/docs/sql`
- `_inc/example/example` (i. e. the name of the module)
- `_inc/example/layout`
- `_inc/example/libraries`
- `_inc/example/templates`
- `_inc/example/zzbrick_forms`
- `_inc/example/zzbrick_make`
- `_inc/example/zzbrick_page`
- `_inc/example/zzbrick_request`
- `_inc/example/zzbrick_request_get`
- `_inc/example/zzbrick_tables`
- `_inc/example/zzform`
- `_inc/example/zzwrap_sql`

For a start, you normally don’t need all these folders.

### Files inside main folder

- `/config.inc.php` – local configuration
- `/README.md` – ReadMe
- `/LICENSE.md` – License

### Files: `/behaviour`

This folder is for your own JavaScript files. It is recommended to put complete external JavaScript libraries inside the folder `/www/_behaviour`. A file `/behaviour/test.js` can be accessed via this URL: `example.org/_behaviour/example/test.js`. It is treated as a zzbrick template, you can put %%% blocks inside it.

### Files: `/docs/sql`

- `/docs/sql/install.sql` SQL install script
- `/docs/sql/update.sql` SQL update script, indexed with comment by date and sequence, e. g. `/* 2020-09-10-1 */` followed by a tab
- `/docs/sql/settings.cfg` INI file with possible settings for this module (recommended: use module name as prefix for settings)

### Files: `/example`

This folder has the same name as the module itself. It might contain language files:

- `/example/example.pot` - PO template file
- `/example/example-de.po` - German language PO file
- `/example/_functions.inc.php` - Common functions which are always included. It is recommended to use `mf_` plus the module name, i. e. here `mf_example_`, as a prefix for each function.

### Files: `/layout`

This folder is for your own layout files, CSS and graphics. A file `/layout/test.csss` can be accessed via this URL: `example.org/_layout/example/test.css`. It is treated as a zzbrick template, you can put %%% blocks inside it.

### Files: `/templates`

For webpage and mail templates for use with `zzbrick`

- `example-page.template.txt` complete HTML page (template name ending with `-page`)
- `example1.template.txt` HTML fragment; template with equal name in `/templates/` folder overwrites this template
- `example1-de.template.txt` HTML fragment; German version (if exists, is preferred over `example1.template.txt`) – use with ISO codes and language variants, e. g. `de-informal` for German with “Du”
- `feedback-mail.template.txt` Mail template, first lines can be mail headers like `Subject: Test`, empty line separates mail header lines from body

### Files: `/zzbrick_forms`

Form definitions, based on table definitions in folder `/zzbrick_tables`, for use with `zzform` module.

- Filename: `table_name.php`
- Include in template via `%%% forms table_name %%%`

### Files: `/zzbrick_make`

Make functions. Similar to request functions below, these functions change data via POST requests.

- Function names: start with `mod_example_make_`
- Filename for `mod_example_make_test()` function is `test.inc.php`
- Include in template via `%%% make test %%%`

### Files: `/zzbrick_page`

Page functions.

- Function names: start with `page_`
- Filename for `page_test()` function is `test.inc.php`
- Include in template via `%%% page test %%%`

### Files: `/zzbrick_request`

Request functions.

- Function names: start with `mod_example_`
- Filename for `mod_example_test()` function is `test.inc.php`
- Include in template via `%%% request test %%%`

### Files: `/zzbrick_request_get`

Request/Get functions. If setting `brick_cms_input` is active, a function in this folder is automatically used for request functions to read data.

- Function names: start with `mod_example_get`

### Files: `/zzbrick_tables`

Definition files for single tables (or tables with subtables) for use with `zzform` module.

- Filename: `table_name.php`
- Include in template via `%%% tables table_name %%%`

### Files: `/zzform`

- `editing.inc.php` – functions used in table definition scripts to reformat values when validating input
- `hooks.inc.php` – Hook functions for zzform module, called after/before upload, insert, update or delete

It is recommended to use `mf_` plus the module name, i. e. here `mf_example_`, as a prefix for each function.

## Contact

Gustaf Mossakowski <gustaf@koenige.org> or <https://www.koenige.org>
Zugzwang Project: <https://www.zugzwang.org>
