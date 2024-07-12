---
title: Sustainability Self-Assessment 2024-07-12
date: 2024-07-11 08:00:00 UTC
layout: page
excerpt_separator: "

"
---
This post is a self-assessment of Manyfold against the [Web Sustainability Guidelines](https://w3c.github.io/sustyweb/) version 1.0 (Seventh Draft), carried out by [James Smith](https://floppy.org.uk) on 2024-07-12.

WSG is a new set of draft recommendations for the sustainability of websites, intending to play a similar role to [WCAG](https://www.w3.org/WAI/standards-guidelines/wcag/) for accessibility. As part of Manyfold's funding from NLNet / NGI Zero, I proposed doing a WSG audit alongside our security and accessibility audits.

## Contents
{: .no_toc }

<details markdown="block">
  <summary>
    Expand
  </summary>
- TOC
{:toc}
</details>

## Methodology

There isn't a formal grading process for WSG yet, so I'm taking a simple a red / amber / green approach, as follows:

* 🟢 Good : We've got this pretty well covered (although there's always more to do).
* 🟡 OK : We're partway there, but there's plenty to improve.
* 🔴 Bad : This is definitely a problem, or we've not considered it.
* 🟣 Not Applicable / Not Assessed : Not relevant to this application or organization, or we didn't understand.

At this point, I am not assessing against section 5 of the recommendations, which covers Business Strategy and Product Management; it's not really appropriate for this project, and that section has been left out completely.

## Conclusions

<div id="results" style="text-align: center; line-height: 2rem;">
  <div id="good" style="display: inline-block; background-color: green; width: calc(100% / 170 * 53)" >Good</div><div id="ok" style="display: inline-block; background-color: yellow; width: calc(100% / 170 * 37)" >OK</div><div id="bad" style="display: inline-block; background-color: red; width: calc(100% / 170 * 64)" >Bad</div><div id="na" style="display: inline-block; background-color: purple; width: calc(100% / 170 * 16)" >N/A</div>
</div>

|Rating|Criteria|
|---|---|
|🟢 Good|53|
|🟡 OK|37|
|🔴 Bad|64|
|🟣 N/A|16|
|Total|170|

## Section 2. User-Experience Design

### Guideline 2.1. [Undertake Systemic Impacts Mapping](https://w3c.github.io/sustyweb/#undertake-systemic-impacts-mapping)

Many variables can impact the user-experience, and a bunch of these can impact how sustainable your website will be. Attempting to identify where you can make a difference to the visitor and give them a more sustainable experience will be beneficial.

<details markdown="block">
<summary>
Criteria: 🔴
</summary>

#### External Variables

List the negative external variables and identify where your product's sustainable impact can be diminished (systemic design).

{:.bad}
We have not identified externalities in any useful way; there are the obvious ones around energy and bandwidth use, but this isn't done in an organised fashion.

</details>

### Guideline 2.2. [Assess and Research Visitor Needs](https://w3c.github.io/sustyweb/#assess-and-research-visitor-needs)

When creating a product or service, identifying your target audience through user-research, analytics, data collected using ethical anonymous methods, or feedback from and with visitors is important in being able to create a customized service for and with them that is tailor-made for their specific preferences, adapted for any needs they may have, and particularly useful in helping a website or application evolve its service to meet sustainability targets.

<details markdown="block">
<summary>
Criteria: 🔴 🔴 🟡 🔴 🟡
</summary>

#### Identify And Define

Primary and secondary target visitors are identified, and their needs are defined through quantitative or qualitative research, testing, or analytics, ensuring your visitors and affected communities remain a close part of the research and testing process.

{:.bad}
The application is being developed through following our own instincts on what's useful, and listening to our community for their needs and feature requests. However, this is all very ad-hoc.

#### Visitor Constraints

Potential visitor constraints like the device age, operating system version, browser, and connection speeds are considered when designing user-experiences.

{:.bad}
We've not done any research on this or defined a policy.

#### Barriers And Access

The team has researched and identified whether a technical, material, or human constraint might require an adapted version of the product or service that reduces barriers or improves access to content.

{:.ok}
We've not researched this with users, but we have done an accessibility audit and made changes to improve accessibility of the application. That's not the same as finding out what users *actually need* up front, but it's probably the best we can do for this sort of project.

#### Barrier Removal

In the user-research, identify with your visitors if some barriers should be removed (pain points or dark / deceptive design patterns).

{:.bad}
We've not been able to do direct user research yet.

#### Seat At The Table

When undertaking research, identifying needs, or conducting iterative design work, ensure that all stakeholders including your visitors have an equitable role in the decision-making process.

{:.ok}
As an open source project run solely over the web, the "seat at the table" is in theory open to all equally. We acknowledge that that's not always true though, and have adopted the [Contributor Covenant](https://github.com/manyfold3d/manyfold?tab=coc-ov-file) as a way to hopefully show that we are a safe space for all contributors. We know there's more we can and should do.

</details>

### Guideline 2.3. [Research Non-Visitor's Needs](https://w3c.github.io/sustyweb/#research-non-visitor-s-needs)

If you provide physical goods or services, you may also have to account for the sustainability impact of delivery services. This can often be tricky, but courier companies may provide useful tooling to help you identify emissions data for routing.

<details markdown="block">
<summary>
Criteria: 🟣
</summary>

#### Non-Human Impact

Consider and work with non-users and other stakeholders who might be passively impacted by a digital product or service, such as neighbors accepting parcels, traffic jams due to deliveries, etc. Research their needs and understand how they might be affected.

{:.na}
No physical product involved.

</details>

### Guideline 2.4. [Consider Sustainability in Early Ideation](https://w3c.github.io/sustyweb/#consider-sustainability-in-early-ideation)

While some things require the use of electricity, during the early ideation phase you could consider wireframing or rapid prototyping (using paper) among other offline tools to reduce energy consumption. Even the electronic versions of these may have a lower carbon cost than committing to building a full-blown experience for each idea.

<details markdown="block">
<summary>
Criteria: 🟡 🟡
</summary>

#### Wireframes And Prototypes

Utilize wireframes, and rapid prototyping to quickly build consensus, reduce risk, and lower the number of resources needed to build features.

{:.ok}
Most features are prototyped in the live code, but with just a single-person team that is quite a lightweight process.

#### Participation And Testing

Involve your users within the iteration and design process using participatory design, and when conducting user-testing reach out to your community to help improve your product by allowing them to apply their knowledge and experience to your product or service.

{:.ok}
We do try to expose users to new features for testing before release through our edge builds, social and support channels. User feedback and suggestions are incorporated into the feature lists for future improvements.

</details>

### Guideline 2.5. [Account for Stakeholder Issues](https://w3c.github.io/sustyweb/#account-for-stakeholder-issues)

Brainstorming allows you to flush out ideas before you commit to pursuing a path. Being considerate of not just your visitors but other individuals who may be affected by your product or service (including non-humans, like the environment!) is a useful practical exercise as it may influence your decisions in how you scope your project.

<details markdown="block">
<summary>
Criteria: 🔴 🔴
</summary>

#### Human-Centered Brainstorming

In the brainstorming process, consider all stakeholders using a human-centered approach.

{:.bad}
We've not considered this approach.

#### Ecological Brainstorming

In the brainstorming process, take the planetary needs and ecological boundaries into account.

{:.bad}
We've not considered this approach.

</details>

### Guideline 2.6. [Create a Lightweight Experience by Default](https://w3c.github.io/sustyweb/#create-a-lightweight-experience-by-default)

When providing the option to download, save, print, or access anything online, defaulting to the most lightweight, least featureful version will reduce emissions through passive browsing; with non-essential information removed from the screen either to be shown when it's required or eliminated.

<details markdown="block">
<summary>
Criteria: 🟡 🔴 🟡 🟢 🟢
</summary>

#### Efficient Paths

The path taken to access the service (the initial contact with the website or service) should be as efficient and as simple as possible (time required to complete an action displayed, reducing too much choice, ensuring visitors know what's required at the start of a complex set of steps, etc).

{:.ok}
This is certainly something we aim for, though I'm not sure we achieve it yet.

#### Patterns For Efficiency

Make your user-journey (when browsing an accessed website or service) as smooth as possible. User-research is key, as is building on established design patterns that people already understand.

{:.bad}
As above, this is a definite aim, but we need to do some proper user testing and research to see if we're hitting it.

#### Distraction-Free Design

Visitors can complete tasks without distractions or non-essential features getting in the way.

{:.ok}
We do try to keep the user interface simple, so that each page has a particular purpose, and actions are clearly marked. We perhaps don't always achieve it though.

#### Eliminate The Non-Essential

Visitors see only information that is relevant to their experience, without non-essential information being displayed on the screen.

{:.good}
We try to only display directly relevant information in the UI. There isn't anything coming from any source that's not directly related to what the user is doing.

#### User-Initiated Actionable Content

Ensure that actionable information such as pop-up or modal windows can only be initiated by the visitor.

{:.good}
Actionable elements are only displayed in response to direct user input.

</details>

### Guideline 2.7. [Avoid Unnecessary or an Overabundance of Assets](https://w3c.github.io/sustyweb/#avoid-unnecessary-or-an-overabundance-of-assets)

It's great to have a pretty-looking website or application but to ensure a sustainable design, it's important to avoid cluttering up the interface with too many visuals (which aren't necessary to the content). Keeping a clean design will reduce website rendering, and thereby emissions.

<details markdown="block">
<summary>
Criteria: 🟢
</summary>

#### Decorative Design

Decorative design is used only when it improves the user-experience, and unnecessary assets or ones that fail to benefit the visitor or sustainability are removed (or rendered optional and disabled by default).

{:.good}
Manyfold's design is kept as clean and simple as possible, with as few assets as possible. The only decorative elements used are small icons from the [Bootstrap Icons](https://icons.getbootstrap.com/) set; everything else is functional.

</details>

### Guideline 2.8. [Ensure Navigation and Way-Finding Are Well-Structured](https://w3c.github.io/sustyweb/#ensure-navigation-and-way-finding-are-well-structured)

Information architecture is a central part of the Web development process, and how you structure a website ensures that people can way-find your content easily. Having appropriately marked-up links within your product or service allows visitors, search engines, and social networks to identify key information quickly.

<details markdown="block">
<summary>
Criteria: 🟡 🔴 🟢
</summary>

#### Navigation And Search

Provide an accessible, easy-to-use navigation menu with search features that help visitors easily find what they need.

{:.ok}
A primary purpose of the application is information management and organisation, so this is a primary focus for us. The navigation is reasonably clear; however, we know there are areas that need to be improved, particularly in terms of search results.

#### Navigable Sitemaps

Implementing an efficient (human-readable) sitemap that is organized and regularly updated helps search engines better index website content, which helps visitors more quickly find what they are looking for.

{:.bad}
We have not added sitemaps yet, either human or machine readable.

#### New Content

Provide a way for visitors to find out about new content and services.

{:.good}
The main user dashboard page provides a list of recently uploaded content.

</details>

### Guideline 2.9. [Respect the Visitor's Attention](https://w3c.github.io/sustyweb/#respect-the-visitor-s-attention)

Time is precious, wasting a visitor's will cause frustration and lead to abandonment or resentment. Additionally, the more time a visitor spends in front of a screen, the more energy they utilize. As such, throwing stuff in front of the visitor vying for their attention might sound like good business (even though we know due to banner blindness it rarely works), but it mostly damages the environment and dissuades the visitor.

<details markdown="block">
<summary>
Criteria: 🟢 🟢 🟡
</summary>

#### Respecting Attention

Respect a visitor's attention by allowing them to easily control how (and when) they receive information.

{:.good}
Visitors are completely in control of what information they receive.

#### Avoid Distraction

Prioritize features that don't distract people or unnecessarily lengthen the time they spend using the product or service.

{:.good}
We have no interest in distracting people to do something they didn't intend to; the idea is to make a simple yet effective tool that helps people achieve what they want to do.

#### Avoid Attention-keeping

Avoid using infinite scroll or related attention-keeping tactics.

{:.ok}
We don't have infinite scroll in the sense that many social media sites do, though we do have an "unpaged" mode for viewing models, which will allow people to scroll the entire collection. This will probably go away soon.

</details>

### Guideline 2.10. [Use Recognized Design Patterns](https://w3c.github.io/sustyweb/#use-recognized-design-patterns)

Visitors can identify patterns fairly easily, and they like browsing websites and apps and feeling as if they know what they are dealing with. As such, focusing your efforts on producing a product or service that is clean and has key components in easy-to-recognize locations (and visuals) will allow faster user-experiences and fewer emissions.

<details markdown="block">
<summary>
Criteria: 🟢
</summary>

#### Design Patterns

Provide only essential components visible at the time they are needed. Where appropriate, interfaces should deploy visual styles (patterns) that are easily recognized and used.

{:.good}
We do aim to use common design patterns for the site, whether in terms of visual design using Bootstrap, or in terms of the technical setup where we try to conform to the way that similar systems operate (e.g. linuxserver containers).

</details>

### Guideline 2.11. [Avoid Manipulative Patterns](https://w3c.github.io/sustyweb/#avoid-manipulative-patterns)

Manipulating the visitor into doing things you want them to is a short-term gain, long-term loss tactic tool. It's ethically bad, unsustainable, and should be avoided at all costs.

<details markdown="block">
<summary>
Criteria: 🟢 🟢 🟢 🟢
</summary>

#### Dark and Deceptive Design Patterns

Avoid what are commonly known as dark patterns, deceptive design, or unethical coding techniques, which manipulate visitors into taking actions not necessarily in their best interest (anti-right click, no-copy, requiring an account to purchase, etc).

{:.good}
We do not use dark patterns to drive user actions; in fact, we try our utmost to do the opposite (for instance with the design of our [usage tracking system](/sysadmin/tracking)).

#### Using Advertisements

Advertisements and sponsorships are both ethical and clearly identified with the product or service, only presenting them when they provide real economic and ethical value and don't diminish a visitor's experience.

{:.good}
We have no advertising.

#### Page Tracking

Remove unused and unconsented page tracking.

{:.good}
Manyfold itself has no page tracking, or any way to add it in short of changing the code. The Manyfold website uses [Umami](https://umami.is) privacy-preserving analytics to measure visits.

#### Search Engine Optimization

Optimization for search engines, social networks, and third-party services should be organically led with good coding practices and user-experience being the focus, not manipulating the services to gain greater priority through obfuscating content, pages, websites, or applications with redundancy or non-useful and optimized (to the visitor) material.

{:.good}
We do not attempt to manipulate search rankings, we just rely on well-structured and useful content to do the work.

</details>

### Guideline 2.12. [Document and Share Project Outputs](https://w3c.github.io/sustyweb/#document-and-share-project-outputs)

Everything produced by designers, developers, writers, and those involved with a project should be in an open format, well maintained, and curated in a common format (so everyone is working from the same model).

<details markdown="block">
<summary>
Criteria: 🟢 🟡 🟢
</summary>

#### Deliverables Reusability

The deliverables output, including documentation, are used upstream of the project and produced in ways that will allow it to be reused in subsequent projects.

{:.good}
We regularly make upstream contributions to open source software that we use, and have published a number of open source components of our own, both in terms of software but also things like technical specifications and proposals.
#### Deliverables Documentation

Design functionality and technical specifications are documented so that deliverables are comprehensible by the project team and transferable to the development team.

{:.ok}
We try to write in a comprehensible way, but could always do better.

#### Deliverables Readability

Ensure that developers have access to code comments and other View Source affordances which can reduce the burden to access, understand, maintain, and utilize production-ready code as this will reduce redundancy and foster an open source culture.

{:.good}
Everything we do is open source for others to see and reuse.

</details>

### Guideline 2.13. [Use a Design System To Prioritize Interface Consistency](https://w3c.github.io/sustyweb/#use-a-design-system-to-prioritize-interface-consistency)

Design systems allow common components and patterns to be formalized and managed within a website or application. By using such a tool, designers and developers can avoid reinventing existing tooling and thereby reduce wasted time (and emissions).

<details markdown="block">
<summary>
Criteria: 🟢
</summary>

#### Design System

Employ a design system based on web standards and recognizable patterns to mutualize interface components and provide a consistent experience for visitors.

{:.good}
We use the common Bootstrap design framework, which will be familiar to users from across the web, and incorporates a large amount of good design patterns and experience.

</details>

### Guideline 2.14. [Write With Purpose, in an Accessible, Easy To Understand Format](https://w3c.github.io/sustyweb/#write-with-purpose-in-an-accessible-easy-to-understand-format)

Everyone should be able to understand what you've written without wasting time staring at a screen or jumping from page to page looking for answers, whether they have accessibility requirements or not. This also means avoiding using technical language (without explanations) and including enough information to help direct people (and search engines) from page to page.

<details markdown="block">
<summary>
Criteria: 🟡 🟡 🔴
</summary>

#### Write Clearly

Write clearly, using plain, inclusive language delivered at an easy-to-understand reading level considering accessibility and internationalization inclusions as required (for example, dyslexia).

{:.ok}
We try to use simple concise language within the application, and our documentation is intended to be easy to read; however, as there is some level of technical detail involved, we can certainly do better.

#### Content Formatting

Deliver content formatted in ways that support how people read online, including a clear document structure, visual hierarchy, headings, bulleted lists, line spacing, and so on.

{:.ok}
We try to do this, but a proper content designer could certainly improve things.

#### Search Engine Optimization (SEO)

Prioritize SEO at early design stages and throughout a product or service's lifecycle to improve content findability.

{:.bad}
We haven't considered SEO outside the approach of creating well-structured documents.

</details>

### Guideline 2.15. [Take a More Sustainable Approach to Image Assets](https://w3c.github.io/sustyweb/#take-a-more-sustainable-approach-to-image-assets)

Of all the data that comprises the largest over-the-wire transfer rates within the average website or application, images are usually those that are responsible due to their quantity and usefulness. As such, doing all you can to reduce their size and unnecessary loading will be beneficial for sustainability.

<details markdown="block">
<summary>
Criteria: 🟢 🔴 🔴 🔴 🔴
</summary>

#### Need For Images

Assess the need for images considering the quantity, format, and size necessary for implementation.

{:.good}
Manyfold uses very few unnecessary images, with the exception of our logo and icons from Bootstrap Icons.

#### Optimize Images

Resize, optimize, and compress each image (outside the browser), offering different sizes (for each image) for different screen resolutions.

{:.bad}
Models tend to contain images, which are often quite large. These should be optimized and turned into different sizes; this is now possible with Shrine, our new storage engine, which should make this straightforward.

#### Lazy Loading

Provide Lazy Loading to ensure image assets only load when they are required.

{:.bad}
We do load complex 3d assets on demand, but this is not properly enforced and checked across the site, especially for images.

#### Sizing And Deactivation

Let the visitor select the display size, and provide the option to deactivate images.

{:.bad}
This is not currently an option.

#### Management And Usage

Set up a media management and use policy to reduce the overall impact of images, with criteria for media compression and file formats.

{:.bad}
We've not done this.

</details>

### Guideline 2.16. [Take a More Sustainable Approach to Media Assets](https://w3c.github.io/sustyweb/#take-a-more-sustainable-approach-to-media-assets)

Video and audio-heavy websites are often those that can have significant sustainability costs in terms of storage and carbon intensity for viewers who have to process the media with their devices to watch them (draining batteries). Optimizing such assets as much as possible is critical for a sustainable product or service.

<details markdown="block">
<summary>
Criteria: 🟢 🔴 🟢 🟢 🟣
</summary>

#### Need For Media

Assess the need for video or sound usage (including only when they add visitor value), and ban non-informative media (background media) including autoplaying functionality.

{:.good}
We do not have any non-informative media on the site, nor audio/video.

#### Optimize Media

Choose the right media to display by compressing according to the visitor's requirements, selecting the appropriate format, ensuring it works across browsers, and avoiding embedded player plugins.

{:.bad}
We are sending original 3d files in their normal formats to the visitor's browser; this sends way too much data, which can be in very inefficient forms. We have a plan to create a more efficient progressive transmission file format that can efficiently stream model data on demand, to the required resolution. This should save a lot of data.

#### Lazy Loading

Media requiring a lot of data to be downloaded on the client side (including the media itself) must be loaded via a facade (a non-functional, static, representational element).

{:.good}
We do this for 3d content by default, only auto-downloading and rendering smaller models. All this is controllable by the user.

#### Labels And Choice

Increase visitor awareness and control by informing them of the length, format, and weight of the media; allowing media deactivation, and giving a choice of resolutions; all while providing alternative resolutions and formats.

{:.good}
We do provide information on the size of media to be downloaded before the user clicks on it to trigger the download.

#### Management And Usage

Set up a media management and use policy to reduce the overall impact of audio and video, with criteria for media compression and file formats.

{:.na}
We do not handle audio or video.

</details>

### Guideline 2.17. [Take a More Sustainable Approach to Animation](https://w3c.github.io/sustyweb/#take-a-more-sustainable-approach-to-animation)

Animation can be both CPU and GPU-intensive and have implications for accessibility. While visually appealing and useful in certain situations, care and attention should be taken when considering the use of a high emissions technology.

<details markdown="block">
<summary>
Criteria: 🟢 🟡 🟢
</summary>

#### Need For Animation

Use animation only when it adds value to a visitor's experience, and not for decorative elements.

{:.good}
Animation is only used for 3d model preview, which is the primary purpose of the application.

#### Avoid Overburdening

Progressively display an appropriate quantity of animation so as not to overburden the visitor or diminish expected device behavior.

{:.ok}
We have done a lot of work on making sure the 3d model displays are performant, but there's a lot more that can be done to make it smarter and only render what's absolutely required.

#### Control Animation

Allow visitors to start, stop, pause, or otherwise control animated content.

{:.good}
3D models are fully user-controlled; image carousels do autoplay, but are under user control and correctly respond to `prefers-reduced-motion`.

</details>

### Guideline 2.18. [Take a More Sustainable Approach to Typefaces](https://w3c.github.io/sustyweb/#take-a-more-sustainable-approach-to-typefaces)

Since the advent of the modern web, the ability to include embedded fonts and provide a more customized experience has seen their use explode. They aren't always the most performant option (which poses emissions hazards) and come with a few issues such as Flash Of Unstyled Content (FOUC) / Flash Of Unstyled Text (FOUT) which should be addressed.

<details markdown="block">
<summary>
Criteria: 🟢 🟢
</summary>

#### Default Typefaces

Use standard system-level (web-safe / pre-installed) fonts as much as possible.

{:.good}
We use a web-safe font stack that should always use fonts available on a visitor's computer.

#### Font Optimization

Ensure the number of fonts, and the variants within typefaces (such as weight and characters) are limited within a project, using the most performant file format available.

{:.good}
We use a web-safe font stack that should always use fonts available on a visitor's computer.

</details>

### Guideline 2.19. [Provide Suitable Alternatives to Web Assets](https://w3c.github.io/sustyweb/#provide-suitable-alternatives-to-web-assets)

Media, images, fonts, and documents enrich the Internet. The problem is that people may not want to watch a video, listen to an audio file, look at an image, or use a specific application. By providing alternative formats to anything you embed, you ensure the widest possible audience can benefit from it (and reduced carbon output will occur as the alternative text will induce less consumer hardware thrashing than its rich media alternative).

<details markdown="block">
<summary>
Criteria: 🟢 🟢 🟡 🟣 🟣
</summary>

#### Open Formats

All proprietary file formats (such as PDF) should also be offered in HTML for accessibility and to ensure future availability.

{:.good}
We do not use any proprietary formats in our own work. The system can be used to index and manage files in proprietary formats, but that is beyond the scope of assessment.

#### Font Subsetting

All custom typefaces (using font-display) should be subsetted and offered as part of a font stack with a system font as a backup.

{:.good}
We have no custom fonts, and our web-safe font choices are backed with a font stack that includes system fonts.

#### Alternative Text

All images should provide meaningful alternative text for screen reader users (or when images fail to load) accessibility.

{:.ok}
All of our built-in imagery has alternative text, but the images included in catalogued models do not. We do have a "caption" field for files, which could be displayed as alt text, but that's not currently editable, or displayed for images.

#### Audio Alternatives

Audio should provide text transcripts of conversations as an alternative to playing the media.

{:.na}
We have no audio content.

#### Video Alternatives

Video should provide text transcripts (at minimum), subtitles (using WebVTT), and for accessibility best practice, offer closed captions and sign language options.

{:.na}
We have no video content of this type.

</details>

### Guideline 2.20. [Provide Accessible, Usable, Minimal Web Forms](https://w3c.github.io/sustyweb/#provide-accessible-usable-minimal-web-forms)

Understandably, businesses want to know more about their customers, but a key part of sustainability is being ethical towards visitors and as such, the right to privacy is considered paramount. Don't demand information when it's not required and not only will this help visitors complete transactions quicker (reducing emissions), it will help with legal compliance such as GDPR.

<details markdown="block">
<summary>
Criteria: 🟡 🟡
</summary>

#### Form Simplicity

Assess the need for forms and reduce form content to the bare minimum necessary to meet the visitor's needs and the organization's business goals. Clearly communicate why a form is necessary, what its value proposition is, how many steps it will take to complete, and what an organization will do with collected data (informed consent).

{:.ok}
We aim to do this, by including explanatory text in forms, help text for inputs, and useful placeholders, but we can do it better and more consistently.

#### Form Functionality

Avoid auto-completion / auto-suggest if it would prove unhelpful (to conserve bandwidth) whilst allowing autofill for ease of repeat entry (including the use of helpful tooling such as password managers).

{:.ok}
In general we allow autocompletion on the client side. Tag editing involves loading a complete list of tags up front, which is pretty inefficient when we could fetch completions on demand instead.

</details>

### Guideline 2.21. [Support Non-Graphic Ways To Interact With Content](https://w3c.github.io/sustyweb/#support-non-graphic-ways-to-interact-with-content)

Certain visitors such as those with visual disabilities or speech agents (like Amazon Alexa) may rely on an experience without the graphical part of an interface. As such, they potentially may use less data or may have a different carbon impact on the Web.

<details markdown="block">
<summary>
Criteria: 🟡
</summary>

#### Alternative Interactions

Support speech browsing and other non-graphical ways to interact with content that provide alternatives to a visual interface.

{:.ok}
Our accessibility audit did raise a number of issues with screen readers which have been addressed. However, a lot of the content that the site is intended to work with is inherently visual.

</details>

### Guideline 2.22. [Provide Useful Notifications To Improve The Visitor's Journey](https://w3c.github.io/sustyweb/#give-useful-notifications-to-improve-the-visitor-s-journey)

Notifications whether through the browser or messaging can be potentially useful, but only used in moderation. Spam and the lack of control are contributing sources of Internet emissions and as such, businesses should aim to reduce such actions.

<details markdown="block">
<summary>
Criteria: 🟢 🟢 🔴
</summary>

#### Notification Justification

Remove non-essential notifications while justifying and reducing the practice of e-mailing or text messaging to what is strictly necessary. Useful notifications (such as alerts for new content) should be used with care and restraint.

{:.good}
At present, we only have emails for essential account actions like password resets. There are no optional notifications.

#### Notification Control

Let the visitor control notifications (for example through the browser, SMS, or by email) and adjust messaging preferences, and the option to unsubscribe, logout, and close an account should be available and visible.

{:.good}
At present, we only have emails for essential account actions like password resets. There are no optional notifications.

#### Prompts And Responses

Help visitors manage expectations by clearly explaining the result of a potential input through helpful prompts and messages that explain errors, next steps, and so on.

{:.bad}
We try to do this, to provide useful context, but it's not good enough at the moment, especially in the area of error messages.

</details>

### Guideline 2.23. [Reduce the Impact of Downloadable or Physical Documents](https://w3c.github.io/sustyweb/#reduce-the-impact-of-downloadable-or-physical-documents)

Printing or downloading documents can both be a net benefit and a net cost in terms of sustainability as it can reduce repeat requests to websites, but the act of printing (especially when unoptimized) wastes valuable ink and paper.

<details markdown="block">
<summary>
Criteria: 🟣 🟡 🔴 🔴
</summary>

#### Printing Documents

Design documents to limit the printing impact. If the production of paper documents is essential, it should be designed to limit its impact to the lowest possible. Create a CSS Print stylesheet and test it with different types of content. Ensure PDF printing is encouraged over paper-based storage.

{:.na}
We do not have any documents that fit this category at present.

#### Optimize Documents

Offer optimized, compressed documents in a variety of accessible file formats.

{:.ok}
We offer the ability to manually compress and optimize 3d assets, but not automatically. However, we do have plans to.

#### Optimize Delivery

If a document is likely to be re-used, generate the document once on the server-side (preferably on a cookie-free domain) rather than forcing the effort to be duplicated.

{:.bad}
We're not currently doing any pre-generation or caching of this sort, but we should do.

#### Labels And Choice

Clearly display the document name, a summary, the file size, and the format, allowing the visitor a choice if possible of both the format, and the language (if not the same as the web page). Furthermore, be sure to avoid embedding the document within Web pages (provide a direct link to download or view within the browser instead).

{:.bad}
We do embed rich content in the web pages, and we should display file details more clearly at all points where the user can download the file.
</details>

### Guideline 2.24. [Create a Stakeholder-Focused Testing & Prototyping Policy](https://w3c.github.io/sustyweb/#create-a-stakeholder-focused-testing-prototyping-policy)

The organization has policies and practices in place to incorporate stakeholder-focused testing and prototyping into its product development cycles.

<details markdown="block">
<summary>
Criteria: 🔴 🔴 🟡 🔴
</summary>

#### New Features And Perspectives

The organization has outlined processes it uses to prototype and test new features, product ideas, and user-interface components when applicable with real users who represent various stakeholder perspectives, including people with slow connection, with disabilities, with difficulties using digital services, and so on.

{:.bad}
We don't have a plan for this other than ad-hoc testing after release. We will need to get more organised about it at some point, certainly.

#### Resourcing And Viability

The organization has appropriately resourced these processes to support its long-term product viability.

{:.bad}
Manyfold is not yet financially sustainable. We're trying to build a donation and sponsorship base through OpenCollective, but for now we're dependent on grant funding.

#### Training And Onboarding

The organization has training materials to onboard new product team members to these practices.

{:.ok}
We do have onboarding documentation that works for new developers, but it's fairly minimal and could do with being a lot more comprehensive.

#### Testing And Validation

The organization regularly conducts extensive testing and user interviews to validate whether the released features are meeting both business goals and visitor needs.

{:.bad}
We only do this through ad-hoc user feedback.

</details>

### Guideline 2.25. [Conduct Regular Audits, Regression, and Non-Regression Tests](https://w3c.github.io/sustyweb/#conduct-regular-audits-regression-and-non-regression-tests)

Products and services at any stage of a project can suffer bugs or issues that need to be resolved. Fixing these regressions also generates additional development and environmental costs. By resolving such issues, you can reduce the chances of a visitor giving up on a session and thereby reduce the amount of wasted energy your website emits overall.

<details markdown="block">
<summary>
Criteria: 🟡 🟡 🟢
</summary>

#### Regular Issue Testing

Check your codebase for bugs, identify any performance issues, and account for accessibility or security problems at either monthly or quarterly timeframes (depending on your scheduling allowance).

{:.ok}
We run continuous testing using automated tests, as well as automated accessibility and security checks where possible. We don't yet have automated performance testing, though it should be possible. Regular manual accessibility and security testing will depend upon future funding.

#### Non-Regression Tests

Non-regression tests are implemented for all important functionality.

{:.ok}
Around 85% of the features are covered by automated tests - we should add the rest.
#### Regression Tests

Incorporate regression testing into each release cycle to ensure that new features don't introduce bugs or otherwise conflict with existing software functionality.

{:.good}
Automated tests run on every commit to ensure that new code doesn't break old code.

</details>

### Guideline 2.26. [Incorporate Performance Testing Into Each Major Release-Cycle](https://w3c.github.io/sustyweb/#incorporate-performance-testing-into-each-major-release-cycle)

Try to ethically measure how efficient a visitor's experience is by analyzing the performance of the website or application and how it has been constructed, by doing so you might be able to reduce any issues they may have encountered previously, decrease loading times, and reduce the burden of loading unnecessary pages.

<details markdown="block">
<summary>
Criteria: 🔴 🟢
</summary>

#### Performance Testing

Regularly measure with each release-cycle (using tooling or through research and auditing) the performance of a website or application to identify and resolve bottlenecks or issues in the underlying code or infrastructure which could ultimately impact the sustainability of a website or application.

{:.bad}
We don't currently do any structured performance testing, just manual and ad-hoc.

#### Measurement And Compliance

Only collect the data required to provide a streamlined and effective user-journey, put policies in place to ensure strict adherence, and comply with relevant accessibility policies and privacy laws, such as the General Data Protection Regulation (GDPR).

{:.good}
We don't collect any data from live services.

</details>

### Guideline 2.27. [Incorporate Value Testing Into Each Major Release-Cycle](https://w3c.github.io/sustyweb/#incorporate-value-testing-into-each-major-release-cycle)

Occasionally, you may find that features you have developed for a product or service have little to no active users or could be better implemented to bring better value. Undertaking research to identify redundancy allows you to optimize your codebase (and reduce emissions).

<details markdown="block">
<summary>
Criteria: 🟡
</summary>

#### Usage Changes

Consider visitor feedback and monitor adoption and churn rates of product or service features, incorporating insights into future releases.

{:.ok}
We don't do this in a structured way, but do take feedback from users through support channels and GitHub issues, and feed that into the product.

</details>

### Guideline 2.28. [Incorporate Usability Testing Into Each Minor Release-Cycle](https://w3c.github.io/sustyweb/#incorporate-usability-testing-into-each-minor-release-cycle)

Researching a product or service and how it is used over time allows you to iterate and ensure the features and functionality being offered match how user-needs change over time. Doing so will help you reduce code redundancy further and reduce emissions through optimization.

<details markdown="block">
<summary>
Criteria: 🔴
</summary>

#### Usability Testing

Incorporate usability testing into product cycles and measure the impact of these tests for future releases.

{:.bad}
We don't have any structured usability testing or measures.

</details>

### Guideline 2.29. [Incorporate Compatibility Testing Into Each Release-Cycle](https://w3c.github.io/sustyweb/#incorporate-compatibility-testing-into-each-release-cycle)

Compatibility is a critical part of the sustainability mindset and should be prioritized through all products and services. If individuals wish to use older devices (or cannot upgrade due to cost) or do not wish to upgrade as frequently, it will reduce the amount of e-waste that enters the system. If something doesn't work, it's also likely to result in visitors suffering a wasted effort, potentially leading to refused access to your service (and thereby emitting further emissions).

<details markdown="block">
<summary>
Criteria: 🔴 🟡 🔴 🔴 🟢
</summary>

#### Compatibility Policy

Establish a policy for compatibility with obsolete devices and software versions, listing the supported devices brands, operating systems, and browsers (including versions).

{:.bad}
We do not have a stated official policy at present.

#### Maintaining Compatibility

Avoid planned obsolescence in software updates, striving to maintain compatibility for as long as possible and clearly communicating whether an update is evolutionary (large updates that can significantly reduce performance) or corrective (smaller updates that fix bugs or improve security).

{:.ok}
We use semantic versioning for our releases, and hopefully soon will be at 1.0 where we can make the commitment to retain compatibility until version 2.0 comes along, which hopefully will never happen!

#### Frequent Testing

Regularly test the product or service with weak connections, old browsers, and devices older than five years to ensure compatibility.

{:.bad}
We don't do this in any organised fashion (other than the fact that my main development laptop is currently 11 years old).

#### Mobile Friendly

Prototype your interfaces using mobile-first methods to ensure progressive enhancement, content prioritization, and improved accessibility.

{:.bad}
We don't do mobile UI development first, it's a secondary thing.
#### Progressive Web Applications (PWAs)

Consider whether a PWA will be more sustainable and compatible over a native mobile application.

{:.good}
We don't create a native application, and if we ever did, it would likely be a PWA.

</details>

## Section 3. Web Development

### Guideline 3.1. [Identify Relevant Technical Indicators](https://w3c.github.io/sustyweb/#identify-relevant-technical-indicators)

Performance is a key part of the sustainability mindset as reductions in loading times can have a considerable impact on energy loads within CPU, GPU, RAM, and hard drive caching (among other variables), as such ensuring a performant product is essential.

<details markdown="block">
<summary>
Criteria: 🔴 🟢
</summary>

#### Performance Goals

Set goals that impact the environment and performance of the service, for example, HTTP requests, or the amount of DOM elements that need to be rendered.

{:.bad}
We haven't done this, but we should be able to come up with some.

#### Accountancy Types

Because the payload being delivered may not always be equal in terms of energy intensity, operators of websites and applications must ensure that consideration is given for the energy intensity (or unit being evaluated) of each component. For example, non-rendering text is less computational than CSS, which in turn is less process-heavy than JavaScript, which is less resource-heavy than WebGL.

{:.good}
It's clear that the most energy-intensive part of Manyfold is the 3D file handling. Making this more efficient will give us the most reward.

</details>

### Guideline 3.2. [Minify Your HTML, CSS, and JavaScript](https://w3c.github.io/sustyweb/#minify-your-html-css-and-javascript)

Whitespace holds no value when it's being presented to the visitor (unless they view the source code), by using minification, valuable data savings can be made which will reduce loading times.

<details markdown="block">
<summary>
Criteria: 🟡
</summary>

#### Minify Code

All source code is minified upon compilation (including inline code).

{:.ok}
Javascript code is minified, but HTML is not.

</details>

### Guideline 3.3. [Use Code-Splitting Within Projects](https://w3c.github.io/sustyweb/#use-code-splitting-within-projects)

When dealing with heavy components (such as JavaScript), the ability to modularize them into smaller pieces that can be loaded as and when required reduces the amount of redundancy and serves as a great way to make your scripts more sustainable.

<details markdown="block">
<summary>
Criteria: 🔴
</summary>

#### Code Splitting

Breakdown bandwidth-heavy components into segments that can be loaded as required.

{:.bad}
We do have some code-splitting in that the renderer is in a separate background worker script, but there are definitely things that are pulled into every page that aren't always needed, like the bulk editor code, selectize for tag editing, and more.

</details>

### Guideline 3.4. [Apply Tree Shaking To Code](https://w3c.github.io/sustyweb/#apply-tree-shaking-to-code)

Often when coding, projects can accumulate clutter and functions that are no longer used (due to newer, more effective features being developed). By utilizing tree shaking techniques, all the "dead wood" will be automatically dropped upon compilation, reducing a file's size.

<details markdown="block">
<summary>
Criteria: 🟡
</summary>

#### Remove Redundancy

Identify and eliminate unused and dead code within CSS and JavaScript.

{:.ok}
We apply tree-shaking when compiling our Javascript bundle, but we're not doing the same for CSS.

</details>

### Guideline 3.5. [Ensure Your Solutions Are Accessible](https://w3c.github.io/sustyweb/#ensure-your-solutions-are-accessible)

Not everyone can access services equally, being sustainable is also about being accessible, fair, ethical, and ensuring that your product or service doesn't discriminate. As such, ensuring your website complies with best practices and relevant laws whilst meeting the needs of your visitors is critical as well as good business.

<details markdown="block">
<summary>
Criteria: 🟢 🟢 🟣
</summary>

#### Accessibility Compliance

Your website or application must conform to WCAG (at the necessary level), plus extend beyond to obey relevant laws and meet additional visitor accessibility requirements. Building inclusively means that people with permanent, temporary, or situational disabilities will be able to more quickly find what they are looking for, and not have to spend extra time searching for a way to use your product or service.

{:.good}
We recently had an accessibility audit performed and have addressed all the findings.

#### Enhancing Accessibility

Enhance your website or application with Accessible Rich Internet Applications (ARIA) ONLY if applicable or necessary, and accessibility enhancing features when useful or beneficial.

{:.good}
ARIA attributes are only added if actually useful - wherever possible we just use core semantic HTML attributes.

#### Electronic Inequalities

Deploy solutions that fight against electronic inequalities in products and services.

{:.na}
I'm not sure how to assess or apply this...

</details>

### Guideline 3.6. [Avoid Code Duplication](https://w3c.github.io/sustyweb/#avoid-code-duplication)

Redundancy is the enemy of sustainability. Having systems in place to ensure that everyone can work from established patterns, the website or application remains clean and easy to use, and iteration over redesign is firmly in the mindset that will help promote sustainable practices. It's also worth being wary of abstracting code too early (see AHA methodology) or incorrectly, as while good abstractions can be more efficient, poor ones can waste effort and introduce complexity, bloat, and bugs to your codebase which can lead to emissions.

<details markdown="block">
<summary>
Criteria: 🟢 🟢 🟢
</summary>

#### Remove Or Simplify

Don't be afraid to remove or simplify (through rewriting for performance) your code to focus on essential features and have a cleaner, less redundant product (and codebase).

{:.good}
We regularly refactor old code to make it simpler and more efficient, with less duplication. Less code is better code. We use static analysis tools to highlight areas of code that need improving.

#### Iteration Over Recreation

Improve (iterate) an existing creation rather than constantly redeveloping and redesigning products from scratch (duplication of coding effort) if possible to reduce visitor learning burden and developer impact.

{:.good}
We do take an iterative approach to development, and reuse code and third party libraries wherever possible.

#### Organize Code Arrangement

Within CSS and JavaScript, use methodologies (like BEM) and systems like DRY and WET to optimize the arrangement and output of your source code.

{:.good}
We use good software engineering approaches to code design, and continually consider the tradeoffs between maintainability, complexity and repetition.

</details>

### Guideline 3.7. [Rigorously Assess Third-Party Services](https://w3c.github.io/sustyweb/#rigorously-assess-third-party-services)

Whether advertising, chatbots, maps, or other tooling; outsourcing your service to a third-party provider may be potentially useful in certain scenarios in reducing design or development time and redundancy (which can be a win for sustainability). Third-party services, however, come with issues, such as the lack of control over emissions, and they often can potentially suffer from latency and large file sizes which may not exist if you self-hosted or created the material.

<details markdown="block">
<summary>
Criteria: 🟣 🟣 🔴 🟢 🟢 🟢
</summary>

#### Assess Third-Parties

Assess third-party services (including plugins, widgets, feeds, maps, carousels, etc) as early in the ideation or creation process as possible and use as few as possible to reduce the product or service's overall ecological impact, including Scope 3 emissions.

{:.na}
We do not embed any third party services.

#### Third-party Implementation

Third-party content (including plugins, widgets, feeds, maps, carousels, etc) should be placed behind a click-to-load delay screen (using the "import on interaction" pattern), while alternatives to automated solutions such as chatbots should be offered.

{:.na}
We do not embed any third party services.

#### Libraries And Frameworks

Large CSS libraries and JavaScript frameworks should only be used if a more performant alternative that achieves the same goal cannot be used instead.

{:.bad}
We haven't done an assessment of the software we use against this criterion.

#### Self-Hosting

Prioritize self-hosted content over embedded content from third-party services.

{:.good}
Manyfold doesn't include any external third party content.

#### Avoiding Dependency

Create your own clickable icons and widgets, rather than relying on third-party services to host or allow embedding within your product or service.

{:.good}
We use no third party services for embedded content.

#### Third-party Preferences

Third-party products, services, libraries, and frameworks are often a source of sustainability issues that cannot be controlled or managed by the first-party provider of a service. While many do provide benefits to a website, the need to justify their inclusion should be made not only by those creating the product or service but also be able to be controlled by the consumer. As showcased with cookies, websites or applications should provide a similar mechanism of disabling or refusing non-first-party features (with explanations of their purpose) - unless such features can be proven as critical for functionality.

{:.good}
We use no third party services outside our control.

</details>

### Guideline 3.8. [Use HTML Elements Correctly](https://w3c.github.io/sustyweb/#use-html-elements-correctly)

HTML semantics are important. They don't just play a key role in making the Web look the way it does, they have a function in accessibility, SEO, and even in sustainability. Ensuring that you markup your content correctly and avoid cluttering your markup wastefully will reduce emissions.

<details markdown="block">
<summary>
Criteria: 🟡 🔴 🟢 🟢
</summary>

#### Semantic Code

Ensure content is marked up semantically using the right HTML element for the right job.

{:.ok}
Manyfold aims to always use clean and semantic HTML. But we can always do better, and we should explicitly check and validate this.

#### Optional Features

Consider removing optional HTML tags (which aren't required for rendering), attribute quotes, or attributes that are set to their default value.

{:.bad}
We should set up automated linting that can highlight these issues for fixing; we're not currently aware if this problem is present in our application or not.

#### Avoid Non-standard Code

Avoid using non-standard elements or attributes.

{:.good}
All code conforms to web standards.

#### Custom Code

Only use custom elements or Web Components if you cannot utilize native HTML elements or if you need tightly regulated control over the implementation of design system components.

{:.good}
We don't have any custom elements or Web Components.

</details>

### Guideline 3.9. [Resolve Render Blocking Content](https://w3c.github.io/sustyweb/#resolve-render-blocking-content)

The ability to work around render-blocking issues is a great addition to the web. From deferring code, to lazy loading, to asynchronous loading, each has its use case and each can have the potential to reduce or give performance benefits to a website or application.

<details markdown="block">
<summary>
Criteria: 🟡 🔴
</summary>

#### Asynchronous Code

All external assets should be deferred or set to async (unless required) to avoid Flash Of Unstyled Content (FOUC).

{:.ok}
We do some of this, but I'm not sure if everything is properly deferred.

#### Priority Loading

If external resources are required on load, ensure their priorities (delivery route) are set correctly.

{:.bad}
We've not set priorities for loading of assets.

</details>

### Guideline 3.10. [Provide Code-Based Way-Finding Mechanisms](https://w3c.github.io/sustyweb/#provide-code-based-way-finding-mechanisms)

Helping visitors avoid wasting their time can reduce the number of emissions from time spent in front of a screen. As such, by using existing technologies like metadata, robots files, and accessibility-friendly aids within the page, improvements to the experience can be made.

<details markdown="block">
<summary>
Criteria: 🔴 🔴 🟢
</summary>

#### Metadata And Microdata

Optimize your metadata and microdata for search engines and social media.

{:.bad}
We've not done this.

#### Search Engines

Assist search engines, while blocking any ill-intentioned robots and scripts.

{:.bad}
We've not done this.

#### Accessibility Aids

Offer accessibility and usability aids to find content, such as skip links and signposts.

{:.good}
Many issues like this were raised in our recent accessibility audit, and have been addressed. Links and buttons are well labeled, and we have skip links in a number of places, including around large lists of content.

</details>

### Guideline 3.11. [Validate Form Errors and External Input](https://w3c.github.io/sustyweb/#validate-form-errors-and-external-input)

Entering information on a page can lead to problems. If a visitor makes a mistake along the way, it makes good sense to have systems in place to guide them through resolving the typos, confusion, and glitches that can occur which lead to abandonment and extra emissions through wasted device usage.

<details markdown="block">
<summary>
Criteria: 🔴 🟢 🟢
</summary>

#### Error Validation

Errors should be identified through live validation as well as upon submission.

{:.bad}
Most form validation only happens server-side.

#### Label Elements

Required elements should be clearly identified and labeled (for the benefit of voice tools such as screen readers and virtual assistants), and optional elements (if unnecessary) removed.

{:.good}
Checked and improved as part of our accessibility audit.

#### Allow Paste

Always allow the pasting of content (including passwords) from external sources.

{:.good}
Pasting is allowed.

</details>

### Guideline 3.12. [Use Metadata Correctly](https://w3c.github.io/sustyweb/#use-metadata-correctly)

Search engines and social networks make use of the content within a website, by ensuring that your metadata is correctly marked up, you can reduce emissions by improving way-finding.

<details markdown="block">
<summary>
Criteria: 🔴 🔴 🔴
</summary>

#### Required Elements

Include the required title element, plus any optional HTML head elements (such as link).

{:.bad}
Our titles are probably not set to useful values, and I don't think we've done much other head metadata.

#### Meta Tags

Include necessary meta tag references that search engines and social networks recognize, using a recognized name scheme such as Dublin Core Metadata Initiative (DCMI), Friend Of A Friend (FOAF), or RDFa.

{:.bad}
We don't do this, but there are probably opportunities to do so.

#### Structured Data

Embed Microdata, Structured Data (Schema), or Microformats within your pages.

{:.bad}
We don't do this, but there are probably opportunities to do so.

</details>

### Guideline 3.13. [Adapt to User Preferences](https://w3c.github.io/sustyweb/#adapt-to-user-preferences)

Sustainability benefits can be generated in numerous ways, by making sure that your website adheres to the requests made by a browser for specific conditions to be taken into account (such as CSS media and preference queries), you can unlock benefits for the visitor, and as a by-product reduce your emissions. It's worth noting that the introduction of user preferences and APIs has increased the risk of visitor fingerprinting and privacy issues.

<details markdown="block">
<summary>
Criteria: 🟡
</summary>

#### Media and Preference Queries

Apply the monochrome, prefers-contrast, prefers-color-scheme, prefers-reduced-data, prefers-reduced-transparency, and prefers-reduced-motion CSS preference queries if they will benefit your website or application. Also, consider the print & scripting CSS media queries if they will improve the sustainability of your website.

{:.ok}
Bootstrap handles a lot of these automatically, but we should look into `prefers-contrast`, `monochrome`, and particularly `prefers-reduced-data`, because those are definitely things we could apply to the 3d renderer.

</details>

### Guideline 3.14. [Develop a Mobile-First Layout](https://w3c.github.io/sustyweb/#develop-a-mobile-first-layout)

Visitors approach our products and services on a wide variety of devices these days. Ensuring that your device works on the widest range of devices and differing screen resolutions ensures that you will have a compatible website or application. As such, visitors can actively choose to browse on devices that emit less carbon if they wish.

<details markdown="block">
<summary>
Criteria: 🔴 🟡 🔴 🔴
</summary>

#### Mobile-First

Allow a website or app to work on mobile devices primarily (testing with various connection speeds), expanding to accommodate larger displays thereafter (mobile-first). It is much more effective to do the hard work to ensure that it works well on a mobile device and then scale it up to larger interfaces.

{:.bad}
Manyfold is mobile-friendly, but definitely not mobile-first. We can do better.

#### Responsive Design

Utilize progressive enhancement and responsive web design to ensure that your work accommodates a device's capabilities, different screen sizes, and will not fail if it meets an unsupported technology.

{:.ok}
We use Bootstrap's responsive design to cope with different screen sizes, but there are some places where this doesn't work properly on small screens.

#### Carbon Aware Design

To maximize the use of renewable energy, adapt your website or service to electricity availability using carbon-aware design techniques. This should include using situational design to reduce the codebase or functionality during high-intensity periods or adapting the user-interface to perform better in situations where scaling hardware resources can be avoided to reduce emissions.

{:.bad}
We've not looked into this at all, and I didn't even know it was possible. We should find out more.

#### Alternative Browsing

Consider supporting other indirect methods of interaction such as voice (speech), code (QR, etc), reader view (browser, application, or RSS), or connected technology (watch, appliance, transport, etc).

{:.bad}
We've not explored these interaction methods at all.

</details>

### Guideline 3.15. [Use Beneficial JavaScript and Its APIs](https://w3c.github.io/sustyweb/#use-beneficial-javascript-and-its-api-s)

When new best practices or if beneficial scripting guidance exists that will improve the visitor experience, following it should be of the highest priority (only using scripts ethically should be promoted).

<details markdown="block">
<summary>
Criteria: 🔴 🔴
</summary>

#### Beneficial JavaScript

Improve sustainability through accessible and performant code implementations.

{:.bad}
Performance is a goal and we've worked on it, though it could definitely be improved in many places. There are definitely parts of the code we know are taking far longer than they should.

#### API Requests

When using an API, make sure you only call it when necessary. On the other side, make sure no unrequired data is sent by the API.

{:.bad}
While we do try to minimise it, Manyfold still transfers a lot of 3d data that's not strictly necessary - there are more efficient ways we could provide the same experience to a user, such as an image preview of a model.

</details>

### Guideline 3.16. [Ensure Your Scripts Are Secure](https://w3c.github.io/sustyweb/#ensure-your-scripts-are-secure)

The dangers of scripting are well known, and vulnerabilities are discovered with increasing regularity. As such, it's of ethical benefit for authors to ensure all code used regularly passes security processes.

<details markdown="block">
<summary>
Criteria: 🟢
</summary>

#### Script Security

Check the code for vulnerabilities, exploits, header issues, and code injection.

{:.good}
Security audit was recently performed, and identified only a few issues, which have been fixes. Various code-scanning tools are also used to detect potential security issues.

</details>

### Guideline 3.17. [Manage Dependencies Appropriately](https://w3c.github.io/sustyweb/#manage-dependencies-appropriately)

While JavaScript may not cause the most website bloat, it can cause very high emissions in terms of CPU load due to the rendering process, thereby it makes sense to consider the use of dependencies and third-party code carefully.

<details markdown="block">
<summary>
Criteria: 🟢 🟡 🟢
</summary>

#### Dependency Management

Prevent developers from downloading and installing JavaScript libraries to run locally (client-side) when they are not needed by checking for unused dependencies and uninstalling those that aren't needed and removing them from your package.json file.

{:.good}
All our Javascript is packaged up and delivered directly, without any downloads from third parties.

#### Dependency Necessity

Reduce the amount of JavaScript that has to be downloaded and parsed by the browser by only using libraries where necessary. Consider whether you can use a native JavaScript API instead. Check the package size, and whether individual modules can be installed and imported rather than the whole library.

{:.ok}
There's almost certainly some code in the large libraries like THREE.js that we can avoid pulling in, but it should be removed by tree-shaking. We should be clearer on that though and make sure it's the case.

#### Dependency Updates

Regularly check dependencies and keep them up-to-date.

{:.good}
Dependencies are automatically maintained by Dependabot on GitHub, and pushed out with regular releases.

</details>

### Guideline 3.18. [Include Files That Are Automatically Expected](https://w3c.github.io/sustyweb/#include-files-that-are-automatically-expected)

Search engines and browsers regularly examine websites, requesting specific files by default (they expect them to exist). If the files don't exist, this will lead to potential errors and emissions being caused when they could be created, especially as the files offer SEO, user-experience, and other benefits to visitors.

<details markdown="block">
<summary>
Criteria: 🔴
</summary>

#### Expected File Formats

Take advantage of the favicon.ico, robots.txt, opensearch.xml, site.webmanifest, and sitemap.xml documents.

{:.bad}
We don't have these yet.

</details>

### Guideline 3.19. [Use Plaintext Formats When Appropriate](https://w3c.github.io/sustyweb/#use-plaintext-formats-when-appropriate)

Several small assets can be included within a website, conferring a range of benefits upon the website or application that utilizes them. They each have a low carbon footprint, so while they do create emissions, it's worth including them for the benefits they provide.

<details markdown="block">
<summary>
Criteria: 🔴
</summary>

#### Beneficial File Formats

Utilize standards such as ads.txt, carbon.txt, humans.txt, security.txt and robots.txt.

{:.bad}
We don't have these yet.

</details>

### Guideline 3.20. [Avoid Using Deprecated or Proprietary Code](https://w3c.github.io/sustyweb/#avoid-using-deprecated-or-proprietary-code)

The Web is full of dead, often proprietary code, created using standards that have been superseded or by groups that aren't recognized. By following recognized coding standards, you ensure that your code will be rendered properly by browsers (and reduce the potential for added emissions occurring from unmaintained rendering processes).

<details markdown="block">
<summary>
Criteria: 🟡 🟡
</summary>

#### Deprecated Code

Upgrading or avoiding deprecated formats is important, the only exception being if consumer support demands maintaining older standards to provide a functional product.

{:.ok}
We do have to support a number of outdated formats for 3d models. But, a primary purpose of Manyfold is to help users turn those old formats into more efficient newer forms, a process we've started with our 3MF conversion.

#### Outdated Code

Don't use an older standard if a newer recommendation will do the same job as / or more effectively.

{:.ok}
We do stay up to date with recent standards and recommendations, though we may sometimes fall behind. For instance, our HTML could probably be a bit more up to date.

</details>

### Guideline 3.21. [Align Technical Requirements With Sustainability Goals](https://w3c.github.io/sustyweb/#align-technical-requirements-with-sustainability-goals)

Every product or service is different, and each will require a different set of tooling to accomplish the most sustainable result. Deciding whether to go with a bulky framework, Static Site Generator (SSG), or a Content Management System (CMS) takes careful planning based on client or service requirements.

<details markdown="block">
<summary>
Criteria: 🔴 🟡 🟢 🟡 🔴
</summary>

#### Identify Requirements

List (and choose carefully) the requirements of the product or service. A simpler technological implementation may use more human resources but could have a smaller footprint. A prebuilt solution may use more system resources (and thereby produce more emissions upon render) but have a faster build-time (emitting less carbon during development).

{:.bad}
This has not been done carefully or intentionally.

#### Optimized Methodology

As a general rule, coding from scratch is the best-performing methodology (though if an existing solution is actively maintained, it may be better optimized than what you could produce). Therefore, prefer native components and file systems to a WYSIWYG editor or heavy framework, and be considerate of the impact of third-party solutions.

{:.ok}
Our language and framework choice optimises for development velocity, and in general will be more efficient than something we could write to do the same job. However, we can use them more efficiently.

#### Static VS Dynamic

If you do decide to use a code generation tool, consider using a Static Site Generator in preference to a bulky content management system. Because SSGs often start using a minimalist content entry format (like markdown) and all of the compilation is done before the website is uploaded, the emissions benefit comes from the server not having to place as much effort into serving pages (as they are static) for each visitor. In the case of a CMS, the dynamic nature of a site will involve additional computation (server-side processing) and bulkier libraries.

{:.good}
Our core application is inherently dynamic, so this cannot be applied, but our documentation site is fully statically-generated using Jekyll.

#### Expandability Considerations

Plugins, extensions, and themes have been carefully reviewed and selected to maximize interoperability, accessibility, and performance. They are regularly audited over time to ensure continued compatibility.

{:.ok}
We do consider these aspects for libraries and plugins, though the functionality is probably the primary driver. We do keep an eye on them to make sure they still work and that other solutions wouldn't be a better fit.

#### Interface Impact

Make sure all the components of the user-interface are the subject of special attention in terms of its sustainability impact while respecting accessibility and the performance of such components.

{:.bad}
We have not approached the UI in this way; it's something we should explore.

</details>

### Guideline 3.22. [Use the Latest Stable Language Version](https://w3c.github.io/sustyweb/#use-the-latest-stable-language-version)

Languages evolve regularly, and it's important for security and performance reasons to keep on top of the technology stack you are using. It's also important to consider whether the language you are using is appropriate or optimized for the task you wish to use it for.

<details markdown="block">
<summary>
Criteria: 🟢 🔴
</summary>

#### Versioning

Use the latest build of your chosen syntax language and its coupled framework.

{:.good}
We do automatically stay up to date with recent language and framework versions, except where blocked by other problems, in which case we work to actively resolve the blockers.

#### Language Choice

Many tools and programming languages are optimized for performing particular tasks, and utilizing those most appropriate to the problem, especially if there is a reasonable visitor base involved justifies the time and effort, as long as it doesn't impact ESG factors such as the well-being of those involved or become too cost prohibitive.

{:.bad}
Ruby is not the best language for processing heavy 3D content server side. We could save a lot of computation by using a lower-level native-code library for model manipulation.

</details>

### Guideline 3.23. [Take Advantage of Native Features](https://w3c.github.io/sustyweb/#take-advantage-of-native-features)

Ensuring that your code is free of redundancy by using pre-existing functionality provided by the web browser is important as it will help you to reduce the amount of time wasted, re-creating the same components, this offers obvious sustainability benefits in terms of time in front of the screen.

<details markdown="block">
<summary>
Criteria: 🟡
</summary>

#### Native Over Custom

Use native functions, APIs, and features over writing your own.

{:.ok}
We try to do this wherever possible, though we have some legacy code that still needs updating.

</details>

### Guideline 3.24. [Run Fewer, Simpler Queries As Possible](https://w3c.github.io/sustyweb/#run-fewer-simpler-queries-as-possible)

Making multiple requests whether HTTP or within a database has a carbon cost as infrastructure has to send that information back and forth. As such, managing how you store and use data locally for a visitor will help reduce wasted cycles.

<details markdown="block">
<summary>
Criteria: 🔴
</summary>

#### Database Queries

If you need information that is stored in a database, and you require it (or it's likely to be requested) more than once in your code, access the database only once, and store the data locally for subsequent processing. Also, avoid reliance on framework helpers that might defer filtering to later on in the process.

{:.bad}
We definitely have some database query optimisation to do. We've done some, but it has to be kept on top of, and we're probably a bit behind. Improving fragment caching would probably have a big impact here.

</details>

## Section 4. Hosting, Infrastructure And Systems

### Guideline 4.1. [Choose a Sustainable Hosting Provider](https://w3c.github.io/sustyweb/#choose-a-sustainable-hosting-provider)

In addition to reducing the environmental impacts of a website, choose a hosting service that mitigates the remaining impacts. To make sure of this, there are many criteria to look for.

<details markdown="block">
<summary>
Criteria: 🔴 🟣 🟣 🟡 🔴
</summary>

#### Monitor Metrics

To assess the environmental impacts of hosting and detect overconsumption, some indicators should be monitored: energy / water usage, CPU / Memory usage, allocation of servers and CPU cores, etc. These indicators could be used to calculate metrics directly related to environmental impacts, such as Power Usage Effectiveness (PUE), Water Usage Effectiveness (WUE), and Carbon Usage Effectiveness (CUE). They could be displayed to visitors for transparency and monitoring reasons.

{:.bad}
We're not monitoring metrics for either the self-hosted service or the demo instance.

#### Equipment Longevity

Manage equipment responsibly by keeping them as long as possible, using them as efficiently as possible, making sure they are certified, and purchasing long-lifespan products.

{:.na}
Manyfold doesn't have any of its own equipment. My laptop's over a decade old though, if that counts!

#### Recycling Waste

Recover, recycle, and upcycle waste including equipment.

{:.na}
Manyfold doesn't have any of its own equipment.

#### Renewable Electricity

Electricity comes entirely from sources with the lowest possible carbon intensity (ideally generated by wind or solar rather than from non-renewable sources). For example, Renewable Energy Credits (RECs) can help verify the source, or, ideally, prove that electricity comes directly from renewable sources.

{:.ok}
Power used by the dev team (me) is all renewable. However, our code hosting, image distribution, demo instance and website are on public cloud infrastructure (render.io and various GitHub services) and I'm not sure of their renewables status.

#### Remaining Emissions

Compensate remaining emissions, keeping in mind that the priority should be to avoid then reduce them and only compensate for them if they cannot be avoided. Carbon credits may not be sustainable, therefore the effectiveness of an offset solution must be verified, shown to be both environmentally viable and sustainable, and part of a longer-term strategy to eliminate emissions entirely from a chain, benefitting the wider ecosystem.

{:.bad}
We're not doing this, as we've not quantified our emissions yet.

</details>

### Guideline 4.2. [Optimize Browser Caching](https://w3c.github.io/sustyweb/#optimize-browser-caching)

Browser caching reduces the requirement for files to need to be constantly reloaded from the server, and in certain situations, it can even allow for files to be viewed offline (or in the case of a reverse proxy, send immediate recurring requests without additional calculation or computation from the server). As such, this will have sustainability and performance benefits (for instance by greatly reducing Time-To-First-Byte).

<details markdown="block">
<summary>
Criteria: 🔴 🔴
</summary>

#### Server-side Caching

If using a CMS, install an applicable plugin to enable on-the-fly server-side caching. Otherwise, use the provided server configuration files to include and tweak the file-type cache expiration using expires, bfcache, or cache-control HTTP header. If using a language or framework that generates pages on request, cache responses for static pages so that they can be reused for future visitors.

{:.bad}
We do not yet have proper server-side caching. This definitely needs adding.

#### Offline Access

Client-side JavaScript uses a combination of ServiceWorkers, WebWorkers, storage Application Programming Interfaces (APIs), or cookies (if necessary) to streamline the user-journey. For example, through the use of a PWA (Progressive Web Application) to ensure that an offline version is available and accessible at all times to reduce inequality and improve accessibility.

{:.bad}
We've not yet looked at PWAs for offline and efficient access to the service.

</details>

### Guideline 4.3. [Compress Your Files](https://w3c.github.io/sustyweb/#compress-your-files)

Every file will take up a certain amount of room on a server's hard drive, and this data will need to be sent across the wire to each visitor. Doing so will consume resources, but by using compression algorithms you can shrink each file to make its journey less impactful.

<details markdown="block">
<summary>
Criteria: 🔴 🔴
</summary>

#### Server-side Compression

If using a CMS, install an applicable plugin to enable on-the-fly server-side compression, such as Brotli or GZIP. Otherwise, use the provided server configuration files to include and tweak the performance-related features to the requirements.

{:.bad}
We're not doing this yet.

#### Media Compression

Compress your various images, fonts, audio, and video; by reducing the quality and offering different resolutions / dimensions (sizes) before uploading to a server or content management system.

{:.bad}
We're not yet doing this, though we have plans to do so using novel 3d compression formats and other tools.

</details>

### Guideline 4.4. [Use Error Pages and Redirects Carefully](https://w3c.github.io/sustyweb/#use-error-pages-and-redirects-carefully)

Navigation errors lead to mistakes, which lead to visitors wasting time trying to resolve them, or abandoning a website altogether. Anything that can be done to interject, predict, and way-find around potential problems will reduce emissions over time.

<details markdown="block">
<summary>
Criteria: 🔴 🔴
</summary>

#### Error Pages

Maintain sites by ensuring links are correct, and if errors occur, provide suitable way-finding within optimized pages for each error type to ensure resources can be identified to help visitors complete the task they started.

{:.bad}
We don't have useful error pages.

#### Redirection

Redirect websites, subdomains, and pages only when necessary. Proactively seek broken or outdated links and fix them. A redirect or search will often help reduce the number of pages a visitor needs to load.

{:.bad}
We probably rely on redirection quite a bit - we could probably reduce that, though a lot of it is built into the framework design.

</details>

### Guideline 4.5. [Limit Usage of Additional Environments](https://w3c.github.io/sustyweb/#limit-usage-of-additional-environments)

Decommission or switch off additional environments, such as testing / Quality Assurance QA) / re-production and other such environments when they are not useful.

<details markdown="block">
<summary>
Criteria: 🟡
</summary>

#### Unused Environments

Ensure no unused environment is available, balancing the cost of deploying an environment with the cost of keeping it online while unused.

{:.ok}
CI environments are spun up on demand through GitHub actions. However, our demo instance is always-on, and does not auto-scale up or down based on demand.

</details>

### Guideline 4.6. [Automate To Fit the Needs](https://w3c.github.io/sustyweb/#automate-to-fit-the-needs)

Any tasks, especially repetitive, that can be automated should be automated (compilation, deployment, tests, etc.) to reduce time at the computer being wasted by people.

<details markdown="block">
<summary>
Criteria: 🟢 🔴 🟡 🔴
</summary>

#### Automate Tasks

Every recurring task, such as deployment, testing, or compilation, can be run automatically, as recommended by continuous integration / continuous delivery best practices.

{:.good}
All our deploys, tests, builds and releases are run automatically through github actions.

#### Necessitate Tasks

To reduce wasted processing cycles, every automated task is only run when needed.

{:.bad}
We probably run too many builds; we could reduce duplication (especially, for instance, unnecessary repeated Docker builds).

#### Automated Scaling

Use automated scaling infrastructure to automatically increase the capacity of the web server and implement buffering / throttling to respond to visitor demand.

{:.ok}
The application itself is built in a way that supports simple horizontal scaling, so instance admins could do this. However, we're not doing it on our demo instance.

#### Security Tooling

Web browsing from bots has been steadily increasing in recent years. As such, it is a growing concern for security, performance, and sustainability. Use security tools that automatically block bad actors and minimize bad behavior. This results in substantially less load on the server, fewer logs, less data, less effect due to compromise, and more. The result of compromised websites is a large increase in HTTP, email, and other traffic as malicious code attempts to infiltrate other resources and exfiltrate data. Compromised websites are typically identified by anomalous patterned behavior.

{:.bad}
We don't currently do this, but do have plans to put in place rate limiting in the future.

</details>

### Guideline 4.7. [Maintain a Relevant Refresh Frequency](https://w3c.github.io/sustyweb/#maintain-a-relevant-refresh-frequency)

Only send data from the server when the visitor needs it. As much as possible, you can rely on client-side or server-side cache and client-side / local storage. Rather than refreshing data on a given frequency, it might be up to the visitor to manually ask for a refresh.

<details markdown="block">
<summary>
Criteria: 🔴
</summary>

#### Refresh Frequency

The frequency for refresh (of both the cache, locally stored data, and the page) is defined depending on visitor needs.

{:.bad}
A lot of data is probably sent unnecessarily and we've not spent time making sure cache behaviour is good, yet.

</details>

### Guideline 4.8. [Be Mindful of Duplicate Data](https://w3c.github.io/sustyweb/#be-mindful-of-duplicate-data)

For security reasons and in accordance with a Service-Level Agreement (SLA), it is often recommended to duplicate data to make sure it remains available if a problem occurs. This should be balanced with the cost of such duplication. Not all data is critical and, rather than overcompensating with multiple saves, duplication should be designed with efficiency in mind.

<details markdown="block">
<summary>
Criteria: 🟣
</summary>

#### Data Backups

Backups of system and user data are both incremental and secure.

{:.na}
We don't have any system or user data that needs backing up.

</details>

### Guideline 4.9. [Enable Asynchronous Processing and Communication](https://w3c.github.io/sustyweb/#enable-asynchronous-processing-and-communication)

Depending on carbon intensity, some processes and communications should be delayed and sometimes batched. This could also be a way to reduce the workload on a server or Virtual Machine (VM). In such cases, visitors should be warned that the process is asynchronous and notified when it is over.

<details markdown="block">
<summary>
Criteria: 🔴 🔴 🔴
</summary>

#### Batch Processing

By default, non-critical processes and communications are batched and launched only when carbon intensity is under a given threshold.

{:.bad}
We don't do this, though our background worker architecture would let us do so.

#### Protocol Usage

Ensure the communication protocols are relevant to the visitor's needs and data transferred. Avoid using insecure protocols (HTTP, FTP), and prioritize more efficient and privacy-aware data routes for visitors (HTTPS, SSH).

{:.bad}
The app doesn't yet have built-in support for HTTPS, so can still be run over HTTP.

#### Event-Driven Architecture

When creating products or services that utilize state changes (without triggering a complete refresh), consider if the utilization of Event-Driven Architecture and Microservices will be more environmentally friendly (based on the ESG variables involved) than traditional APIs in handling the server-side workload of your solution.

{:.bad}
We can use this more with the UI; Rails has support for things like Turbo and ActionCable to update pages more efficiently, which we're not currently using.

</details>

### Guideline 4.10. [Consider CDNs and Edge Caching](https://w3c.github.io/sustyweb/#consider-cdn-s-and-edge-caching)

Edge caching and CDN delivery can help optimize the sustainable delivery of digital services by optimizing how your website's traffic is transferred over the internet.

<details markdown="block">
<summary>
Criteria: 🟣 🟣 🟣 🔴 🔴
</summary>

#### Content Delivery Networks (CDNs)

When building for a globally distributed audience, use a CDN to store and serve simple read-only, pre-generated resources in a fast and efficient manner. Although they definitely can increase performance, it is also another layer of infrastructure that needs to be considered for sustainability.

{:.na}
We're not running a service that requires this sort of scale.

#### Sustainability Commitment

Check the CDN to verify that it provides a commitment to sustainability.

{:.na}
We have no CDN.

#### Local Servers

Choose a hosting provider with servers located close to the visitor.

{:.na}
Other than our small demo instance, we don't host our own service.

#### Avoid Caching Inappropriate Resources

Avoid using the service to host dynamic resources or JavaScript (unless through a first-party host) as due to cache partitioning, cross-origin resource sharing (CORS), and other browser mechanics, any benefits are negated by weaker performance, the inability to cache or interact, and the potential introduction of security and privacy issues to be introduced. This doesn't affect JSON or other static assets.

{:.bad}
Our cache behaviour isn't very good at the moment, so this could easily happen.

#### Process Data Close to the Source

All information passed between the layers of an application incurs a cost, both in terms of data transferred, and CPU cycles for (de)serialization. Wherever possible, data transformations should be performed close to the source to reduce these costs and avoid processing data that will later be discarded.

{:.bad}
There is definitely some excess data transfer within the app at the moment that could be reduced, particularly around background processing, mesh analysis, etc.

</details>

### Guideline 4.11. [Use the Lowest Infrastructure Tier Meeting Business Requirements](https://w3c.github.io/sustyweb/#use-the-lowest-infrastructure-tier-meeting-business-requirements)

Select infrastructure with minimal specifications meeting business requirements of performance, availability, etc.

<details markdown="block">
<summary>
Criteria: 🟢
</summary>

#### Lowest Requirements

Select infrastructure elements with the lowest requirements tier, meeting your service-level agreements. Avoid over-provisioning multi-datacenter, multi-zone, or distributed deployments if standalone instances meet the requirements. Also avoid provisioning infrastructure that will be under-utilized by provisioning for established average loads, ensuring reasonable resource utilization and autoscaling occurs as needed. Avoid provisioning for peak loads.

{:.good}
Our demo instance is run on a very very low tier!

</details>

### Guideline 4.12. [Store Data According to Visitor Needs](https://w3c.github.io/sustyweb/#store-data-according-to-visitor-needs)

Optimize storage of data according to what is most important, relevant, and required in service to visitors. This will help to avoid unnecessary storage of data that may not be useful or valuable, which will reduce required infrastructure, power, and data transfer.

<details markdown="block">
<summary>
Criteria: 🟢 🔴 🟢 🟣 🟣 🟢
</summary>

#### Reduce Redundancy

Remove unnecessary and redundant data from your servers, whether it is single-use (dark data) or abandoned.

{:.good}
Removal of duplicated data is a primary function of the app. It's highlighted to the user for easy removal.

#### Expiration Dates

Create data with an expiration date. Excess data is a form of technical debt, and routinely cleaning up old data needs to be normalized.

{:.bad}
We could create a list of the oldest content to encourage users to review and discard old models.

#### Classify And Tag

Use a data classification / tagging policy to make it easier to find, handle, and remove.

{:.good}
This is within the app design itself, not infrastructure, but tagging and classifying data is a primary function of Manyfold.

#### Justify Storage

Store data only when it is difficult to recreate.

{:.na}
We don't store any data that's not chosen to be put there by the user.

#### Optimize Logging

Optimize log collection, storage (off-site), and rotation; scheduling during low-activity hours and using carbon-neutral backup providers.

{:.na}
We do not store any long-term logs.

#### Asset Downloads

Ensure long-term assets, especially those of a large size, are made available for download.

{:.good}
The whole app is about download of large assets kept for the long term. This is a primary function.

</details>
