# Enums

The HeartZones API uses the following enums:

## Type
`Gender`

Used for assigning a `gender` to a user account.

Value | Name | Default
----- | ---- | -------
0 | None | true
1 | Male
2 | Female

## License
`License`

Used for assigning a `license` to a user account.

Value | Name | Default
----- | ---- | -------
0 | Active | true
1 | Pending
2 | Suspended

## Account Type
`type`

The user account's type.

Value | Name | Description
----- | ---- | -----------
0 | Super Admin | View and modify all users, external or internal. Cannot view Participant data
1 | Sub Admin | View and modify all users. Cannot edit other sub or super admins. Cannot view participant data
2 | Sales & Support | Only able to view license info and contact info. Cannot modify anything.
3 | District Admin | Can view, but not modify, Facility Admins who fall below them. Can schedule and modify classes/participants. Cannot view participant data.
4 | Facility Admin | Can view, but not modify, Instructors who fall below them. Can schedule and modify classes/participants. Cannot view participant data.
5 | Instructor | Can view and modify classes/participants, can view report data. No admin tab.

## CLASS TYPE
`type`

Value | Name
----- | ----
0 | Scheduled
1 | Impromptu
