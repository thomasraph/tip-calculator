# Release Notes

## Version: 1.0.1

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

## Tried and reverted
The summary card was briefly a bar pinned to the bottom of the screen, then put back on top. The bar showed per person and total, and expanded to show base, tax and tip, and it held up with 20 people and a $12,345.67 bill. You preferred the card on top, with only the covering details moved down to the split area.
