<script>
import AddHouse from "./components/AddHouse.svelte";
import Modal from "./components/modal.svelte";

	let houses = [
			{
				id:1,
				type:"Bungalow",
				owner:"Unknown Developer",
				rooms:3,
				accessories:["WiFi","Heater"],
				ownership:"Rented"
			},
			{
				id:2,
				type:"Duplex",
				owner:"Michael Tyson",
				rooms:6,
				accessories:["WiFi","Heater"],
				ownership:"Fully Paid"
			},
			{
				id:3,
				type:"Storey building",
				owner:"Developers",
				rooms:13,
				accessories:["WiFi","Heater"],
				ownership:"Fully Paid"
			}
		];
		const handelClick = (id)=>{
			houses = houses.filter((house) => house.id != id);
			
		}
		let promo = true;
		let isModalVisible = false;

		const handleAddHouse =(e)=>{
			let house = e.detail;

			houses = [house, ...houses];
			// console.log(houses);
			

			isModalVisible = !isModalVisible;
		}
	</script>
	
	<main>
		<Modal  {isModalVisible} on:click={()=>{isModalVisible= !isModalVisible}} isPromo={promo}>
			<h2>Add A New House</h2>
			<AddHouse on:addHouse={handleAddHouse}/>
		</Modal>
			
			
			<h1>House2Lodge <p>Varities Houses to Lodge for the Weekend...</p></h1>
			
		<ul class="houses-list">
			{#each houses as house (house.id)}
			<li class="house">
				<div class="h3">
					<span>Owner:</span>
					<h3>{house.owner}</h3>
					 <span>{house.ownership} Apartment</span>
				</div>
				<div class="p">
					<b>{house.type}</b>
					<br>
					<span> ({house.rooms} rooms)</span>
					<br>
					<span>
						<b>House Accessories:</b>
						{#each house.accessories as accessory}
							{accessory + " "} 
						{/each}
					</span>
				</div>
				<button on:click={()=>handelClick(house.id)}>x</button>
			</li>
			{:else}
			<p>There are no houses here...</p>
		{/each}
		</ul>
		<div class="add-house" >
			<button on:click={()=>{isModalVisible= !isModalVisible}}>Add House</button>
		</div>
	</main>
	
	<style type="text/scss">
	main{
		text-align: center;
		padding: 5% 0;
		background: rgb(16, 2, 20);
		height: 100vh;
	}
	h1{
		color: #fff;
		font-family:'Comic Sans MS',cursive;
		font-size: 40px;
	}
	h1 p{
		padding: 0;
		margin: 0;
		font-size: 16px;
		font-family: sans-serif;
		font-weight: normal;
		font-style: italic;


	}
		.houses-list{
			list-style-type: none;
			max-width: 600px;
			margin: auto;
			
		}
		.house{
			display: flex;
			/* width: 100px; */
			width: 80%;
			background-color: rgb(97, 19, 133);
			color: #fff;
			padding: 10px 15px;
			margin: 2px;
			text-align: left;
		}
		.house:first-child{
			border-top-left-radius: 10px;
			border-top-right-radius: 10px;
		}
		.house:last-child{
			border-bottom-left-radius: 10px;
			border-bottom-right-radius: 10px;
		}
		.house .h3{
			width: 40%;
		}
		.house .h3 h3{
			padding: 0;
			margin: 0;
		}
		.house .p{
			width: 50%;
			
		}
		.house .p span{
			padding: 0;
			margin: 0;
		}
		.house button{
			color: red;
			border: 0;
			max-width: 30px;
			margin: auto;
			max-height: 20px;
			padding: 15px 10px;
			line-height: 0;
			text-align:center;
			border-radius: 50%;
			cursor: pointer;
			font-weight: bold;
			font-family: sans-serif;
		}
		.add-house{
			padding: 10px;
			margin: 5px;
			max-width: 250px;
			margin: auto;
		}
		.add-house button{
			border: none;
			padding: 15px 10px ;
			width: 100%;
			background: rgb(97, 19, 133);
			color:#fff;
			border-radius: 10px;
			font-size: 20px;
			
		}
	</style>