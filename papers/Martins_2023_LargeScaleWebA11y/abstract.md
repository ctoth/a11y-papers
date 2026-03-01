# Abstract

## Original Text (Verbatim)

This paper reports the results of the automated accessibility evaluation of nearly three million web pages. The analysis of the evaluations allowed us to characterize the status of web accessibility. On average, we identified 30 errors per web page, and only a very small number of pages had no accessibility barriers identified. The more frequent problems found were inadequate text contrast and lack of accessible names. Additionally, we identified the technologies present in the websites evaluated, which allowed us to relate web technologies with the accessibility level, as measured by A3, an accessibility metric. Our findings show that most categories of web technologies impact the accessibility of web pages, but that even for those categories that show a negative impact, it is possible to select technologies that improve or do not impair the accessibility of the web content.

---

## Our Interpretation

This paper gives us the largest automated WCAG 2.1 audit of the open web (2.9M pages), confirming that web accessibility is broadly and severely broken: 99.5% of pages have detectable errors, contrast and accessible-name failures dominate, and improper ARIA usage causes 24% of pages to fail WCAG 1.3.1 (Info and Relationships). The technology fingerprinting analysis is the paper's unique contribution — it identifies that the framework or CMS you choose has measurable, statistically significant effects on your site's accessibility, with some JS libraries (Isotope, Slick, bare jQuery) strongly associated with poor outcomes and others (Polyfill.js, jQuery Migrate, Python-based stacks) associated with better ones. For this project, this paper establishes the empirical ground truth that ARIA misuse is a widespread, measurable phenomenon at web scale — not just an edge case in user studies.
