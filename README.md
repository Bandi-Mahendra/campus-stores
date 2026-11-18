# Campus Stores

Campus Stores is a Product Engineer work sample set at a fictional campus media equipment desk. This project explores how a desk operator manages equipment requests, checkouts, returns, and shift handovers.

## My Product Decision: Making Equipment Handover Clearer

### What works well

The loan register maintains individual records for each physical equipment unit. It records the asset ID, request, borrower, and expected return time. Operators can also record returns against the correct loan slip.

This is useful because equipment is tracked at the individual-unit level rather than only by request. It helps operators identify which specific items are still with borrowers.

### What I would change

During the Film Society screening scenario, the projector and speaker are returned, while the adapter remains with another person and is expected the following morning.

The Desk book contains a message explaining this partial return. However, the operator must switch to the Loan register to identify which physical items are still outstanding and check their due times.

This creates an unnecessary step during shift handover. The next operator should be able to understand the current equipment status without reconstructing it from messages and separate records.

### My solution: Outstanding Equipment in the Desk book

I added an automatically generated **Outstanding Equipment** section to the Desk book.

It uses the existing open loan records to display:

- Physical asset ID and equipment type.
- Request ID.
- Borrower's name.
- Expected return time.

The section updates automatically when a return is recorded. Once an item is returned and its loan is closed, it no longer appears in the outstanding list.

I kept the existing messages and manual handover notes because they provide additional context that structured loan records cannot capture.

## Walkthrough

The improvement can be evaluated using the existing Film Society scenario:

1. Start the sample shift and check the Desk book. Existing outstanding loans are displayed.
2. Issue the Film Society's projector, speaker, and adapter.
3. Advance to the partial-return stage. Record the projector and speaker as returned while leaving the adapter outstanding.
4. Check the Desk book. The adapter should remain visible with its asset ID, borrower, request, and due time.
5. Advance to the next morning. Use the displayed asset ID to identify the correct loan in the Loan register and record the adapter's return.
6. Return to the Desk book. The adapter should no longer appear in the outstanding list.

## What I Would Keep

I would retain the existing per-asset loan records, return process, and manual handover notes.

The loan register is the source of structured equipment status, while messages and notes capture additional context. The improvement brings the important outstanding-loan information into the handover workflow without duplicating or replacing the existing system.

## How I Would Evaluate the Change

At a real equipment counter, I would observe whether an incoming operator can identify outstanding equipment and locate the correct loan record without asking the previous operator for clarification.

I would pay particular attention to:

- Time taken to identify outstanding items.
- Incorrect asset or loan-slip identification.
- Number of clarification requests during shift handover.

A reduction in these issues would indicate that the change is making handovers clearer and more reliable.

## Run the App

Open `index.html` in a modern browser. The app includes its scripts, styles, and icons and can run offline.

To serve it over local HTTP, run this from the repository folder:

```sh
python3 -m http.server 8000 --bind 127.0.0.1