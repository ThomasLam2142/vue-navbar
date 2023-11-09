<template>
    <div>
        <h1>Contact Us</h1>
        <form @submit.prevent="submitForm">
            <div>
                <label for="name">Name:</label>
                <input type="text" id="name" name="name" required>
            </div>

            <div>
                <label for="email">Email:</label>
                <input type="email" id="email" name="email" required>
            </div>

            <button type="submit">Send</button>
        </form>
    </div>
</template>

<script>
export default {
    name: 'ContactVue'
}
</script>

<style>
/* Add custom styles here */
</style>
