<template>
  <div class="contact-section">
    <h2 class="section-title">Contact Me</h2>
    <form @submit.prevent="handleSubmit" class="contact-form">
      <div class="form-group">
        <label for="name">Name</label>
        <input
          type="text"
          id="name"
          v-model="formData.name"
          :class="{ 'error': errors.name }"
          @blur="validateField('name')"
        >
        <span class="error-message" v-if="errors.name">{{ errors.name }}</span>
      </div>

      <div class="form-group">
        <label for="phone">Phone Number</label>
        <input
          type="tel"
          id="phone"
          v-model="formData.phone"
          :class="{ 'error': errors.phone }"
          @blur="validateField('phone')"
        >
        <span class="error-message" v-if="errors.phone">{{ errors.phone }}</span>
      </div>

      <div class="form-group">
        <label for="email">Email</label>
        <input
          type="email"
          id="email"
          v-model="formData.email"
          :class="{ 'error': errors.email }"
          @blur="validateField('email')"
        >
        <span class="error-message" v-if="errors.email">{{ errors.email }}</span>
      </div>

      <div class="form-group">
        <label for="message">Message</label>
        <textarea
          id="message"
          v-model="formData.message"
          :class="{ 'error': errors.message }"
          @blur="validateField('message')"
          rows="5"
        ></textarea>
        <span class="error-message" v-if="errors.message">{{ errors.message }}</span>
      </div>

      <button type="submit" class="submit-btn" :disabled="isSubmitting">
        {{ isSubmitting ? 'Sending...' : 'Send Message' }}
      </button>

      <div class="form-status" v-if="formStatus">
        <p :class="formStatus.type">{{ formStatus.message }}</p>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: 'ContactSection',
  data() {
    return {
      formData: {
        name: '',
        phone: '',
        email: '',
        message: ''
      },
      errors: {
        name: '',
        phone: '',
        email: '',
        message: ''
      },
      isSubmitting: false,
      formStatus: null
    }
  },
  methods: {
    validateField(field) {
      this.errors[field] = ''

      switch (field) {
        case 'name':
          if (!this.formData.name) {
            this.errors.name = 'Name is required'
          } else if (this.formData.name.length < 2) {
            this.errors.name = 'Name must be at least 2 characters long'
          }
          break

        case 'phone':
          // eslint-disable-next-line no-case-declarations
          const phoneRegex = /^[+]?[(]?[0-9]{3}[)]?[-\s.]?[0-9]{3}[-\s.]?[0-9]{4,6}$/
          if (!this.formData.phone) {
            this.errors.phone = 'Phone number is required'
          } else if (!phoneRegex.test(this.formData.phone)) {
            this.errors.phone = 'Please enter a valid phone number'
          }
          break

        case 'email':
            // eslint-disable-next-line no-case-declarations
            let emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/
          if (!this.formData.email) {
            this.errors.email = 'Email is required'
          } else if (!emailRegex.test(this.formData.email)) {
            this.errors.email = 'Please enter a valid email address'
          }
          break

        case 'message':
          if (!this.formData.message) {
            this.errors.message = 'Message is required'
          } else if (this.formData.message.length < 10) {
            this.errors.message = 'Message must be at least 10 characters long'
          }
          break
      }
    },

    validateForm() {
      let isValid = true
      Object.keys(this.formData).forEach(field => {
        this.validateField(field)
        if (this.errors[field]) {
          isValid = false
        }
      })
      return isValid
    },

    async handleSubmit() {
      if (!this.validateForm()) {
        return
      }

      this.isSubmitting = true
      this.formStatus = null

      try {
        // Replace this with your actual email sending logic
        // For example, using a backend API endpoint
        await new Promise(resolve => setTimeout(resolve, 1000)) // Simulated API call
        
        // For demonstration, we'll just log the data
        console.log('Form submitted:', this.formData)
        
        this.formStatus = {
          type: 'success',
          message: 'Message sent successfully!'
        }
        
        // Reset form
        Object.keys(this.formData).forEach(key => this.formData[key] = '')
      } catch (error) {
        this.formStatus = {
          type: 'error',
          message: 'Failed to send message. Please try again.'
        }
      } finally {
        this.isSubmitting = false
      }
    }
  }
}
</script>

<style lang="scss" scoped>
.contact-section {
  padding: 4rem 2rem;
  max-width: 800px;
  margin: 0 auto;
}

.section-title {
  font-size: 2.5rem;
  margin-bottom: 3rem;
  text-align: center;
  color: var(--text-light);
  
  .dark & {
    color: var(--text-dark);
  }
}

.contact-form {
  background: var(--background-light);
  padding: 2rem;
  border-radius: 15px;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
  
  .dark & {
    background: var(--background-dark);
  }
}

.form-group {
  margin-bottom: 1.5rem;
  
  label {
    display: block;
    margin-bottom: 0.5rem;
    color: var(--text-light);
    font-weight: 500;
    
    .dark & {
      color: var(--text-dark);
    }
  }
  
  input,
  textarea {
    width: 100%;
    padding: 0.8rem;
    border: 2px solid #ccc;
    border-radius: 8px;
    background: #fff;
    color: #333;
    transition: all 0.3s ease;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    
    &:focus {
      outline: none;
      border-color: var(--primary-light);
      box-shadow: 0 2px 8px rgba(0, 0, 0, 0.15);
    }
    
    &.error {
      border-color: #ff4444;
    }
    
    .dark & {
      background: #2a2a2a;
      color: #fff;
      border-color: #444;
      
      &:focus {
        border-color: var(--primary-dark);
        box-shadow: 0 2px 8px rgba(0, 0, 0, 0.3);
      }
    }
  }
}


.error-message {
  display: block;
  color: #ff4444;
  font-size: 0.875rem;
  margin-top: 0.5rem;
}

.submit-btn {
  width: 100%;
  padding: 1rem;
  background: var(--primary-light);
  color: white;
  border: none;
  border-radius: 8px;
  font-size: 1rem;
  font-weight: 600;
  cursor: pointer;
  transition: background-color 0.3s ease;
  
  &:hover:not(:disabled) {
    background: var(--primary-light-hover);
  }
  
  &:disabled {
    opacity: 0.7;
    cursor: not-allowed;
  }
  
  .dark & {
    background: var(--primary-dark);
    
    &:hover:not(:disabled) {
      background: var(--primary-dark-hover);
    }
  }
}

.form-status {
  margin-top: 1rem;
  text-align: center;
  
  p {
    padding: 1rem;
    border-radius: 8px;
    
    &.success {
      background: #d4edda;
      color: #155724;
    }
    
    &.error {
      background: #f8d7da;
      color: #721c24;
    }
  }
}
</style>