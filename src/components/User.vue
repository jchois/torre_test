<template>
    <div class="column is-12-mobile is-4-desktop is-4-tablet">
        <div class="card">
        <div class="card-header p-4 flex-direction is-justify-content-center">
            <img
            v-bind:src="userName.pictureThumbnail"
            v-bind:alt="userName.name"
            />
        </div>

        <div class="card-container p-4 has-text-centered">
            <span class="title is-size-6"
            >Name: <span class="is-size-6 has-text-weight-normal">{{ userName.name }}</span></span
            >
            <br />
            <span class="title is-size-6"
            >Profession:
            <span class="is-size-6 has-text-weight-normal">{{
                userName.professionalHeadline
            }}</span></span
            >
            <!-- <button class="button is-success is-rounded is-small" @click="showMore(character.id)">Ver mas</button> -->
        </div>
        </div>
    </div>
</template>

<script>
export default {
    props: ["userName"]
}
</script>

<style>

</style>