Progress notes for nav/icon fixes

- Fixed 'My Moves' links to open `mymoves` route instead of `inventory` from Home, Booking, Services, Inventory pages.
- Replaced several emojis with inline SVG icons across Home, Services, Booking, About, MyMoves, Inventory pages for consistent visuals.
- Added `Movers.css` and `MapView.css` and ensured Inventory imports its CSS.
- Ran `npm run build` — build succeeded.

Next items to confirm with you:
- Do you want a separate `Quote` page (e.g., route `quote`) distinct from the current booking form? I can add one and wire "Get Free Quote" buttons to that route.
- Do you want the site to use the shared `Header` for the home page as well (align header across pages)? I can enable that to make the nav identical on all pages.
- Shall I extract the duplicated small utility styles into a single `src/style.css` and import it globally to reduce duplication?
