<script context="module">
  import get from 'lodash/get';
</script>

<script>
  export let fields;
  export let records;
</script>

<table border>
<thead>
  <tr>
  {#each Object.keys(fields) as field}
    <th>{field}</th>
  {/each}
  </tr>
</thead>
<tbody>
  {#each records as record}
    <tr>
    {#each Object.keys(fields) as field}
      <td>{get(record, field)}</td>
    {/each}
    </tr>
  {/each}
</tbody>
</table>
