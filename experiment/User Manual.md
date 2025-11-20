# User Manual
### 1. System Purpose

The Gym Class Reservation System is a browser-based tool that allows gym members and administrators to manage class attendance:

- **Regular users (members)** can:
    - View the gym class schedule.
    - Sort and filter classes.
    - Reserve seats in upcoming classes.
    - Cancel their own reservations under certain conditions.
- **Admins** can:
    - Manage the catalog of classes (create, edit, delete).
    - Adjust capacities and schedules.
    - Manually reorder classes.
    - Override class status when needed.

The system runs as a single HTML file opened in a web browser and stores all data in memory for the duration of the session.

---

### 2. Logging In as a Regular User

1. Open the HTML file in a modern web browser.
2. At the top of the screen, locate the **User ID** input field.
3. Enter a name or identifier (for example, `alice01`).
4. Leave the **Admin Key** field empty.
5. Click the **“Set User / Role”** button.
6. The label on the right side of the bar will show:
    - `Current: alice01 (User)` or similar.
7. You are now acting as a regular user and can:
    - View, sort, and filter classes.
    - Create and cancel reservations according to the business rules.

You can change the active user at any time by entering another User ID and clicking **“Set User / Role”** again. The **“My Reservations”** panel will then display reservations for the newly selected user.

---

### 3. Logging In as an Admin

1. In the same top bar, enter your admin User ID (for example, `admin`) in the **User ID** field.
2. Enter the admin password in the **Admin Key** field (according to your deployment’s configuration).
3. Click **“Set User / Role”**.
4. If the credentials are correct:
    - The role label will show `Current: admin (Admin)`.
    - The **Admin Panel** will become visible below the main panels.
5. As an admin, you have both:
    - All regular user capabilities (view, sort, filter, reserve, cancel).
    - Additional admin functions to manage classes.

If your credentials are not correct, you will remain in **User** role and the Admin Panel will not be accessible.

---

### 4. Viewing, Sorting, and Filtering Classes

### 4.1 Available Classes Panel

The **Available Classes** panel (left side) shows the list of all gym classes. Each class card displays:

- **Title** – name of the class.
- **Type** – Strength, Cardio, Mind & Body, or Mobility.
- **Instructor** – the trainer’s name.
- **Time** – date and start time of the class.
- **Capacity / Remaining** – total seats and available seats.
- **Status** – one of:
    - **Available** – future class with remaining slots.
    - **Full** – future class with no remaining slots.
    - **Past** – class whose start time is in the past.

### 4.2 Sorting Classes

Above the panels, there is a **Sort** section with two controls:

- **Sort by**:
    - **Date/Time** – default and primary sorting field.
    - Possibly other fields such as Title.
- **Direction**:
    - **Ascending** – earliest classes first.
    - **Descending** – latest classes first.

To sort classes:

1. Choose the desired **Sort by** option.
2. Choose **Ascending** or **Descending**.
3. The list in the **Available Classes** panel updates to reflect the specified ordering, taking into account the current filters and search criteria.

### 4.3 Filtering and Searching

Next to the sorting controls, you will find:

- **Filter type**:
    - All
    - Strength
    - Cardio
    - Mind & Body
    - Mobility
- **Filter instructor**:
    - All
    - List of known instructors.
- **Search**:
    - A text input used to search by title keywords.

To filter:

1. Select a **Type** from the dropdown to see only classes of that type.
2. Select an **Instructor** to see only classes taught by that person.
3. Optionally, type a keyword into the **Search** field to restrict by title.
4. The class list will show only classes that match all active criteria.

Filters and search work together with sorting:

- If you change filters or search text, the list is re-filtered and then sorted.
- If you change sorting, the list is re-sorted using the currently active filter and search settings.

---

### 5. Reserving and Cancelling Classes (Regular Users)

### 5.1 Reserving a Class

To reserve a class:

1. Make sure you are logged in as a **User** (see Section 2).
2. In the **Available Classes** panel, locate a class you wish to attend.
3. Verify that:
    - Its **Status** is **Available**.
    - The class time is in the future.
4. Check that you:
    - Do not already have a reservation at the same date/time.
    - Have fewer than **3 future reservations**.
5. Click the **“Reserve”** button on the class card.

If the reservation is accepted:

- The class’s **Remaining** slot count decreases by 1.
- If the class becomes full, its status changes to **Full**.
- A new entry appears in the **My Reservations** panel.
- A success message is shown.

If the reservation cannot be accepted because of business rules (past class, full class, double booking, or exceeding the maximum number of future reservations), an error message is displayed and no changes are made.

### 5.2 Viewing “My Reservations”

The **My Reservations** panel (right side) shows all reservations for the current User ID. Each reservation card includes:

- Class title, type, instructor, and time.
- A status label:
    - **Past** – if the class has already ended.
    - **Starting soon** – if the class starts within the next hour.
    - **Upcoming** – for later future classes.
- A **“Cancel”** button if the reservation is eligible for cancellation.

Whenever you change the User ID, create a reservation, or cancel a reservation, this panel is refreshed.

### 5.3 Cancelling a Reservation

To cancel a reservation:

1. Ensure that you are logged in as the user who owns the reservation.
2. In the **My Reservations** panel, locate the reservation.
3. Check that:
    - The class has not started yet.
    - There is more than **1 hour** before the class starts.
4. Click the **“Cancel”** button.

If cancellation is allowed:

- The reservation is removed from your list.
- The corresponding class **Remaining** count increases by 1.
- The class status (Available/Full) is recalculated as needed.
- A success message is shown.
- The **Available Classes** and **My Reservations** panels are updated.

If cancellation is not allowed (past class or less than 1 hour before start), an error message is shown and the reservation remains active.

---

### 6. Admin Operations

> Admins must log in as described in Section 3.
> 

Once logged in as an admin, an **Admin Panel** becomes visible below the main panels.

### 6.1 Admin Panel Overview

The Admin Panel typically contains:

- A **Class Editor** section with fields:
    - Title
    - Type
    - Instructor
    - Date/Time
    - Capacity
    - Remaining / status override
- Buttons for:
    - **Create Class**
    - **Update Class**
    - **Delete Class**
    - **Clear** editor fields
- A **Class List & Manual Order** section showing a compact list of classes with controls to:
    - Load a class into the editor.
    - Move classes up or down to define a manual ordering.

### 6.2 Creating a Class

1. In the Admin Panel, open the **Class Editor**.
2. Enter:
    - **Title** – name of the new class.
    - **Type** – select from Strength / Cardio / Mind & Body / Mobility.
    - **Instructor** – trainer’s name.
    - **Date/Time** – planned start date and time.
    - **Capacity** – maximum number of participants.
    - **Remaining** – initial available slots (typically equal to capacity).
3. Click **“Create Class”**.
4. The new class appears:
    - In the **Admin Class List**.
    - In the **Available Classes** panel, according to the current sort and filter settings.

### 6.3 Loading and Editing a Class

1. In the **Admin Class List**, find the class you want to edit.
2. Click **“Load”** next to that class.
3. The class details populate the **Class Editor** fields.
4. Adjust values as needed:
    - Update title, type, instructor, date/time, capacity, or remaining slots.
5. Click **“Update Class”**.
6. The changes are applied to:
    - The internal class data.
    - The **Available Classes** panel.
    - The **My Reservations** panel (existing reservations show updated details).

Admins may also adjust remaining slots or override status for operational reasons (e.g., closing a class early).

### 6.4 Deleting a Class

1. Load the class you wish to delete into the editor (see 6.3).
2. Click **“Delete Class”**.
3. Confirm deletion if the system asks for confirmation (depending on implementation).
4. The class is removed from:
    - The internal data model.
    - The **Available Classes** panel.
    - The **Admin Class List**.
5. Any associated reservations are handled according to your policy (e.g., cancelled or removed).

### 6.5 Manually Reordering Classes

The **Class List & Manual Order** section shows each class with **Up** (`↑`) and **Down** (`↓`) controls.

To change the order:

1. Locate the class in the Admin Class List.
2. Click **↑** to move it one position up.
3. Click **↓** to move it one position down.
4. The manual order is applied to how classes are displayed (either directly or as an admin-specific view), combined with the current sorting configuration.

---

### 7. Expected Normal Behavior

Under normal operation, the system behaves as follows:

- Users must set a **User ID** before reserving or cancelling.
- **Sorting, filtering, and search** work together to shape a consistent view of classes:
    - Filters and search restrict which classes are shown.
    - Sorting determines their order.
- The **Available Classes** panel always reflects:
    - Correct status for each class.
    - Up-to-date remaining slot counts.
    - The combined effect of sort and filter controls.
- The **My Reservations** panel always shows:
    - Only the current user’s reservations.
    - Correct reservation status labels (Past / Starting Soon / Upcoming).
- Reservation rules are enforced:
    - No reservations for past or full classes.
    - No double booking at the same date/time.
    - Maximum of three future reservations per user.
- Cancellation rules are enforced:
    - No cancellations for past classes.
    - No cancellations within 1 hour of the class start.
- Permission rules are respected:
    - Only admins can access and use the Admin Panel.
    - Only admins can create, edit, delete, or reorder classes.
    - Regular users cannot modify class definitions.

Users and admins interact only through the provided UI elements. All feedback on operations (success or failure) is communicated via the message area and updates in the class and reservation panels.
