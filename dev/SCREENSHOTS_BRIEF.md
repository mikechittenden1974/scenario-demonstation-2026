# Screenshot Capture Brief — StreamWave EPA Prep
**18 screenshots across Days 2, 3, 4, 5, 6. ~3 minutes per shot. ~60 minutes total.**

---

## How to work through this

1. **Open the StreamWave dataset** in Excel for Windows desktop (the only version that supports authoring Power Query with From PDF). Files live in `F:\scenario-demo-26\StreamWave_EPA_Prep\Data\`.
2. **Capture each shot as a PNG** using either the Windows Snipping Tool (`Win + Shift + S`) or Greenshot. Aim for a clean rectangle around just the relevant pane — no spare desktop, no unrelated windows.
3. **Save into** `F:\scenario-demo-26\StreamWave_EPA_Prep\Screenshots\` using the filename listed under each shot.
4. **Resolution:** anything between 1200px and 2400px wide works. Higher is fine — I'll scale on insert.
5. **Annotations:** where I've asked for callouts (Shots 01, 14), draw them in Greenshot or paste into PowerPoint and re-export. Otherwise just the clean UI.
6. When all 18 are saved, tell me and I'll insert them and re-render.

**Naming convention:** `NN_short-description.png` — two-digit number first, lowercase, hyphens for spaces, no extension surprises. Use exactly the filenames listed below.

---

## DAY 2 — Cleaning with Confidence (12 shots)

### 01 — `01_pq-editor-annotated.png`
**Show:** the full Power Query Editor window with `sw_cancellations` query open.
**Must include:** Ribbon at top · Queries pane on left · Column profile bar (the thin coloured strip directly under each column header) · Preview grid in the middle · Formula bar above the grid · Applied Steps pane on the right · a Data type icon visible on a column header (the `ABC` / `123` / calendar symbol left of the column name).
**Annotate** with arrow callouts labelled exactly: *Ribbon · Queries pane · Column profile · Preview grid · Formula bar · Applied Steps · Data type icon*.
**Why:** sets the map for the whole chapter — every later screenshot is a zoom-in on one of these regions.

### 02 — `02_use-first-row-as-headers.png`
**Show:** either side-by-side or two stacked screenshots in one image.
**Before:** any query loaded with generic `Column1, Column2, Column3…` headers and the real header names sitting in row 1.
**After:** the same query after clicking *Home → Use First Row as Headers* — real names now in the header row.
**Tip:** Use `sw_content_library.csv` and import it without first-row-as-headers, then capture before, click the button, capture after.

### 03 — `03_trim-before-after.png`
**Show:** the column profile bar on `sw_subscribers` → `status` column.
**Before:** three distinct values visible — `active`, `active ` (with trailing space), `cancelled`.
**After clicking** *Transform → Format → Trim*: two distinct values — `active`, `cancelled`. Applied Steps pane on the right shows the new "Trimmed Text" step.
**Tip:** to make the trailing-space case appear, you may need to seed one. Open `sw_subscribers.csv`, change one `active` to `active ` (with space), save, then refresh the query.

### 04 — `04_transform-format-menu.png`
**Show:** the *Transform* ribbon tab active, *Format* dropdown open. The dropdown lists *lowercase · UPPERCASE · Capitalize Each Word · Trim · Clean · Add Prefix · Add Suffix*. Just the open dropdown — no need to capture the whole editor.

### 05 — `05_type-icons-and-dropdown.png`
**Show:** a close-up of two or three adjacent column headers (say, `join_date`, `plan_type`, `status` from `sw_subscribers`) with their data-type icons visible. Click one icon to open the dropdown, capture showing the type options (*Whole Number, Decimal Number, Text, Date, Date/Time, True/False, etc.*).

### 06 — `06_change-type-using-locale.png`
**Show:** the *Change Type With Locale* dialog open on a date column. Data Type = *Date*. Locale dropdown showing *English (United Kingdom)* selected. The sample-value preview at the bottom of the dialog should show a UK-format date being parsed correctly.
**Tip:** use a date column from `sw_viewing_activity.xlsx` — the `watch_date` field.

### 07 — `07_replace-values-nulls.png`
**Show:** two states in one image (or capture two and I'll combine).
**Left:** column profile bar on `watch_duration_mins` (in `sw_viewing_activity`) showing "Empty 5%" or similar — point at the Empty value.
**Right:** the Replace Values dialog open with "Value to Find: null" and "Replace With: 0".

### 08 — `08_group-by-dialog.png`
**Show:** the Group By dialog open on `sw_cancellations`. Group by column = `subscriber_id`. Operation = *Count Rows*. New column name = `row_count`. **Bonus:** if you can fit it, show the result preview behind the dialog with 45 grouped rows visible.

### 09 — `09_remove-duplicates-result.png`
**Show:** `sw_cancellations` after sorting by `migration_flag` (descending) and using *Remove Duplicates* on `subscriber_id`. The bottom-left row count should read 45 (down from 55). Applied Steps pane on the right shows "Sorted Rows" then "Removed Duplicates".

### 10 — `10_conditional-column-dialog.png`
**Show:** the *Add Conditional Column* dialog open, mid-build.
- New column name: `is_churned`
- If clause: Column = `status`, Operator = *equals*, Value = `cancelled`, Output = `1`
- Else: `0`

### 11 — `11_columns-from-examples.png`
**Show:** the *Column From Examples* panel open on the right side of the Power Query Editor. `first_name` and `last_name` columns selected. In the empty new column, you've typed "Becky Quinn" on row 1 and "Sinead Iqbal" on row 2; Power Query has inferred the rest of the rows. The suggested transform text should be visible at the top of the panel (something like `[first_name] & " " & [last_name]`).
**Tip:** the names need to actually be in your subscribers data — pick any two for the example rows.

### 12 — `12_replace-values-prefix.png`
**Show:** the Replace Values dialog open on the `subscriber_id` column. Value to Find = `SW-`, Replace With = (empty). Behind the dialog, show the column with `SW-00047` having become `00047` (or similar) after a previous run.

---

## DAY 3 — The Merge (3 shots)

### 13 — `13_append-queries-dialog.png`
**Show:** the *Append Queries as New* dialog with "Three or more tables" radio button selected. The three viewing-activity queries (`sw_viewing_activity`, `sw_viewing_activity_FY2025_26`, `sw_viewing_activity_FY2026_27`) added on the right side. **Bonus:** if you can capture in two halves and combine — show the new appended query appearing in the Queries pane after clicking OK.

### 14 — `14_merge-queries-annotated.png`
**Show:** the full *Merge Queries* dialog. Top pane = left (primary) query (`sw_viewing_activity_combined`) with `subscriber_id` highlighted. Bottom pane = right (related) query dropdown set to `sw_subscribers`, also with `subscriber_id` highlighted. Below = Join Kind dropdown set to *Left Outer (all from first, matching from second)*. At the bottom of the dialog = the matching-rows indicator (e.g. "10,638 of 10,638 rows match").
**Annotate** with callouts labelled exactly: *Left (primary) query · Right (related) query · Matching column · Join Kind · Match indicator*.

### 15 — `15_row-count-before-after.png`
**Show:** two captures of the bottom-left of the Power Query Editor (where the row count is displayed) — once before the merge step, once after. **In both:** the Applied Steps pane on the right should be visible. **In the "after":** the new "Merged Queries" step should be highlighted in Applied Steps. Combine into one image with the labels "BEFORE" and "AFTER".

---

## DAY 4 — Reading the Data (1 shot)

### 16 — `16_close-and-load-to.png`
**Show:** the *Import Data* dialog (the one that opens when you click *Close & Load To…*). All four output options visible: *Table · PivotTable Report · PivotChart · Only Create Connection*. The worksheet target picker below ("Existing worksheet" with a cell reference field, or "New worksheet").

---

## DAY 5 — Patterns & Relationships (1 shot)

### 17 — `17_format-trendline-pane.png`
**Show:** Excel chart workspace with a scatter plot of `tenure_months` vs `total_hours_watched` (or whatever pairing you used in Day 5). The chart in the background should show:
- A trendline drawn in red (or whatever colour Excel defaults to)
- The equation `y = 1.4x + 9.2` (or close to it) shown next to the line
- The `R² = 0.71` value also visible
- The actual data points as dots

The *Format Trendline* task pane should be open on the right with:
- Trendline Options section visible
- *Linear* radio button selected
- "Display Equation on chart" checkbox ticked
- "Display R-squared value on chart" checkbox ticked

---

## DAY 6 — Pivots and Charts (1 shot)

### 18 — `18_pivottable-fields-pane.png`
**Show:** an Excel worksheet with a built PivotTable on the left and the *PivotTable Fields* pane open on the right.

**Field assignments:**
- Rows: `region`
- Columns: `plan_type`
- Values: Count of `record_id` (or `subscriber_id`)
- Filters: (empty, or `is_churned` if you want to demo)

The resulting pivot in the worksheet should clearly show region names down the left, plan types across the top (Basic, Standard, Premium), and count values in the cells.

---

## When you're done

1. Verify all 18 files are in `F:\scenario-demo-26\StreamWave_EPA_Prep\Screenshots\` with the exact filenames above.
2. Spot-check that text is legible at 100% zoom (especially the dialog boxes).
3. Tell me they're ready — I'll insert them into the HTML, scale/position to fit the existing callout box layout, and re-render the affected PDFs (Days 2, 3, 4, 5, 6).

If any shot turns out to be impractical (e.g. you can't conveniently reproduce the trailing-space case for Shot 03), skip it and tell me which numbers — I'll either rework the surrounding text to remove the screenshot dependency, or generate a stylised SVG mockup as a fallback.
