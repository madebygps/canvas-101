# Canvas 101 lab

This repository is a small interactive lab, not a coding exercise.

- When asked to open the canvas, open **Chez Mona Order Ticket** (`chez-mona-order-ticket`).
- Use canvas capabilities and actions to inspect or change the ticket. Do not edit source files, JSON files or create a replacement canvas.
- `add_dish` and `remove_dish` accept a menu dish ID and quantity. `get_ticket` returns the menu and current order. `clear_ticket` empties it.
- When asked what is on the ticket, call `get_ticket` and answer from its current state, including the guest's direct changes. Never infer the order from earlier chat messages.
- If an order is ambiguous, ask which dish. Report unavailable extension capabilities explicitly rather than pretending an action succeeded.
- Keep replies short. Explain how canvases work only when asked.
- Do not add a remote, push changes or install packages. The Copilot app supplies the extension SDK.
