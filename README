# PHPWebBuilder (later Kusala)

A component-based web application framework for PHP, built by Alejandro Siri and Mariano Montone between 2005 and 2011 in La Plata, Argentina. This repository is an archive of the original SourceForge Subversion history (1,778 commits, March 2006 – January 2011).

The framework was inspired by Seaside (Smalltalk) and tried to bring its programming model, and a lot of Smalltalk along with it, to PHP 4 and 5. It was later renamed Kusala and became the subject of the authors' thesis at the Facultad de Informática, Universidad Nacional de La Plata.

This code is kept for historical interest. It targets PHP 4/5 and is not maintained.

## What it did

**Components instead of pages.** Applications are trees of stateful components. A component can `call` another one, which takes over its place in the page until it `answer`s (called `callback` in the code). Flow control is modal and local to the component, as in Seaside, but built on callbacks, since PHP had no continuations.

**Declarative templates and streaming DOM updates.** Templates are pure XML with `<template>` and `<container>` tags: no loops, no code. Because the framework owns the mapping from components to view nodes, it records every change to the server-side view tree (`View/XML/XMLNodeModificationsTracker.class.php`) and sends only those modifications to the browser. Switching between full-page, AJAX and Comet rendering is a single configuration setting (`page_renderer`).

**A live session over Comet.** With `CometPageRenderer`, the application stays alive in a long-running PHP process per user. Requests are relayed to it by message passing, so the session is never reloaded, and the server can push updates caused by other sessions.

**Composable edit transactions.** Each chain of editing components gets its own in-memory transaction, found through a dynamic variable scoped to the component thread. Cancel undoes only that editor's changes; concurrent conflicts are detected with version numbers on commit.

**Persistence and querying.** Metadata-described persistent objects, schema generation and diffing, persistence by reachability, and OQL, an object query language embedded in PHP through macros.

**Extending PHP from inside PHP.** A PHP-to-PHP compiler with macros (`#@macro … @#`), mixins, multiple and context-dependent dispatch, weak references, typechecks and assertions that compile away in production, and single-file output that only includes the classes an application uses.

**PHPCC.** A parser generator used to implement OQL (`lib/Compiler/`). It is top-down and supports left-recursive grammars by detecting when a rule re-enters itself and then growing the parse from a seed.

## Where to look

| Path | Contents |
|---|---|
| `Application/` | Components, call/callback, events, sessions |
| `View/` | Templates, page renderers (standard, AJAX, Comet, XUL), DOM modification tracking |
| `Model/` | Persistent objects, fields, value models, OQL reports |
| `lib/Compiler/`, `lib/Compiler.class.php` | PHPCC and the macro compiler |
| `DefaultCMS/`, `examples/` | A generated CMS and example applications |
| `doc/versions/JAIIO2007/` | LaTeX sources of the 2007 paper |

## Publications

- A. Siri, M. Montone. PHPWebBuilder paper, JAIIO 2006.
- A. Siri, M. Montone. *PHPWebBuilder: Framework integral para el desarrollo de aplicaciones Web sobre PHP*. JAIIO 2007 (sources in `doc/versions/JAIIO2007/`).
- A. Siri, M. Montone. *Un framework para el desarrollo de aplicaciones complejas basadas en Web*. Thesis, Facultad de Informática, UNLP.

## License

GNU General Public License version 2 (see `LICENSE`).
