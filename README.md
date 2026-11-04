## Installation

1. Download `smart-scheduler.zip` from the [latest release](https://github.com/arv1nv/smart-scheduler/releases/latest). Don't unzip it.
2. In Claude, go to **Customize > Skills** (or **Plugins** in newer versions).
3. Click **+**, then **Create skill**, then **Upload a skill**, and choose the ZIP.
4. Make sure the skill is toggled on by using "/smart-scheduler" or clicking the '+' button and finding it there.
5. Connect a calendar, such as Google Calendar, under **Connectors**. Without one, the skill gives you an .ics file to import instead.

## Usage

Send Claude a screenshot, email, or syllabus and say something like
"add these to my calendar." To change an event later, just say what changed,
for example "the midterm moved to Room 204."

## About

Smart Scheduler is a Claude skill that turns messy schedule information into clean calendar events. Send it a screenshot of a group chat, a forwarded email, a booking confirmation, or a full course syllabus. It pulls out every date, deadline, and plan, shows you a summary to approve, and adds the events to your calendar.

It also handles changes. Tell it “the midterm is in LAS C” or “move my dentist appointment to Friday,” and it finds the right event and updates it. It doesn’t create duplicates.

Features
Reads any input: images, PDFs, pasted text, tables, and forwarded messages
Resolves dates: converts “next Friday” or “Week 6” into exact dates using your timezone and term start date
Flags instead of guessing: asks about missing, vague, or TBA details in one grouped question
Checks your calendar first: skips duplicates and points out conflicts before adding anything
Confirms before acting: nothing is added or changed until you approve it
Smart updates: edits events in place, asks before changing a recurring series, and logs what changed in the event description
Works with your calendar: uses whichever calendar connector you have (Google Calendar, Outlook, and others). If none is connected, it gives you an .ics file instead
Example

You: [uploads syllabus] add all my deadlines

Claude: shows a table of 9 assignments, 2 midterms, and the final exam, flags one quiz marked “TBA,” and adds them after you approve.
