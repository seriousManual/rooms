<style>
    div {
        width: 5rem;
        height: 5rem;
    }

    div.available {
        background-color: darkgreen;
    }

    div.middleCapacity {
        background-color: orange
    }

    div.capacityReached {
        background-color: red
    }

    .hasBookedThisRoom {
        
    }
</style>

<script>
    import reservationsState from './state/reservations'
    import userState from './state/user'

    export let data;

    function createReservation() {
        reservationsState.createReservation(data.day, data.roomName, $userState.name)
    }

    function cancelReservation() {
        reservationsState.cancelReservation(data.day, data.roomName, $userState.name)
    }
</script>

<div title={data.reservers.join(', ')} class='{data.state}'>
    {#if data.isBookable}
        <button on:click={createReservation}>
            ✔️
        </button>
    {:else if data.hasBookedThisRoom}
        <button on:click={cancelReservation}>
            ❌
        </button>
    {/if}
</div>