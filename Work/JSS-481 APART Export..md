- Instead of "AVAILABILITY AGGREGATE REPORT: 01 Nov 2023 - 30 Nov 2023 " we should show the report name followed by the date range.
    - i.e, replace AVAILABILITY AGGREGATE REPORT to report name.
- Column header values should match the table headers in UI.

This ticket doesn't explain it well, it seems like a small fix in the beginning, but when I actually thought about it, it turns out that I'm going to be the one implementing the whole Export functionality.

Lets do it! Then.

- Let's first see how other reports are doing it, from ui to report generation.
- We need to find a report that has a table as a result and that displays the same table on export. (I don't think a table like that exists).




- Aggregate report has an updated report view that has it's own export and download buttons. Both are run by some plugin.
	- Turns out the functionality was already in place, but inside the html file, there were two generate report buttons, two download report dropdowns, two download buttons and so on. One in "HEAD" (unrendered) and one in "BODY" (actually rendered). But the couple had the same ids, which was triggering the functionality in the head but not in the body which was actually rendering. Fixed that!
- So I managed to export and download aggregate report, but now what? because I don't see any sheet. Why the sheet isn't being created. Not only in aggregate but I think in all the reports!

What have I managed to do till now?

- Got a basic understanding of the feature.
- Got the gist of how the frontend is connecting with the backend and how things are being done. Studied the two functions that are used to generate the report in ui and xl.
- Managed to change the column headers in the required way. Structure of the report looks as expected (sheet name/header not yet changed, though)
