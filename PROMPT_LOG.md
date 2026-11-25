# Prompt Log — Slay Nails

## 1 — Generate initial Slay Nails booking page (FR-01)
- Prompt: Six-line prompt specifying Slay Nails service menu with prices, owner vacant slot input, customer booking with immediate slot locking/disabling, and localStorage persistence (generated via backup chat assistant per Step 7b because VS Code Copilot returned model_not_supported).
- Result: Created single-file index.html with vanilla HTML, CSS, and JavaScript.
- Verified: Services display with prices; owner can add vacant slots; booking a slot locks it and makes it unclickable; data persists across page refresh.
- Commit: e756bf2

## 2 — Separate Customer View and Owner Mode toggles without login
- Prompt: Separate the Owner slot input and confirmed bookings list into an Owner Mode toggle so customers only see services and booking by default without requiring a server or login.
- Result: Added Customer View (default) and Owner Mode toggle pills in the header of index.html.
- Verified: Page opens in Customer View hiding owner controls; clicking Owner Mode reveals slot creation and confirmed bookings.
- Commit: e756bf2

## 3 — Add Home Service option with +₱150 additional fee
- Prompt: Add a "Home Service" option to the nail services list with its additional price (+₱150), live total price calculation, and a demo barangay/area input when selected.
- Result: Displayed Home Service (+₱150) in the price list, added a Home Service checkbox with a demo barangay/area input, and added a live Estimated Total bar.
- Verified: Checking Home Service adds ₱150 to the total and displays a Home Service badge in Owner Mode; data persists after refresh.
- Commit: e756bf2

## 4 — Enforce minimum date on calendar picker and minimum name length
- Prompt: Set the owner date picker minimum date to today and reject customer names shorter than 2 characters. Change only validation and date initialization.
- Result: Set slotDate.min to today's date and added a 2-character minimum check on customerName.
- Verified: Past dates are disabled in the date picker; 1-character names show an error message.
- Commit: 3f4474a

## 5 — Add button to remove unbooked vacant slots in Owner Mode
- Prompt: Add a "Remove All Unbooked Slots" button in Owner Mode that clears unbooked slots without affecting already-booked slots.
- Result: Added clearUnbookedBtn button and click listener that filters out unbooked slots and updates localStorage.
- Verified: Clicking Remove All Unbooked Slots deletes available slots while keeping booked slots locked.
- Commit: 29638c9

## 6 — Add Cancel Booking feature that reopens locked time slots
- Prompt: Add a Cancel Booking button next to each confirmed booking in Owner Mode that asks for confirmation, deletes the booking, and unlocks the time slot so customers can book it again.
- Result: Added cancelBooking() function and Cancel Booking button in renderBookings() inside index.html.
- Verified: Canceling a booking removes it from Owner Mode, unlocks the slot in Customer View, and persists across refresh.