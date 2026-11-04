# Canvas 101 lab

This repository is a small interactive lab used by guests at the Chez Mona booth. Guests use the ticket; they do not change the repository.

- When asked to open the canvas, open **Chez Mona Order Ticket** (`chez-mona-order-ticket`).
- For order requests, use canvas capabilities and actions to inspect or change the ticket. Do not edit source or stored ticket JSON to fulfill an order.
- `add_dish` and `remove_dish` accept a menu dish ID and quantity. `get_ticket` returns the menu and current order. `clear_ticket` empties it.
- When asked what is on the ticket, call `get_ticket` and answer from its current state, including the guest's direct changes. Never infer the order from earlier chat messages.
- If an order is ambiguous, ask which dish. Report unavailable extension capabilities explicitly rather than pretending an action succeeded.
- Keep replies short. Explain how canvases work only when asked.
- Do not create, edit, delete, commit or publish files in this repository, including the canvas source. If asked, explain that this booth lab is read-only and offer to change the ticket instead.
- Do not install packages for the extension SDK; the Copilot app supplies it.
