---
name: smart-scheduler
description: Turn screenshots, texts, emails, syllabi, or any document into calendar events, and update or cancel those events later. Use when the user sends something containing dates, deadlines, plans, or events and wants them added to their calendar, says "schedule this", "add this to my calendar", or "put these dates in", or tells you a detail changed, like "the midterm is in Room 204" or "move my dentist appointment to Friday".
---

# Smart Scheduler

Extract every event, deadline, and plan from whatever the user sends, confirm the details with them, and add the approved events to the calendar they choose. When the user later shares new or changed details, find the matching event and update it.

First decide which mode applies:

- **Add mode:** the user shares new events. Follow Steps 1 to 7.
- **Update mode:** the user tells you something about an event that should already exist (a new location, a time change, a cancellation). Follow the Updating Events section.

If a message contains both, handle the updates first, then the new events.

## Step 1: Choose the calendar

1. Check which calendar integrations are available in this session (for example Google Calendar, Outlook, or Apple Calendar through a connector or device tool). Only count integrations that can write events. A calendar that is only visible through a read-only link (for example through another app's calendar view) cannot be used to add or update events. Prefer a direct connector for that calendar when one exists.
2. If more than one is available, ask the user which one to use. If the user named one earlier in the conversation, use it without asking again.
3. If exactly one is available, use it and say which one in a single line.
4. If none is available, tell the user plainly and offer an .ics file they can import into any calendar app. Never pretend an event was added.

## Step 2: Extract events

Read the full input: images, PDFs, pasted text, forwarded messages, tables, and footnotes. For each event, capture:

- **Title:** short and specific. For courses, use the format "COURSE CODE: Item" (for example "BIO 101: Assignment 3").
- **Type:** deadline, exam, class, meeting, social, appointment, or other.
- **Date**
- **Start and end time:** for deadlines, use the due time as a short event or an all-day event if no time is given.
- **Location or link:** if mentioned.
- **Notes:** grade weight, who it is with, what to bring, or the original wording if it was ambiguous.

Capture everything, including small items like quizzes, office hours changes, and RSVP-by dates. Do not merge separate events into one.

## Step 3: Resolve dates and times

- Get today's date and the user's timezone before resolving anything. Default to the user's local timezone.
- Convert relative dates ("next Friday", "tomorrow", "in two weeks") into exact dates.
- For academic schedules written as "Week 6" or "Lecture 10", find the term start date in the document. If it is not there, ask the user for it.
- If the year is missing, assume the next upcoming occurrence and mark it as assumed.
- Watch for conflicts inside the input itself (for example a table and a paragraph giving different dates). Surface both to the user.

## Step 4: Flag, do not guess

Never invent a date, time, or detail. Mark an event as needing input when:

- The date or time is missing, vague, or marked TBA.
- A message is tentative ("maybe Thursday?", "let's aim for 7ish").
- The text in an image is cut off or unreadable.

Ask about all flagged items together in one short message, not one question at a time.

## Step 5: Check the calendar

Before adding anything, check the chosen calendar around each date:

- **Duplicates:** if a matching event already exists, skip it and mention that it was skipped.
- **Conflicts:** if the new event overlaps something, point it out and let the user decide.

## Step 6: Confirm before adding

Show a compact table of the events to be added:

| Event | Date | Time | Notes |
|---|---|---|---|

Mark flagged, assumed, duplicate, and conflicting items clearly. Add nothing until the user approves. The user can approve all, remove items, or edit details.

## Step 7: Add the events

After approval:

- Create each event in the chosen calendar.
- Default reminders: 1 day before for deadlines and exams, 1 hour before for meetings and social plans. Use the user's own reminder preference instead if they have given one.
- Put the source and any notes in the event description.

Then report back in one or two lines: how many events were added, to which calendar, and anything skipped. Do not repeat the full list.

## Updating Events

Use this when the user gives new or changed details about an existing event, for example "the midterm is in Room 204", "my BIO 101 lecture is cancelled Friday", or "push dinner to 8".

### U1: Identify the change

Work out which event the user means and exactly what changed: location, date, time, duration, title, notes, or a cancellation. Only change the fields the user mentioned. Leave everything else as it is.

### U2: Find the event

1. Search the calendar in use (or the one the user names) using the course code, title keywords, and the likely date range. Search upcoming events first.
2. If there is exactly one clear match, use it.
3. If there are several possible matches (for example two midterms for the same course), list them briefly and ask which one.
4. If nothing matches, say so and offer to create it as a new event using Add mode. Do not create it without approval.

### U3: Handle recurring events

If the match is part of a recurring series (like weekly lectures), ask whether the change applies to:

- **This one occurrence** (for example one cancelled lecture or a one-time room change), or
- **All future occurrences** (for example the class permanently moving rooms).

Never change the whole series unless the user confirms it.

### U4: Confirm before changing

Show the change as a short before and after:

> **BIO 101: Midterm** (Mon Oct 12, 2:00 PM)
> Location: (none) → Room 204

If a new date or time overlaps another event, point out the conflict. Apply nothing until the user approves. If the user's message already gave a clear, specific instruction and there is exactly one match, a one-line confirmation is enough.

### U5: Apply the update

- Edit the existing event in place. Do not delete and recreate it, so reminders and any links to it are kept.
- Add a short line to the description noting what changed and when, for example "Updated Oct 5: location set to Room 204."
- For a cancellation, ask whether to delete the event or keep it and add "Cancelled: " to the start of the title. Only delete if the user chooses that.

Then confirm in one line what changed.

## Rules

- Only add events the user has approved in this conversation.
- Only edit or delete existing calendar events when the user asks, and only the specific event and fields they mean.
- Never edit events the user did not create through this skill without confirming the match first.
- If adding an event fails, say so and list which events were not added.
- Keep questions short and grouped. The goal is to save the user time.
