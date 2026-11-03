# Canvas 101

A local Chez Mona lab for the GitHub Copilot app. No remote, package installation, web deployment, or separate dev server is needed.

## Try it

1. Open GitHub Copilot app from the taskbar.
2. Look for the folder **Canvas 101**. On its right side, click the **+** button to start a new session.
3. Use this prompt: **Open the Chez Mona Order Ticket canvas**.
4. Click **Add Omelette** in the canvas.
5. Ask the agent: **Add two Soups to the ticket**, then **Remove the Omelette**.

Both your clicks and the agent's canvas actions update the same order ticket. A new session starts with an empty ticket. Reopening the canvas in the same session preserves the order.

## What is in this repo?

The repository-scoped extension lives in `.github/extensions/chez-mona-order-ticket/`. `extension.mjs` registers the canvas with the SDK bundled in the Copilot app. `canvas.mjs` connects agent actions to the ticket server. `ticket.mjs` owns ticket state and a loopback-only server; `public/` is the interactive panel.

The canvas exposes `get_ticket`, `add_dish`, `remove_dish`, and `clear_ticket`. The agent should use these actions rather than editing files to change the order.

The ticket is stored in the session's workspace under `artifacts/chez-mona-order-ticket.json`. It is not stored in the repository or shared between guest sessions. Reloading the panel or restarting its extension preserves that session's ticket.

## Booth setup

The parent launcher repository's `npm run prepare:canvas` command creates a separate local Git repository from these sources at `.local/Canvas 101`, with no push remote. Add that folder to the GitHub Copilot app once and pin the app to the Windows taskbar.

Use an app version that supports repository-scoped extension canvases. Node.js is needed by the extension runtime. The SDK import is supplied by the app; do not install a separate SDK package here.

Authenticate Copilot before guest use. After the lab, delete the guest session using the app's session menu, with the exact current label checked by staff. Start a new session for the next guest.
