# MySQL Database for issue tracker REST API

## Requirements

- One User can be assigned to multiple Bugs, but one Bug can be assigned to only one User. 
- One Bug can have multiple Comments, but one Comment can only belong to one Bug.
- One User can comment on multiple Bugs, but one Comment can only belong to one User.

## Technical Requirements
- Bugs and Comments have One to Many Relationship
- Users and Bugs have One to Many Relationship
- Users and Comments have One to Many Relationship
- Bugs and Comments have One to Many Relationship

## Database Schema

### Bugs Table
<table>
  <tbody>
    <tr>
      <th>Field Name</th>
      <th>Type</th>
      <th>Key</th>
    </tr>
    <tr>
      <td>ID</td>
      <td>int</td>
      <td>primary</td>
    </tr>
    <tr>
      <td>Title</td>
      <td>char</td>
      <td></td>
    </tr>
    <tr>
      <td>Body</td>
      <td>char</td>
      <td></td>
    </tr>
    <tr>
      <td>Status</td>
      <td>enum</td>
      <td></td>
    </tr>
    <tr>
      <td>AssignedUser</td>
      <td>int</td>
      <td>foreign</td>
    </tr>
  </tbody>
</table>


### Comments Table
<table>
  <tbody>
    <tr>
      <th>Field Name</th>
      <th>Type</th>
      <th>Key</th>
    </tr>
    <tr>
      <td>ID</td>
      <td>int</td>
      <td>primary</td>
    </tr>
    <tr>
      <td>Title</td>
      <td>char</td>
      <td></td>
    </tr>
    <tr>
      <td>Body</td>
      <td>char</td>
      <td></td>
    </tr>
    <tr>
      <td>Bug</td>
      <td>int</td>
      <td>foreign</td>
    </tr>
    <tr>
      <td>User</td>
      <td>int</td>
      <td>foreign</td>
    </tr>
  </tbody>
</table>


### Users Table
<table>
  <tbody>
    <tr>
      <th>Field Name</th>
      <th>Type</th>
      <th>Key</th>
    </tr>
    <tr>
      <td>ID</td>
      <td>int</td>
      <td>primary</td>
    </tr>
    <tr>
      <td>Name</td>
      <td>char</td>
      <td></td>
    </tr>
    <tr>
      <td>Email</td>
      <td>char</td>
      <td></td>
    </tr>
    <tr>
      <td>Password</td>
      <td>char</td>
      <td></td>
    </tr>
  </tbody>
</table>


___