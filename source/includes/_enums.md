# Enums

The HeartZones API uses the following enums:

## Type
`gender`

Used for assigning a `gender` to a user account.

Value | Name | Default
----- | ---- | -------
0 | None | true
1 | Male
2 | Female

## License
`license`

Used for assigning a `license` to a user account.

Value | Name | Default
----- | ---- | -------
0 | Active |
1 | Pending | true
2 | Suspended

## Roles
`roles`

The user assigned roles. Users can have more than one role and most endpoints are authorized as a "minimum required role"

Value | Name | Description
----- | ---- | -----------
6 | Super Admin | View and modify all users, external or internal. Cannot view Participant data
5 | Sub Admin | View and modify all users. Cannot edit other sub or super admins. Cannot view participant data
4 | Sales & Support | Only able to view license info and contact info. Cannot modify anything.
3 | District Admin | Can view, but not modify, Facility Admins who fall below them. Can schedule and modify classes/participants. Cannot view participant data.
2 | Facility Admin | Can view, but not modify, Instructors who fall below them. Can schedule and modify classes/participants. Cannot view participant data.
1 | Instructor | Can view and modify classes/participants, can view report data. No admin tab.
0 | Participant | Can only view their own data.

## CLASS TYPE
`type`

Value | Name
----- | ----
0 | Scheduled
1 | Impromptu

## SENSOR TYPES
`type`

Value | Name
----- | ----
0 | Heart Rate
1 | Power
2 | Cadence
3 | Step
4 | Speed & Cadence
5 | FIT
