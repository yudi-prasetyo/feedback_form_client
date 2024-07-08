<template>
    <div class="feedback-form">
        <h1>How would you rate your satisfaction with our product?</h1>
        <form @submit.prevent="submitFeedback">
            <div class="star-rating">
                <label v-for="n in 5" :key="n">
                    <input type="radio" :value="n" v-model="rating" />
                    <i class="fas fa-star" :class="{ checked: n <= rating }"></i>
                    <div class="rating-number">{{ n }}</div>
                </label>
            </div>
            <div class="rating-labels">
                <span class="label">Very Dissatisfied</span>
                <span class="label">Very Satisfied</span>
            </div>
            <button type="submit">Submit</button>
        </form>
        <p v-if="message">{{ message }}</p>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    /**
     * Initializes the component's data.
     * 
     * @returns {Object} The initial data object.
     */
    data() {
        // Initialize the rating to null and the message to an empty string.
        return {
            rating: null, // The rating selected by the user.
            message: '' // The message to display after submitting feedback.
        };
    },
    methods: {
        /**
         * Submits the feedback to the server.
         * 
         * @returns {Promise} A promise that resolves when the feedback is submitted successfully.
         * @throws {Error} If an error occurs during the submission process.
         */
        async submitFeedback() {
            try {
                // Send a POST request to the server with the selected rating.
                await axios.post('http://localhost:8000/feedback/', {
                    rating: this.rating
                });

                // Update the message to indicate that the feedback was submitted successfully.
                this.message = 'Feedback submitted successfully!';
            } catch (error) {
                // If an error occurs, update the message to indicate that an error occurred.
                this.message = 'An error occurred. Please try again.';
            }
        }
    }
};
</script>

<style scoped>
.feedback-form {
    max-width: 400px;
    margin: 0 auto;
    padding: 1em;
    border: 1px solid #ccc;
    border-radius: 4px;
    text-align: center;
}

.star-rating {
    display: flex;
    justify-content: center;
    margin-bottom: 1em;
}

.star-rating label {
    cursor: pointer;
    text-align: center;
    margin: 0 5px;
}

.star-rating input[type="radio"] {
    display: none;
}

.star-rating i {
    font-size: 3em;
    color: #ddd;
    transition: color 0.2s;
}

.star-rating i.checked {
    color: #ffc107;
}

.rating-number {
    font-size: 1.2em;
    margin-top: 0.5em;
}

.rating-labels {
    display: flex;
    justify-content: space-between;
    margin-bottom: 1em;
}

.rating-labels .label {
    font-size: 1em;
    color: #555;
}

button {
    background: linear-gradient(135deg, #6e8efb, #a777e3);
    border: none;
    border-radius: 25px;
    color: white;
    font-size: 1em;
    padding: 10px 20px;
    cursor: pointer;
    transition: background 0.3s, transform 0.3s;
}

button:hover {
    background: linear-gradient(135deg, #a777e3, #6e8efb);
    transform: scale(1.05);
}

button:focus {
    outline: none;
    box-shadow: 0 0 0 3px rgba(110, 142, 251, 0.5);
}
</style>
