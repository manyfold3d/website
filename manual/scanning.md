---
title: Scanning Files
parent: User Guide
layout: page
nav_order: 2
---

Scanning is the process of checking Manyfold's storage location and detecting any changes or problems.

To run a scan, click the "Scan" button and choose "Scan for new files". The scan button will become inactive and show a spinning icon while the scan runs. You can always tell if a scan is in progress by the state of the button.

![Scan button and menu](/images/manual/scan-button.png){:.screenshot}

A scan will:

1. create new models for anything folder that has been added to the storage location outside Manyfold (for instance, by manual copying);
1. raise errors for any files or folders that are missing;
1. find and index all supported files inside each new model;
1. choose a preview image for each model, or a 3d file if no images are present
1. apply default tags to new models;
1. if enabled, analyse model paths to extract metadata, according to your folder naming and tag settings;
1. detect any problems with the models, such as missing images, files, or models that are nested inside each other;
1. detect which files are supported or unsupported, and attempt to match them together;
1. analyse individual files to measure size and detect duplicates;
1. if enabled, run geometric analysis on files to detect mesh errors.

You can see how the scan is progressing in the background by clicking the "activity" icon in the navigation bar. The page shows which jobs have been queued, run, completed, or failed in the last 24 hours.

![Activity screen](/images/manual/activity.png){:.screenshot}

# Rescanning models

Alternatively, you can choose "Rescan all models" in the scan menu; this will not detect completely new models, but will run integrity checks and metadata parsing across all the models currently in your library.

The check will:

1. detect any problems with all existing models, such as missing images, files, or models that are nested inside each other;
1. parse metadata from local sources, like files, path templates, etc.
1. detect which files are supported or unsupported, and attempt to match them together;
1. analyse individual files to measure size and detect duplicates;
1. if enabled, run geometric analysis on files to detect mesh errors.

The check will also remove any problems that no longer apply.

If you're working with a filtered subset of models (e.g. via a search result, tag filter, etc), you will also have the option in the menu to "Rescan filtered models" which will just run the process on the current result set.
