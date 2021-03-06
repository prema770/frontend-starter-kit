# Frontend project checklist

Ideally we would want as many of those line items to already be taken care of, but in practice, it is not that simple and we need such a checklist to make sure that we deliver top-notch experiences.

This is meant to be used when a site goes live, but do go through it sooner to make sure there won't be too many surprises.

It might be a good idea to copy this file to your project and go through the checklist.

## The project's `README.md` contains

- [ ] Project installation instructions.
- [ ] Links to all deploy environments and any associated Git branch names.
- [ ] Links to CI, Trello board, Harvest project, project run sheet, Google Drive folder, Zeplin, InVision, Atomic, other.
- [ ] Expected Browser support and accessibility support.
- [ ] Debugging tricks.

## Code quality

- [ ] Try a fresh install of the project (preferably in a new VM or on a different machine) to ensure it can be installed from scratch... eg, that all dependencies are referenced and not implicit.
- [ ] CI runs the CI tests and the build breaks if they fail.
- [ ] GitHooks on changed files.
- [ ] Clean up commented/unnecessary code.
- [ ] Check all TODO and FIXME comments in the code are still relevant.
- [ ] Unintentional console logs and breakpoints removed.
- [ ] Code comments to document quirks or odd workarounds / compromises as is appropriate.

## Testing

- [ ] Production site has Sentry tracking.
- [ ] Site tested in all relevant browsers and devices.
- [ ] Site works with adblock.
- [ ] Site works with JavaScript turned off, or the sections that do not work are indicated to the user via messages in `<noscript>` tags.

## HTTP

- [ ] Static files are cache-busted with a unique hash (eg. main._4hjk54j6_.js) in production JS/CSS/etc.

##  CSS

- [ ] Print styles are defined and tested on all templates / pages.
- [ ] CSS classes use a consistent naming methodology (BEM).
- [ ] No vendor prefixes or IE filters in Sass (autoprefixer should handle this).

## JS

- [ ] JS is minified and concatenated in production.
- [ ] Polyfills are included if appropriate.

## HTML

- [ ] Links with `target="_blank"` use [`rel="noopener`](https://mathiasbynens.github.io/rel-noopener/) to avoid security problems.
- [ ] Links from user-submitted (untrusted) content use [`rel="nofollow`](https://support.google.com/webmasters/answer/96569)
- [ ] Where possible `data-thing` attributes are used to select elements, not classes or ids or tags.

## Accessibility

- [ ] Make sure all pages, in all states, are keyboard navigable.
- [ ] Body copy and visuals have enough contrast according to WCAG guidelines https://leaverou.github.io/contrast-ratio/.
- [ ] Most important content and pages are tested for color-blindness and vision disorders with http://lowvision.support/.
- [ ] Ensure form fields have labels.
- [ ] Ensure any acronyms use the `<abbr>` tag.
- [ ] In forms for accessibility reasons you may wish to display a validation summary of all page errors, or a “Sorry, there were some errors” at the top of the form.
- [ ] Roles (ARIA landmarks) are assigned to basic site sections.
header - `role="banner"`, main content - `role="main"`, footer - `role="contentinfo"`
- [ ] All images must have appropriate alt tags - extra great if you include all text that appears. Eg. English and Māori translation text in a lot of company logos in NZ. [empty `alt=""` can be appropriate](http://osric.com/chris/accidental-developer/2012/01/when-should-alt-text-be-blank/).
- [ ] If relevant, icons include an accessible label with the `<title>` SVG tag.
- [ ] `<html>` element has attribute `lang="en-nz"`.
- [ ] If you have used outline: 0 anywhere make sure you have called the tab focus function in utils js file or any other alternative style for focus state.
- [ ] Screen reader only text for links with images/icons only.
- [ ] Form fields are inside the label element.
- [ ] Form error messages should be inside label element.
- [ ] All toggle content should have aria controls and expanded states.

## Images

- [ ] Images use the right file format (SVG if possible, PNG for lossless graphics, JPG for lossy pictures).
- [ ] Run SVG's through SVGO.

## Fonts

- [ ] All of the fonts used on the project are correctly licensed, at the appropriate license level (expected pageviews/month).
- [ ] If relevant, Analytics email alerts are set up when audience levels go over the fonts' license thresholds.

### Functional completeness

- [ ] 404 page exists and is styled.
- [ ] 500 page exists and is styled.
- [ ] Maintenance page exists and is styled, if relevant.
- [ ] Site has a favicon.ico.

## Mobile

- [ ] Site uses a mobile-friendly, zoomable viewport.
- [ ] Platform-specific ([Apple](https://developer.apple.com/library/safari/documentation/AppleApplications/Reference/SafariHTMLRef/Articles/MetaTags.html),Android, Windows, etc) meta tags and favicons are added and checked with the [Favicon checker](https://realfavicongenerator.net/favicon_checker).

### Forms

- [ ] Forms use CSRF tokens when they mutate state (POST/PUT/DELETE, eg. editing a user/booking/listing’s data).
- [ ] Form fields use the correct [input types for the appropriate mobile keyboard](http://baymard.com/labs/touch-keyboard-types).
  - [ ] careful not to use input type=number unless you want a floating point number.
- [ ] Form fields have their [`name`, `autocomplete` and `autocorrect` attributes](https://html.spec.whatwg.org/multipage/forms.html#attr-fe-autocomplete) set correctly.

## SEO / SMO

- [ ] Run site url through the Facebook debugger (https://developers.facebook.com/tools/debug/) to check it will appear correctly if shared.
- [ ] Ensure that `<META NAME="ROBOTS" CONTENT="NOINDEX, NOFOLLOW">` is only on the correct pages.
- [ ] Ensure meta tags, Open Graph tags, Twitter card tags, and descriptions are set.
- [ ] Ensure the social meta tags only use a default sharing image if there is no page-specific image to use.
- [ ] Significant UI states (tabs, modals, etc) should be tracked in the URL via query parameter or the hash or else search engines might not index them.
- [ ] Google Tag Manager or Google Analytics are loaded on all pages (but not both).
- [ ] Check analytics are configured in development with a development property.
- [ ] Check analytics are configured in production with the production property on the live site.
- [ ] Check the relevant client-side interactions are tracked with events.
- [ ] If relevant, client-side JS errors are logged as [exceptions](https://developers.google.com/analytics/devguides/collection/analyticsjs/exceptions).
- [ ] Page and event tracking is being displayed correctly in the GA dashboard.
- [ ] Help pagination with `rel=”next”` and `rel=”prev”` attributes.

## Performance

- [ ] Static files are gzipped in production (JS/CSS/SVG/etc, check this with [PageSpeed](https://developers.google.com/speed/pagespeed/insights/) or [GTmetrix](https://gtmetrix.com/)) on the live site. 
- [ ] Test across varying network speeds, setup [Speedcurve](https://speedcurve.com/) and run tests through [WebPageTest](http://www.webpagetest.org/).
- [ ] Static files are cached for a long time in production (JS/CSS/images/etc, check this with [PageSpeed](https://developers.google.com/speed/pagespeed/insights/) or [GTmetrix](https://gtmetrix.com/)) on the live site.
- [ ] Canonical URL redirect exists, if relevant (eg. `example.com` ➞ `www.example.com`).
- [ ] HTTP to HTTPS redirect exists, if relevant.

## Github 

- [ ] Appropriate labels set on GitHub. See https://github.com/springload/labels.

You made it to the end! Whoo, high five my friend! Now go treat yourself to a drink :tropical_drink:, a hug, or whatever floats your waka :rainbow:. Don’t forget to let your team know that you’ve got this under control, and be proud of that top-notch site you just built.
