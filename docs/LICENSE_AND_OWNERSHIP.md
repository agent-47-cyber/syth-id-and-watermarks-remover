# License and project ownership

## What this repository currently is

GitHub currently identifies `agent-47-cyber/syth-id-and-watermarks-remover` as a **public fork** of `guillaumemeyer/watermarks-remover`. You control your fork and can develop it independently, but the GitHub page will continue to show the upstream relationship until you detach it. A fork is a separate working copy; it does not transfer copyright in the upstream code to you.

You may describe it as **your project** or **your maintained fork**, as long as you credit the upstream project and do not claim to have authored its existing code. Copyright in your original additions belongs to you (subject to any contribution agreements you accept); the upstream contributors keep copyright in their contributions.

## Current license and practical choices

The checked-in upstream `LICENSE` is MIT. The simplest choice for this derivative is to keep that MIT license and keep the original copyright and permission text. You can add your own copyright line for your original work, without replacing upstream attribution.

If you want a different license for a future version, MIT code can generally be incorporated into projects distributed under other licenses, including Apache-2.0 or GPL-3.0, while preserving the MIT notice for the copied MIT portions. That does **not** let you erase upstream notices or change the license of code you did not write. Apache-2.0 adds express patent terms; GPL-3.0 adds reciprocal source-sharing obligations when distributing covered combined works. Review every dependency and bundled asset before choosing either.

Do not advertise the entire application as MIT or Apache-2.0 without qualification while an optional backend with no published license is installed or distributed. `mertizci/noai-watermark` currently has no license file in the pinned checkout used by the setup script; absent a license, public availability alone does not grant permission to redistribute its source. This project deliberately keeps that backend out of the main repository and its distributable images. Ask its maintainer for permission before bundling, redistributing, or offering it as a service. Model weights may carry separate terms too.

The optional MarkDiffusion code is Apache-2.0 according to its project, but its dependencies and model weights still need separate review. The main repository's MIT license covers the repository's own code; it does not automatically license third-party models or packages.

This is practical project guidance, not legal advice. For a commercial release or a new license choice, get a license scan and legal review.

## Making the GitHub repo standalone

The current repository is a public fork. GitHub provides a **Leave fork network** option for eligible repositories. Detaching is permanent and preserves Git commits, but drops GitHub metadata such as issues, pull requests, stars, watchers, comments, and child forks. Save anything you need before using it. If you do not need GitHub to remove the fork label, simply keep working in the fork and describe it transparently as your maintained project based on upstream.
