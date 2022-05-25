<script>
  import Table from "sveltestrap/src/Table.svelte";
  import { onMount } from "svelte";

  let users = [];

  onMount(async () => {
    const res = await fetch(`https://jsonplaceholder.typicode.com/users`);
    users = await res.json();

    console.log(users);
  });

  const tableHeading = ["ID", "Name", "Username", "email"];

  // const tableHeading = ["#", "First Name", "Last-Name", "Username"];
  // const tableData = [
  //   { SNo: "1", firstName: "Mark", lastName: "Otto", userName: "@mdo" },
  //   { SNo: "2", firstName: "Jacob", lastName: "Thornton", userName: "@fat" },
  //   { SNo: "3", firstName: "Larry", lastName: "the Bird", userName: "@twitter" }
  // ];

  
</script>

<Table bordered responsive>
  <thead>
    <tr>
      {#each tableHeading as heading}
        <th>{heading}</th>
      {/each}
    </tr>
  </thead>
  <tbody>

    {#each users as user}
      <tr>
        <th scope="row">{user.id}</th>
        <td>{user.name}</td>
        <td>{user.username}</td>
        <td>{user.email}</td>
      </tr>
      {:else}
      <!-- this block renders when users.length === 0 -->
       <p>loading...</p>
    {/each}
  </tbody>
</Table>
