# Release Notes

## Version: 1.0.6
### Date: November 1, 2026

Four fixes from a bug report on history, texting and defaults. Each one was reproduced on 1.0.5 before being fixed.

## History fixes
- **Identical bills both saved:** clearing the amount to 0.00 starts a new bill, and the new bill now always gets its own History entry even if it matches the last one. Before, a second $10 bill after a first $10 bill was dropped, so History showed $10 instead of $20. The same goes for the first bill after reopening the app. Saving an unchanged bill twice without clearing still adds nothing.
- **Changes at the same total are saved:** editing a bill now updates History whenever any line changes, not only when the total or split changes. Before, changing $0 tax / $20 tip to $20 tax / $0 tip on a $100 bill (both $120) kept the old breakdown.

## Texting fix
- **New bill, fresh texts:** clearing the amount to start a new bill now clears the "✓ Texted" marks. Before, an identical new bill showed Alex as already texted, and Text everyone skipped them.

## Defaults fix
- **Saving defaults leaves the current bill alone:** a tip typed in dollars now saves its exact percent ($174.50 on $1,000 saves 17.45%, not 17.5%), and the current bill keeps its $174.50 tip and $1,174.50 total. Before, saving switched the bill to the rounded percent and changed it to $175.00. Tax typed in dollars from a receipt also stays as typed.

## Testing
- **Full regression before release:** 226,000+ random bills against the independent reference calculator (zero mismatches), 2,496 rounding cases, the 141-check feature suite, 235 start-to-finish scenario checks across four scenario packs (including 39 new checks for these four bugs, which fail on 1.0.5 and pass now), and the three real receipts, all passing on the exact version pushed.
- **Offline cache bumped to v11.**

## Version: 1.0.5
### Date: November 1, 2026

History now shows uneven splits the way the main screen does, saved tips stay exactly as typed, and the offline copy of the app is harder to break.

## History fixes
- **Uneven splits shown in full:** when a bill doesn't divide evenly, History now lists both amounts, for example "1 × $6.54, 1 × $6.53" for $13.07 split 2 ways. Before, it showed one "each" amount that was a cent off for some people. This applies to the list, opened bills, Share this bill and the shared history. Bills saved before this update still show their single amount.
- **Card fee and cash rounding in opened bills:** tapping a bill now shows the Card fee and Cash rounding rows. Shared text already had them, but the expanded view didn't.
- **Fits small phones:** on narrow screens (320px), the two amounts wrap neatly onto two lines instead of squeezing the date and number of people.

## Defaults fix
- **Exact saved tip:** Save Defaults now keeps the tip exactly as typed, so 17.45% stays 17.45% (it was saved as 17.5%). A tip typed in dollars saves its percent equivalent, as before.

## Offline reliability
- **Only good pages are saved for offline use:** the app no longer stores a failed load (like a "not found" page) over its working offline copy. Offline cache bumped to v10.

## Testing
- **Full regression before release:** 226,000+ random bills against the independent reference calculator (zero mismatches), 2,496 rounding cases, the 141-check feature suite, 196 start-to-finish scenario checks across three scenario packs (including 68 new checks for this release), and the three real receipts, all passing on the exact version pushed.

## Version: 1.0.4
### Date: October 25, 2026

Three new options that fit into the existing screens: a card price for restaurants that charge more for cards, tax entered in dollars straight from a receipt, and a choice of how tax is rounded.

## Card price
- **Cash price / Card price:** a new two-button choice in the Bill section. Cash price is the default, so nothing changes unless you pick Card price.
- **Card fee %:** picking Card price shows a small box, set to 3% to start. The fee is added to the food and tax, not the tip, and appears in the summary, the screenshot, shared text, texts and History.
- **State rules:** in Connecticut, Maine and Massachusetts (which ban card surcharges) and in Colorado and Illinois (which cap them), a short note says so.

## Tax in dollars
- **Tap % on the tax box** to switch it to $ and type the tax printed on your receipt. Base, tax and total then match the receipt to the penny, and the tip and split follow from it.
- **Example:** a Las Vegas receipt charged $7.31 on $87.00 (the restaurant used 8.4% instead of the official 8.375%). Entering $7.31 gives the receipt's exact $111.71.
- Tapping $ goes back to the rate, and changing the state or city switches back automatically.

## Real receipts tested
- **Card fee on the whole bill:** some restaurants put the card surcharge on everything, including an automatic service charge. Under Card price you can now pick "Fee on food + tax" (default) or "Fee on total with tip". Yum Cha in Las Vegas: $91.97 with a 3% surcharge on the whole bill gives the receipt's $94.73.
- **Cash rounded to 5¢:** with pennies going away, some places round cash totals to the nearest nickel (1–2¢ down, 3–4¢ up). Under Cash price, check "Round cash total to the nearest 5¢". A Chinatown, New York receipt: $48.64 becomes the receipt's $48.65 cash price, and the rounding shows in the summary, screenshot and shared text.
- **Exact tip % label:** the tip percentage shown is now rounded half-up with exact math, so a custom 17.45% shows as 17.5% (it could show 17.4% before). Dollar amounts were never affected.
- **Full regression before release:** 216,000+ random bills against an independent reference calculator (zero mismatches), 2,496 rounding cases, the 141-check feature suite, 128 start-to-finish scenario checks across two scenario packs, and the three real receipts, all passing on the exact version pushed.
- **Checked against three real receipts** (Donutique and Yum Cha in Las Vegas, a Chinatown café in New York): every line matches once the receipt's printed tax is entered in dollars.

## Tax rounding
- **To the cent (default):** tax is rounded to two decimals before the tip, the way receipts do it.
- **Exact:** tax keeps every decimal and only the total and each person's share are rounded. The lines can differ from the total by 1¢, and a note says so when they do. Found in Defaults and saved with them.
- **Tested:** the reference calculator now covers all three options; 100,000+ random bills had zero mismatches, and 88 start-to-finish scenario checks plus the 141-check feature suite pass.

## Version: 1.0.3
### Date: October 16, 2026

Discounts now work correctly when you enter the total from your receipt, and the app shows exactly what the tip is based on.

## Discount fixes
- **No more double discount:** in Total with tax mode, the amount you enter is now treated as the receipt total with the discount already taken off. Before, the app took the discount off a second time: a $87.10 receipt with 20% off showed an $80 original price and a $64 subtotal. It now rebuilds the real numbers: $100 original, $20 off, $80 subtotal, $7.10 tax.
- **Flat-dollar discounts fixed:** the same mode with a $20 discount gave a total of $82.75, less than the $87.10 actually paid. It now matches the receipt.
- **Tip basis shown:** with a discount on, the line under the tip buttons and the summary card say what the tip is figured on, for example "Tip is 20% of $108.88, the price before the discount, plus its tax." Before, a $21.78 tip next to an $80 base looked wrong even though it was correct.
- **Exact math at any bill size:** every number you type is now read as an exact fraction and all amounts are kept in whole cents, so results no longer drift by a cent on very large bills. Before, a $3.5 million receipt in Total with tax mode came out 1–2¢ off.
- **Fair leftover pennies:** when leftover cents tie between people, the extra penny now always goes to the first person in the list. Before, tiny decimal noise sometimes gave it to someone else (totals were always right).
- **Negative numbers count as 0:** typing a negative tax rate, tip or discount (for example "-7") now counts as 0 and shows 0%, and the box resets to 0 when you leave it. Before, "-7" was read as 7%.
- **Tested:** an independent reference calculator checked 153,000+ random bills across every tax rate, tip type, discount type, split and covering setup with zero mismatches; 63 start-to-finish dinner scenarios and the 141-check feature suite all pass.

## Version: 1.0.2
### Date: October 12, 2026

Today the app learned to remember: every bill now saves to a History section you can filter, share and clean up. A full regression pass also caught and fixed a 1¢ rounding error and two display bugs, and the app is now set up to install on Android.

## History
Your last 20 bills are kept in a History section that opens like Defaults. Bills save on their own, so there is no Save button.

- **Automatic saving:** a bill saves about 3 seconds after you stop changing it, so half-typed amounts are never stored. Editing the tip, people or discount afterward updates the same entry instead of adding a duplicate. Clearing the amount back to 0.00 starts a new bill.
- **Instant saves:** sharing, taking a screenshot, copying or texting saves right away, and so does switching away from the app.
- **Filter by person:** type a name or open the dropdown, which lists everyone in your history with their bill counts. Typing is forgiving, so "jrd" finds Jordan Diaz. The summary shows that person's totals, for example "Alex Kim: 3 bills · paid $132.40," and each bill shows what they paid or who covered them.
- **Filter by date:** Any time, Today, Last 7 days, Last 30 days, This month, or Pick a date.
- **Five at a time:** the list opens with the 5 most recent bills. "Show 5 more" loads older ones, and "Show fewer" collapses back.
- **Details:** tap a bill to see the base, discount, tax, tip and each person's share.
- **Share:** a share icon sends every bill that matches your filters, with a total at the bottom. Each opened bill also has Share this bill. On a phone this opens the share sheet; where sharing is blocked, the text is copied instead.
- **Delete:** a trash icon on every row removes a bill, with an Undo for 6 seconds. Clear history asks for a second tap before wiping everything.
- **Where it's stored:** in the phone's browser storage for this site, not on a server. It lasts until you clear Chrome's site data or uninstall the app, and it doesn't move to a new phone or a different web address.

## Fixes from regression testing
A 138-check automated suite now covers every feature, and a separate pass ran 2,496 odd-number cases against an exact reference. Everything passes.

- **Exact-cent rounding:** a $10.05 bill with 10% off has a discount of exactly 100.5¢, which should round up to $1.01; the app rounded it to $1.00, leaving the total 1¢ high. All money math now runs in whole cents with consistent half-up rounding, which also protects tax and tip on amounts ending in 5¢.
- **Large bills on the summary card:** above about $1,000, the Base and Tax figures overlapped. The breakdown now switches to two rows when amounts get long, and the big per-person number shrinks on small phones so even a $13 million bill fits.
- **Screenshot in Who's paying mode:** the image showed an extra-pennies line ("3 pay $35.93, 1 pay $35.92") that didn't match covered amounts like $71.85. That line is gone in this mode, since each person's exact amount is listed.
- **Pop-up messages restored:** confirmations like "Copied as text" had been removed by mistake when the share icons moved to the top bar, which also made those actions throw an error after finishing. They show again.

## Install on Android
The repo's manifest, icon and offline file are now linked from the app, so Chrome on Android offers Install app.

- **Installs like an app:** home-screen icon, full-screen window and navy status bar.
- **Works offline,** and checks for a new version each time it opens.
- **Keeps your data safer:** the app asks Chrome to protect its storage so History and favorites aren't cleared when the phone runs low on space.
- **Contacts and texting** work once the app is installed.

## Version: 1.0.1
### Date: October 9, 2026

Today the app learned to handle real group dinners: one person can pay for others, each payer can be texted their exact amount, and discounts come off before tax. Bill entry also got faster, with the amount starting at 0.00 and the decimal filling in as you type.

## Split and covering
Any person can now cover one or more others, and their share grows by one share per person covered. In a test with five people where Alex covers Sam, Alex owed $44.16, the other three owed $22.08 each, and the shares added up exactly to the $110.40 total.

- **Who's paying mode:** open a person's ⋯ menu, tap Pays for someone, and pick who they cover. The covered person tucks under the payer as "Covered by Alex" with an Undo button, and the payer shows "2 shares · covering Sam."
- **You can be covered too:** "You" appears in the pick list. If you were covering others when someone picks you up, those people move to the new payer. Removing the payer puts you back as paying.
- **Number of people mode:** a "Someone's covering others?" link reveals a People paying dropdown (for example 4 of 5). Below it, a line shows what a payer owes for themselves, for 2 people, and so on.
- **Where it shows:** covering details live in the split area, not on the summary card. The card keeps only the main numbers and a label like "New York City, NY · 5 people."
- **Shared output:** the screenshot and copied text list each payer, for example "Alex (+ Sam): $44.16." Leftover cents are spread so the payer amounts always add up to the total.

## Texting each person their amount
A small speech-bubble icon next to the Split label sends each payer a text with their own amount, one person at a time. It only appears when Who's paying is on.

- **Each tap** opens your messages app with the next person's number and message filled in. You tap send yourself, since a web app can't send texts on its own.
- **The message** includes the payer's total, including anyone they cover: "Hi Alex! Your share of the bill is $52.27. That covers you and Sam. (Total $130.66 split 5 ways, tax and tip included.)"
- **A green badge** on the icon counts the people still to text, and a pop-up names who's next.
- **Sent tracking:** anyone texted shows "✓ Texted" under their name. If the amounts change afterward, the mark clears so you know to resend.
- **Who gets skipped:** covered people (their payer gets the combined amount) and people with no phone number, which means anyone typed in rather than picked from contacts.
The design went through three versions today: a text icon on every row with a big Text everyone button, then a separate Send amounts panel, then the single small icon you settled on. Person rows were simplified along the way to name, amount and a ⋯ menu with Pays for someone, Favorite and Remove.

## Discounts
A Discount section now sits between Tip and Split, built like the tip controls. The discount comes off the food price before tax, so tax is charged only on the lower amount.

- **Options:** None, 10%, 15%, 20%, 25%, and Custom, which takes a % or a flat dollar amount. A green badge shows the savings, for example −$20.00.
- **Tip choice:** once a discount is on, two buttons appear. Tip on original price is the default, so the server isn't tipped less because of a coupon. Tip on discounted is the alternative, and a short line explains whichever is selected.
- **Summary card:** the base shows the discounted amount with a label like "Base −20%," plus a line such as "Includes $20.00 off (20%), from $100.00." The screenshot and shared text list the subtotal and discount separately.
- **Not saved with defaults,** since a discount usually applies to a single meal.
Example: $100 bill, NYC, 20% off, 20% tip on original

Amount

Subtotal

$100.00

Discount (20%)

−$20.00

Tax (8.875% on $80.00)

$7.10

Tip (20% of $108.88, the original price plus its tax)

$21.78

Total

$108.88

## Bill entry and other polish
The bill amount now starts at 0.00 and fills from the right like a card terminal: typing 8, 4, 5, 0 shows 0.08, 0.84, 8.45, then 84.50.

- **Bill entry:** backspace removes the last digit, large amounts get commas (8,450.12), phones open the number keypad, and pasting "84.50" keeps the decimal as typed.
- **Tip explanation:** a line under Tip with tax / Tip without tax says what the selected option means, for example "Tip is based on the full bill, tax included."
- **Person rows:** reduced to name, amount and a ⋯ menu, so long names no longer get cut off.
- **Location label:** on the summary card, a long label like "New York City, NY · 1 person" now moves above the big number instead of overlapping it.
