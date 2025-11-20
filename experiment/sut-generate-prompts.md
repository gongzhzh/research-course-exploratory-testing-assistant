You are a senior software systems generator and your task is to produce:

1. a buggy demo web system,
2. a correct requirements specification document,
3. a correct user manual.

Follow the structured instructions below exactly.

========================================================

# 1. ROLE

Act as:

- A software architect,
- A full-stack engineer,
- A requirements analyst,
- A technical writer.

Your tone must be: clear, professional, technical, and specification-driven.

========================================================

# 2. OVERALL GOAL

Generate **three artifacts**:

## Artifact A — Buggy Web System (HTML + JS)

A fully executable single-file browser application implementing an extended **Gym Class Reservation System** with a permission model.

The implementation MUST contain intentional logic bugs, including bugs in:

- reservation rules
- cancellation rules
- admin permission system
- sorting
- filtering
- UI consistency
- state management
- any additional bugs if helpful

## Artifact B — Requirements Specification (Correct System Only)

A clean, correct formal SRS describing the intended correct system **WITHOUT mentioning any bugs**:

- fully consistent specifications
- correct rules for reservation, cancellation, sorting, filtering, admin permissions

## Artifact C — User Manual

A normal user manual describing:

- how regular users operate the system
- how admins operate the system (edit, sort courses)
- how sorting, filtering, linking operations work
- how to log in as admin

⚠ IMPORTANT:
Artifacts B and C MUST NOT mention bugs, faulty behavior, or inconsistencies.

========================================================

# 3. SYSTEM REQUIREMENTS (Correct Behavior Target)

You must generate code and documents that assume the intended correct system satisfies:

### 3.1 Core Features

- Users identify themselves with a text field.
- Users can view available gym classes.
- Each class has:
    - title
    - type (Strength, Cardio, Mind & Body, Mobility)
    - instructor
    - date/time
    - capacity
    - remaining slots
    - status badge (Available / Full / Past)

### 3.2 Sorting Feature

- Users can sort classes **by date/time**.
- Sorting order (ascending/descending) must be selectable.

### 3.3 Filtering Feature

Users can filter classes by:

- Type
- Instructor
- (Optional) Search keywords

### 3.4 Sort + Filter Linkage

Sorting and filtering must:

- **work together**,
- maintain each other's state,
- produce a consistent UI output.

### 3.5 Permission System

There are **two roles**:

### User Role

- View classes
- Reserve classes
- Cancel own reservations
- Use sort/filter/search

Users CANNOT:

- edit classes
- modify schedule
- reorder classes manually
- change capacity
- modify instructors/types

### Admin Role

Admin can additionally:

- edit class info: title, type, instructor, capacity, date/time
- manually reorder classes (admin-defined sort)
- create/delete classes
- override status
- bypass filters if needed

### 3.6 Reservation Business Rules (Ground Truth)

- Users cannot reserve:
    - past classes
    - full classes
    - two classes at the same date/time
    - more than 3 future reservations
- Users cannot cancel:
    - past reservations
    - reservations within 1 hour before start time

### 3.7 UI Requirements

The system contains:

- “Available Classes” panel
- “My Reservations” panel
- “Admin Panel” (visible only to admin)
- Sorting UI, filtering UI, search UI
- Success/error message UI

========================================================

# 4. BUG INJECTION REQUIREMENTS

Artifact A (the HTML/JS implementation) MUST include intentional logic bugs.

Minimum required bugs (must implement ALL):

### Reservation Bugs

1. Overbooking allowed → capacity rule ignored
2. Past classes can still be reserved
3. Double booking allowed (same time)
4. Unlimited future reservations allowed

### Cancellation Bugs

1. Cancelling past classes allowed
2. Cancelling within 1 hour allowed

### Admin Permission Bugs

1. Non-admin users can sometimes edit classes
2. Admin panel may partially appear for normal users
3. Permission checks missing or inconsistent

### Sorting + Filtering Bugs

1. Sorting sometimes does not update UI
2. Filtering and sorting produce inconsistent results
3. Filtering can break sorting order
4. Some filter parameters ignored

### UI Bugs

1. Slot count not refreshed after cancellation
2. Admin edit UI updates only partially
3. Some UI views show outdated state

### Additional Bugs (optional)

- duplicate class IDs
- wrong status labels
- inconsistent time display
- incorrect capacity display
- search not case-insensitive
- filter excludes valid items

**DO NOT MENTION ANY BUGS** in Artifact B or C.

========================================================

# 5. OUTPUT STRUCTURE (STRICT)

Your output must contain ALL THREE artifacts in EXACT order:

---

## ARTIFACT A — Buggy Web System (HTML File)

Provide a complete, single-file HTML+JS application implementing:

- reservation system
- sorting
- filtering
- linked sort/filter logic
- admin panel with editing capabilities
- AND intentional bugs

It must run directly when opened in a browser.

---

## ARTIFACT B — Requirements Specification (Correct System)

A formal SRS including:

1. Overview
2. Actors
3. Functional Requirements
4. Business Rules
5. Non-Functional Requirements
6. UI Requirements
7. Permission Model
8. Constraints
9. Glossary

Must describe the intended perfect system.

---

## ARTIFACT C — User Manual

Include:

1. System purpose
2. How to log in as user
3. How to log in as admin
4. How to view/sort/filter classes
5. How to reserve and cancel classes
6. How admin edits classes
7. Expected normal behavior

**No bug hints allowed.**

========================================================

# 6. STYLE REQUIREMENTS

- Use clear headings
- Use bullet lists
- Use neutral technical tone
- Keep code readable and commented
- Write documentation in English

========================================================

# 7. WHEN READY

Immediately produce all three artifacts.
