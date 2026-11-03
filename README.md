# Canvas 101

A local Chez Mona lab for the GitHub Copilot app. No remote, package installation, web deployment, or separate dev server is needed.

## Try it

1. Open GitHub Copilot app from the taskbar.
2. Look for the folder **Canvas 101**. On its right side, click the **+** button to start a new session.
3. Use this prompt: **Open the Chez Mona Order Ticket canvas**.
4. Click **Add Omelette** in the canvas.
5. Ask the agent: **Add two Soups to my ticket.** Watch the order update.
6. Use the canvas to remove one Soup yourself.
7. Ask: **What's on my ticket now?** Compare the answer with the visible order: one Omelette and one Soup.

Both your clicks and the agent's canvas actions update the same order ticket. A new session starts with an empty ticket. Reopening the canvas in the same session preserves the order.

The lesson is to switch between clicking, asking and checking. The agent reads the current ticket using `get_ticket`, including changes you made directly. A click changes the ticket; it does not automatically trigger agent reasoning or a chat reply.

The canvas includes all four exercise steps above the menu, with the exact chat prompts, expected final order and a reminder to return to the launcher for the quiz.

## Take it with you

A release checklist, issue board or project dashboard can use the same shared-work-surface pattern. In your own session after the lab, try:

```text
/create-canvas Create a release checklist canvas where I can check off items and the agent can read, add, and update them.
```

Describe the workflow, what you should be able to do and what the agent should be able to do. Creating a new canvas is a takeaway, not a required step in this booth lab.

## What is in this repo?

The repository-scoped extension lives in `.github/extensions/chez-mona-order-ticket/`. `extension.mjs` registers the canvas with the SDK bundled in the Copilot app. `canvas.mjs` connects agent actions to the ticket server. `ticket.mjs` owns ticket state and a loopback-only server; `public/` is the interactive panel.

The canvas exposes `get_ticket`, `add_dish`, `remove_dish`, and `clear_ticket`. The agent should use these actions rather than editing files to change the order.

The ticket is stored in the session's workspace under `artifacts/chez-mona-order-ticket.json`. It is not stored in the repository or shared between guest sessions. Reloading the panel or restarting its extension preserves that session's ticket.

## Booth setup

The parent launcher repository's `npm run prepare:canvas` command creates a separate local Git repository from these sources at `.local/Canvas 101`, with no push remote. Add that folder to the GitHub Copilot app once and pin the app to the Windows taskbar.

Use an app version that supports repository-scoped extension canvases. Node.js is needed by the extension runtime. The SDK import is supplied by the app; do not install a separate SDK package here.

Authenticate Copilot before guest use. After the lab, delete the guest session using the app's session menu, with the exact current label checked by staff. Start a new session for the next guest.
