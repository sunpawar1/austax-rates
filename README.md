# austax-rates
To maintain current FY ATO published rates 
Why Not Fetch Directly from the ATO Website?
In an ideal world you would. The reality is the ATO doesn't publish rates as a clean API or JSON feed. Here's what they actually have:
ATO Source
What It Is
Why It Won't Work Directly
ato.gov.au web pages
Human-readable HTML pages
No API, HTML structure changes every year, would require screen-scraping which breaks constantly
ATO Tax Withheld Calculator
A web tool
No public API, requires browser session
ATO Developer Portal
API for lodgement and STP
Requires ATO software developer licence, OAuth, not for rate lookups
legislation.gov.au
Legal text of tax acts
Plain text legislation, not structured data
There is genuinely no public ATO JSON API that says "here are this year's tax brackets." The rates are buried in HTML pages, PDF documents, and legislation. Apps like TaxPack, Etax, and H&R Block all hardcode their rates manually too — they just have dedicated staff who do it each year.
Where to Get the Rates Each Year
The best sources in order of reliability:
1. ATO Individual Tax Rates page — most reliable, updated each July:
https://www.ato.gov.au/rates/individual-income-tax-rates/
2. ATO HECS repayment thresholds:
https://www.ato.gov.au/individuals-and-families/study-and-training/help-hecs-and-other-student-loans/repaying-your-help-debt/repayment-thresholds-and-rates
3. ATO Medicare Levy:
https://www.ato.gov.au/individuals-and-families/medicare-and-private-health-insurance/medicare-levy
4. ATO Super guarantee rate:
https://www.ato.gov.au/businesses-and-organisations/super-for-employers/paying-super-contributions/how-much-super-to-pay
Each May/June you visit these four pages, read the new numbers, and update rates.json. It genuinely takes about 10 minutes.
The Smarter Middle Ground — Use Claude
Here's what I'd suggest instead of doing it manually. Each year around May/June, come back here and say:
"The ATO has published 2025-26 rates. Please search for the current ATO tax brackets, HECS thresholds, Medicare levy, home office rate, and vehicle rate, then generate the updated rates.json block for me to paste into GitHub."
I'll search the ATO website, extract all the numbers, and produce the exact JSON block ready to paste. You just copy and paste it into GitHub — no manual reading of ATO pages needed.## Direct answer to your question — why not fetch straight from ATO?
The ATO does not offer a public API or JSON feed for tax rates. Their rates live inside human-readable HTML pages and PDF documents. There is no URL you can call to get back structured JSON data. Every tax app in Australia — Etax, H&R Block, TaxPack — hardcodes rates manually for exactly this reason.
The Two-Step Process Each Year
Where to get the numbers:
What you need
ATO page
Tax brackets
ato.gov.au/rates/individual-income-tax-rates
HECS thresholds
Search "ATO HECS repayment thresholds 2025-26"
Medicare levy
Search "ATO Medicare levy 2025-26"
Home office rate
Search "ATO fixed rate method 2025-26"
Vehicle rate
Search "ATO cents per km 2025-26"
Super guarantee
Search "ATO super guarantee rate 2025-26"
Concessional cap
Search "ATO concessional contributions cap 2025-26"
How to skip the manual reading entirely — use me:
Each May or June, come back here and say:
"ATO has published 2025-26 rates. Search and generate the new JSON block for my rates.json file."
I'll search the ATO pages, extract every number, and produce the exact block ready to paste. You copy it into GitHub. Done in 2 minutes. No manual reading of ATO pages required.
What Your GitHub Update Looks Like
When the time comes, you just add one block to rates.json — the structure you already have for 2024 and 2025, repeated for 2026 with new numbers. Commit it. Every user's app picks up the new rates within 24 hours automatically.
