---
title: Manyfold ❤️ NLNet
date: 2025-01-01 12:00:00 UTC
layout: post
excerpt_separator: "

"
---
During 2024, Manyfold development was supported by a grant from [NLNet](https://nlnet.nl/), as part of the EU [NGI Zero](https://ngi.eu/ngi-projects/ngi-zero/) R&D programme. That support took the product from a side project to something *real*, with a whole load of instances, federation, file conversion, and so many other features.

So, we're really really pleased to announce that Manyfold has been awarded another grant by NLNet and NGI Zero, under the [NGI0 Commons Fund](https://nlnet.nl/commonsfund/), which should see us through 2025. We're hugely grateful to NLNet for their support of the project so far, both in funding and services provided, and this award only makes that even more true!

The exact deliverables for the grant aren't set yet, but currently our plan (in no particular order) looks something like:

1. Full JSON API; it should be possible to use most features of Manyfold without using the HTML frontend at all; a comprehensive JSON API (with full documentation) will allow alternative frontends to be built, and enable integration into other software tools.

2. Printer & Slicer integration; building on the JSON API, we can then develop integrations for existing open source slicer software to pull in content directly from Manyfold.

3. Search & Searchability; search is fundamental to a platform like Manyfold - we need to improve built-in search, but also allow search through other services and efforts like [Fediverse Discovery Providers
](https://www.fediscovery.org/).

4. Full integration of federated content; Manyfold’s federation can be much deeper, allowing models from one instance to appear as if natively present on another.

5. Model efficiency improvements; many 3d models distributed by creators are unnecessarily complex. We can simplify these with built-in tools, saving disk space and bandwidth for our users.

6. Content portability; make it easy to move content between Manyfold instances, and beyond.

7. Content synchronisation; develop a synchronisation framework to allow integration with existing external hosting services like Thingiverse and Printables, for model and collection import.

8. 3MF Production Extension Support; 3MF files produced by slicers include production details, such as printer specs, slice settings, etc. These files cannot currently be loaded by Manyfold but are in common use. We need to implement a 3MF loader that can handle that extension.

9. Support for commercial creators; while Manyfold is not a commercial tool, and never will be, many creators do create commercial content. We need to support that workflow so that creators can be paid for their efforts. We don’t intend to integrate payment directly into Manyfold, but rather support linking up external providers, and providing the sort of permission management needed for commercial sales.

If you've got feedback on that list, please let us know! We have the flexibility to change it at the moment, and while we think these are the most important things to focus on right now, YOU, our users, know best, so don't hesitate to [get in touch](/community.html) and tell us what you need!

And, if you're building open source software for a free and open Internet, we highly recommend applying to one of the NGI0 calls; it's a great developer-friendly system run by lovely people, and their [current call is open until February 1st](https://nlnet.nl/commonsfund/)!
