<script>
export default {
    data() {
        return {
            name: '',
            job: '',
            bio: '',
            imageUrl: '/assets/head1.jpg',
            bgColor: '#333',
            textColor: '#fff',
            themes: [
                { bg: '#333', text: '#fff' },
                { bg: '#fff', text: '#000' },
                { bg: '#39ff14', text: '#000' }
            ],
            currentThemeIndex: 0
        }
    },
    methods: {
        cycleTheme() {
            this.currentThemeIndex = (this.currentThemeIndex + 1) % this.themes.length
            this.bgColor = this.themes[this.currentThemeIndex].bg
            this.textColor = this.themes[this.currentThemeIndex].text
        }
    }
}
</script>

<template>
    <div class="container">
        <div class="form-section">
            <h2>Customize Profile</h2>
            <label>Name:</label><br>
            <input id="name" v-model="name" placeholder="Your Name"><br><br>
            <label>Job Title:</label><br>
            <input id="job" v-model="job" placeholder="Web Developer"><br><br>
            <label>Bio:</label><br>
            <textarea id="bio" v-model="bio" rows="3" placeholder="A short bio..."></textarea><br><br>
            <label>Profile Image URL:</label><br>
            <input id="imageUrl" v-model="imageUrl" placeholder="https://example.com/me.jpg"><br><br>
            <label>Theme Presets:</label><br>
            <button class="theme-button" @click="cycleTheme">Cycle theme</button>
        </div>
        <div class="preview-section">
            <h2>Live Preview</h2>
            <div class="preview-card" :style="{ backgroundColor: bgColor, color: textColor }">
                <img :src="imageUrl" class="preview-img">
                <h3>{{ name || 'Your Name' }}</h3>
                <h4>{{ job || 'Job Title' }}</h4>
                <p>{{ bio || 'Write something about yourself...' }}</p>
            </div>
        </div>
    </div>
</template>
