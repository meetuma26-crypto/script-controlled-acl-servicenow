# Script-Controlled ACL – Restrict Record Access Based on Field Value

## Project Description

This project demonstrates how Script-Controlled Access Control Lists (ACLs) can be used in ServiceNow to restrict record access based on user roles and field values.

In this project, access to Institution Details records is controlled using the Branch field and custom user roles.

## Objective

The main objective of this project is to implement record-level security in ServiceNow using Access Control Lists (ACLs).

The project demonstrates:

- Read access
- Create access
- Write access
- Delete access
- Role-based access control
- Field-based record restriction

## User and Roles

### Test User

**User:** EEE User

### Custom Roles

- `bb1` – Read access
- `bb2` – Create access
- `bb3` – Write access
- `bb4` – Delete access

## Custom Table

### Institution Details

**Table Name:**

`u_institution_details`

### Fields

- Student Roll Number
- Student Name
- Faculty Name
- Branch
- Email
- Phone Number
- Description

## Branch Values

The Branch field contains:

- EEE
- ECE
- CSE

## Access Control Lists

### 1. READ ACL

**Operation:** Read

**Required Role:** `bb1`

**Data Condition:**

`Branch is EEE`

The READ ACL allows users with the `bb1` role to access EEE branch records.

Administrators have full access.

### READ ACL Script

```javascript
(function () {

    // Allow administrators full access
    if (gs.hasRole('admin')) {
        return true;
    }

    // Allow users with bb1 role
    if (gs.hasRole('bb1')) {
        return true;
    }

    // Deny other users
    return false;

})();
