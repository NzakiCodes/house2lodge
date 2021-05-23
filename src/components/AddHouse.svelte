<script>
    import { createEventDispatcher } from 'svelte'
  let houseType;
  let houseOwner;
  let rooms;
  let accessories = [];
  let ownership;

  
const dispatch = createEventDispatcher();
  const handleAddHouse = () => {

    const house = {
        owner:houseOwner,
        type:houseType,
        rooms,
        accessories,
        ownership,
        id: Math.random()
    }

    dispatch("addHouse",house);

  };
</script>

<form on:submit|preventDefault={handleAddHouse}>
  <input required type="text" placeholder="House Type" bind:value={houseType} />
  <input required type="text" placeholder="House Owner" bind:value={houseOwner} />
  <input required type="number" bind:value={rooms} placeholder="Number of Rooms">
  <p>House Accessories:</p>
  <label>
    Air Conditioner
    <input type="checkbox" bind:group={accessories} value="AC" />
  </label>
  <label>
    Room Heater
    <input type="checkbox" bind:group={accessories} value="heater" />
  </label>
  <label>
    WiFi:
    <input type="checkbox" bind:group={accessories} value="wifi" />
  </label>
  <label>
    Ownership
    <select bind:value={ownership}>
      <option value="FullyPaid">Fully Paid</option>
      <option value="Rented">Rented</option>
    </select>
  
  </label>
  <button type="submit">Add House.</button>
</form>
