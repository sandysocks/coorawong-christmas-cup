# Coorawong Christmas Cup – setup

Season: 1 November to 25 December 2026. Ranked on raw kilometres.
Runners: Sandy, Hadley, Rowan, Laura, Ruby, Cat.

## 1. Make the Google Form (about 3 minutes)

Go to forms.google.com, start a blank form called "Coorawong Christmas Cup – Log a run", and add these four questions, all required:

1. **Name**: Dropdown with Sandy, Hadley, Rowan, Laura, Ruby, Cat
2. **Date of run**: Date
3. **Distance (km)**: Short answer (Response validation > Number)
4. **Time (minutes)**: Short answer (Response validation > Number)

Keep the question titles exactly as above; the dashboard finds columns by these words.
In Settings > Responses, make sure "Collect email addresses" and "Limit to 1 response" are OFF (the shortcut can't sign in).

## 2. Link it to a Sheet and publish as CSV

1. In the form, open the Responses tab and click "Link to Sheets" > create a new spreadsheet.
2. In that Sheet: File > Settings > Locale = United Kingdom or Australia (so dates read correctly).
3. File > Share > Publish to web. Choose the responses tab and "Comma-separated values (.csv)", then Publish.
4. Copy the link it gives you.

## 3. Add the links to the dashboard

Open index.html and, near the top of the script, fill in:

- `CSV_URL` = the published CSV link
- `FORM_URL` = your form's share link (Send > link icon)

Until CSV_URL is filled in, the dashboard shows demo data so you can preview the look.

## 4. Put it on GitHub Pages

1. Create a new public repo, e.g. `coorawong-cup`.
2. Upload index.html (drag and drop on GitHub works fine, or push with git).
3. Settings > Pages > Deploy from a branch > main, / (root).
4. Live at `https://your-username.github.io/coorawong-cup/` in a minute or two.

## 5. Set up auto-tracking (Apple Health shortcut)

The "Automatically track my runs?" link on the Log a run page shows each runner the steps. You just need to fill in four IDs first:

1. Open your form in edit mode, click the ⋮ menu > "Get pre-filled link".
2. Fill in dummy answers (Sandy, any date, 5, 30) and click "Get link", then "Copy link".
3. The link looks like `https://docs.google.com/forms/d/e/1FAIpQ.../viewform?usp=pp_url&entry.123456=Sandy&entry.234567=2026-11-01&entry.345678=5&entry.456789=30`
4. In index.html set:
   - `FORM_POST_URL` = the same link up to `/viewform`, with `/viewform` changed to `/formResponse`
   - `ENTRY.name`, `ENTRY.date`, `ENTRY.distance`, `ENTRY.time` = the four `entry.NNNN` numbers, in that order

Test it on your own phone first before sharing with the family. If Shortcuts on your iOS version can't read workouts, everyone can still use the Log it button.

Tips: share the site link with the family and they can "Add to Home Screen" for one-tap logging. Google caches published sheets, so new runs can take up to about 5 minutes to appear.
