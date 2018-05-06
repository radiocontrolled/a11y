# Accessibility projects and tickets
I have incorporated accessibility into a range of personal projects, and tickets across the Software Engineering Grad Scheme.

## Side project: An accessible D3 line chart with ARIA table semantics
See https://github.com/radiocontrolled/d3-aria-table-chart

## Rotation: News Discovery and Curation

### Make 'Most Recent' offscreen h2 optional in Morph news-lx-wrapper component
https://jira.dev.bbc.co.uk/browse/NEWS-6311 <br/>
On News companies, commmodities, currencies and market pages, a 'Latest Updates' `H2` was present, alonside an offscreen 'Most Recent' `h2`. This created a P2 accessibility / usability error for AT users listening to these pages. To fix this bug, I created an optional config to suppress the 'Most Recent' `h2` in the Morph `news-lx-wrapper` component and updated the relevant Mozart page configs for companies, commodities and currencties. 

Example page free of offscreen 'Most Recent' `h2`:<br/>
https://www.bbc.co.uk/news/topics/crr7mlg0gqqt/apple

## Rotation: CPS
### Optimo header

Optimo is the next generation article editor from CPS. Building a new web-based editor presents a good opportunity to incorporate accessibility 'from the ground up'. I worked on the beginning stages of its UI in a workstream that focused on Optimo's header. The header is a React component that provides navigation and article creation buttons. 

<figure>
<img src="https://raw.githubusercontent.com/radiocontrolled/benj.info/master/assets/images/OptimoV1.png" alt="Early stage Optimo header with Optimo logo, dashboard, and create article button"/>
  <caption>Implementation of the Optimo header based on early wireframe</caption>
</figure>

<br/><br/>
The first way I incorporated accessibility into this workstream was by adding ARIA support to an Optimo dependency. Optimo's header implements the header provided by [int-gel-matter](https://github.com/bbc/int-gel-matter). Int-gel-matter is a bare-bones library of React components with the GEL 'look and feel'. Through manual testing I observed the int-gel-matter header was missing ARIA support, so I added this support: 

**PR: Add optional role attribute to AppHeader**<br/>
https://github.com/bbc/int-gel-matter/pull/133

**PR: AppHeader aria label**<br/>
https://github.com/bbc/int-gel-matter/pull/141 

The second way I incorporated accessibility into the Optimo workstream through knowledge sharing. In February 2018, I presented a CPS tech session walkthrough of the Optiomo header's accessibility features, including

* keyboard accessibility
* buttons with appropriate contrast on hover/focus states
* ARIA landmark roles
* ARIA support in the int-gel-matter header

### [CPSROADMAP-7171] Add Homes and Genre to Vivo Dashboard and Search
In the course of this ticket, which I pair programmed with Olivier Huin, I ensured appropriate colour contrast of home/genre information added to Vivo Dashboard, and implemented this change:<br/>
[https://github.com/bbc/vivo-client/pull/547](https://github.com/bbc/vivo-client/pull/547)

## Rotation: Visual Journalism
In Visual Journalism I worked on a range of bespokes. Across this work, I experimented with the use of ARIA roles, undertaking testing against BBC News accessibility guidelines where possible. A key point of reference apart, apart from these guidelines, was the Paciello group's suggestions for working with SVG accessibility around identifying SVGs with `role="img"` and using `aria-labelledby` to reference `title` and `desc` elements (this approach may be superceded by other techniques). Some examples of where I did this work include: 

* <a href="http://www.bbc.co.uk/news/business-40756834"> Does your job pay less than it did five years ago?</a>
* <a href="https://www.bbc.co.uk/sport/athletics/40779741">How the 100m record has fallen over time</a>
* <a href="http://www.bbc.co.uk/news/election-2017-39856354">Poll tracker: How the parties compare</a>

So for example, the Usian Bolt piece is an interactive piece that exposes keyboard operable left/right controls, and makes use of ARIA roles and labelling:

<img src="https://raw.githubusercontent.com/radiocontrolled/benj.info/master/assets/images/bolt.png" alt="Usain bolt piece screengrab, showing line chart with accessible controls visible and a snapshot of the inline SVG in the DOM">

This approach makes it <i>more</i> accessible than a standard D3 chart or animation, but what successes and lessons should be drawn from this example that might be applicable to future bespokes and reusable UI components?

After my rotation, I concluded the above approaches require more thorough testing that wasn't possible to due news deadlines. This has led to my current investigation of <a href="https://github.com/radiocontrolled/d3-aria-table-chart">d3 charts and ARIA</a>. Aside from bespokes, I also looked at the keyboard accessibility of the VJ facewall and various VJ components incorporating best practices into my development work. 

## Rotation: iPlayer Radio

### Mandatory Sign-In Modal accessibility
I demonstrated the modal window that pops up for iPlayer Radio's mandatory sign in feature was not accessibile as it was:

* not operable for keyboard-only users
* had a keyboard trap
* had innappropriate contrast

To address this, I incorporated [https://github.com/edenspiekermann/a11y-dialog](https://github.com/edenspiekermann/a11y-dialog) as a dependency of the MSI feature and the addressed other accessibility bugs.

See https://jira.dev.bbc.co.uk/browse/IPR-3176