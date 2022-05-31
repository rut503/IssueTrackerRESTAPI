# REST API design for an issue tracker

## Bug

<table>
  <tbody>
    <tr>
      <th>Endpoint</th>
      <th>POST</th>
      <th>GET</th>
      <th>PUT</th>
      <th>DELETE</th>
    </tr>
    <tr>
      <td><code>/v1/bugs</code></td>
      <td>Create a bug</td>
      <td>View all bugs</td>
      <td>N/A</td>
      <td>N/A</td>
    </tr>
    <tr>
      <td><code>/v1/bugs/{id}</code></td>
      <td>N/A</td>
      <td>View a specific bug</td>
      <td>
        <ul>
          <li>Edit a bug</li>
          <li>Mark a bug as "resolved"</li>
          <li>Mark a bug as "unresolved"</li>
          <li>Assign the bug to a user</li>
        </ul>
      </td>
      <td>Delete a bug</td>
    </tr>
    <tr>
      <td><code>`/v1/bugs?status={resolved/unresolved}`</code></td>
      <td>N/A</td>
      <td>View all bugs marked as "resolved"</td>
      <td>N/A</td>
      <td>N/A</td>
    </tr>
  </tbody>
</table>

## Comment

<table>
  <tbody>
    <tr>
      <th>Endpoint</th>
      <th>POST</th>
      <th>GET</th>
      <th>PUT</th>
      <th>DELETE</th>
    </tr>
    <tr>
      <td><code>`/v1/comments/{id}`</code></td>
      <td>N/A</td>
      <td>N/A</td>
      <td>N/A</td>
      <td>Delete a comment from a bug</td>
    </tr>
    <tr>
      <td><code>`/v1/comments`</code></td>
      <td>Create a comment on a bug</td>
      <td>N/A</td>
      <td>N/A</td>
      <td>N/A</td>
    </tr>
  </tbody>
</table>

___