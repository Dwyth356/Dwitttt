# C.I.H.R.M. – Hotel Reservation Management Learning System

A PHP 8 + MySQL educational hotel operations simulator built from the supplied research specification. It is designed for local classroom demonstration and should be security-reviewed before public deployment.

## Requirements
- XAMPP (Apache + MySQL) or equivalent
- PHP 8.0+ with PDO MySQL enabled
- MySQL 5.7+ / MariaDB 10.4+
- Modern browser

## Installation (Windows / XAMPP)
1. Extract the `CIHRM` folder into `C:\xampp\htdocs\`.
2. Start **Apache** and **MySQL** in XAMPP Control Panel.
3. Open `http://localhost/phpmyadmin`.
4. Choose **Import**, select `CIHRM/database/cihrm.sql`, and execute it. The script creates the `cihrm` database and demo records.
5. Open `CIHRM/config/database.php`. The default XAMPP values are host `localhost`, database `cihrm`, user `root`, blank password. Change these if your local MySQL credentials differ.
6. Visit `http://localhost/CIHRM/`.

## Demo sign-ins
All demo accounts use password `password123`:
- Student: `student@cihrm.test`
- Instructor: `instructor@cihrm.test`
- Administrator: `admin@cihrm.test`

Change demo passwords before any use beyond a local classroom demo. Registration creates Student accounts only. Admin can create Instructor and Administrator accounts from User Management.

## Main workflows
- Student: register/sign in → add guest → create reservation → manage check-in/check-out → view billing → submit scenario activity.
- Instructor: create learning scenarios → review and grade student submissions → view reports.
- Administrator: add rooms → manage user roles/status → view activity logs.
- Housekeeping: mark rooms Clean, Dirty, or Maintenance in the room status tracker (the current screen shares room records; use database updates for status changes in this starter build).
- Billing: update discount/tax and simulation payment status; use Print for browser print.

## Important implementation notes
- The database preserves the core ERD entities: USER, GUEST, ROOM, RESERVATION, FOLIO, FOLIO_ITEM, ACTIVITY_LOG, SCENARIO, STUDENT_ASSESSMENT. Supporting fields are included for the simulator.
- Passwords are stored with PHP `password_hash` / verified with `password_verify`.
- Database statements use PDO prepared statements.
- Role checks are applied to protected modules and sensitive operations.
- Reservation creation checks room capacity and overlapping active reservations.
- Check-in marks a room Occupied; check-out marks it Available and Dirty.
- Billing and payment statuses are simulated only. No payment gateway or real-money transaction is present.

## Scope / limitations of this generated first build
This is a runnable functional foundation, not a claim that every research requirement is complete. The initial build includes authentication, role-based navigation, room and guest records, reservation creation/status transitions, folio calculations, learning scenarios, assessment submissions/review, user administration, activity logs, and summary reports. Advanced features still requiring implementation/testing include full edit flows for guests/reservations/rooms, scenario assignment workflows, rubric-based assessments, comprehensive exports (PDF/CSV), calendar/floor-plan views, fine-grained permissions, and automated integration tests. The housekeeping page currently presents the room inventory; use the room status form in a subsequent enhancement to make status changes directly available in the UI.
